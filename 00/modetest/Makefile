#CFLAGS += -Wall -Werror
#LDFLAGS += -avoid-version -module -shared -export-dynamic

define all-c-files-under
$(patsubst ./%,%, \
  $(shell find -L $(1) -name "*.c" -and -not -name ".*") \
 )
endef

OUT:=$(shell pwd)
$(shell mkdir -p $(OUT))

TARGET = modetest
all: $(OUT)/$(TARGET)

SOURCES = $(call all-c-files-under,.)

CINCLUDES += -I . -I include -I include/util -I include/drm
LIBS += -ldrm -lpthread

$(OUT)/$(TARGET): $(SOURCES)
	$(CC) $(SOURCES) -o $@ \
		$(CFLAGS) $(CPPFLAGS) $(LDFLAGS) $(CINCLUDES) $(LIBS)
