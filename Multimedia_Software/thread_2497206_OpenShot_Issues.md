---
title: "OpenShot Issues"
date: 2024-04-26
forum: Multimedia Software
---

### Post by mpmckinnon on 2024-04-26
Hi there I had OpenShot working a few days ago and did the last of the updates for Ubuntu 24.04. Now for some reason I can not get it to run I have tried the Snap version and the official version and still not loading. When I try to install via terminal I get this message

```
"Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 python3-openshot : Depends: python3 (< 3.12) but 3.12.3-0ubuntu1 is to be installed
                    Depends: libpython3.11 (>= 3.11.5) but it is not installable
E: Unable to correct problems, you have held broken packages."

```
When I try Snap in terminal I get this

```
"openshot-community 
Testing for explicit PulseAudio choice... 
...and PulseAudio has been explicitly chosen, so using it. 
Loaded modules from:  /snap/openshot-community/3/usr/lib/python3/dist-packages/openshot_qt 
Warning: Ignoring XDG_SESSION_TYPE=wayland on Gnome. Use  QT_QPA_PLATFORM=wayland to run on Wayland anyway. 
libGL error: DRI driver not from this Mesa build  ('23.2.1-1ubuntu3.1~22.04.2' vs '23.0.4-0ubuntu1~22.04.1') 
libGL error: failed to load driver: radeonsi 
libGL error: DRI driver not from this Mesa build  ('23.2.1-1ubuntu3.1~22.04.2' vs '23.0.4-0ubuntu1~22.04.1') 
libGL error: failed to load driver: swrast 
Qt: Session management error: None of the authentication protocols  specified are supported 
INFO app: ------------------------------------------------ 
INFO app:             Thu Apr 25 19:47:22 2024 
INFO app:               Starting new session 
INFO app: ------------------------------------------------ 
INFO app:             OpenShot (version 3.1.1) 
INFO app: ------------------------------------------------ 
INFO app: openshot-qt version: 3.1.1 
INFO app: libopenshot version: 0.3.2 
INFO app: platform: Linux-6.8.7-x64v4-xanmod2-x86_64-with-glibc2.35 
INFO app: processor: x86_64 
INFO app: machine: x86_64 
INFO app: python version: 3.10.12 
INFO app: qt5 version: 5.15.3 
INFO app: pyqt5 version: 5.15.6 
INFO project_data: Setting profile to HD 720p 30 fps 
INFO project_data: Apply default audio playback settings: 48000, 2 channels 
INFO app: checking babl_ext_path:  /snap/openshot-community/3/usr/lib/python3/dist-packages/openshot_qt/lib/babl-ext 
Screen HDMI-1 
   devicePixelRatio: 1.0 
   logicalDotsPerInch: 96.0 
   physicalDotsPerInch: 80.3149469623915 
   availableSizes: PyQt5.QtCore.QSize(3840, 2128) 
INFO language: Qt Detected Languages: ['en-US'] 
INFO language: LANG Environment Variable: en_US.UTF-8 
INFO language: LOCALE Environment Variable: 
INFO language: OpenShot Preference Language: Default 
INFO app: Setting font to  /snap/openshot-community/3/usr/lib/python3/dist-packages/openshot_qt/images/fonts/Ubuntu-R.ttf 
INFO app: Setting custom dark theme 
INFO logger_libopenshot: Connecting to libopenshot with debug port: 5556 
INFO ui_util: Initializing UI for MainWindow 
INFO thumbnail: Starting thumbnail server listening on ('127.0.0.1', 41741) 
Sandboxing disabled by user. 
WebEngineContext used before [QtWebEngine::initialize()](QtWebEngine::initialize()) or OpenGL context  creation failed. 
QGLXContext: Failed to create dummy context 
INFO webengine: WebEngine backend initializing 
[1715752:1716540:0425/194723.277117:[ERROR:zygote_host_impl_linux.cc(263)](ERROR:zygote_host_impl_linux.cc(263))]  Failed to adjust OOM score of renderer with pid 1716541: Permission  denied (13) 
INFO transition_model: updating transitions model. 
INFO effects_model: updating effects model. 
INFO emoji_model: updating emoji model. 
INFO version: Found current version: {'error_rate_unstable': 0.05,  'openshot_version': '3.1.1', 'trans_rate_unstable': 0.001,  'error_rate_stable': 0.25, 'trans_rate_stable': 0.01} 
INFO sentry: Sentry initialized for 'production': 0.25 sample rate, 0.01  transaction rate 
INFO main_window: InitCacheSettings 
INFO main_window: cache-mode: CacheMemory 
INFO main_window: cache-limit-mb: 512 
INFO main_window: cache-ahead-percent: 0.7 
INFO main_window: cache-preroll-min-frames: 24 
INFO main_window: cache-preroll-max-frames: 48 
INFO main_window: cache-max-frames: 600 
INFO main_window: Creating CacheMemory object with 536870912 byte limit 
INFO preview_thread: QThread Start Method Invoked 
ERROR main_window: Unhandled crash detected:  linux-/lib/x86_64-linux-gnu/libc.so.6 raise 0x16 [0x7bb0aafbb476] 
Failed to create OpenGL context for format QSurfaceFormat(version 2.0,  options QFlags[<QSurfaceFormat::FormatOption>]("QSurfaceFormat::FormatOption")(), depthBufferSize 24,  redBufferSize -1, greenBufferSize -1, blueBufferSize -1, alphaBufferSize  -1, stencilBufferSize 8, samples 0, swapBehavior  [QSurfaceFormat::DefaultSwapBehavior](QSurfaceFormat::DefaultSwapBehavior), swapInterval 1, colorSpace  [QSurfaceFormat::DefaultColorSpace](QSurfaceFormat::DefaultColorSpace), profile  [QSurfaceFormat::NoProfile](QSurfaceFormat::NoProfile)) 
Caught signal 6 (SIGABRT) 
---- Unhandled Exception: Stack Trace ---- 
  /lib/x86_64-linux-gnu/libc.so.6 (  raise                                     + 0x16  ) [0x79f3da63e476] 
  /lib/x86_64-linux-gnu/libc.so.6 (  abort                                     + 0xd3  ) [0x79f3da6247f3] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5Core.so.5  (                                           + 0x90ba3) [0x79f3d8004ba3] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5QuickWidgets.so.5  (                                           + 0xce95) [0x79f3c24e3e95] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5QuickWidgets.so.5  (                                           + 0xd1ff) [0x79f3c24e41ff] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5QuickWidgets.so.5  ( [QQuickWidget::resizeEvent(QResizeEvent*)](QQuickWidget::resizeEvent(QResizeEvent*))  + 0x2f5 ) [0x79f3c24e63e5] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5WebEngineWidgets.so.5  (                                           + 0x3958d) [0x79f3cacf558d] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5 (  [QWidget::event(QEvent*)](QWidget::event(QEvent*))                   + 0xc8c ) [0x79f3d5212f6c] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5 (  [QApplicationPrivate::notify_helper(QObject*](QApplicationPrivate::notify_helper(QObject*), QEvent*)  + 0x83 )   [0x79f3d51cf713] 
/snap/openshot-community/3/usr/lib/python3/dist-packages/PyQt5/QtWidgets.abi3.so  (                                           + 0x3a0f16) [0x79f3cb438f16] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5Core.so.5 (  [QCoreApplication::notifyInternal2(QObject*](QCoreApplication::notifyInternal2(QObject*), QEvent*)  + 0x13a )  [0x79f3d822de3a] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5 (  [QWidgetPrivate::sendPendingMoveAndResizeEvents(bool](QWidgetPrivate::sendPendingMoveAndResizeEvents(bool), bool)  + 0x146 )   [0x79f3d520a366] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5 (  [QWidgetPrivate::show_helper()](QWidgetPrivate::show_helper())             + 0x37  ) [0x79f3d520ee07] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5 (  [QWidgetPrivate::showChildren(bool)](QWidgetPrivate::showChildren(bool))        + 0x169 ) [0x79f3d520eda9] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5 (  [QWidgetPrivate::show_helper()](QWidgetPrivate::show_helper())             + 0x53  ) [0x79f3d520ee23] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5 (  [QWidgetPrivate::setVisible(bool)](QWidgetPrivate::setVisible(bool))          + 0x1a3 ) [0x79f3d5211fe3] 
/snap/openshot-community/3/usr/lib/python3/dist-packages/PyQt5/QtWebEngineWidgets.abi3.so  (                                           + 0x2029b) [0x79f3cad2b29b] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5 (  [QWidgetPrivate::showChildren(bool)](QWidgetPrivate::showChildren(bool))        + 0x149 ) [0x79f3d520ed89] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5 (  [QWidgetPrivate::show_helper()](QWidgetPrivate::show_helper())             + 0x53  ) [0x79f3d520ee23] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5 (  [QWidgetPrivate::showChildren(bool)](QWidgetPrivate::showChildren(bool))        + 0x169 ) [0x79f3d520eda9] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5 (  [QWidgetPrivate::show_helper()](QWidgetPrivate::show_helper())             + 0x53  ) [0x79f3d520ee23] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5 (  [QWidgetPrivate::setVisible(bool)](QWidgetPrivate::setVisible(bool))          + 0x1a3 ) [0x79f3d5211fe3] 
/snap/openshot-community/3/usr/lib/python3/dist-packages/PyQt5/QtWidgets.abi3.so  (                                           + 0x3401fb) [0x79f3cb3d81fb] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5 (  [QWidgetPrivate::showChildren(bool)](QWidgetPrivate::showChildren(bool))        + 0x149 ) [0x79f3d520ed89] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5 (  [QWidgetPrivate::show_helper()](QWidgetPrivate::show_helper())             + 0x53  ) [0x79f3d520ee23] 
/snap/openshot-community/3/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5 (  [QWidgetPrivate::setVisible(bool)](QWidgetPrivate::setVisible(bool))          + 0x1a3 ) [0x79f3d5211fe3] 
/snap/openshot-community/3/usr/lib/python3/dist-packages/PyQt5/QtWidgets.abi3.so  (                                           + 0x25a76b) [0x79f3cb2f276b] 
/snap/openshot-community/3/usr/lib/python3/dist-packages/PyQt5/QtWidgets.abi3.so  (                                           + 0x3d1e22) [0x79f3cb469e22] 
  python3 (                                           + 0x15a138)  [0x5e4cb7022138] 
  python3                        (  _PyObject_MakeTpCall                      + 0x25b ) [0x5e4cb7018a7b] 
  python3                        (  _PyEval_EvalFrameDefault                  + 0x6a79) [0x5e4cb7011629] 
  python3                        (  _PyObject_FastCallDictTstate              + 0xc4  ) [0x5e4cb7017c14] 
  python3 (                                           + 0x164a64)  [0x5e4cb702ca64] 
  python3                        (  _PyObject_MakeTpCall                      + 0x1fc ) [0x5e4cb7018a1c] 
  python3                        (  _PyEval_EvalFrameDefault                  + 0x64e6) [0x5e4cb7011096] 
  python3 (                                           + 0x1687f1)  [0x5e4cb70307f1] 
  python3                        (  _PyEval_EvalFrameDefault                  + 0x614a) [0x5e4cb7010cfa] 
  python3                        (  _PyFunction_Vectorcall                    + 0x7c  ) [0x5e4cb70229fc] 
  python3                        (  _PyEval_EvalFrameDefault                  + 0x6bd ) [0x5e4cb700b26d] 
  python3 (                                           + 0x13f9c6)  [0x5e4cb70079c6] 
  python3                        (  PyEval_EvalCode                           + 0x86  ) [0x5e4cb70fd256] 
  python3 (                                           + 0x260108)  [0x5e4cb7128108] 
  python3 (                                           + 0x2599cb)  [0x5e4cb71219cb] 
  python3 (                                           + 0x25fe55)  [0x5e4cb7127e55] 
  python3                        (  _PyRun_SimpleFileObject                   + 0x1a8 ) [0x5e4cb7127338] 
  python3                        (  _PyRun_AnyFileObject                      + 0x43  ) [0x5e4cb7126f83] 
  python3                        (  Py_RunMain                                + 0x2be ) [0x5e4cb7119a5e] 
  python3                        (  Py_BytesMain                              + 0x2d  ) [0x5e4cb70f002d] 
  /lib/x86_64-linux-gnu/libc.so.6  (                                           + 0x29d90) [0x79f3da625d90] 
  /lib/x86_64-linux-gnu/libc.so.6 (  __libc_start_main                         + 0x80  ) [0x79f3da625e40] 
  python3                        (  _start                                    + 0x25  ) [0x5e4cb70eff25] 
---- End of Stack Trace ---- "
```

I really need help fixing this issue please and thank you.

---

### Post by vmpx on 2024-06-02
Try QDVDAuthor: sf.net/p/qdvd

---

### Post by currentshaft on 2024-06-02
AFAIK Ubuntu 24 ships with Python 3.11 or 3.12, which will predictably break any incompatible software.

You could use miniconda to run an earlier, compatible version of Python; this is what I do to make my pytorch ML tools work. Let me know if you have any questions setting this up.

I've found kdenlive to be a good video editor as well.

---

