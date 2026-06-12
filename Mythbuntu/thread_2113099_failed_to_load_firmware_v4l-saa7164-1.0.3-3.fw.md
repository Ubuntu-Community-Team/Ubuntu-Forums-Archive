---
title: "failed to load firmware v4l-saa7164-1.0.3-3.fw"
date: 2013-01-11
forum: Mythbuntu
---

### Post by mythtvuser1175 on 2013-01-11
I am having problem to fully load the firmware of Hauppauge  2250 card. I have compiled the driver for both firmware:  v4l-saa7164-1.0.3-3.fw and NXP7164-2010-03-10.1.fw. Both firmware files  are in /lib/firmware.

dmesg only shows it was loading NXP7164-2010-03-10.1.fw. 

Further more, I was able to set card and scan channels in mythtv-setup of adapter0/frontend0 and adapter1/frontend0. 

Furthermore, in the mythtv frontend, it shows:
   Tuner1 is unavailable
   Tuner2 is unavailable
   Tuner9 is not recording
   Tuner11 is not recording

I am not sure what causes the kernel ignores the v4l-saa7164-1.0.3 file. 

It would be great if you can shed some light on this issue.

Thanks,
David

PS: I am running Linux Mint 14. Here is the dmesg:

david@homeserver /etc $ uname -r
3.5.0-21-generic
david@homeserver /etc $ dmesg |grep saa
[    1.836181] saa7164 driver loaded
[    1.836949] CORE saa7164[0]: subsystem: 0070:8880, board: Hauppauge WinTV-HVR2250 [card=3,insmod option]
[    1.836952] saa7164[0]/0: found at 0000:01:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xf7800000
[    1.995280] saa7164_downloadfirmware() no first image
[    1.995292] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[    1.998598] saa7164_downloadfirmware() firmware read 4019072 bytes.
[    1.998600] saa7164_downloadfirmware() firmware loaded.
[    1.998604] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[    1.998609] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[    1.998609] saa7164_downloadfirmware() BSLSize = 0x0
[    1.998610] saa7164_downloadfirmware() Reserved = 0x0
[    1.998611] saa7164_downloadfirmware() Version = 0x1661c00
[    5.802326] saa7164_downloadimage() Image downloaded, booting...
[    5.906420] saa7164_downloadimage() Image booted successfully.
[    8.633601] saa7164_downloadimage() Image downloaded, booting...
[   10.505141] saa7164_downloadimage() Image booted successfully.
[   10.550380] saa7164[0]: Hauppauge eeprom: model=88041
[   11.162878] DVB: registering new adapter (saa7164)
[   14.099675] DVB: registering new adapter (saa7164)
[   14.100009] saa7164[0]: registered device video0 [mpeg]
[   14.330941] saa7164[0]: registered device video1 [mpeg]
[   14.542600] saa7164[0]: registered device vbi0 [vbi]
[   14.542690] saa7164[0]: registered device vbi1 [vbi]

---

### Post by thaibuntu on 2013-02-01
Ditto on this. Did you ever get it resolved? I've googled all I can google. We need some help! 

Installed the firmware on a rev 3 board, but can't get the cards to be recognized by mythbackend setup, but just the digital tuners. It recognizes the analog tuners.

dmesg output looks the same as above. Also each reboot resets prermissions on /dev/dvb. Doing  sudo chgrp -R mythtv /dev/dvb && chmod g+w /dev/dvb will add the mythtv group, but this doesn't help with getting the cards to work with mythbackend.

Please help.

---

### Post by topcat5 on 2013-02-02
> **mythtvuser1175 said:**
> I am having problem to fully load the firmware of Hauppauge  2250 card. I have compiled the driver for both firmware:  v4l-saa7164-1.0.3-3.fw and NXP7164-2010-03-10.1.fw. Both firmware files  are in /lib/firmware.

david@homeserver /etc $ uname -r
**3.5.0-21-generic**

I believe kernal support for the HVR-2250 is different for 3.5 Kernals than 3.2 being used on the current generation of Mythbuntu, so you would not want to follow those instructions.  For 3.5+ you should not need to compile anything.   

I ran against this last fall when I was looking to install Mythtv on Arch.  They are at kernel version 3.7+ and if I remember correctly the HVR-2250 ran fine and scanned perfectly on that level. There was a post about support changing in 3.4 or so.   I recommend that you do a search on the Arch Forums & Wiki for info on the HVR-2250, and follow those instructions. 

[https://www.archlinux.org/]("https://www.archlinux.org/")

---

### Post by thaibuntu on 2013-02-05
So an update on my issue: Switching from XBMCBuntu to Mythbuntu has turned my grey skies blue. I don't know what was different between the two distros, but Mythbuntu worked perfectly. All I had to do was put the firmware in the /lib/firmware directory.
:popcorn:

---

### Post by jlp_engineer on 2013-02-06
> **thaibuntu said:**
> So an update on my issue: Switching from XBMCBuntu to Mythbuntu has turned my grey skies blue. I don't know what was different between the two distros, but Mythbuntu worked perfectly. All I had to do was put the firmware in the /lib/firmware directory.
:popcorn:

Are both the analog and digital tuners working?  I have seen conflicting information on the functionality of the analog tuners for this card.

It would be nice to hear some feedback from a few success stories regarding the analog specifically.  I know most of the focus is on the digital tuners, but that is less than 20% of what my local cable company feeds me (clear QAM).  The rest is analog, with no plans to change.

---

### Post by tgm4883 on 2013-02-06
Moved posts as so much has changed since the old thread was opened (5 years ago). These new posts should really be a new thread.

In case anyone does want reference, the old thread is here
[http://ubuntuforums.org/showthread.php?p=12495549](http://ubuntuforums.org/showthread.php?p=12495549)

---

