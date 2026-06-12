---
title: "Hauppauge USB-Live2"
date: 2010-09-02
forum: Multimedia Software
---

### Post by don51 on 2010-09-02
I purchased a Hauppauge USB-Live2 video capture device.  I've been looking for the driver to load in my Ubuntu machine for the device.  I've found a few sites that say a driver was found, but no link to the specific information.  Is there a sudo command to load the driver?

I did find what I thought would be the answer, information about Hauppauge WinTV.  I ran sudo apt-get install tvtime.  I'm able to see TVtime Television Viewer under Applications, Sound & Video.  But that does not get me the driver I need.

I loaded the device and CD on my wife's Windows computer just to see how it all worked.  I was able to get through the process and see image from a camera that is connected to the Hauppauge USB-Live2 device.  But who wants to mess with Windows when I have a real computer like Linux.

I'll keep trying to look for a solution.

The reason why I am doing this to to get ZoneMinder to operate on my Ubuntu computer.  I'm trying to use an existing camera that has RCA connectors.  I asked a Linux minded friend at work and he suggested I upgrade to 10.04 and see if the driver is loaded in that version.

Now I have another question.  Could I have just bought a card for my Ubuntu computer that has RCA connectors?  Could I have just plugged the output from the camera into that card and have it work on Ubuntu?

Thanks, Don

---

### Post by jimko on 2010-09-06
I was just looking at this device myself for digitizing 8mm home movies. It might be new because there is very little info about it. Analog video capture in Linux has been a tough thing to do. You can [look here for drivers]("http://www.linuxtv.org/wiki/index.php/Video_via_USB"), but there are none specifically for this device yet. I've tried a competing device from Pinnacle, but couldn't get it to work correctly under Linux. I could see the device and load a module, but the video was always unusably bad quality (missing scan lines, missing a color, no sound, etc) and I just couldn't get it tuned. No GUI capture programs either.

The best conversions I ever got were by recording onto DVD using a Panasonic DVD Recorder and then ripping the dvd. But that won't help you with ZoneMinder. Sorry it's not been much help.

You're going to find the same problems with analog support for internal cards. The best support seems to be with older PCI cards that use the [ivtv drivers.]("http://www.ivtvdriver.org/index.php/Supported_hardware") I have no personal experience with them, but that's where I'd point you to start your research. Good luck.

---

### Post by Wieshka on 2010-09-08
I also purchased Hauppauge USB live 2 and now looking for solution ... my Hauppauge HD PVR already works ... so if any information found, please share ...

Looks like V4L hasn,t supported it yet ...




Later I will check out, does this works: 
[http://www.linuxtv.org/wiki/index.php/Pvrusb2](http://www.linuxtv.org/wiki/index.php/Pvrusb2)

---

### Post by Wieshka on 2010-09-08
```
hg clone http://kernellabs.com/hg/~dheitmueller/polaris4
cd polaris4
sudo -s
make
```The make will fail on ubuntu ... so ...

> You have to edit v4l/.config:
- find CONFIG_DVB_FIREDTV=m
- change the value from manual to none:
-> CONFIG_DVB_FIREDTV=nIt will deactivate build of module, what made make fail
Then:

```
make
make install
```If everything went fine, after reboot (to prevent usage of old drivers), it should work over V4L (for example in VLC)



Give a try - if works, looks like this is solved :)

---

### Post by Wieshka on 2010-09-08
Hmmm after all this install & compiling i got my device recognized, but now i have blue screen

> Sep  8 19:37:19 mediaplayer kernel: [ 6341.940071] usb 2-2: new high speed USB device using ehci_hcd and address 10
Sep  8 19:37:19 mediaplayer kernel: [ 6342.075285] usb 2-2: configuration #1 chosen from 1 choice
Sep  8 19:37:19 mediaplayer kernel: [ 6342.077591] cx231xx #1: New device Hauppauge Hauppauge Device @ 480 Mbps (2040:c200) with 5 interfaces
Sep  8 19:37:19 mediaplayer kernel: [ 6342.077601] cx231xx #1: registering interface 0
Sep  8 19:37:19 mediaplayer kernel: [ 6342.078935] cx231xx #1: registering interface 1
Sep  8 19:37:19 mediaplayer kernel: [ 6342.091234] cx231xx #1: registering interface 5
Sep  8 19:37:19 mediaplayer kernel: [ 6342.093930] cx231xx #1: Identified as Hauppauge USB Live 2 (card=9)
Sep  8 19:37:19 mediaplayer kernel: [ 6342.173024] cx231xx #1: cx231xx_dif_set_standard: setStandard to ffffffff
Sep  8 19:37:19 mediaplayer kernel: [ 6342.186428] cx25840 7-0044: cx23102 A/V decoder found @ 0x88 (cx231xx #1)
Sep  8 19:37:19 mediaplayer kernel: [ 6342.198126] cx25840 7-0044: firmware: requesting v4l-cx231xx-avcore-01.fw
Sep  8 19:37:21 mediaplayer kernel: [ 6344.164491] cx25840 7-0044: loaded v4l-cx231xx-avcore-01.fw firmware (16382 bytes)
Sep  8 19:37:21 mediaplayer kernel: [ 6344.197734] cx231xx #1: cx231xx #1: v4l2 driver version 0.0.1
Sep  8 19:37:21 mediaplayer kernel: [ 6344.219495] cx231xx #1: cx231xx_dif_set_standard: setStandard to ffffffff
Sep  8 19:37:21 mediaplayer kernel: [ 6344.264603] cx231xx #1: video_mux : 0
Sep  8 19:37:21 mediaplayer kernel: [ 6344.264610] cx231xx #1: do_mode_ctrl_overrides : 0xb000
Sep  8 19:37:21 mediaplayer kernel: [ 6344.265346] cx231xx #1: do_mode_ctrl_overrides NTSC
Sep  8 19:37:21 mediaplayer kernel: [ 6344.272072] cx231xx #1: cx231xx #1/0: registered device video1 [v4l2]
Sep  8 19:37:21 mediaplayer kernel: [ 6344.272163] cx231xx #1: cx231xx #1/0: registered device vbi1
Sep  8 19:37:21 mediaplayer kernel: [ 6344.272170] cx231xx #1: V4L2 device registered as video1 and vbi1
Sep  8 19:37:21 mediaplayer kernel: [ 6344.272177] cx231xx #1: cx231xx-audio.c: probing for cx231xx non standard usbaudio
Sep  8 19:37:21 mediaplayer kernel: [ 6344.273260] cx231xx #1: EndPoint Addr 0x83, Alternate settings: 3
Sep  8 19:37:21 mediaplayer kernel: [ 6344.273272] cx231xx #1: Alternate setting 0, max size= 512
Sep  8 19:37:21 mediaplayer kernel: [ 6344.273280] cx231xx #1: Alternate setting 1, max size= 28
Sep  8 19:37:21 mediaplayer kernel: [ 6344.273288] cx231xx #1: Alternate setting 2, max size= 52
Sep  8 19:37:21 mediaplayer kernel: [ 6344.273299] cx231xx #1: EndPoint Addr 0x84, Alternate settings: 5
Sep  8 19:37:21 mediaplayer kernel: [ 6344.273308] cx231xx #1: Alternate setting 0, max size= 512
Sep  8 19:37:21 mediaplayer kernel: [ 6344.273316] cx231xx #1: Alternate setting 1, max size= 184
Sep  8 19:37:21 mediaplayer kernel: [ 6344.273324] cx231xx #1: Alternate setting 2, max size= 728
Sep  8 19:37:21 mediaplayer kernel: [ 6344.273330] cx231xx #1: Alternate setting 3, max size= 2892
Sep  8 19:37:21 mediaplayer kernel: [ 6344.273337] cx231xx #1: Alternate setting 4, max size= 1800
Sep  8 19:37:21 mediaplayer kernel: [ 6344.273344] cx231xx #1: EndPoint Addr 0x85, Alternate settings: 2
Sep  8 19:37:21 mediaplayer kernel: [ 6344.273353] cx231xx #1: Alternate setting 0, max size= 512
Sep  8 19:37:21 mediaplayer kernel: [ 6344.273360] cx231xx #1: Alternate setting 1, max size= 512
Sep  8 19:37:21 mediaplayer kernel: [ 6344.273367] cx231xx #1: EndPoint Addr 0x86, Alternate settings: 2
Sep  8 19:37:21 mediaplayer kernel: [ 6344.273376] cx231xx #1: Alternate setting 0, max size= 512
Sep  8 19:37:21 mediaplayer kernel: [ 6344.273384] cx231xx #1: Alternate setting 1, max size= 576
Sep  8 19:37:21 mediaplayer kernel: [ 6344.279680] cx231xx #1:  setPowerMode::mode = 48, No Change req.
Sep  8 19:37:21 mediaplayer kernel: [ 6344.281573] cx231xx #1: cx231xx_stop_stream():: ep_mask = 8
Sep  8 19:37:21 mediaplayer kernel: [ 6344.299038] cx231xx #1: cx231xx_stop_stream():: ep_mask = 8
Sep  8 19:37:21 mediaplayer kernel: [ 6344.329146] cx231xx #1:  setPowerMode::mode = 48, No Change req.
Sep  8 19:37:21 mediaplayer kernel: [ 6344.336406] cx231xx #1: cx231xx_stop_stream():: ep_mask = 8
Sep  8 19:37:21 mediaplayer kernel: [ 6344.386334] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
Sep  8 19:37:21 mediaplayer kernel: [ 6344.386844] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
Sep  8 19:37:21 mediaplayer kernel: [ 6344.387907] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
Sep  8 19:37:21 mediaplayer kernel: [ 6344.388292] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
Sep  8 19:37:21 mediaplayer kernel: [ 6344.390087] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
Sep  8 19:37:21 mediaplayer kernel: [ 6344.390708] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
Sep  8 19:37:21 mediaplayer kernel: [ 6344.391773] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
Sep  8 19:37:21 mediaplayer kernel: [ 6344.392963] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
Sep  8 19:37:21 mediaplayer kernel: [ 6344.395188] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
Sep  8 19:37:21 mediaplayer kernel: [ 6344.396149] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
Sep  8 19:37:21 mediaplayer kernel: [ 6344.404133] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
Sep  8 19:37:22 mediaplayer kernel: [ 6344.478607] cx231xx #1: cx231xx_init_audio_isoc: Starting ISO AUDIO transfers
Sep  8 19:37:27 mediaplayer kernel: [ 6349.486451] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4


---

### Post by don51 on 2010-09-12
I have tried this bit of code given to me from my local Linux User's group:

     Code:
     hg clone [http://kernellabs.com/hg/~dheitmueller/polaris4]("http://kernellabs.com/hg/%7Edheitmueller/polaris4") cd polaris4 sudo -s make 
The make will fail on ubuntu ... so ...

     Quote:
                                                 You have to edit v4l/.config:
- find CONFIG_DVB_FIREDTV=m
- change the value from manual to none:
-> CONFIG_DVB_FIREDTV=n                                 
It will deactivate build of module, what made make fail
Then:

     Code:
     make make install 
OK, I found the .config file.  In order to change the contents of the file I changed the owner.
sudo chown don /home/don/polaris4/v4l/.conf
Is there a better code to use to change to contents of a file as root in Ubuntu?

---

### Post by ocgltd on 2010-10-01
This seems to be a driver problem - please report it.

I'm running the same driver (same version).  Video works fine, then suddenly I get a blue screen until I reboot.

---

### Post by uniquegodwin on 2011-06-15
I'm trying and I am unable to view the video at all..
Please see the screenshot of [my desktop here]("http://csharpnews.wordpress.com/2011/06/15/usb-live-2-on-ubuntu-shows-only-black-screen/")..TVTime just displays it black.

I would appreciate any help..
Thanks.

---

