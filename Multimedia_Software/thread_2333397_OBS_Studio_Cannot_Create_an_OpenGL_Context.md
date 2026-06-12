---
title: "OBS Studio Cannot Create an OpenGL Context"
date: 2016-08-09
forum: Multimedia Software
---

### Post by Elijah_Duffy on 2016-08-09
Whenever I try to open OBS studio, I get "Failed to initialize video: Unspecified error". I'm running Ubuntu 16.04 on my Lenovo Thinkpad T410 with Intel Ironlake Mobile graphics. I've never used OBS studio before, this is my first time. Apparently this was an issue before, but has possibly come up again. [Here]("https://endev.xyz/cloud/index.php/s/GKBWiszb7oharBa") is a screen shot of the error. I couldn't upload it as an attatchment for another unknown reason.

Here is the full log when launched from the command line: 
```
Attempted path: share/obs/obs-studio/locale/en-US.ini
Attempted path: /usr/share/obs/obs-studio/locale/en-US.ini
Attempted path: share/obs/obs-studio/locale.ini
Attempted path: /usr/share/obs/obs-studio/locale.ini
Attempted path: share/obs/obs-studio/themes/Default.qss
Attempted path: /usr/share/obs/obs-studio/themes/Default.qss
Attempted path: share/obs/obs-studio/license/gplv2.txt
Attempted path: /usr/share/obs/obs-studio/license/gplv2.txt
info: Processor: 4 logical cores
info: Processor: Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
info: Physical Memory: 7779MB Total
info: Kernel Version: Linux 4.4.0-34-generic
info: Distribution: "Ubuntu" "16.04"
info: OBS 0.15.1 (linux)
info: ---------------------------------
info: ---------------------------------
info: audio settings reset:
    samples per sec: 44100
    speakers:        2
error: X Error: GLXBadFBConfig
error: Failed to create OpenGL context.
error: Failed to create context!
error: device_create (GL) failed
error: Failed to initialize video:  Unspecified error
0x12aa590 void QWindowPrivate::setTopLevelScreen(QScreen*, bool) ( QScreen(0x126d0b0) ): Attempt to set a screen on a child window.
0x15619e0 void QWindowPrivate::setTopLevelScreen(QScreen*, bool) ( QScreen(0x126d0b0) ): Attempt to set a screen on a child window.
0x15614d0 void QWindowPrivate::setTopLevelScreen(QScreen*, bool) ( QScreen(0x126d0b0) ): Attempt to set a screen on a child window.
0x1561030 void QWindowPrivate::setTopLevelScreen(QScreen*, bool) ( QScreen(0x126d0b0) ): Attempt to set a screen on a child window.
0x1560b50 void QWindowPrivate::setTopLevelScreen(QScreen*, bool) ( QScreen(0x126d0b0) ): Attempt to set a screen on a child window.
0x158a1e0 void QWindowPrivate::setTopLevelScreen(QScreen*, bool) ( QScreen(0x126d0b0) ): Attempt to set a screen on a child window.
0x14e6b20 void QWindowPrivate::setTopLevelScreen(QScreen*, bool) ( QScreen(0x126d0b0) ): Attempt to set a screen on a child window.
0x1560610 void QWindowPrivate::setTopLevelScreen(QScreen*, bool) ( QScreen(0x126d0b0) ): Attempt to set a screen on a child window.
0x1733ce0 void QWindowPrivate::setTopLevelScreen(QScreen*, bool) ( QScreen(0x126d0b0) ): Attempt to set a screen on a child window.
0x14b8580 void QWindowPrivate::setTopLevelScreen(QScreen*, bool) ( QScreen(0x126d0b0) ): Attempt to set a screen on a child window.
info: Freeing OBS context data
info: == Profiler Results =============================
info: run_program_init: 14493.5 ms
info:  &#9507;OBSApp::AppInit: 3.617 ms
info:  &#9475; &#9495;OBSApp::InitLocale: 0.92 ms
info:  &#9495;OBSApp::OBSInit: 109.468 ms
info:    &#9507;obs_startup: 1.244 ms
info:    &#9495;OBSBasic::OBSInit: 31.042 ms
info:      &#9507;OBSBasic::InitBasicConfig: 0.543 ms
info:      &#9507;OBSBasic::ResetAudio: 0.258 ms
info:      &#9495;OBSBasic::ResetVideo: 30.145 ms
info: obs_hotkey_thread(25 ms): min=0.156 ms, median=0.581 ms, max=10.634 ms, 99th percentile=1.882 ms, 100% below 25 ms
info: audio_thread(Audio): min=0 ms, median=0.009 ms, max=0.019 ms, 99th percentile=0.015 ms
info: =================================================
info: == Profiler Time Between Calls ==================
info: obs_hotkey_thread(25 ms): min=25.253 ms, median=25.693 ms, max=35.737 ms, 36.3964% within ±2% of 25 ms (0% lower, 63.6036% higher)
info: =================================================
info: Number of memory leaks: 128
```

---

