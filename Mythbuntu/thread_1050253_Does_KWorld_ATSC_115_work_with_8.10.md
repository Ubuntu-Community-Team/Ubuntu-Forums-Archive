---
title: "Does KWorld ATSC 115 work with 8.10?"
date: 2009-01-25
forum: Mythbuntu
---

### Post by Lido on 2009-01-25
I tried an ATSC channel scan last night and got nothing so I'm not sure if my signal is the problem or the card/setup isn't working right. I've got the same card working fine in a 7.xx machine, but I'm trying to set up a new one. I found this [thread]("http://ubuntuforums.org/showthread.php?t=959407&highlight=Kworld+115.") that says there's a problem with the card and 8.10, but I tried the patch and nothing seemed to change. Is anyone using the 115 with 8.10 successfully? Should I just try 8.04? Thanks.

---

### Post by owenlinx on 2009-01-27
Yes I am using it now. Do you have the firmware?

cd /usr/src/linux-headers-2.6.27-11/Documentation/video4linux/
sudo ./get_dvb_firmware nxt2004
sudo modprobe saa7134-dvb
sudo sh -c "echo "saa7134-dvb" >> /etc/modules"
sudo echo "options saa7134 i2c_scan=1" > /etc/modprobe.d/saa7134
lspci
look for 
02:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

Oh, one more thing. I didn't have the get_dvb_firmware file I downloaded this one

[https://help.ubuntu.com/community/MythTV_Feisty_hardware_list?action=AttachFile&do=get&target=get_dvb_firmware]("https://help.ubuntu.com/community/MythTV_Feisty_hardware_list?action=AttachFile&do=get&target=get_dvb_firmware")

then try mplayer dvb://
Have fun I just did this so I'll try to help get you running too.

I have 1 question though. How do I add files to mythtv upnp server?
All my ps3 sees is /var/lib/myth file x is in /share

---

### Post by Lido on 2009-01-29
Thanks for the reply. Not sure how that works. I don't even have a directory /etc/modules. Does that matter? Also, my card is being recognized as an "Air2PC v2" already when I do "add card" in Myth and select "DVB..." as the Card type. It goes through the channel scan but never finds any channels.There are tons of this message in the logs:
```
nxt200x: Timeout waiting for nxt2004 to init.
```
.....and a few of these:
```
DVB: frontend 1 frequency 887000000 out of range (54000000..860000000)

```

---

### Post by Lido on 2009-01-29
Anyone have any ideas?

---

### Post by owenlinx on 2009-01-29
I missed a step after you run that perl_get_dvb copy that fle to /lib/firmware
then 
sudo modprobe saa7134-dvb

---

### Post by owenlinx on 2009-01-29
To get the firmware you must...
cd /usr/src/linux-headers-2.6.your running kernel/Documentation/video4linux/ ***see below 
sudo ./get_dvb_firmware nxt2004
sudo cp nxt2004* /lib/firmware/
sudo modprobe saa7134-dvb
sudo sh -c "echo "saa7134-dvb" >> /etc/modules"
sudo echo "options saa7134 i2c_scan=1" > /etc/modprobe.d/saa7134
lspci
look for
02:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

***Oh, one more thing. I didn't have the get_dvb_firmware file I downloaded this one

[https://help.ubuntu.com/community/MythTV_Feisty_hardware_list?action=AttachFile&do=get&target=get_dvb_firmware]("https://help.ubuntu.com/community/MythTV_Feisty_hardware_list?action=AttachFile&do=get&target=get_dvb_firmware")

then try mplayer dvb://

---

### Post by Lido on 2009-01-30
Thanks. This line gives me permission denied (even with sudo):
```
sudo echo "options saa7134 i2c_scan=1" > /etc/modprobe.d/saa7134
```
But regardless, I see this in lspci:
```
01:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
01:07.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
```

I don't have any channels set up in channels.conf so mplayer won't run, but I'm still seeing the card(s) recognized in mythtv-setup as air2pc DVB, which I don't think is necessarily the problem. The problem is the version of the firmware or driver or whatever is messed up I think and it gets recognized but doesn't actually work. I found a patch somewhere on my previous attempt at this install and had the cards working, but as I recall the patch process wasn't smooth and error free and in the end I had no sound and decided to try another install. Tried mythbuntu 8.10 and that was the same but more taxing on my cpu for some reason so I've gone back to standard intrepid with myth installed via synaptec.

---

### Post by owenlinx on 2009-01-30
In myth my card also shows up as "Air2PC v2" I was having the same problem as you with the nxt2004 failed to init. The nxt2004 is firmware you can get it off the install cd or from the link I used. nxt2004 is binary firmware that you have to have in /lib/firmware. Is that done???

[http://www.linuxtv.org/wiki/index.php/Firmware]("http://www.linuxtv.org/wiki/index.php/Firmware")

---

### Post by Lido on 2009-01-30
I did put that firmware into /lib/firmware, but I got that error and nothing seemed to change. I had done an install off the exact same dvd on this machine last week and didn't add firmware and the card was also recognized, but not working. Last time I did the patch mentioned on some thread elsewhere and that fixed it. This time your instructions and a reboot seems to have gotten it working, but I really can never be sure what did what with this Myth stuff. Now I just need to improve my reception (and hope that nothing regresses). I'm marking this thread solved. Thanks for the help!

---

### Post by owenlinx on 2009-01-30
I also compiled the v4l-dvb driver
[http://www.linuxtv.org/repo/]("http://www.linuxtv.org/repo/")

---

### Post by owenlinx on 2009-01-30
over the air reception? I have a cool diy antennae design. I live in tulsa OK and receive stations from Oklahoma City, Dallas.

---

### Post by clasicmac on 2010-06-26
I believe the same thing happened to me when I upgraded to Myth 0.23.  Is everyone else having their Kworld 115 detected as a air2pc on 0.23? I did successfully have the card working before I updated but I can't be sure it wasn't another package update that broke it.

---

### Post by clasicmac on 2010-06-26
Reading through another thread apparently this is normal.  My tuner seems to work fine being detected as an air2pc.

---

