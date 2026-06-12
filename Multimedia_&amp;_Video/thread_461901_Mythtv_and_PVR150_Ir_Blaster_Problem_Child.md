---
title: "Mythtv and PVR150 Ir Blaster Problem Child"
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by samk on 2007-06-02
Hi, this is another ir blaster problem.
I installed Mythtv using  this guide [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)
and lirc with this one [https://help.ubuntu.com/community/Install_Lirc_Feisty#head-fb06dc2c3c36ae3a9c1fb78204a125af93245367](https://help.ubuntu.com/community/Install_Lirc_Feisty#head-fb06dc2c3c36ae3a9c1fb78204a125af93245367)

I have the remote working in Mythtv but still haven't been able to get the pvr150 ir blaster to work.

Here are the results of ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2007-06-01 22:05 /dev/lirc0
srw-rw-rw- 1 root root     0 2007-06-01 22:05 /dev/lircd

and  dmesg | grep lirc
[   45.254252] lirc_dev: IR Remote Control driver registered, at major 61 
[   45.281319] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[   45.432400] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[   45.432681] lirc_dev: lirc_register_plugin: sample_rate: 10
[   45.530891]  [<e17a20b8>] init_module+0x48/0x50 [lirc_pvr150]

and i noticed this at the end of the complete dmesg
[   45.254252] lirc_dev: IR Remote Control driver registered, at major 61 
[   45.281319] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[   45.342990] bttv: driver version 0.9.16 loaded
[   45.342998] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   45.413888] cx2388x v4l2 driver version 0.0.6 loaded
[   45.432400] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[   45.432681] lirc_dev: lirc_register_plugin: sample_rate: 10
[   45.530799] kobject_add failed for i2c ir driver with -EEXIST, don't try to register things with the same name in the same directory.
[   45.530834]  [<c01ed9e9>] kobject_add+0x119/0x1a0
[   45.530851]  [<c01edb51>] kobject_register+0x21/0x50
[   45.530858]  [<c02572de>] bus_add_driver+0x6e/0x1a0
[   45.530874]  [<e085423a>] i2c_register_driver+0x1a/0xa0 [i2c_core]
[   45.530891]  [<e17a20b8>] init_module+0x48/0x50 [lirc_pvr150]
[   45.530900]  [<c014422d>] sys_init_module+0x15d/0x1ba0
[   45.530940]  [<c0107a5d>] sys_mmap2+0xcd/0xd0
[   45.530953]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[   45.530970]  =======================
[   50.319934] eth0: no IPv6 routers present

If i can provide any more information to help solve this I will do it.
thanks for any help,
sam

---

### Post by superm1 on 2007-06-03
> **samk said:**
> Hi, this is another ir blaster problem.
I installed Mythtv using  this guide [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)
and lirc with this one [https://help.ubuntu.com/community/Install_Lirc_Feisty#head-fb06dc2c3c36ae3a9c1fb78204a125af93245367](https://help.ubuntu.com/community/Install_Lirc_Feisty#head-fb06dc2c3c36ae3a9c1fb78204a125af93245367)

I have the remote working in Mythtv but still haven't been able to get the pvr150 ir blaster to work.

Here are the results of ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2007-06-01 22:05 /dev/lirc0
srw-rw-rw- 1 root root     0 2007-06-01 22:05 /dev/lircd

and  dmesg | grep lirc
[   45.254252] lirc_dev: IR Remote Control driver registered, at major 61 
[   45.281319] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[   45.432400] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[   45.432681] lirc_dev: lirc_register_plugin: sample_rate: 10
[   45.530891]  [<e17a20b8>] init_module+0x48/0x50 [lirc_pvr150]

and i noticed this at the end of the complete dmesg
[   45.254252] lirc_dev: IR Remote Control driver registered, at major 61 
[   45.281319] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[   45.342990] bttv: driver version 0.9.16 loaded
[   45.342998] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   45.413888] cx2388x v4l2 driver version 0.0.6 loaded
[   45.432400] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[   45.432681] lirc_dev: lirc_register_plugin: sample_rate: 10
[   45.530799] kobject_add failed for i2c ir driver with -EEXIST, don't try to register things with the same name in the same directory.
[   45.530834]  [<c01ed9e9>] kobject_add+0x119/0x1a0
[   45.530851]  [<c01edb51>] kobject_register+0x21/0x50
[   45.530858]  [<c02572de>] bus_add_driver+0x6e/0x1a0
[   45.530874]  [<e085423a>] i2c_register_driver+0x1a/0xa0 [i2c_core]
[   45.530891]  [<e17a20b8>] init_module+0x48/0x50 [lirc_pvr150]
[   45.530900]  [<c014422d>] sys_init_module+0x15d/0x1ba0
[   45.530940]  [<c0107a5d>] sys_mmap2+0xcd/0xd0
[   45.530953]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[   45.530970]  =======================
[   50.319934] eth0: no IPv6 routers present

If i can provide any more information to help solve this I will do it.
thanks for any help,
sam
This sounds like the firmware isn't loaded.  Did you put it in the right place as described in the lirc guide?

---

### Post by samk on 2007-06-04
I'm not home right now to double check, but I believe I put
the firmware in /lib/firmware

---

### Post by samk on 2007-06-04
Thanks Superm1 for responding,
I got  home and checked /lib/firmware
and the firmware is there
samk@ubuntuMyth:~$ cd /lib/firmware
samk@ubuntuMyth:/lib/firmware$ ls
2.6.20-15-generic  2.6.20-16-generic  haup-ir-blaster.bin

should the firmware be executable?, Sorry although
I've used Linux for a few years now I am still learning
this line here is confusing to me
[   45.934744] kobject_add failed for i2c ir driver with -EEXIST, don't try to register things with the same name in the same directory.

sam

---

### Post by ptipton on 2007-06-07
I have identical problem, did you get this fixed? If I try an irsend command i get irsend: hardware does not support sending. I'm guessing its the firmware and am wondering if its permissions make a difference.

---

### Post by samk on 2007-06-07
Sorry, Haven't fixed it and I get the same message with irsend

---

### Post by ptipton on 2007-06-07
With Edgy I used this [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24) guide to get the blaster working. Was hopeing it would be simpler with Feisty. If no other solutions will try the same method again in Feisty. Will be a few days before I get to try it though.

---

### Post by ptipton on 2007-06-12
Tried the guide from as but no luck as yet, will keep working on it.

---

### Post by superm1 on 2007-06-12
Hi guys,

samk,
Can you manually attempt modprobing lirc-pvr150 when lirc-i2c is and isn't loaded?  I'm wondering if this might be a device driver loading issue.

ptipton,
I'm realizing it might not be clear in the Feisty guides.  For PVR-150 blaster support, you need to build both the lirc-pvr150 module and the lirc-i2c module.

---

### Post by ptipton on 2007-06-12
Superm, thanks. Am pretty sure i did build both modules but let me check. My DMESG for lirc looks identical to Sams, how would I make sure lirc-i2c isnt loaded so I can modprob lirc-pvr150. Thanks Paul

---

### Post by ptipton on 2007-06-12
Superm1, Sam. Have fixed my problem. As I only need the blaster I removed my previous lirc install and followed the lirc feisty guide but only built the pvr150 module and not the i2c. My blaster now works fine and funnily enough the remote works as well. Thanks for your help. Paul

---

### Post by samk on 2007-06-13
Thats Great,
I'll try the same tonight.
Thanks for the info
samk

---

### Post by samk on 2007-06-15
OK, I only built the PVR150 module and now my blaster does flash when I use the send_power_new script from
[http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24). I was beginning to think that there was a problem with the blaster. So at this time the ir receiver does work, and I can navigate around mythtv using the Hauppauge remote but I still can’t get the blaster to flash using that remote. I found a codeset reccomendation for the setup box I have but it doesn’t work nor did any in the send_power_new script. I know there is irrecord, so has anyone used irrecord with the Hauppauge ir reciever and a differnt remote. (I'm assuming I need to capture the codes from the settop box remote). 
sam

---

### Post by ptipton on 2007-06-18
Sam. Interesting, I dont have everything working  100% either, not sure whether its the same problem. For me if i send an IRSEND command from the terminal then the blaster flashes no problem. However when I try to change chennel in Mythtv, using lircd and channel change files that used to work fine in Edgy the blaster does not flash at all. Am wondering if perhaps not building the i2c  module has some knock on effects with Mythtv. Unfortuately am travelling for the next two weeks so will be a while before I can try and solve the problem let me know if you make any progress with your system.

---

### Post by gonij on 2007-06-19
I started using Linux a couple of months ago and I would still call myself a Linux newb.  Still new to the linux command line but I'm not afraid of it just inexperienced. 

I have the PVR-150 with the grey 45 button remote.  

It is working flawlessly using gbpvr in Windows but Windows doesn't support firewire that great so I decided to start dabbling in the dark arts of Linux.

I was able to get another mythtv box working with my other motorola 6200 using firewire for channel changing and video capture.  Now I am trying to setup the same thing for another room except using the hauppauge pvr-150 card.

So far I've gotten my remote working in MythTV for navigation but I can't seem to get the darn ir blaster working.   I am getting the same error from my pvr-150 mentioned previously which is -

irsend: command failed: SEND_ONCE blaster POWEROFF
irsend: hardware does not support sending


Could one of you try to help me out a bit?  What commands can I pass in order to get some output that might help in explaining what is happening.

---

### Post by TXPhisher on 2007-06-24
Did anyone ever figure this out?  I'm having the exact same problem.

---

### Post by samk on 2007-06-26
I did get the blaster to flash for a while but was never able to find a correct code set for my STB. Along the way I broke it again and I haven't been working on it since. I did install just the PVR150 module though to get the blaster to flash, and the remote still operated Mythtv, I still couldnot get the blaster to flash by the remote though, only by using irsend
sam

---

### Post by ptipton on 2007-07-04
OK finally I have the pvr150 blaster working fine with mythtv. As above I only built the pvr150 module and not i2c . I then followed the guide from Marks Braindump [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24) for the rest of the install using the lircd.conf , send_power_new and change_channel scripts . 
 In change_channel I edited # $rc_command = "/usr/local/bin/irsend"; to $rc_command = "/usr/bin/irsend"; as thats where my irsend is located.
Its also important not to miss step 12 in the guide, there is further explanation of this further down in the blog if it is not clear. Also dont forget to restart lirc( or just reboot) after changes to the conf file.
I am just using the blaster on a backend server so cant be 100% sure the remote works but in a terminal signals from the remote are recieved ok so it should work I think.

---

### Post by Beezleblub on 2007-08-18
I was facing the same problem. 

In the end I did not use mark's link. it gave a lot of errors. 
 
I just re-installed the lirc package, following this link : [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

BUT I did NOT install the i2c module. 
before re-installing lirc,  I removed the old one. 

sudo dpkg -r lirc-modules-`uname -r`
Then I used the packet manager and removed all lirc packages. 
Reboot. 
following the instructions in the link above,  reinstall lirc packages. 
at 'Configure lirc-modules-source ': ONLY select Pvr150 Module, NOT the i2c module as mentioned. 
...and at Modify /etc/lirc/hardware.conf : MODULES="lirc_pvr150"

After that I find both blaster and receiver working,
If somebody can confirm this, maybe an update on the help page is needed ? 

Thanks for pointing me in the right direction with this ! Cheers !

B.

---

### Post by superm1 on 2007-08-19
> **Beezleblub said:**
> I was facing the same problem. 

In the end I did not use mark's link. it gave a lot of errors. 
 
I just re-installed the lirc package, following this link : [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

BUT I did NOT install the i2c module. 
before re-installing lirc,  I removed the old one. 

sudo dpkg -r lirc-modules-`uname -r`
Then I used the packet manager and removed all lirc packages. 
Reboot. 
following the instructions in the link above,  reinstall lirc packages. 
at 'Configure lirc-modules-source ': ONLY select Pvr150 Module, NOT the i2c module as mentioned. 
...and at Modify /etc/lirc/hardware.conf : MODULES="lirc_pvr150"

After that I find both blaster and receiver working,
If somebody can confirm this, maybe an update on the help page is needed ? 

Thanks for pointing me in the right direction with this ! Cheers !

B.
Updated.  Thanks for nailing this.

---

### Post by dundeemt on 2007-09-17
After each kernel upgrade, does this procedure need to be repeated? 

build pvr150 module
cp haup-ir-blast.bin firmware to /lib/firmware/`uname -r`

any steps I'm leaving out?

Thanks

---

### Post by superm1 on 2007-09-17
> **dundeemt said:**
> After each kernel upgrade, does this procedure need to be repeated? 

build pvr150 module
cp haup-ir-blast.bin firmware to /lib/firmware/`uname -r`

any steps I'm leaving out?

Thanks
Well you can put it in /lib/firmware instead of copying it each time, but otherwise just need to build the pvr150 module each time.  

The need for that goes away with gutsy though.

---

