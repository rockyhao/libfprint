examples = [ 'verify_live', 'enroll', 'verify', 'img_capture' ]
foreach example: examples
    executable(example,
               example + '.c',
               dependencies: libfprint_dep,
               include_directories: [
                 root_inc,
               ],
               c_args: common_cflags)
endforeach

executable('cpp-test',
           'cpp-test.cpp',
           dependencies: libfprint_dep,
           include_directories: [
             root_inc,
           ],
           c_args: common_cflags)

if get_option('x11-examples')
    executable('img_capture_continuous',
               'img_capture_continuous.c',
               dependencies: [ libfprint_dep, xv_dep, x11_dep ],
               include_directories: [
                 root_inc,
               ],
               c_args: common_cflags)
endif

if get_option('gtk-examples')
    gtk_test_resources = gnome.compile_resources('gtk-test-resources', 'gtk-libfprint-test.gresource.xml',
                                                 source_dir : '.',
                                                 c_name : 'gtk_test')

    executable('gtk-libfprint-test',
               [ 'gtk-libfprint-test.c', 'loop.c', 'loop.h', gtk_test_resources ],
               dependencies: [ libfprint_dep, gtk_dep ],
               include_directories: [
                 root_inc,
               ],
               c_args: [ common_cflags,
                         '-DPACKAGE_VERSION="' + meson.project_version() + '"' ]
               )
endif
