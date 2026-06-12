---
title: "HVR1950 IRblaster on 10.10 help"
date: 2011-04-03
forum: Mythbuntu
---

### Post by kb1gtt on 2011-04-03
I have installed Mythbuntu including Ubuntu 10.10 on a 64 bit laptop using the HVR1950 as the tuner device. I followed the instructions that got the correct firmware installed on the HVR1950, and I can receive video. I'm now trying to use the IRblaster to control my Dish 322 receiver. 

A first noticed issue, is that I don't appear to have /dev/lirc so I guess that means I have a problem with my lirc driver. 

A second potential issue, is that I don't know what script to use to control the Dish 322. 

I found MCC's infrared configuration, but that doesn't seem to work, or perhaps I'm trying to use it incorrectly. I know it tries to scan and only finds channel 3, which is the channel the dish is sending over coax. 

Any suggestions on what script to use, or how to verify what script I'm using would be much appreciated. Also if I can verify that I'm sending anything out the IR would also be great.

---

### Post by kb1gtt on 2011-04-03
A couple more details, it appears the lirc is installed and running.

$ ps -A | grep irc
 1936 ?        00:00:00 lircd
25704 ?        00:00:18 lirc_dev

$ lircd -v
lircd 0.8.7-pre3

$ irw 
connect: Connection refused

$ lsmod | grep ir
lirc_serial            12654  0 
lirc_i2c                7401  0 
lirc_dev               11209  2 lirc_serial,lirc_i2c

$ dmesg | grep irc
[   30.543900] lirc_dev: IR Remote Control driver registered, major 250 
[156116.788268] lirc_dev: module unloaded
[156118.327889] lirc_dev: IR Remote Control driver registered, major 250 
[156118.339745] lirc_i2c: module is from the staging directory, the quality is unknown, you have been warned.
[156118.340926] lirc_i2c: chip 0x0 found @ 0x71 (Hauppauge PVR150)
[156118.341325] i2c ir driver 5-0071: lirc_dev: driver lirc_i2c registered at minor = 0
[187218.406034] lirc_serial: module is from the staging directory, the quality is unknown, you have been warned.
[187219.370042] lirc_serial: auto-detected active high receiver
[187219.370190] lirc_serial lirc_serial.0: lirc_dev: driver lirc_serial registered at minor = 1

I did not find any errors in dmesg of significance.

---

### Post by kb1gtt on 2011-04-04
I got the IR receiver working. Here are some notes that seem to have gotten it working. 

Have the HVR1950 plugged in during boot. Also get it going with out the IRblaster. Using mythbuntu-control-centre select Haupauge TV card. It didn't work out of the gate, however, when I choose the Haupauge DVB, then rebooted. It did not work. Then when I switched back to the TV card, and rebooted, it did work. I think that the switch forced something to update that's not updated when you simply choose that TV card option. It currently works after a reboot, however when I did the ubuntu updates, it broke again, and I had to switch it back to DVB then back to TV card to get it to come out of it. So be warned updates might require this extra step to get your IR receiver working again.

Any one know if the IR blaster has been able to work on Linux? I've read some post(s) from as early as a year ago that indicate it wasn't working at that time. Is that still true? I understand it's using an FX2, and I wonder why the IR can't simply be told it's a serial port, then use the serial IR blasters.

---

### Post by kb1gtt on 2011-04-08
I understand the IR features are available in kernel 2.36.39 and I see I currently have 2.6.35 installed. Is there any way to upgrade my kernel? Right now the only option I see is to compile it and remove a large variety of support options. I'm not sure when it will be released normally. I would like to install via deb file if I can.

---

### Post by kb1gtt on 2011-04-09
I see the beta Mythbuntu 11 is out, which I believe includes the 2.6.38 or newer kernel, so I'm downloading that and will give it a try.

---

### Post by kb1gtt on 2011-04-17
Any one know when kernel 2.6.39 or newer will be officially supported? I found the mainline dev dep install, but that doesn't currently offer support for my wifi card. I'm sure my card will be supported, but as of rc3, it's not.

---

### Post by kb1gtt on 2011-04-28
Not much of a reply here, figure I should at least try to help others. On 64 bit Natty Ubuntu 11.04 Adobe Flash would not work. It would claim it installed, but youtube videos and such would claim I needed to install the plugin. I got it working by following the sudo cp command found here, with a slight modification. 

[http://ubuntuforums.org/showthread.php?t=1698675&page=2](http://ubuntuforums.org/showthread.php?t=1698675&page=2)

My actual command was.

sudo cp libflashplayer.so /usr/lib/chromium-browser/plugins/

---

