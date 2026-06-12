---
title: "Problems with HVR-1950 in Ubuntu"
date: 2009-05-14
forum: Multimedia Software
---

### Post by KachimiGaNai on 2009-05-14
Okay, I am completely out of ideas at this point, so I am tossing this one out there. I have been trying to install and make work an HVR-1950 USB tuner in Linux since about Christmas time. I have tried numerous variations on the same theme, but nothing seems to work.

This is all from memory, so cut me a little bit of slack. :)

First attempt:

**Ubuntu 8.04 + pvrusb2**

I ended up stumbling upon the PVRUSB2 page, and after a few days recompiled the kernel to make it work in 8.04. This made it show up when I ran dmesg, however the red light never came on, and nothing ever showed up. I never even got /dev/video0.

**Ubuntu 9.04 and Mythbuntu 9.04**

This seems to be closer to success, as I only need to copy the firmware to get it to show up in dmesg as a device. However nothing will come up using TV-Time, MythTV, VLC, or Mplayer.

*cat /dev/video0 > test.mpg* just renders a black mpeg file. 
*w_scan -X* returns this:

> w_scan version 20081106
Info: using DVB adapter auto detection.
   Wrong type, ignoring frontend /dev/dvb/adapter0/frontend0
main:2762: FATAL: ***** NO USEABLE DVB CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.


*w_scan -a /dev/dvb/adapter0 -X* will begin "scanning" through channels, but it never finds anything.

Here is my current lsusb output in Mythbuntu 9.04:

> Bus 001 Device 007: ID 2040:7501 Hauppauge 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 045e:0053 Microsoft Corp. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD
Bus 002 Device 003: ID 046d:c221 Logitech, Inc. G15 Keyboard / Keyboard
Bus 002 Device 002: ID 046d:c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Here is dmesg after I plugin the USB tuner in Mythbuntu 9.04:

> [ 1222.292014] usb 1-1: new high speed USB device using ehci_hcd and address 7
[ 1222.468463] usb 1-1: configuration #1 chosen from 1 choice
[ 1222.555678] cx25840' 2-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
[ 1222.589136] tuner' 2-0042: chip found @ 0x84 (pvrusb2_a)
[ 1222.613061] tveeprom 2-00a2: Hauppauge model 75111, rev C3E9, serial# 5295216
[ 1222.613064] tveeprom 2-00a2: MAC address is 00-0D-FE-50-CC-70
[ 1222.613067] tveeprom 2-00a2: tuner model is Philips 18271_8295 (idx 149, type 54)
[ 1222.613070] tveeprom 2-00a2: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 1222.613073] tveeprom 2-00a2: audio processor is CX25843 (idx 37)
[ 1222.613075] tveeprom 2-00a2: decoder processor is CX25843 (idx 30)
[ 1222.613078] tveeprom 2-00a2: has radio, has IR receiver, has IR transmitter
[ 1222.613083] pvrusb2: Supported video standard(s) reported available in hardware: PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB
[ 1222.613088] pvrusb2: Mapping standards mask=0x300b700 (PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB)
[ 1222.613091] pvrusb2: Setting up 6 unique standard(s)
[ 1222.613094] pvrusb2: Set up standard idx=0 name=PAL-M
[ 1222.613096] pvrusb2: Set up standard idx=1 name=PAL-N
[ 1222.613098] pvrusb2: Set up standard idx=2 name=PAL-Nc
[ 1222.613101] pvrusb2: Set up standard idx=3 name=NTSC-M
[ 1222.613103] pvrusb2: Set up standard idx=4 name=NTSC-Mj
[ 1222.613105] pvrusb2: Set up standard idx=5 name=NTSC-Mk
[ 1222.613108] pvrusb2: Initial video standard (determined by device type): NTSC-M
[ 1222.613116] pvrusb2: Device initialization completed successfully.
[ 1222.613189] pvrusb2: registered device video0 [mpeg]
[ 1222.613194] DVB: registering new adapter (pvrusb2-dvb)
[ 1222.692636] cx25840' 2-0044: firmware: requesting v4l-cx25840.fw
[ 1224.944944] cx25840' 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[ 1225.024460] cx25840' 2-0044: 0x0000 is not a valid video input!
[ 1225.096457] tda829x 2-0042: setting tuner address to 60
[ 1225.120544] tda18271 2-0060: creating new instance
[ 1225.156462] TDA18271HD/C1 detected @ 2-0060
[ 1226.324594] tda829x 2-0042: type set to tda8295+18271
[ 1229.670462] cx25840' 2-0044: Video signal:              not present
[ 1229.670466] cx25840' 2-0044: Detected format:           NTSC-M
[ 1229.670469] cx25840' 2-0044: Specified standard:        NTSC-M
[ 1229.670471] cx25840' 2-0044: Specified video input:     Composite 7
[ 1229.670473] cx25840' 2-0044: Specified audioclock freq: 48000 Hz
[ 1229.677208] cx25840' 2-0044: Detected audio mode:       forced mode
[ 1229.677211] cx25840' 2-0044: Detected audio standard:   forced audio standard
[ 1229.677214] cx25840' 2-0044: Audio muted:               no
[ 1229.677216] cx25840' 2-0044: Audio microcontroller:     stopped
[ 1229.677218] cx25840' 2-0044: Configured audio standard: automatic detection
[ 1229.677221] cx25840' 2-0044: Configured audio system:   BTSC
[ 1229.677223] cx25840' 2-0044: Specified audio input:     External
[ 1229.677225] cx25840' 2-0044: Preferred audio mode:      stereo
[ 1229.740109] cx25840' 2-0044: 0x0000 is not a valid video input!
[ 1232.039099] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[ 1232.053768] tda829x 2-0042: type set to tda8295
[ 1232.120737] tda18271 2-0060: attaching existing instance


The closest I have really ever gotten was I kept fiddling with VLC until the red light came on, and I got a black screen in TV-Time, as well as VLC for a bit, however a reboot got rid of that. I was too drunk with rage and Guinness at that point to remember what commands I was running.

I have tried multiple firmwares, including the 4.6a+ on Hauppague's site, and the ones that came with the CD. I have run *sudo mythtv-setup* and fudged about with permissions, but it never really got anywhere.

Basically, I seem to be missing a key element to the install process.


If I have an Ubuntu 9.04 disc in hand, what steps need to be taken to make it work? I am assuming right now I need to Install Ubuntu > Copy Firmware > Scan Channels > Watch House. However, clearly that is not working.

Any assistance in this regard would be **greatly** appreciated.

---

### Post by sforces on 2009-05-15
I'm on Ubuntu 9.04 but have gotten things to work on 8.10 same.

I've not been able to get my HVR-1950 to work with anything but VLC and using command line to change channels.

I set my VLC capture device to PVR. On "Device Name" I set it to "/dev/video0". This gives me the video on the default channel. Then from command line I use "ivtv-tune -cxx" where xx is the channel number.

Really wish I could get Mythtv or mythbuntu to work.

---

### Post by wirbel2 on 2009-05-16
May be should define *what* you try to receive. :?:

* analog cable TV or..
* digital cable TV or..
* digital aerial TV
* where you're trying to do this

> **KachimiGaNai said:**
> 
*cat /dev/video0 > test.mpg* just renders a black mpeg file. 

Quite understandable. If you dont setup the card by switching (at least!) matching video input and matching video norm this what everybody would expect. And if you choose the TV input, you will have additionally to setup frequency too.
btw: /dev/videoX is *analog* video only.

> 
*w_scan -X* returns this:

Next thing which is wrong here. You're testing **European DVB-T** ;) as this is the *default scanning option *of this tool. **NOTE: w_scan supports only digital TV.** Therefore im wondering what you are trying, analog? digital? cable? aerial?...

> 
*w_scan -a /dev/dvb/adapter0 -X* will begin "scanning" through channels, but it never finds anything.

expected to fail, yes.
Again: your card doesnt support DVB-T (it supports only analog ATSC, and digital cable/aerial). Next mistake: you specified -a, which you should omit (at least if you dont exactly know what you're doing.)
If you try to scan *digital* TV, you should try
```
w_scan -fa -A1 -X
``` or ```
w_scan -fa -A2 -X
```
depending on weather you receive aerial or cable TV.
> 
Basically, I seem to be missing a key element to the install process.
Basically the question what exactly do you want..

---

### Post by saedelaere on 2009-05-19
For analogue cable you could try [TV-Viewer]("http://home.arcor.de/saedelaere/index_eng.html"). It works with all ivtv, pvrusb2 and cx18 based tv-cards. Be sure to install the latest beta!

Regards

---

### Post by KachimiGaNai on 2009-05-19
I'm going to give the suggestions a try tonight and report back with the results. 

I'm just trying to receive and record standard definition digital cable TV. Ideally I'd like to do it over the composite connectors on the HVR-1950, since I'd like to run it through my LocationFree Player. In case it's relevant, it's Charter cable that I am using.

I had figured /dev/video0 would not work for my setup, but I was grasping at straws toward the end. 


I'll report in later tonight.

:)

---

### Post by KachimiGaNai on 2009-05-19
Okay here is the update as promised.

I forgot mention I am in the US (Near Boston specifically) and using standard digital cable. I ran:

**w_scan -fa -A1 -X** and **w_scan -fa -A2 -X** as mentioned. Both did not return any channels, however they didn't complain about my card forcing me to use -a again (which is good).

I ran VLC, opened a capture device, set it to PVR and /dev/video0 and I did get a signal output when using the coax connection on the USB adapter. So this is a nice change, and the first time I've gotten video. :)

However, it is not using the composite side of things. I'd prefer to use that, since I'd have to re-cable my entire setup just to make a coax cable work and the LocationFree player is mere inches from the machine.

---

### Post by wirbel2 on 2009-05-21
> **KachimiGaNai said:**
> (which is good).

No - not good. In case of several tv cards the tool should choose. Probably this -a option should be removed at all.

> 
I ran VLC, opened a capture device, set it to PVR and /dev/video0 and I did get a signal output when using the coax connection on the USB adapter. So this is a nice change, and the first time I've gotten video. :)

So your goal is oldstyle analog video. May be you should try tvtime then (analog only).

---

### Post by saedelaere on 2009-05-29
> **wirbel2 said:**
> No - not good. In case of several tv cards the tool should choose. Probably this -a option should be removed at all.


So your goal is oldstyle analog video. May be you should try tvtime then (analog only).

TVtime won't work with that device. But like I mentioned [TV-Viewer](http://home.arcor.de/saedelaere/index_eng.html) would.

---

### Post by KachimiGaNai on 2009-05-29
Yeah, I tried TVtime, and all it did was complain about not being able to open /dev/video0. I will attempt to use TV-Viewer tonight after work to see if I have better luck there. So far the best result has still come from opening it in VLC under PVR. 

I found this page a few days ago, and had mild success with it.


[http://klk64.com/docs/wintv-hvr-1950.html](http://klk64.com/docs/wintv-hvr-1950.html)

**scantv -c /dev/video0 -C /dev/null -o ~/.xawtv**

This found channel 3 successfully, just like ivtv-tune allows me to set it for VLC. I can also cat /dev/video0 output once I've used ivtv-tune to channel 3.

I am unable to use /dev/dvb/adapter0/dvr0 for anything however, and I assume that's the compositve connector side of the adapter. I also haven't successfully gotten a Gnome application besides VLC to let me view let alone record TV.

I'll see what happens after TV-viewer.

---

### Post by KachimiGaNai on 2009-06-30
I was able to make much more progress by reconnecting my cable and bypassing the cable box altogether. I now go from the cable jack on the wall to a splitter, wherein one end goes to the TV tuner. I am now able to scan for channels without a problem.

MythTV was able to watch live TV via a LiveCD install of Ubuntu, but then when I installed it on the harddrive with the exact same steps it failed. I am consistently able to watch TV via VLC, and I can scan for channels now.

I am going to try an install to hard drive again, and avoid doing updates (I think that is what made the install fubar), and I am going to attempt to use Kaffeine, since I need to be able to schedule recordings in a reasonable manner.

---

### Post by KachimiGaNai on 2009-07-01
Okay, I able to get my HVR-1950 tuner card working in Ubuntu 9.04 with MythTV using the following steps:

```

- Install Ubunutu.

- Copy firmware from 4.6a+ to /lib/firmware.
(4.8 appears to be the latest, but I am not messing with success yet. I extracted the firmware using this site: http://www.isely.net/pvrusb2/pvrusb2.html).

- Power cycle the tuner.

- Check dmesg to see that it's happy.

- chmod go+rw /dev/video0

- Install VLC.

- Run VLC and open the capture device /dev/video0 under PVR.

- Install MythTV (I referenced: http://parker1.co.uk/mythtv_ubuntu.php, but did not follow it to the letter)

- Scan channels for television, and check LiveTV in MythTV.


```

It's all working for me now. I just logged back in and it's still working (which is a first). I still have to alleviate the permissions issues on /dev/video0, but that's minor.

If anyone needs assistance on this, feel free to PM me about it. I am not an expert, but I have a good handle on the steps needed to be taken.

Thanks for the help guys :)

---

### Post by deadland on 2009-10-12
Hello guys,

I have problems get LIRC with the HVR 1950 running correcly. It would be great if you could post your working hardware.conf.

Thanks in advanced.

---

### Post by KachimiGaNai on 2009-10-12
I ended up just connecting directly to the cable jack, so the HVR-1950 can change channels without sending an IR code. It looked like it was going be a massive pain in the *** to get working anyway so I took the easy way out.

---

### Post by deadland on 2009-10-12
Hi KachimiGaNai,

could you send me your lirc hardware.conf, which locks similar to this one:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge HVR-1300"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Command IR : Motorola Cable box"
#TRANSMITTER_MODULES="lirc_dev lirc_cmdir lirc_pvr150"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
TRANSMITTER_LIRCD_ARGS=""
```

and can be found here:

/etc/lirc/hardware.conf

Thanks in advanced.

---

### Post by sforces on 2010-04-22
Thank you! TV-Viewer 0.8.1 worked flawlessly from the first try! 

Back when Ubuntu 8.10 was released, I went with Mythubuntu and actually had it working for a little while. But when 9.04 was released it broke again and 9.10 hasn't fixed it either. I ended up using VLC player and changing channels via command line.

TV-Viewer so far has been working great with my HVR-1950!

> **saedelaere said:**
> For analogue cable you could try [TV-Viewer]("http://home.arcor.de/saedelaere/index_eng.html"). It works with all ivtv, pvrusb2 and cx18 based tv-cards. Be sure to install the latest beta!

Regards

---

