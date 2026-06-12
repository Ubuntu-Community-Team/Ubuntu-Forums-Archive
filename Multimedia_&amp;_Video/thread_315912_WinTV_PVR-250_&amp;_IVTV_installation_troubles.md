---
title: "WinTV PVR-250 &amp; IVTV installation troubles"
date: 2006-12-09
forum: Multimedia &amp; Video
---

### Post by Nelson-Ray on 2006-12-09
I pulled out my wintv-pvr-250 card from mythtv box (it didnt co-exist very well with my hdtv cards) so I decided to place it in another ubuntu edgy box I have available. I followed this guide : [https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

as before, but encountered some problems this time around. 

After adding this repository : deb [http://dl.ivtvdriver.org/ubuntu](http://dl.ivtvdriver.org/ubuntu) edgy and adding their key I tried to do sudo apt-get update and got this strange message. 

Failed to fetch [http://dl.ivtvdriver.org/ubuntu/dists/edgy/Release](http://dl.ivtvdriver.org/ubuntu/dists/edgy/Release)  No MD5Sum entry in Release file /var/lib/apt/lists/dl.ivtvdriver.org_ubuntu_dists_edgy_Release

Thinking it might be some server issue on their end..I went to their website and downloaded "ivtv-firmware_20061007-0ubuntu0ivtv2_all.deb" from this [page ]("http://dl.ivtvdriver.org/ubuntu/dists/edgy/firmware/"). Hopefully that was the right one, and I installed it via "sudo dpkg -i" command. 

After the installation I follwed the rest of the steps from the IVTV Edgy guide and ended up getting this from dmesg : 

[17179595.508000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179595.724000] ivtv0: Encoder revision: 0x02050032
[17179595.724000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179595.724000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179595.724000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179595.724000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179595.724000] ivtv0: i2c hardware 0x00000008 not found for command 0xc008561c!
[17179595.728000] ivtv0: i2c hardware 0x00000008 not found for command 0x4008646d!
[17179595.728000] ivtv0: i2c hardware 0x00000008 not found for command 0xc008561c!
[17179595.728000] ivtv0: i2c hardware 0x00000008 not found for command 0xc008561c!
[17179595.728000] ivtv0: i2c hardware 0x00000008 not found for command 0xc008561c!
[17179595.728000] ivtv0: Initialized Hauppauge WinTV PVR-250, card #0
[17179595.728000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179595.728000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179595.728000] skge 1.5 addr 0xeb000000 irq 11 chip Yukon rev 1
[17179595.728000] skge eth0: addr 00:04:e2:ae:c9:fd
[17179595.728000] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[17179595.732000] agpgart: AGP aperture is 64M @ 0xe0000000
[17179595.744000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[17179595.744000] ivtv:  ====================  END INIT IVTV  ====================


"[17179595.728000] ivtv0: i2c hardware 0x00000008 not found for command 0xc008561c!" What does that mean and any help in getting this fixed?

---

### Post by superm1 on 2006-12-10
Nelson-Ray, does this occur after a fresh reboot too?

---

### Post by Nelson-Ray on 2006-12-10
Geez...
After a reboot ...problem went away :) Why did that happen?

Also SuperM1 whats the chances of having a Slave Mythbackend howto at [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)   ?

Problem I get stumped at is whether the slave backend should install mysql-server. Over at this Mythtv [page]("http://www.mythtv.org/docs/mythtv-HOWTO-9.html") they say:
 Slave backends must not run a local MySQL daemon. 

But when I tried to install Mythtv without mysql-server following loosely the Edgy Backend install howto, there was a mythtv setup gui that came up in the terminal asking me for the root password for mysql. I didn't install mysql-server on the slave backend so i left it blank and continued. Then I see these errors in apt-get about mythtv-database not configured and mythbackend doesnt seem to start up. So I am a bit confused about the slave backend procedure. I did have the correct ip for the master backend in the mythtv-setup part. 

As always thanks again!

---

### Post by superm1 on 2006-12-10
Couldn't tell you what went wrong with the i2c problem, but i've seen similar things the first time around.  A reboot seems to solve them......:)

Also, I manage that edgy repository at dl.ivtvdriver.org, and the problem you were getting about the bad release md5sum should now be solved.  I think it was just a hiccup earlier today when I put an update out with a new version of ivtv.

Sounds to me like you installed mythtv-database installed on your slave backend.  You only need this on the machine that is your master backend.  When setting up the slave though, you will need to have a copy of the master backend's mysql.txt sitting in your /etc/mythtv/.  Just modify it to point to the way your slave backend sees your master backend if that makes sense.  So if you master is called **MASTER,** and his ip is **192.168.5.232,** then you will change the **'localhost'** to be **MASTER** if that resolves by a ping, or just **192.168.5.232** elsewise.
I've got a lot of stuff i'm working on for the feisty package, but I will eventually get a secondary backend page up there on the howto.

---

### Post by majoridiot on 2006-12-10
a simple set-up for your slave backend backend-

copy /etc/mythtv/mysql.txt from your master backend to /etc/mythtv on your
slave...  then run mythtv-setup and it should have the db location, user and
password already filled in.  copy the db address to the master backend 
address and you should be good to go.

---

### Post by Nelson-Ray on 2006-12-10
Thanks for the tips on setting up a Mythbackend slave. I understand now. :)


SuperM1 - When I told you after a reboot problem was solved, it seems just the problem with ivtv repo. DMESG is still showing this error : 

[17179593.624000] ivtv:  version 0.7.0 (tagged release) loading
[17179593.624000] ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
[17179593.624000] ivtv:  In case of problems please include the debug info between
[17179593.624000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179593.624000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179593.624000] ivtv0: Autodetected Hauppauge WinTV PVR-250 card (cx23416 based)
[17179593.624000] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179593.624000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179593.664000] tveeprom 1-0050: Hauppauge model 32032, rev B310, serial# 7044969
[17179593.664000] tveeprom 1-0050: tuner model is Philips FI1236 MK2 (idx 10, type 2)
[17179593.664000] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[17179593.664000] tveeprom 1-0050: audio processor is MSP4448 (idx 27)
[17179593.664000] tveeprom 1-0050: decoder processor is SAA7115 (idx 19)
[17179593.664000] tveeprom 1-0050: has no radio, has IR remote
[17179594.012000] saa7115 1-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[17179594.900000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179595.116000] ivtv0: Encoder revision: 0x02050032
[17179595.116000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179595.116000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179595.116000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179595.116000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179595.116000] ivtv0: i2c hardware 0x00000008 not found for command 0xc008561c!
[17179595.120000] ivtv0: i2c hardware 0x00000008 not found for command 0x4008646d!
[17179595.120000] ivtv0: i2c hardware 0x00000008 not found for command 0xc008561c!
[17179595.120000] ivtv0: i2c hardware 0x00000008 not found for command 0xc008561c!
[17179595.120000] ivtv0: i2c hardware 0x00000008 not found for command 0xc008561c!
[17179595.120000] ivtv0: Initialized Hauppauge WinTV PVR-250, card #0
[17179595.120000] ivtv:  ====================  END INIT IVTV  ==================


Since this computer is a simple NFS server, I reinstalled edgy this morning, did sudo apt-get update, then followed the IVTV edgy guide verbatim and still get this error. Any other hints or tips? Thanks...

---

### Post by superm1 on 2006-12-10
You may actually have a newer card that isn't supported by this tagged ivtv release.

In your /etc/apt/sources.list, change the 

deb [http://dl.ivtvdriver.org/ubuntu](http://dl.ivtvdriver.org/ubuntu) edgy firmware 

to be

deb [http://dl.ivtvdriver.org/ubuntu/ edgy]("http://dl.ivtvdriver.org/ubuntu/edgy") all

This will allow you to get the newer ivtv release that isn't in edgy at this point.  run a sudo apt-get update, and then follow the commands to rebuild the modules at the bottom of the ivtv guide.  Hopefully this works :)

---

