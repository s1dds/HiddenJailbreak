ARCHS := arm64 arm64e
TARGET := iphone:16.5:15.0

include $(THEOS)/makefiles/common.mk

ifeq ($(THEOS_PACKAGE_SCHEME),rootless)
	PACKAGE_BUILDNAME := rootless
else
	PACKAGE_BUILDNAME := rootful
endif

TWEAK_NAME = HiddenJailbreak

HiddenJailbreakCore= $(wildcard Core/*.m)

$(TWEAK_NAME)_FILES = $(HiddenJailbreakCore) Tweak.x
$(TWEAK_NAME)_EXTRA_FRAMEWORKS = Cephei
$(TWEAK_NAME)_PRIVATE_FRAMEWORKS = AppSupport
$(TWEAK_NAME)_CFLAGS = -fobjc-arc -DHiddenJailbreak="_$(shell git describe --always)"

include $(THEOS_MAKE_PATH)/tweak.mk

after-install::
	install.exec "killall -9 SpringBoard"
SUBPROJECTS += HiddenJailbreakPreferences

include $(THEOS_MAKE_PATH)/aggregate.mk
