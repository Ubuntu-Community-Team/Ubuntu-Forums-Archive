---
title: "Cannot Preview Myself/Black Screen"
date: 2010-10-03
forum: Multimedia Software
---

### Post by Kat of Zion on 2010-10-03
At some point after one of the many updates I do to my system, I seem to have lost the ability to preview myself on cam.  Simply put, software like CamStream and Cheese just give me a black screen when I open it up.  So, I cant see how I look on cam and what's in or out of the shot.  If I tell Cheese or Camstream to capture a still, there is no problem.  In fact, that is the only way I can determine what the camera is seeing of me and my background.

The only "solution" is to either have Cheese takke my pic and determine from there (as just mentioned), or go on a video chat room and have it use my camera to give me a real-time look at what the camera is aimed to.  As someone who creates webcam videos for upload, and sometimes needs to move the camera while still live, this is not convenient so I hope to fix it.  

Here are the command line outputs Im getting:

Cheese:
```
** (cheese:3704): WARNING **: could not generate thumbnail for /home/lixen69y2k/Webcam/2010-08-25-101226.ogv (video/ogg)


** (cheese:3704): WARNING **: Icon 'video-ogg' not present in theme

```

Camstream:
```

W: CamStream version 0.27 starting.
>> void CCamStreamApp::ReadConfigFile()
<< void CCamStreamApp::ReadConfigFile()
D: CVideoCollector::VideoCollector()
D: >> CVideoDevice::CVideoDevice()
D: << CVideoDevice::CVideoDevice()
D: >> CVideoDeviceLinux::CVideoDeviceLinux(/dev/video0)
D: << CVideoDeviceLinux::CVideoDeviceLinux()
>> CCamWindow::CCamWindow(QWidget*, const char*)
<< CCamWindow::CCamWindow(QWidget*, const char*)
>> CWebCamViewer::CWebCamViewer(CVideoDevice*, QWidget*, const char*)
  >> QDomNode CCamStreamApp::FindVideoDeviceConfig(const QString&, const QString&, bool)
    Trying to find video options for USB2.0 UVC 1.3M WebCam@/dev/video0
    D: Creating new node for USB2.0 UVC 1.3M WebCam@/dev/video0
  << QDomNode CCamStreamApp::FindVideoDeviceConfig(const QString&, const QString&, bool)
  >> CVideoOptions::CVideoOptions()
    >> virtual void CVideoOptions::DeclareVariables()
    << virtual void CVideoOptions::DeclareVariables()
  << CVideoOptions::CVideoOptions()
  D: CSnapshotSettingsDlg::CSnapshotSettingsDlg(...)
  W: QFont::setWeight: Value out of range (100)
  D: >> CVideoDeviceLinux::Init()
  W: Cannot query audio capabilities of video device.
  D: Using mmap(), size = 67108864
  W: mmap() failed (22). Falling back to non-mmap()ed mode.
  D: Allocating own buffer.
  D: Initial image size = (176, 144)
  D: << CVideoDeviceLinux::Init()
  D: CVideoSettingsDlg::SizeChanged(176x144)
  D: CVideoSettingsDlg::FramerateChanged(10)
  D: No Philips webcam detected, removing extension tab
  D: CCamPanel::SetSize(176x144)
  D: CCamPanel::SetImageSize(176x144)
  D: CCamPanel::SetVisibleSize(176x144)
  D: CCamPanel::SetSize(176x144)
  D: CCamPanel::SetImageSize(176x144)
  D: CCamPanel::SetVisibleSize(176x144)
  >> void CWebCamViewer::RecalcTotalViewSize()
  << void CWebCamViewer::RecalcTotalViewSize()
<< CWebCamViewer::CWebCamViewer(CVideoDevice*, QWidget*, const char*)
D: >> CVideoDevice::IncrementPalette(0)
D: >> CVideoDeviceLinux::StartCapture()
D: CVideoDeviceLinux::SetPalette picked palette 4 [rgb24]
D: >> CVideoDeviceLinux::CreateImagesRGB()
D: << CVideoDeviceLinux::CreateImagesRGB()
D: << CVideoDeviceLinux::StartCapture()
D: << CVideoDevice::IncrementPalette()
D: >> CVideoDeviceLinux::run()...

```

GUVCstream:
```

guvcview 1.1.3
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
video device: /dev/video0 
/dev/video0 - device 1
Init. USB2.0 UVC 1.3M WebCam (location: usb-0000:00:1d.7-5)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 160, height = 120 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 1280, height = 1024 }
        Time interval between frame: 1/9, 
checking format: 1448695129
vid:064e 
pid:a116 
driver:uvcvideo
 Could not grab image (select timeout): Resource temporarily unavailable

```

Seems that GUVCview gives me the best articulation of what the problem is. I have both a built-in webcam for my laptop as well as a USB one.  Both seem to have this problem so I know its a case of some part of my software being the trouble.  Anyone had this happen?

---

### Post by no2498 on 2010-10-04
try this program wxcam
read and install all the page tells you to


[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

---

### Post by Kat of Zion on 2010-10-04
> **no2498 said:**
> try this program wxcam
read and install all the page tells you to


[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

Oh, any chance that there is a deb for 64 bit. Totally forgot to mention that.

---

### Post by Kat of Zion on 2010-10-05
Does 64 bit Lucid support this app? What kind of libraries would it install which would fix my original problem?

---

### Post by no2498 on 2010-10-05
if i think rite its in the repose in/on 10.4 and up

cheese uses 

gstreamer good, bad, ugly, and 10

this comes from the cheese help faq's

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

---

### Post by Kat of Zion on 2010-10-05
> **no2498 said:**
> if i think rite its in the repose in/on 10.4 and up

cheese uses 

gstreamer good, bad, ugly, and 10

this comes from the cheese help faq's

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

Thanks! I had tried this before and got a black screen when using V4l2, even when I specified my built-in camera instead of default.  I also just tried using "default" and the same problem.  Black screen overall.

Command line errors returned:
```
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
```

Could esdmon, qcamsrc, and all the others mentioned above be lacking in my system and responsible for webcam always showing a black preview?

As for V4l1, the test was not succesful. It gave me this error upon pressing "test".

```
Video for Linux (v4l): Could not get/set settings from/on resource.
```

Only other thing I saw in the gstreamer properties which I havent messed with at all is the Default output plugin under the video tab.  It is set to Autodetect.  Only other options I could get are "X Window System (No Xv)", "X Window System (X11/XShm/Xv)" and "Custom".


Kat

---

### Post by no2498 on 2010-10-05
everybody gets this
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'


did you make sure you have 

gstreamer good bad ugly and 10 installed

---

### Post by no2498 on 2010-10-05
btw type webcam in a terminal click enter what does it tell you

---

### Post by Kat of Zion on 2010-10-05
> **no2498 said:**
> everybody gets this
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'


did you make sure you have 

gstreamer good bad ugly and 10 installed

Sure did.

---

### Post by Kat of Zion on 2010-10-05
> **no2498 said:**
> btw type webcam in a terminal click enter what does it tell you

  size 320x240 [none]
  input (null), norm (null), jpeg quality 75
  rotate=0, top=0, left=0, bottom=240, right=320

Than the prompt hangs so I have to do ctrl+C to get back to the prompt.

Kat

---

### Post by no2498 on 2010-10-06
open cheese and try a diff size for your cam

if it still does not work
put this in a terminal

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

---

### Post by Kat of Zion on 2010-10-06
> **no2498 said:**
> open cheese and try a diff size for your cam

if it still does not work
put this in a terminal

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

First off, regardless of putting that line in terminal or not, Cheese only lets me select resolution from the pulldown.  The camera choice pulldown is greyed out.  

Changing resolution did not solve the problem.  I had tried this before using smaller resolutions such as 178px wide (the lowest setting for my built in cam) and it didnt solve the problem back then either. 

Im tempted to believe its not any specific software (cheese, guvcview, camstream, etc..) that is producing the problem.  I know it has to be something else which is why I thought maybe my error messages from any one of these applications might render a clue.

---

### Post by no2498 on 2010-10-06
did you try this ?

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

---

### Post by Kat of Zion on 2010-10-06
> **no2498 said:**
> did you try this ?

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

As I said, yes, I had tried that as well.

---

### Post by Kat of Zion on 2010-10-08
Any other solutions?  Just did an upgrade to a few packages but alas...nothing that would give me a fix the lucky way.  :)

---

### Post by Kat of Zion on 2010-10-24
Well, in an interesting turn of events, Im finding 2 new things regarding my problem which might be a clue:

1) When using Skype I found out that this black screen problem also exists.  I couldnt preview the webcam I wanted to show my friend, and my friend's webcam feed came up black when he turned his webcam on.  

Yes, the Linux version of Skype is in beta so that could also be it. However, it got me thinking about a Segmentation problem I have with a 3D program when running it under KDE.  In that case, running under Xfce fixed the problem, so I wondered if something was up with KDE and my camera.

2) When I ran my cam under Xfce, both things like Skype and preview programs (Cheese, GUVCview, etc..) the problem is solved.   I can preview myself just fine. No black screen.  Even my Skype call (to the same friend) was sucessful both in letting me see his cam and me being able to see a preview of mine.

Odd business indeed.  I guess Ill be doing my shows and my skype convos using Xfce for now. :/ Not my ideal situation but Im suspecting that Plasma Desktop is the culprit.

---

### Post by Kat of Zion on 2011-01-20
Bumping this thread.  Problem still persists.

---

### Post by ohCanada on 2011-02-01
I have the same problem in Ubuntu 10.04 with a Lifecam HD-5000 and can confirm that opening a session in Xfce solves the problem and both cheese and skype work fine. In Gnome cheese shows only black screen though can take screen shots. Interestingly, in Gnome everything works in Skype except incoming video and preview, everything else working as expected (I can hear the other person and the other person can both hear and can see my video even though I cannot see preview)
Would be very interested to know what is going on here....

---

### Post by Kat of Zion on 2011-02-01
> **ohCanada said:**
> I have the same problem in Ubuntu 10.04 with a Lifecam HD-5000 and can confirm that opening a session in Xfce solves the problem and both cheese and skype work fine. In Gnome cheese shows only black screen though can take screen shots. Interestingly, in Gnome everything works in Skype except incoming video and preview, everything else working as expected (I can hear the other person and the other person can both hear and can see my video even though I cannot see preview)

Would be very interested to know what is going on here....


@ohCanada  At one point, its a comfort to know that Im not the only one who desires to use webcam and is experiencing this problem.  Im pretty annoyed, like considering-a-secondary-MAC-computer annoyed. :/

Incidentally, one other shortcoming Im experiencing is described here:
[http://ubuntuforums.org/showthread.php?t=1672309](http://ubuntuforums.org/showthread.php?t=1672309)

I wonder if the problems are related.

---

