---
title: "TV Card Problems"
date: 2009-02-07
forum: Multimedia Software
---

### Post by Keenan-Windel on 2009-02-07
I've searched the web for days, and, as a last-ditch effort, I'm asking for help. I recently purchased a Hauppauge WinTV HVR-850, and this post [http://dougsland.livejournal.com/tag/850](http://dougsland.livejournal.com/tag/850) suggests that analog TV is possible with this model in Linux (the TV program he uses, tvtime, only does analog). By the way, I need analog because I have to run my cable TV through the set top box in order to watch the standard cable channels that Comcast kindly encrypts for me, so I need to tune to analog channel three or four I would think.

The trouble I'm having is that mythtv recognizes only the /dev/dvb/adapter0 (digital) part of this hybrid card and, though I've installed the video4linux drivers, no /dev/video0 is created according to dmesg and tvtime can't open the card. What am I doing wrong?

The steps I have taken are:

- I installed the xc5000 firmware to /lib/firmware
- I compiled and installed the video4linux modules
- a driver is loaded when I plug in the card which, according to dmesg, is called au0828

But again, when I open mythtv, only the digital part of this card will pick up channels. Is analog even possible with this card? I've heard both yes and no in searching the web.

Here is the pertinent dmesg output:

[ 1992.052481] au0828 driver loaded
[ 1992.412228] au0828: i2c bus registered
[ 1992.510249] tveeprom 0-0050: Hauppauge model 72301, rev B3F0, serial# 6085502
[ 1992.510264] tveeprom 0-0050: MAC address is 00-0D-FE-5C-DB-7E
[ 1992.510272] tveeprom 0-0050: tuner model is Xceive XC5000 (idx 150, type 4)
[ 1992.510280] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 1992.510287] tveeprom 0-0050: audio processor is AU8522 (idx 44)
[ 1992.510294] tveeprom 0-0050: decoder processor is AU8522 (idx 42)
[ 1992.510307] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[ 1992.510315] hauppauge_eeprom: hauppauge eeprom: model=72301
[ 1992.643971] xc5000 0-0061: creating new instance
[ 1992.646224] xc5000: Successfully identified at address 0x61
[ 1992.646236] xc5000: Firmware has not been loaded previously
[ 1992.646244] DVB: registering new adapter (au0828)
[ 1992.646253] DVB: registering adapter 0 frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[ 1992.647097] Registered device AU0828 [Hauppauge HVR850]
[ 1992.647186] usbcore: registered new interface driver au0828
[ 1992.807068] usbcore: registered new interface driver snd-usb-audio


Notice that no /dev/video0 is created.

Thanks in advance for any help or suggestions! The digital part works fine, but I need analog.

Keenan

---

### Post by Keenan-Windel on 2009-02-07
Okay, I at least can explain why analog doesn't work. There are two different chipsets used in the Hauppauge HVR-850 - one uses the AU0828 driver, the other uses the em28xx driver. I apparently have the former chipset, and the driver doesn't do analog, so udev therefore fails to make a video4linux device at /dev/video0. 

This explains why in the link I posted above tvtime works - it was a different driver, em28xx, that was making it work in analog mode. I tried blacklisting the au0828 driver in the hopes that my card would use the em28xx driver instead, but no luck with that.

Oh well, I just wanted to post this in case anyone else runs into the same dilemma.

Keenan

---

### Post by davis68nf on 2013-02-05
SOLVED!


 I had trouble with my tvtime too. HVR-850 sent a video, but there was no audio. The volume was set at 0 and would not move.


 The solution I found was here:
[http://kimbriggs.com/computers/computer-notes/linux-notes/tvtime-volume-notes.file](http://kimbriggs.com/computers/computer-notes/linux-notes/tvtime-volume-notes.file)
 ---------------------------------------
 In a nutshell, type:
  sudo gedit /etc/tvtime/tvtime.xml

and change the line:
  <option name="MixerDevice" value="/dev/mixer:vol"/>


 So, my tvtime.xml now reads:
  <option name="MixerDevice" value="HVR850:vol"/>


 The OLD code used to read:
  <option name="MixerDevice" value="default/Line"/>

---

### Post by wildmanne39 on 2013-02-05
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

