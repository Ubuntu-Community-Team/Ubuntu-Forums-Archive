---
title: "Seeking Advice for MythTV box"
date: 2009-04-07
forum: Multimedia Software
---

### Post by kdx on 2009-04-07
I impulsively purchased an [eMachines EL1210-09]("http://www.newegg.com/Product/Product.aspx?Item=N82E16883114070") for $280 today at Staples with the intention of turning it into a DVR/HTPC with Ubuntu and MythTV (or potentially just Mythbuntu).  It's got an AMD Athlon x64 processor (LE-1620), 2GB RAM (expandable to 4GB), HDMI output, and a 160GB HDD.  

I've been reading up on MythTV and Hauppauge TV tuner cards, but I'm having some difficulty figuring out exactly where to go from here.  Most of the information I've found relates to the older, analog-only PVR-X50 cards.

According to Newegg, this PC has one PCI-E x16 slot available.  I would like to verify that a Hauppauge PCI-E x1 card will work properly in this slot.  I've read that x1 cards will fit into x16 slots, but may not always be enabled in the BIOS.  If it will work, I'm most likely headed for the [Hauppauge WinTV-HVR-1800 MCE]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116016") card.  If I can't do the PCI-E card, it looks like I'll have to go to a USB card, but it doesn't seem that any of the USB-based cards handle hardware encoding, which may be an issue for the eMachine.  Any thoughts on this?  

My next snag is that I don't have an HDTV yet, so the HDMI-out isn't quite useful at this point in time.  The only other video out on this computer is VGA.  First, does anybody know if the NVIDIA GeForce 8200 GPU supports TV-out through VGA?  I'm hopeful that it does, especially since it supports HDMI-out, although I'm not certain they'd even relate to each other in any way.  If it supports TV-out, I can just buy a $10 VGA-to-composite cable.  If not, I'll have to buy a converter box for it, which seem to run anywhere from $100-$250+.  If that's the case, does anybody know of a relatively cheap and effective way to get VGA to RCA/composite output?  I could just run this system headless as a DVR only, except that I don't have a monitor that I could hook up to it for the initial setup and troubleshooting! :icon_frown:

Hopefully this is much easier than I'm making it out to be, but the information I'm looking for seems a bit sparse.  Either that, or I'm just a n00b... \\:D/

---

### Post by kdx on 2009-04-08
Bumpity.

---

### Post by CJ_Hudson on 2009-04-08
I thought most modern TVs had a VGA input socket. Some will show setup info i.e. while the system is booting and inbetween 'splash' screens, others not.
I suggest approaching a few businesses who may have just upgraded their systems and are throwing out old CRT monitors. You might be able to get one free, then you can do the system setup.
  Sorry I can't assist with any other of the problems at the moment.

---

### Post by kdx on 2009-04-08
Thanks for the reply.  My TV is about 10 years old, and I didn't see a VGA input on it.  I solved this dilemma, though, by purchasing a 23" HP LCD monitor to use instead (it was a display model, so I got around $100 off).  I figured it would be a lot less hassle than trying to figure out how to use the TV, and it would give me a better picture.  Plus, with the HDMI input, I could also play Xbox 360 on it in HD. :D

I've also gotten my question answered about the PCI-E slots; the TV card should supposedly work without any issues.

---

### Post by Berryjiveuptown5 on 2009-04-11
please let me us which card you go with.  i'm trying to set up mythtv too and would like to know which one works before I buy one.

---

### Post by kdx on 2009-04-12
> **Berryjiveuptown5 said:**
> please let me us which card you go with.  i'm trying to set up mythtv too and would like to know which one works before I buy one.

I ended up getting the Hauppauge HVR-1950 USB card.  I decided that I preferred to leave the PCI-E slot open in case I wanted to add a different video card later on, and that I also didn't want to be locked into using the card in only a computer with a PCI-E slot available.

I'm running Ubuntu Intrepid x64 on the system, and it's working really great so far; the remote is even supported right out of the box!  Just follow [these]("http://sray.squidpower.com/2009/02/18/hauppauge-wintv-hvr-1950-on-linux-mythbuntu-mythtv-analog-digital-video-including-s-video-and-composite-inputs/") instructions and you should be all set.

One thing I did notice is that I needed to change the permissions for /dev/video0 to allow the mythtv group to access the device.  If I didn't, the mythbackend server wouldn't be able to connect to /dev/video0.  By default upon connecting the box, only the root and video groups have access.  As of right now, I have to manually change this every time the box is disconnected or I restart the computer.  It was a real pain while I was working on setting up the system, but now that it's all set and running all the time, it's not a big deal for now.

---

### Post by CJ_Hudson on 2009-04-14
Why not edit the startup/boot kernal to include a little code to set that up automatically?

---

### Post by kdx on 2009-04-14
> **MogBug said:**
> Why not edit the startup/boot kernal to include a little code to set that up automatically?

That would be a fantastic idea if I knew how to do it... #-o

---

### Post by kdx on 2009-04-14
Just to be on the safe side in case the site I linked earlier ever goes down, here's a copy-paste of the instructions on the site.  

   1. Fresh install of mythbuntu 9.04
   2. Extract and install the firmware files for HVR-1950:
         1. Download [http://www.isely.net/downloads/fwextract.pl](http://www.isely.net/downloads/fwextract.pl) to ~/Desktop
         2. Insert the CD that came with your HVR-1950 (contains windows drivers) [assume it mounted as /media/cdrom0]
         3. cd ~/Desktop
         4. chmod u+x fwextract.pl
         5. ./fwextract.pl /media/cdrom0/Drivers/
         6. sudo copy *.fw /lib/firmware
   3. Run mythtv-setup using sudo
         1. sudo mythtv-setup
         2. Capture Card Type: IVTV MPEG-2 encoder card
         3. Video device: /dev/video0
         4. Probed info: WinTV HVR-1950 Model Category 7 [pvrusb2]
   4. Run mythtvfrontend
   5. (if the video looks really bad in mythfrontend):
         1. Utilities/Setup
         2. Setup
         3. TV Settings
         4. Recording Profiles
         5. MPEG-2 Encoders (PVR-x50, PVR-500)
         6. for Live TV, Default, High Quality, Low Quality
               1. Change Width to 720
               2. Change Height to 480

Once again, here's the link:
[http://sray.squidpower.com/2009/02/18/hauppauge-wintv-hvr-1950-on-linux-mythbuntu-mythtv-analog-digital-video-including-s-video-and-composite-inputs/](http://sray.squidpower.com/2009/02/18/hauppauge-wintv-hvr-1950-on-linux-mythbuntu-mythtv-analog-digital-video-including-s-video-and-composite-inputs/)

---

### Post by sforces on 2009-04-16
I've been trying to get my HVR-1950 to work since Jan. `09. So I'm glad to hear someone's gotten this device to work on Linux and an Ubuntu variant that's also 64bit. :) Now I know the instructions say to use "mythbuntu 9.04" but I've been using Ubuntu and currently on 8.10 64bit and would really like to get it to work if it's possible. Perhaps I need to wait for Ubuntu 9.04 next week to try (sigh)?

On the hopes that it "might work" now, I've installed Mythtv packages and followed the rest of the install. I don't have a /dev/video0 directory. :(

Doing a dmesg I do see that things do get recognized (not sure if correctly though). Any advice on getting this to work?:
[   17.065249] Linux video capture interface: v2.00
[   17.279358] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.279386] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.311384] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   17.449812] usbcore: registered new interface driver pvrusb2
[   17.449830] pvrusb2: Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner : V4L in-tree version
[   17.449832] pvrusb2: Debug mask is 31 (0x1f)
[   17.624036] cx25840' 0-0044: cx25843-24 found @ 0x88 (pvrusb2_a)
[   17.801332] tuner' 0-0042: chip found @ 0x84 (pvrusb2_a)
[   17.825298] tveeprom 0-00a2: Hauppauge model 75111, rev C3E9, serial# 5055510
[   17.825300] tveeprom 0-00a2: MAC address is 00-0D-FE-4D-22-15
[   17.825302] tveeprom 0-00a2: tuner model is Philips 18271_8295 (idx 149, type 54)
[   17.825303] tveeprom 0-00a2: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   17.825305] tveeprom 0-00a2: audio processor is CX25843 (idx 37)
[   17.825306] tveeprom 0-00a2: decoder processor is CX25843 (idx 30)
[   17.825307] tveeprom 0-00a2: has radio, has IR receiver, has IR transmitter
[   17.825311] pvrusb2: Supported video standard(s) reported available in hardware: PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB
[   17.825313] pvrusb2: Mapping standards mask=0x300b700 (PAL-M/N/Nc;NTSC-M/Mj/Mk;ATSC-8VSB/16VSB)
[   17.825315] pvrusb2: Setting up 6 unique standard(s)
[   17.825317] pvrusb2: Set up standard idx=0 name=PAL-M
[   17.825318] pvrusb2: Set up standard idx=1 name=PAL-N
[   17.825319] pvrusb2: Set up standard idx=2 name=PAL-Nc
[   17.825320] pvrusb2: Set up standard idx=3 name=NTSC-M
[   17.825322] pvrusb2: Set up standard idx=4 name=NTSC-Mj
[   17.825323] pvrusb2: Set up standard idx=5 name=NTSC-Mk
[   17.825324] pvrusb2: Initial video standard (determined by device type): NTSC-M
[   17.825329] pvrusb2: Device initialization completed successfully.
[   17.825391] pvrusb2: registered device video0 [mpeg]
[   17.825393] DVB: registering new adapter (pvrusb2-dvb)
[   17.838078] firmware: requesting v4l-cx25840.fw
[   20.183518] cx25840' 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   25.058472] cx25840' 0-0044: Video signal:              not present
[   25.058475] cx25840' 0-0044: Detected format:           NTSC-M
[   25.058477] cx25840' 0-0044: Specified standard:        NTSC-M
[   25.058478] cx25840' 0-0044: Specified video input:     Composite 7
[   25.058480] cx25840' 0-0044: Specified audioclock freq: 48000 Hz
[   25.064597] cx25840' 0-0044: Detected audio mode:       mono
[   25.064599] cx25840' 0-0044: Detected audio standard:   no detected audio standard
[   25.064600] cx25840' 0-0044: Audio muted:               no
[   25.064602] cx25840' 0-0044: Audio microcontroller:     detecting
[   25.064603] cx25840' 0-0044: Configured audio standard: automatic detection
[   25.064605] cx25840' 0-0044: Configured audio system:   BTSC
[   25.064606] cx25840' 0-0044: Specified audio input:     Tuner (In8)
[   25.064607] cx25840' 0-0044: Preferred audio mode:      stereo
[   25.113357] cx25840' 0-0044: 0x0000 is not a valid video input!
[   27.627710] DVB: registering frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   60.190461] bttv: driver version 0.9.17 loaded
[   60.190467] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   60.280877] ivtv:  Start initialization, version 1.4.0
[   60.281931] ivtv:  End initialization
[   60.441007] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   60.442269] lirc_i2c: chip 0x10005 found @ 0x1a (Hauppauge IR)
[   60.442300] lirc_dev: lirc_register_plugin: sample_rate: 10
[   64.440104] pvrusb2: Timed out control-write
[   64.440108] pvrusb2: Device being rendered inoperable
[   64.440122] pvrusb2: Attempted to execute control transfer when device not ok
[   64.440126] pvrusb2: Attempted to execute control transfer when device not ok
[   64.440127] pvrusb2: Attempted to execute control transfer when device not ok
[   64.440129] pvrusb2: Attempted to execute control transfer when device not ok
[   64.440131] pvrusb2: Attempted to execute control transfer when device not ok
[   64.440133] pvrusb2: Attempted to execute control transfer when device not ok

---

### Post by sforces on 2009-04-16
While I've not gotten Mythtv to work under Ubuntu 8.10 I did get the following to work for me, so maybe it helps someone too:
Using pvrusb2, if I go to VLC and open a capture device, then set it to PVR and from terminal I can use ivtv-tune to change the channels. Audio & video working perfectly.

---

### Post by kdx on 2009-04-16
> **sforces said:**
> I've been trying to get my HVR-1950 to work since Jan. `09. So I'm glad to hear someone's gotten this device to work on Linux and an Ubuntu variant that's also 64bit. :) Now I know the instructions say to use "mythbuntu 9.04" but I've been using Ubuntu and currently on 8.10 64bit and would really like to get it to work if it's possible. Perhaps I need to wait for Ubuntu 9.04 next week to try (sigh)?

On the hopes that it "might work" now, I've installed Mythtv packages and followed the rest of the install. I don't have a /dev/video0 directory. :(


I used Ubuntu 8.10 x64, installed the drivers following the instructions, hooked up the HVR-1950, ran lsusb to see if my Hauppauge card showed up (it did), and then installed MythTV.  I had a more difficult time setting up the USB wireless adapter than I did with the tuner.

The only suggestion I might have is disconnecting the HVR-1950 and reconnecting it, then run lsusb to see if it shows up.  I noticed that on occasion mine wouldn't be recognized right away after a boot, but disconnecting and reconnecting seemed to do the trick.  Also, whenever mine was connecting to the computer, the red LED on the front would turn on, so that might give an indication as well.

I unfortunately don't think I have much advice other than that.  My install was surprisingly rather painless.

---

### Post by sforces on 2009-04-28
Thanks for that though. I learned something still. :) I had not realized that instead of me trying to get the Mythtv packages installed on Ubuntu that it was possible to get Mythubuntu packages on top of Ubuntu as well and have it be more natively integrated.

I've since uninstalled Mythubuntu since it hadn't worked (everytime I click on Watch LiveTv) it flickers for a little bit and brings me back to the main screen.

And now that Ubuntu 9.04 is out I upgraded this past weekend. After a reboot the dev/video0 directory was missing but unplugging and replugging the HVR-1950 made it come back and now there's a dev/dvb/adapter0 directory too. Anyone know if there's something that will work with that (dvb I mean in the HVR?).

I'll probably try next week to install the Mythubuntu packages on 9.04. But for now I've tested that VLC in 9.04 (as it did in 8.10) using PVR and dev/video0 works for the video & audio and ivtv-tune -c works for changing channels.

> **kdx said:**
> I used Ubuntu 8.10 x64, installed the drivers following the instructions, hooked up the HVR-1950, ran lsusb to see if my Hauppauge card showed up (it did), and then installed MythTV.  I had a more difficult time setting up the USB wireless adapter than I did with the tuner.

The only suggestion I might have is disconnecting the HVR-1950 and reconnecting it, then run lsusb to see if it shows up.  I noticed that on occasion mine wouldn't be recognized right away after a boot, but disconnecting and reconnecting seemed to do the trick.  Also, whenever mine was connecting to the computer, the red LED on the front would turn on, so that might give an indication as well.

I unfortunately don't think I have much advice other than that.  My install was surprisingly rather painless.

---

### Post by kdx on 2009-04-28
> **sforces said:**
> Thanks for that though. I learned something still. :) I had not realized that instead of me trying to get the Mythtv packages installed on Ubuntu that it was possible to get Mythubuntu packages on top of Ubuntu as well and have it be more natively integrated.

I've since uninstalled Mythubuntu since it hadn't worked (everytime I click on Watch LiveTv) it flickers for a little bit and brings me back to the main screen.

And now that Ubuntu 9.04 is out I upgraded this past weekend. After a reboot the dev/video0 directory was missing but unplugging and replugging the HVR-1950 made it come back and now there's a dev/dvb/adapter0 directory too. Anyone know if there's something that will work with that (dvb I mean in the HVR?).

I'll probably try next week to install the Mythubuntu packages on 9.04. But for now I've tested that VLC in 9.04 (as it did in 8.10) using PVR and dev/video0 works for the video & audio and ivtv-tune -c works for changing channels.

Well I'm glad I could help a little bit.

Try this though.  Open up the terminal and enter:
```
sudo chmod 0777 /dev/video0
```

...then:
```
sudo killall mythbackend
```

...and:
```
mythbackend
```

...then start up the frontend again and see if that helps.  I've found that any time I try to watch LiveTV and it flickers and sends me back to the main screen, this is what solves it.  If that works, you could even write a script to do this for you:

```
sudo gedit ~/.tunerpermissions
```

...then paste this into the file:

```
!#/bin/bash
sudo chmod 0777 /dev/video0
sudo killall mythbackend
mythbackend
```

...then save and close.  Open up the terminal and enter:

```
sudo chmod 0777 ~/.tunerpermissions
```

Then make a launcher on your panel if you wish:
Right-click on the panel
Click "Add to panel"
Click "Custom Application Launcher"
Change "Type" from "Application" to "Application in Terminal"
Paste "/home/<your username>/.tunerpermissions" into the "Command" box
Choose an icon for it if you wish
Click "Close"

Then every time you encounter this problem, just close the frontend, click the icon, enter your sudo password if it asks, wait for the terminal to close, and open the frontend back up again.  You could even add "mythfrontend" to the end of the script file to automatically startup the frontend for you after it does the switch.

I've also found that this typically happens on startup, so you could add the script to run on startup by going to System > Preferences > Sessions and adding the "/home/<your username>/.tunerpermissions" command.  

What happens on my system is that the mythtv group won't have access to /dev/video0.  The chmod 077 will fix this issue, but it reappears again any time the tuner is disconnected or the computer restarts.  It may still work with VLC even if this is the case.

I hope I was able to help.

---

### Post by kdx on 2009-04-28
Also, if you've never scanned for channels in the mythbackend setup, you need to do that before you can watch TV.

---

