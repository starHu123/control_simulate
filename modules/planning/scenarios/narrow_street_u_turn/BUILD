load("@rules_cc//cc:defs.bzl", "cc_library", "cc_test")
load("//tools/platform:build_defs.bzl", "if_gpu")
load("//tools:cpplint.bzl", "cpplint")

package(default_visibility = ["//visibility:public"])

cc_library(
    name = "narrow_street_u_turn",
    copts = ["-DMODULE_NAME=\\\"planning\\\""],
    deps = [
        ":narrow_street_u_turn_scenario",
    ],
)

cc_library(
    name = "narrow_street_u_turn_scenario",
    srcs = ["narrow_street_u_turn_scenario.cc"],
    hdrs = ["narrow_street_u_turn_scenario.h"],
    copts = ["-DMODULE_NAME=\\\"planning\\\""],
    deps = [
        "//cyber/common:log",
        "//modules/planning/proto:planning_cc_proto",
        "//modules/planning/scenarios:scenario",
    ],
)

cc_test(
    name = "narrow_street_u_turn_scenario_test",
    size = "small",
    srcs = ["narrow_street_u_turn_scenario_test.cc"],
    data = [
        "//modules/planning:planning_conf",
    ],
    linkopts = ["-lgomp"],
    deps = [
        ":narrow_street_u_turn",
        "@com_google_googletest//:gtest_main",
    ] + if_gpu(["@local_config_cuda//cuda:cudart"]),
)

cpplint()
