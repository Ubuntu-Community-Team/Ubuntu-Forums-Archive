---
title: "IBM NetCamera help"
date: 2009-04-12
forum: Multimedia Software
---

### Post by LostMagix on 2009-04-12
Here are a few outputs:

```

:~$lsusb
Bus 005 Device 005: ID 0545:8002 Xirlink, Inc. IBM NetCamera

:~$ sudo modprobe ibmcam
:~$ sudo lsmod | grep ibm
ibmcam                 55504  0 
usbvideo               32900  1 ibmcam
usbcore               149488  8 ibmcam,usbvideo,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd


:~$ ls /dev/video
ls: cannot access /dev/video: No such file or directory

:~$ dmesg
[ 5229.616844] Linux video capture interface: v2.00
[ 5229.636103] ibmcam: IBM NetCamera USB camera found (model 4, rev. 0x030a)
[ 5229.637024] videodev: "ibmcam USB Camera" has no release callback. Please fix your driver for proper sysfs support, see http://lwn.net/Articles/36850/
[ 5229.637029] usbvideo: ibmcam on /dev/video0: canvas=352x288 videosize=352x288
[ 5229.638685] usbcore: registered new interface driver ibmcam


```


then this came up, im not sure if related:

```
:~$  cat < /dev/video0 > foo.dat
bash: /dev/video0: Cannot allocate memory

```


also I noticed that /var/log/syslog is coming back with a lot or errors like this

```
Apr 10 14:13:15 lost-desktop kernel: [64951.904659] Write-error on swap-device (254:0:405880)
Apr 10 14:13:15 lost-desktop kernel: [64951.904700] compcache: Error allocating memory for compressed page: 50599, size=578
```


I was able to get the netcam to reconizes under camstream, output here:

```
:~$ camstream
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
    Trying to find video options for IBM USB Camera@/dev/video0
    D: Creating new node for IBM USB Camera@/dev/video0
  << QDomNode CCamStreamApp::FindVideoDeviceConfig(const QString&, const QString&, bool)
  >> CVideoOptions::CVideoOptions()
    >> virtual void CVideoOptions::DeclareVariables()
    << virtual void CVideoOptions::DeclareVariables()
  << CVideoOptions::CVideoOptions()
  D: CSnapshotSettingsDlg::CSnapshotSettingsDlg(...)
  W: QFont::setWeight: Value out of range (100)
  D: >> CVideoDeviceLinux::Init()
  W: Cannot query audio capabilities of video device.
  D: Using mmap(), size = 608256
  D: mmap()ed 2 buffers.
  W: Failed to restore image size (176, 144)
  D: Initial image size = (352, 288)
  D: << CVideoDeviceLinux::Init()
  D: CVideoSettingsDlg::SizeChanged(352x288)
  D: CVideoSettingsDlg::FramerateChanged(10)
  D: No Philips webcam detected, removing extension tab
  D: CCamPanel::SetSize(352x288)
  D: CCamPanel::SetImageSize(352x288)
  D: CCamPanel::SetVisibleSize(352x288)
  D: CCamPanel::SetSize(352x288)
  D: CCamPanel::SetImageSize(352x288)
  D: CCamPanel::SetVisibleSize(352x288)
  >> void CWebCamViewer::RecalcTotalViewSize()
  << void CWebCamViewer::RecalcTotalViewSize()
<< CWebCamViewer::CWebCamViewer(CVideoDevice*, QWidget*, const char*)
D: >> CVideoDevice::IncrementPalette(0)
D: >> CVideoDeviceLinux::StartCapture()
D: CVideoDeviceLinux::SetPalette picked palette 4 [rgb24]
D: >> CVideoDeviceLinux::CreateImagesRGB()
D: << CVideoDeviceLinux::CreateImagesRGB()
D: >> CVideoDeviceLinux::run()...
D: << CVideoDeviceLinux::StartCapture()
D: << CVideoDevice::IncrementPalette()

```

while camstream is running:

```

:~$ ls /dev/video
ls: cannot access /dev/video: No such file or directory
:~$ ls /dev/video0
/dev/video0

```

any clues on what is going on?

---

### Post by LostMagix on 2009-04-12
Extended  dmesg

```
[ 2656.721512] Linux video capture interface: v2.00
[ 2656.745270] ibmcam: IBM NetCamera USB camera found (model 4, rev. 0x030a)
[ 2656.745376] videodev: "ibmcam USB Camera" has no release callback. Please fix your driver for proper sysfs support, see http://lwn.net/Articles/36850/
[ 2656.745380] usbvideo: ibmcam on /dev/video0: canvas=352x288 videosize=352x288
[ 2656.745407] usbcore: registered new interface driver ibmcam
[ 2656.820744] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 2656.820768] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3152.268172] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3152.268195] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3155.914179] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3155.914204] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3239.147519] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3239.147541] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3243.295780] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3243.295804] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3276.306238] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3276.306261] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3278.622812] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3278.622836] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3312.243912] usbvideo: usbvideo_v4l_open: Someone tried to open an already opened device!
[ 3312.243929] usbvideo: usbvideo_v4l_open: Someone tried to open an already opened device!
[ 3312.326868] usbvideo: usbvideo_v4l_open: Someone tried to open an already opened device!
[ 3312.326883] usbvideo: usbvideo_v4l_open: Someone tried to open an already opened device!
[ 3312.760593] usbvideo: usbvideo_v4l_open: Someone tried to open an already opened device!
[ 3312.760613] usbvideo: usbvideo_v4l_open: Someone tried to open an already opened device!
[ 3313.910735] usbvideo: usbvideo_v4l_open: Someone tried to open an already opened device!
[ 3313.910753] usbvideo: usbvideo_v4l_open: Someone tried to open an already opened device!
[ 3313.910775] usbvideo: usbvideo_v4l_open: Someone tried to open an already opened device!
[ 3314.217874] usbvideo: usbvideo_v4l_open: Someone tried to open an already opened device!
[ 3314.217892] usbvideo: usbvideo_v4l_open: Someone tried to open an already opened device!
[ 3319.613540] usbvideo: usbvideo_v4l_open: Someone tried to open an already opened device!
[ 3319.613560] usbvideo: usbvideo_v4l_open: Someone tried to open an already opened device!
[ 3319.613582] usbvideo: usbvideo_v4l_open: Someone tried to open an already opened device!
[ 3337.136217] usbvideo: usbvideo_v4l_open: Someone tried to open an already opened device!
[ 3346.446302] usbvideo: usbvideo_v4l_open: Someone tried to open an already opened device!
[ 3356.334480] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3356.334510] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3356.401114] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3356.401136] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3374.612328] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3374.612349] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3374.636814] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3374.636832] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3382.607205] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3382.607228] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3384.508398] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3384.508420] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3567.796639] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3567.796661] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3574.260976] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3574.260992] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3595.357094] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3595.357116] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3596.686451] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3596.686473] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3627.580033] usbvideo: usbvideo_v4l_open: Someone tried to open an already opened device!
[ 3817.536394] usb 5-2.2: USB disconnect, address 4
[ 3817.537745] usbvideo: usbvideo_Disconnect: In use, disconnect pending.
[ 3817.537750] usbvideo: USB camera disconnected.
[ 3821.907529] usb 5-2: USB disconnect, address 3
[ 3821.907536] usb 5-2.3: USB disconnect, address 5
[ 3826.056029] usb 1-2: new full speed USB device using uhci_hcd and address 5
[ 3826.225883] usb 1-2: configuration #1 chosen from 1 choice
[ 3826.228556] ibmcam: IBM NetCamera USB camera found (model 4, rev. 0x030a)
[ 3826.229317] videodev: "ibmcam USB Camera" has no release callback. Please fix your driver for proper sysfs support, see http://lwn.net/Articles/36850/
[ 3826.229323] usbvideo: ibmcam on /dev/video0: canvas=352x288 videosize=352x288
[ 3826.360402] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3826.360410] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3847.021080] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3847.021089] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 3848.777128] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 3848.777136] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 4054.665350] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 4054.665359] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28
[ 4060.726051] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(0) ret -28
[ 4060.726060] usbvideo: usbvideo_StartDataPump: usb_submit_isoc(1) ret -28

```

---

### Post by LostMagix on 2009-04-12
cat /dev/video0 foo.dat

its not giving me an output for some reason.

---

### Post by dmizer on 2009-04-12
Closed this. Duplicate here: [http://ubuntuforums.org/showthread.php?t=1121279](http://ubuntuforums.org/showthread.php?t=1121279)

---

