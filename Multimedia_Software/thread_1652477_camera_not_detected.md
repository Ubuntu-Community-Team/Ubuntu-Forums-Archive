---
title: "camera not detected"
date: 2010-12-24
forum: Multimedia Software
---

### Post by Angelbrand on 2010-12-24
i have an msi vr6o1 laptop with built in camera but the camera inst being detected by anything. please help!!

---

### Post by Angelbrand on 2010-12-25
please help..?

---

### Post by Angelbrand on 2010-12-25
i think all i have to do is unlock the camera but i have no clue how to do that...? any know how anyone at all???

---

### Post by ElSlunko on 2010-12-25
What are you using to test your camera out?

---

### Post by Angelbrand on 2010-12-25
i tried cheese then i tried usuing you tube to record video straight from there as i have done that before when i ran vista but its not picking up that there is a built in camera. someone else had the same prob and said the just had to unlock it but i cant figure out how to do that...

---

### Post by no2498 on 2010-12-25
some lap tops need to click the fn key to turn a cam on
hope its all you need to do
ive never had a lap top

---

### Post by 0N3 on 2010-12-25
Try webcam studio see if that detects your camera

[http://www.ws4gl.org/](http://www.ws4gl.org/)

---

### Post by Syed75 on 2010-12-25
Probably need a driver. [Check here to see if theres a driver available.]("https://wiki.ubuntu.com/SkypeWebCams")

---

### Post by no2498 on 2010-12-27
if you can type lsusb in a terminal click enter post the output here

---

### Post by bcschmerker on 2010-12-27
What packages related to video streaming are on your system?  I found an issue with CamServ, which ran mutual interference on CamStream and prevented Adobe Flash Player from detecting any cameras (which cleared itself upon purging CamServ).

---

### Post by lidex on 2010-12-29
This should help:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by Angelbrand on 2011-01-10
the name of the driver for it is "gspca_main" but i cannot find anywhere to download the driver,

---

### Post by BicyclerBoy on 2011-01-10
Have you tried the webcam button next to the power button ?

Have you tried guvcview ?
It is much more interactive than the cheese thing.

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
[https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)

The gspca & v4l2 (video 4 linux) are kernel modules so you already have a version.

You should search gspca & LinuxTV v4l websites for compatibility.

If you need a later module/driver then you must compile/install a kernel module or upgrade the kernel to one that does.
The latter is much easier.

There is a ubuntu kernel ppa that lets you install the latest Ubuntu approved.
Are you sure that you need to do this ?

---

### Post by Angelbrand on 2011-01-11
> **BicyclerBoy said:**
> Have you tried the webcam button next to the power button ?

Have you tried guvcview ?
It is much more interactive than the cheese thing.

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
[https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)

The gspca & v4l2 (video 4 linux) are kernel modules so you already have a version.

You should search gspca & LinuxTV v4l websites for compatibility.

If you need a later module/driver then you must compile/install a kernel module or upgrade the kernel to one that does.
The latter is much easier.

There is a ubuntu kernel ppa that lets you install the latest Ubuntu approved.
Are you sure that you need to do this ?

1 what webcam button... there isnt one...
2 i have tried so many different web cam programs the problem is there is no driver what so ever. so the computer is not registering that there is a built in camera.

---

### Post by Angelbrand on 2011-01-11
any one where to download a driver for the bison 1.3megapixel in built camera for linux OS? anyone?

---

### Post by Angelbrand on 2011-01-11
this is the result i got typing lsusb


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Angelbrand on 2011-01-11
so after running lsusb i google a driver for that and was give code to run in terminal

**[SIZE=2]apt-get install kernel-package linux-headers build-essential ctags libv4l[/SIZE]**



the result to that was

sudo apt-get install kernel-package linux-headers build-essential ctags libv4l
[sudo] password for angel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'exuberant-ctags' instead of 'ctags'
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.35-23-virtual 2.6.35-23.41
  linux-headers-2.6.35-23-generic-pae 2.6.35-23.41
  linux-headers-2.6.35-23-generic 2.6.35-23.41
  linux-headers-2.6.35-23 2.6.35-23.41
  linux-headers-2.6.35-22-virtual 2.6.35-22.35
  linux-headers-2.6.35-22-generic-pae 2.6.35-22.35
  linux-headers-2.6.35-22-generic 2.6.35-22.35
  linux-headers-2.6.35-22 2.6.35-22.35
You should explicitly select one to install.

E: Package 'linux-headers' has no installation candidate
E: Unable to locate package libv4l

unsure of next step.

---

### Post by no2498 on 2011-01-11
put this in your packager manager libv4l click search
i come up with only 3 for me they was installed
i use the 2.6.32-27 kernel

---

### Post by BicyclerBoy on 2011-01-11
Wow you are game..
What I think you are doing is installing a wrapper over the v4l & v4l2 kernel modules.
This will get you more supported devices.

What you do now is :

uname -r

This will reveal your current installed kernel version.
Then select the matching kernel linux-headers in synaptic & install.

I think synaptic will then complete the previous failed install.

The downside could be that you need to rerun the libv4l install process after every kernel upgrade.

By the way..
If you had installed guvcview, the *buntu package of libv4l would be installed.
But your method will result in a later version.

---

### Post by Angelbrand on 2011-01-11
> **no2498 said:**
> put this in your packager manager libv4l click search
i come up with only 3 for me they was installed
i use the 2.6.32-27 kernel


thanks! i searched libv41 in software centre, intalled both that showed up and my cam works now!! i cant believe it was that easy!! been running so many programs and script and to find out it was that simple... 

thanks!!!

---

### Post by no2498 on 2011-01-12
glad it worked for you
mark this solved 
so it can help others too

---

### Post by dunbrokin on 2011-08-20
> **BicyclerBoy said:**
> Have you tried the webcam button next to the power button ?

Have you tried guvcview ?
It is much more interactive than the cheese thing.

?

My webcam runs very well on Cheese and on guvcview....but it does not seem to be detected on camstream.....I want to use camstream as I want to ftp my weather images to my weather site on a regular basis...this is my output from camstream.....any idea what the problem is here.

W: CamStream version 0.27 starting.
>> void CCamStreamApp::ReadConfigFile()
  W: Failed to open configuration file '/home/pj-weather/.camstream/config.xml' for reading.
  D: creating <defaults> node
  D: creating <videodevices> node
  D: creating <audiodevices> node
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
    Trying to find video options for USB 2.0 Camera@/dev/video0
    D: Creating new node for USB 2.0 Camera@/dev/video0
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
>> void CWebCamViewer::TakeSnapshot()
  D: TakeSnapshot: stampimage = F, stampfile T, savetodisk = T, ftptoserver = F, runcommand = F
  D: CCamPanel::SetSize(176x144)
  D: CCamPanel::SetImageSize(176x144)
  D: CCamPanel::SetVisibleSize(176x144)
  >> void CWebCamViewer::RecalcTotalViewSize()
  << void CWebCamViewer::RecalcTotalViewSize()
<< void CWebCamViewer::TakeSnapshot()
>> virtual void CCamStreamMainWindow::closeEvent(QCloseEvent*)
  >> void CCamStreamMainWindow::CloseAll()
    >> virtual CWebCamViewer::~CWebCamViewer()
      >> void CWebCamViewer::StopTimeSnap()
        >> void CWebCamViewer::StopFTP()
        << void CWebCamViewer::StopFTP()
      << void CWebCamViewer::StopTimeSnap()
      D: >> CVideoDeviceLinux::StopCapture()
      D: Waiting for capture thread to stop...

Thanks in advance for any help on this.

---

### Post by dunbrokin on 2011-08-20
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0c45:62e0 Microdia MSI Starcam Racer
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


and should add that on this machine I am on 10.04.

---

