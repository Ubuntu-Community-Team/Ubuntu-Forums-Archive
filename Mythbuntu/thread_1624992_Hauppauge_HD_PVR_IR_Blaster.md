---
title: "Hauppauge HD PVR IR Blaster"
date: 2010-11-18
forum: Mythbuntu
---

### Post by Herber on 2010-11-18
I have a Hauppauge HD PVR connected by USB to a Dell 8100 running mythbuntu 10.10, I can record and replay shows but cannot control the Motorola cable box to let mythbuntu change channels.  Is anyone aware of a "HOW TO" to set up the IR blaster for the HD-PVR?

---

### Post by LowSky on 2010-11-18
two link on the subject

[http://ubuntuforums.org/showthread.php?t=1354386](http://ubuntuforums.org/showthread.php?t=1354386)

[http://www.mythtv.org/wiki/Hauppauge_HD-PVR#IR_Transmitter_Support](http://www.mythtv.org/wiki/Hauppauge_HD-PVR#IR_Transmitter_Support)

you can also change channels using firewire if you wish. I find it works better.
[http://webcache.googleusercontent.com/search?q=cache:9R6ZoBNNlisJ:www.mythtv.org/wiki/FireWire+mythtv+firewire&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a](http://webcache.googleusercontent.com/search?q=cache:9R6ZoBNNlisJ:www.mythtv.org/wiki/FireWire+mythtv+firewire&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a)
[http://www.mythtv.org/wiki/Firewire_Cable_Box_Compatibility](http://www.mythtv.org/wiki/Firewire_Cable_Box_Compatibility)

---

### Post by Herber on 2010-11-20
Thanks for the interest in my post.  I was familiar with both the links you provided. When I get to:

#  Enter the hdpvr folder and issue the command make to build the HD-PVR driver.
# Enter the lirc folder and issue the make command to build lirc_dev.ko and lirc_zilog.ko. Note: This tarball contains an updated version of the LIRC driver framework, lirc_dev. If you have other lirc devices on this box you'll need to download and compile updated drivers for them as well. Copy the needed source to this working folder and re-issue the make command to build additional modules. See the LIRC source code included in your distribution. 

And I use the "make" command I get some errors and I do not end up with any *.ko type files.  I think this may be due to the my not being in "root"???

---

