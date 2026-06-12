---
title: "Overlay doesn't work (Ati fglrx drivers)"
date: 2006-08-16
forum: Multimedia &amp; Video
---

### Post by Dryer Lint on 2006-08-16
Running any program that tries to use overlay (like many emulators, AdvanceMAME/MESS, Generator and some games, too) it will result in this error:

```
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Value in failed request:  0x76
  Serial number of failed request:  25
  Current serial number in output stream:  26
```

This is my gfx card device section from xorg.conf:

```
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "OverlayOnCRTC2" "0"
	Option	    "Capabilities" "0x00000800"
EndSection
```

I have an Ati X1300.

Also, using Xv or SDL with xine instead of OpenGl will result in completely messed up colors and image in Kaffeine. So overlay only semi-works there.

---

