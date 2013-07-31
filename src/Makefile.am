include $(top_srcdir)/support/automake/noweb.am
include $(top_srcdir)/support/automake/guile.am

.SECONDARY:

NOWEAVE_FLAGS = -n -delay
BUILT_SOURCES = $(NOWEB_BUILT_FILES) logging.c.x 
CLEANFILES = $(NOWEB_CLEANFILES) logging.c.x 

WARN_NOTANGLE = $(top_builddir)/bin/warn-notangle

dist-hook:
	cp $(distdir)/*.pdf $(top_distdir)

NOWEB_INCLUDES = $(nowebdir)/boiler-plate.nw

NOWEB_DOCS = logging.pdf
NOWEB_FILES = logging.nw
NOWEB_PRODUCTS = logging.c logging.h scm-logging.c scm-logging.h logging.scm
EXTRA_DIST = $(NOWEB_DOCS) $(NOWEB_EXTRA_DIST)

logging.o : logging.c.x

scm-logging.h scm-logging.c : logging.nw $(NOWEB_INCLUDES)
	$(AM_V_GEN)	$(warn_notangle) -o $@ $(WARN_NOTANGLE_LISP_FLAGS) -- $(NOTANGLE_LISP_FLAGS) -R"file:$@" $^


check_PROGRAMS = 

TESTS = 
TEST_EXTENSIONS = .scm 
SCM_LOG_COMPILER = $(ENV) guile 

lib_LTLIBRARIES = libguile-logging.la

guilemoduledir = $(prefix)/share/guile/site/
dist_guilemodule_DATA = logging.scm

AM_CFLAGS  = $(GUILE_CFLAGS)
# hello_world_test_c_LDADD   = $(GUILE_LIBS) libguile-logging.la
# hello_world_test_c_LDFLAGS = $(GUILE_LDFLAGS)
# hello_world_test_c_SOURCES = logging-test.c

libguile_logging_la_LIBADD  = $(GUILE_LIBS)
libguile_logging_la_SOURCES = logging.c scm-logging.c
include_HEADERS = logging.h 

MAINTAINERCLEANFILES = Makefile.in config.h.in 
