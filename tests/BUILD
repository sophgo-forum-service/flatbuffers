package(
    default_visibility = ["//visibility:private"],
)

# Test binary.
cc_test(
    name = "flatbuffers_test",
    testonly = 1,
    srcs = [
        "evolution_test/evolution_v1_generated.h",
        "evolution_test/evolution_v2_generated.h",
        "namespace_test/namespace_test1_generated.h",
        "namespace_test/namespace_test2_generated.h",
        "native_type_test_impl.cpp",
        "native_type_test_impl.h",
        "test.cpp",
        "test_assert.cpp",
        "test_assert.h",
        "test_builder.cpp",
        "test_builder.h",
        "union_vector/union_vector_generated.h",
    ],
    copts = [
        "-DFLATBUFFERS_TRACK_VERIFIER_BUFFER_SIZE",
        "-DBAZEL_TEST_DATA_PATH",
    ],
    data = [
        ":arrays_test.bfbs",
        ":arrays_test.fbs",
        ":arrays_test.golden",
        ":evolution_test/evolution_v1.fbs",
        ":evolution_test/evolution_v1.json",
        ":evolution_test/evolution_v2.fbs",
        ":evolution_test/evolution_v2.json",
        ":include_test/include_test1.fbs",
        ":include_test/sub/include_test2.fbs",
        ":monster_extra.fbs",
        ":monster_test.bfbs",
        ":monster_test.fbs",
        ":monsterdata_extra.json",
        ":monsterdata_test.golden",
        ":monsterdata_test.json",
        ":native_type_test.fbs",
        ":prototest/imported.proto",
        ":prototest/test.golden",
        ":prototest/test.proto",
        ":prototest/test_union.golden",
        ":unicode_test.json",
        ":union_vector/union_vector.fbs",
        ":union_vector/union_vector.json",
    ],
    includes = [
        "",
        "include/",
    ],
    deps = [
        ":arrays_test_cc_fbs",
        ":monster_extra_cc_fbs",
        ":monster_test_cc_fbs",
        ":native_type_test_cc_fbs",
        "//:flatbuffers",
    ],
)

# Test bzl rules
load("//:build_defs.bzl", "flatbuffer_cc_library")

flatbuffer_cc_library(
    name = "monster_test_cc_fbs",
    srcs = ["monster_test.fbs"],
    include_paths = ["tests/include_test"],
    includes = [
        "include_test/include_test1.fbs",
        "include_test/sub/include_test2.fbs",
    ],
)

flatbuffer_cc_library(
    name = "monster_extra_cc_fbs",
    srcs = ["monster_extra.fbs"],
)

flatbuffer_cc_library(
    name = "arrays_test_cc_fbs",
    srcs = ["arrays_test.fbs"],
    flatc_args = [
        "--gen-object-api",
        "--gen-compare",
        "--no-includes",
        "--gen-mutable",
        "--reflect-names",
        "--cpp-ptr-type flatbuffers::unique_ptr",
        "--scoped-enums",
    ],
)

flatbuffer_cc_library(
    name = "native_type_test_cc_fbs",
    srcs = ["native_type_test.fbs"],
    flatc_args = [
        "--gen-object-api",
        "--gen-mutable",
        "--cpp-ptr-type flatbuffers::unique_ptr",
    ],
)