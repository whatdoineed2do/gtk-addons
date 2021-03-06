AC_PREREQ(2.64)
AC_INIT([eog-plugin-exif-rating-raw-viewer], [m4_esyscmd([git describe --tags --dirty --always | tr -d '\n'])], [https://github.com/whatdoineed2do/eog-plugin-exif-rating-raw-viewer/issues], [https://github.com/whatdoineed2do/eog-plugin-exif-rating-raw-viewer], [whatdoineed2do@nospam-github.com])

AM_INIT_AUTOMAKE([dist-bzip2 no-dist-gzip])
AC_CONFIG_MACRO_DIRS([m4])
m4_ifdef([AM_SILENT_RULES], [AM_SILENT_RULES([yes])])
AC_CONFIG_SRCDIR([src])
AC_CONFIG_HEADERS([config.h])

AC_PROG_CC
AC_PROG_CXX
AM_PROG_CC_C_O
AC_HEADER_STDC
AC_PROG_INSTALL
AC_PROG_LIBTOOL
PKG_PROG_PKG_CONFIG

LIBEXIV2_RATINGS_SO_VERSION = 1.3.2
LIBEXIV2_PIXBUF_LOADER_SO_VERSION = 1.3.2

PKG_CHECK_MODULES(EOG,         [eog             >= 3.24.1])
PKG_CHECK_VAR([EOG_PLUGINS_DIR],[eog],[pluginsdir])

PKG_CHECK_MODULES(IMAGEMAGICK, [Magick++        >= 6.9.9])
PKG_CHECK_MODULES(EXIV,        [exiv2           >= 0.25])

PKG_CHECK_MODULES(GDKPIXBUF,   [gdk-pixbuf-2.0  >= 2.36.9])
PKG_CHECK_VAR([GDKPIXBUF_MODULES_DIR],[gdk-pixbuf-2.0],[gdk_pixbuf_moduledir])
PKG_CHECK_VAR([GDKPIXBUF_LOADER_CACHE],[gdk-pixbuf-2.0],[gdk_pixbuf_cache_file])

PKG_CHECK_MODULES(PEAS,        [libpeas-1.0     >= 1.20.0])

AC_ARG_ENABLE([debug-code],
	[AS_HELP_STRING([--enable-debug],
	[enable debug (default is no)])],
	[no_debug=false],
	[no_debug=true])
if test "$no_debug" = true; then
        building_debug=no
        AC_DEFINE(NDEBUG,1,[debug code])
else
        building_debug=yes
        AC_DEFINE(DEBUG,1,[debug code])
fi


AC_OUTPUT([
Makefile
src/Makefile
src/eog-plugin/Makefile
src/gdk-pixbuf/Makefile
tests/Makefile
])
