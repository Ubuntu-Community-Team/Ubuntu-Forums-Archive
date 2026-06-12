---
title: "Mythbuntu 10.04 + Hauppauge HVR-1950 non functional"
date: 2010-09-13
forum: Mythbuntu
---

### Post by danroh on 2010-09-13
I've just purchased a Hauppauge WinTV-HVR-1950 to tune analog and QAM HD stations from Time Warner cable.  The device absolutely exceeds my expectations in Windows Media Center on Windows 7.. beautiful picture and flawless operation.  

Running under Mythbuntu 10.04 though, this is a completely different story.  Both analog and dvb device nodes are created under /dev, but all attempts to use them have failed.  I can't even scan for channels or cat a signal out of /dev/video0.

The tuner is clearly being detected, but for whatever reason the device never finishes loading.  My eyes burn from Googling solutions to this.. can anyone give me some direction?

Thanks

 [  450.962468] usb 1-1: new high speed USB device using ehci_hcd and address 3
  [  451.645033] usb 1-1: configuration #1 chosen from 1 choice
  [  452.036102] cx25840' 0-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
  [  452.142202] tuner' 0-0042: chip found @ 0x84 (pvrusb2_a)
  [  452.142259] tda9887 0-0042: creating new instance
  [  452.142261] tda9887 0-0042: tda988[5/6/7] found
  [  452.321153] tveeprom 0-00a2: Hauppauge model 75111, rev D2F5, serial# 7274161
  [  452.321157] tveeprom 0-00a2: MAC address is 00-0D-FE-6E-FE-B1
  [  452.321158] tveeprom 0-00a2: tuner model is unknown (idx 155, type 0)
  [  452.321160] tveeprom 0-00a2: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
  [  452.321161] tveeprom 0-00a2: audio processor is CX25843 (idx 37)
  [  452.321163] tveeprom 0-00a2: decoder processor is CX25843 (idx 30)
  [  452.321164] tveeprom 0-00a2: has radio, has IR receiver, has IR transmitter
  [  452.321169] pvrusb2: Supported video standard(s) reported available in hardware: PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB
  [  452.321171] pvrusb2: Mapping standards mask=0x300b700 (PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB)
  [  452.321174] pvrusb2: Setting up 6 unique standard(s)
  [  452.321176] pvrusb2: Set up standard idx=0 name=PAL-M
  [  452.321178] pvrusb2: Set up standard idx=1 name=PAL-N
  [  452.321180] pvrusb2: Set up standard idx=2 name=PAL-Nc
  [  452.321181] pvrusb2: Set up standard idx=3 name=NTSC-M
  [  452.321182] pvrusb2: Set up standard idx=4 name=NTSC-Mj
  [  452.321184] pvrusb2: Set up standard idx=5 name=NTSC-Mk
  [  452.321186] pvrusb2: Initial video standard (determined by device type): NTSC-M
  [  452.321194] pvrusb2: Device initialization completed successfully.
  [  452.351099] pvrusb2: registered device video0 [mpeg]
  [  452.351103] DVB: registering new adapter (pvrusb2-dvb)
  [  452.491195] cx25840' 0-0044: firmware: requesting v4l-cx25840.fw
  [  456.745440] cx25840' 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
  [  457.823607] cx25840' 0-0044: Video signal:              not present
  [  457.823611] cx25840' 0-0044: Detected format:           NTSC-M
  [  457.823613] cx25840' 0-0044: Specified standard:        NTSC-M
  [  457.823615] cx25840' 0-0044: Specified video input:     Composite 7
  [  457.823617] cx25840' 0-0044: Specified audioclock freq: 48000 Hz
  [  457.879505] cx25840' 0-0044: Detected audio mode:       forced mode
  [  457.879507] cx25840' 0-0044: Detected audio standard:   no detected audio standard
  [  457.879509] cx25840' 0-0044: Audio muted:               no
  [  457.879510] cx25840' 0-0044: Audio microcontroller:     detecting
  [  457.879512] cx25840' 0-0044: Configured audio standard: automatic detection
  [  457.879513] cx25840' 0-0044: Configured audio system:   BTSC
  [  457.879514] cx25840' 0-0044: Specified audio input:     Tuner (In8)
  [  457.879516] cx25840' 0-0044: Preferred audio mode:      stereo
  [  457.879519] tda9887 0-0042: Data bytes: b=0xd4 c=0x30 e=0x44
  [  458.047702] cx25840' 0-0044: firmware: requesting v4l-cx25840.fw
  [  462.089935] cx25840' 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
  [  462.625202] usb 1-1: firmware: requesting v4l-cx2341x-enc.fw
  [  463.155494] cx25840' 0-0044: 0x0000 is not a valid video input!
  [  463.719852] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
  [  463.751476] tda18271 0-0060: creating new instance
  [  463.754011] tda18271_read_regs: ERROR: i2c_transfer returned: -5
  [  463.754026] Unknown device detected @ 0-0060, device not supported.
  [  463.759508] tda18271_read_regs: ERROR: i2c_transfer returned: -5
  [  463.759510] Unknown device detected @ 0-0060, device not supported.
  [  463.759512] tda18271_attach: error -22 on line 1170
  [  463.759514] tda18271 0-0060: destroying instance

---

### Post by LowSky on 2010-09-13
have you downloaded and installed the firmware?

[http://sray.squidpower.com/2009/02/18/hauppauge-wintv-hvr-1950-on-linux-mythbuntu-mythtv-analog-digital-video-including-s-video-and-composite-inputs/](http://sray.squidpower.com/2009/02/18/hauppauge-wintv-hvr-1950-on-linux-mythbuntu-mythtv-analog-digital-video-including-s-video-and-composite-inputs/)

---

### Post by danroh on 2010-09-13
I have.  To confirm, see the directory listing of /lib/firmware below.  I haven't gotten any errors indicating that the firmware has not been found or cannot be loaded.

$ ls -l /lib/firmware/v4l*
-rw-r--r-- 1 root root  16382 2010-05-26 12:10 /lib/firmware/v4l-cx231xx-avcore-01.fw
-rw-r--r-- 1 root root 141200 2010-05-26 12:10 /lib/firmware/v4l-cx23418-apu.fw
-rw-r--r-- 1 root root 158332 2010-05-26 12:10 /lib/firmware/v4l-cx23418-cpu.fw
-rw-r--r-- 1 root root  16382 2010-05-26 12:10 /lib/firmware/v4l-cx23418-dig.fw
-rw-r--r-- 1 root root 262144 2010-05-26 12:10 /lib/firmware/v4l-cx2341x-dec.fw
-rw-r--r-- 1 root root 376836 2010-09-11 22:42 /lib/firmware/v4l-cx2341x-enc.fw
-rw-r--r-- 1 root root 155648 2010-05-26 12:10 /lib/firmware/v4l-cx2341x-init.mpg
-rw-r--r-- 1 root root  16382 2010-05-26 12:10 /lib/firmware/v4l-cx23885-avcore-01.fw
-rw-r--r-- 1 root root  16382 2010-05-26 12:10 /lib/firmware/v4l-cx23885-enc.fw
-rw-r--r-- 1 root root  16382 2010-09-11 22:42 /lib/firmware/v4l-cx25840.fw
-rw-r--r-- 1 root root   8192 2010-05-26 12:10 /lib/firmware/v4l-pvrusb2-24xxx-01.fw
-rw-r--r-- 1 root root   8192 2010-09-11 22:42 /lib/firmware/v4l-pvrusb2-29xxx-01.fw
-rw-r--r-- 1 root root   8192 2010-09-11 23:05 /lib/firmware/v4l-pvrusb2-73xxx-01.fw

---

### Post by ehula on 2010-09-23
> **danroh said:**
> I've just purchased a Hauppauge WinTV-HVR-1950 to tune analog and QAM HD stations from Time Warner cable.  The device absolutely exceeds my expectations in Windows Media Center on Windows 7.. beautiful picture and flawless operation.  

Running under Mythbuntu 10.04 though, this is a completely different story.  Both analog and dvb device nodes are created under /dev, but all attempts to use them have failed.  I can't even scan for channels or cat a signal out of /dev/video0.

The tuner is clearly being detected, but for whatever reason the device never finishes loading.  My eyes burn from Googling solutions to this.. can anyone give me some direction?

Thanks

 [  450.962468] usb 1-1: new high speed USB device using ehci_hcd and address 3
  [  451.645033] usb 1-1: configuration #1 chosen from 1 choice
  [  452.036102] cx25840' 0-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
  [  452.142202] tuner' 0-0042: chip found @ 0x84 (pvrusb2_a)
  [  452.142259] tda9887 0-0042: creating new instance
  [  452.142261] tda9887 0-0042: tda988[5/6/7] found
  [  452.321153] tveeprom 0-00a2: Hauppauge model 75111, rev D2F5, serial# 7274161
  [  452.321157] tveeprom 0-00a2: MAC address is 00-0D-FE-6E-FE-B1
  [  452.321158] tveeprom 0-00a2: tuner model is unknown (idx 155, type 0)
  [  452.321160] tveeprom 0-00a2: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
  [  452.321161] tveeprom 0-00a2: audio processor is CX25843 (idx 37)
  [  452.321163] tveeprom 0-00a2: decoder processor is CX25843 (idx 30)
  [  452.321164] tveeprom 0-00a2: has radio, has IR receiver, has IR transmitter
  [  452.321169] pvrusb2: Supported video standard(s) reported available in hardware: PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB
  [  452.321171] pvrusb2: Mapping standards mask=0x300b700 (PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB)
  [  452.321174] pvrusb2: Setting up 6 unique standard(s)
  [  452.321176] pvrusb2: Set up standard idx=0 name=PAL-M
  [  452.321178] pvrusb2: Set up standard idx=1 name=PAL-N
  [  452.321180] pvrusb2: Set up standard idx=2 name=PAL-Nc
  [  452.321181] pvrusb2: Set up standard idx=3 name=NTSC-M
  [  452.321182] pvrusb2: Set up standard idx=4 name=NTSC-Mj
  [  452.321184] pvrusb2: Set up standard idx=5 name=NTSC-Mk
  [  452.321186] pvrusb2: Initial video standard (determined by device type): NTSC-M
  [  452.321194] pvrusb2: Device initialization completed successfully.
  [  452.351099] pvrusb2: registered device video0 [mpeg]
  [  452.351103] DVB: registering new adapter (pvrusb2-dvb)
  [  452.491195] cx25840' 0-0044: firmware: requesting v4l-cx25840.fw
  [  456.745440] cx25840' 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
  [  457.823607] cx25840' 0-0044: Video signal:              not present
  [  457.823611] cx25840' 0-0044: Detected format:           NTSC-M
  [  457.823613] cx25840' 0-0044: Specified standard:        NTSC-M
  [  457.823615] cx25840' 0-0044: Specified video input:     Composite 7
  [  457.823617] cx25840' 0-0044: Specified audioclock freq: 48000 Hz
  [  457.879505] cx25840' 0-0044: Detected audio mode:       forced mode
  [  457.879507] cx25840' 0-0044: Detected audio standard:   no detected audio standard
  [  457.879509] cx25840' 0-0044: Audio muted:               no
  [  457.879510] cx25840' 0-0044: Audio microcontroller:     detecting
  [  457.879512] cx25840' 0-0044: Configured audio standard: automatic detection
  [  457.879513] cx25840' 0-0044: Configured audio system:   BTSC
  [  457.879514] cx25840' 0-0044: Specified audio input:     Tuner (In8)
  [  457.879516] cx25840' 0-0044: Preferred audio mode:      stereo
  [  457.879519] tda9887 0-0042: Data bytes: b=0xd4 c=0x30 e=0x44
  [  458.047702] cx25840' 0-0044: firmware: requesting v4l-cx25840.fw
  [  462.089935] cx25840' 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
  [  462.625202] usb 1-1: firmware: requesting v4l-cx2341x-enc.fw
  [  463.155494] cx25840' 0-0044: 0x0000 is not a valid video input!
  [  463.719852] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
  [  463.751476] tda18271 0-0060: creating new instance
  [  463.754011] tda18271_read_regs: ERROR: i2c_transfer returned: -5
  [  463.754026] Unknown device detected @ 0-0060, device not supported.
  [  463.759508] tda18271_read_regs: ERROR: i2c_transfer returned: -5
  [  463.759510] Unknown device detected @ 0-0060, device not supported.
  [  463.759512] tda18271_attach: error -22 on line 1170
  [  463.759514] tda18271 0-0060: destroying instance

I am having the exact same issues. Any solution would be much appreciated...

I notice that Mythbuntu 10.10 comes with Linux 2.6.35, and that in turn contains a newer pvrusb2. Would it be worthwhile to upgrade to 10.10 beta now? Can I simply install 10.10 beta over 10.04, and then 10.10 final release over 10.10 beta when it comes out?

---

### Post by saedelaere on 2010-10-08
[TV-Viewer]("http://tv-viewer.sourceforge.net") is an alternative Software to watch analogue TV with devices that have a build-in hardware MPEG2 encoder. If you are running Ubuntu 10.04 64bit and get segfaults when starting the application have a look at this [howto]("http://tv-viewer.sourceforge.net/mediawiki/index.php/Howto#Replacing_included_Tcl.2FTk_packages_with_ActiveTcl")

Regards

---

### Post by notanumber67890 on 2010-11-02
Here is some new information that might help someone more talented to get this hardware working:

The accepted solution of downloading and installing an old version of the [extracted firmware driver]("http://www.steventoth.net/linux/hvr1950/v4l-pvrusb2-73xxx-01.fw") does work, but only for older versions of the WinTV-HVR-1950.  

Newer versions of the WinTV-HVR-1950 do not work with the accepted solution. Specifically, I can confirm that the WinTV-HVR-1950 **REV C3E9** works with the accepted solution, but the WinTV-HVR-1950 **REV D2F5** does not. Instead of loading successfully, the REV D2F5 version seems to go well until the following errors are posted:

```
DVB: registering new adapter (pvrusb2-dvb)
cx25840 0-0044: firmware: requesting v4l-cx25840.fw
cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
usb 2-1.1: firmware: requesting v4l-cx2341x-enc.fw
DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
tda18271 0-0060: creating new instance
Unknown device detected @ 0-0060, device not supported.
Unknown device detected @ 0-0060, device not supported.
tda18271 0-0060: destroying instance
```

Unfortunately, using the latest firmware drivers doesn't work. As others have found, it is possible to extract a newer firmware driver from the installation CD (or from the latest driver Hauppauge's website) using a [script]("http://www.isely.net/downloads/fwextract.pl"). However, linux fails to load the firmware file, producing the following error:

```
pvrusb2: wrong fx2 firmware size
pvrusb2: Failure uploading firmware
```

So it seems to me the problem might be solved by using a newer driver, if only linux could load it.  

Can anyone help from here?

---

### Post by cooper76 on 2010-11-02
> **notanumber67890 said:**
> 

Unfortunately, using the latest firmware drivers doesn't work. As others have found, it is possible to extract a newer firmware driver from the installation CD (or from the latest driver Hauppauge's website) using a [script]("http://www.isely.net/downloads/fwextract.pl"). However, linux fails to load the firmware file, producing the following error:

```
pvrusb2: wrong fx2 firmware size
pvrusb2: Failure uploading firmware
```

So it seems to me the problem might be solved by using a newer driver, if only linux could load it.  

Can anyone help from here?

The reason that the newer firmware is not loading is because the linux kernel in 10.04 doesn't support the larger firmware. (See [http://www.isely.net/pvrusb2/setup.html#Firmware](http://www.isely.net/pvrusb2/setup.html#Firmware) and the "Important" section) 

I just got my 1950 and I haven't had time to attempt the setup.

---

