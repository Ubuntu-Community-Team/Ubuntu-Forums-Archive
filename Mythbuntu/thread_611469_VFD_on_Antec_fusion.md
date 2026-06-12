---
title: "VFD on Antec fusion"
date: 2007-11-13
forum: Mythbuntu
---

### Post by axelsvag on 2007-11-13
I have now tried in several ways to get my LCD screen on the ANTEC Fusion to work. First I used the instruction from 
[HTML]http://www.mythtv.org/wiki/index.php/LCDproc[/HTML]
but I get stucked on the [CODE][/usr/local/sbin/LCDd -c /home/mythtv/lcd/LCDd.conf/CODE] where I got the message that I can´t get acces as it already in use. I assume that, that means that Mythtv already have started the process. So I am stucked, where should I search? Have someone got the vfd to work in mythbuntu. ( it worked perfectly in feisty with mythtv so I know the VFD works OK)

---

### Post by axelsvag on 2007-11-13
I have solved everything. What I did was to change a line in LCDd.conf from ```
driver=curses
```to ```
driver=imon
``` Then I restarted everything. At first everything works as it should. The only problem seems to be that my lirc device constantly changes from lirc1 to lirc 0 so my remote sometimes work after reboot and sometimes not. Then I have to change in hardware.conf from lirc1 to lirc 0 and back if it is needed. Isn´t that a way to fix the lirc0 respectively lirc1 to a specific device ?

---

### Post by Sir_Ty on 2007-11-13
I seem to be having the same problem.  Sometime I boot up and /dev/lirc0 and /dev/lirc1 are present.  Sometimes it's just /dev/lirc0.  If it boots with just 0, remote works, VFD seems to work.

Do you have a Hauppage TV capture card by chance?  I'm thinking that both the TV card and the VFD module have IR detectors for remotes, and the drivers are getting confused.

---

### Post by axelsvag on 2007-11-14
Yes I have and  I think you are right about that both the antec fusion and the loose ir receiver for Hauppage has something to do with eachother. Maybe it is easy to get the antec fusion ir receiver to work with my mce remote?

---

### Post by Sir_Ty on 2007-11-14
I'm not sure, everytime I get it working and I need to reboot for some reason I lose the use of the remote now.  And, the VFD is showing garbage characters, sometimes scrolling.  If I run "mode2 -d /dev/lirc1" to test out the remote the characters stop scrolling.

Superm1 can you assist in entering a bug about having these two devices?

Thanks!

---

### Post by Sir_Ty on 2007-11-14
It looks like (according to this thread [http://www.mythtvtalk.com/forum/viewtopic.php?t=3280&start=0](http://www.mythtvtalk.com/forum/viewtopic.php?t=3280&start=0)) that the original Antec Fusion case came with an OEM version of the iMON VFD and Knob that did NOT include the IR receiver.  But, the Fusion v2 documentation which I'm holding in my hand DOES say it includes the IR receiver.  SO I'm sure this is still just a driver configuration issue.  (Sometimes when I hit buttons on the remote, the random chars that are scrolling on the VFD right now change.  Interesting.)

I noticed that when I did have the remote working, it put out keyboard button presses.  For instance, the Up and Down arrows were putting out PageUp and PageDown keyboard presses.  The numbers were putting out the keyboard numbers.  This was from the Myth Command setup.

At this point I'd like to uninstall the WinTV-PVR350 IR driver and use the one built into the case.  That would be one less cable to worry about anyway.  Anyone have any idea how?

Another tip - there is a Soundgraph iMON knob in the Remote Control setup tab of the Mythbuntu control center.  I've loaded that but have yet to test it.

---

### Post by blahmartinblah on 2007-11-30
> **Sir_Ty said:**
> I'm not sure, everytime I get it working and I need to reboot for some reason I lose the use of the remote now.  And, the VFD is showing garbage characters, sometimes scrolling.  If I run "mode2 -d /dev/lirc1" to test out the remote the characters stop scrolling.

Superm1 can you assist in entering a bug about having these two devices?

Thanks!


Sir_Ty,
Did you ever resolve this? I appear to have the same problem.
I have an Antec fusion (original, no IR sensor), mce model 1039 remote with usb receive and Hauppauge WinTV-Nova-T 500 which I think also has a IR receiver built in (that I dont use).

I just rebooted, the remote and VFD aren't working. I checked for /dev/lircX, and I have lirc0 and lirc1.

Martin.

---

### Post by Pavlo on 2007-12-05
I'm an absolute beginner in the world of linux and mythtv.  I managed to install mythbuntu and followed the "how-to" for setting up the VFD display on my Antec Fusion V2.  I am having difficulties getting the VFD to work in mythTV.  I've turned on LCD option under Appearance but I do not see information being passed to the VFD.  Any suggestions as to where I should start looking for the problem?  I did read in another thread that there maybe some timing of the drivers being loaded but I do not have a clue as to where I would find this information, any help is greatly appreciated.

Thanks,
Pav

---

### Post by volkswagner on 2007-12-10
Same boat here.  I have the antec fusion with Bus 004 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller

I cannot get the vfd to work in mythbuntu.  I also have pvr150 and pvr350 installed.  I have tried to follow the instructions in this thread [http://ubuntuforums.org/showthread.php?t=306437](http://ubuntuforums.org/showthread.php?t=306437)

I get stuck at this point

```
eric@FamilyRoom:~/imon$ make -C /usr/src/linux SUBDIRS=$PWD modules
make: *** /usr/src/linux: No such file or directory.  Stop.
eric@FamilyRoom:~/imon$ 
```

When I browse to the folder /usr/src  it is an empty folder

The how to is for edgy so this may be a kernel thing items in different folders

---

### Post by superm1 on 2007-12-10
You may consider installing module-assistant.

Then you can prepare that directory (and the right headers) like this:

```
sudo m-a update,prepare
```

---

### Post by volkswagner on 2007-12-10
Thanks for the info.  I am sthill struggeling however.

I did have the module-assistand installed so I ran the above command and it created the files in /etc/src

So I edited the command to include my specific kernel and her is what i get.  I tried to add switch -B to force the make but i must have used wron syntax
```

eric@FamilyRoom:~/imon$ make -C /usr/src/linux-headers-2.6.22-14-generic/ SUBDIRS=$PWD modules
make: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/eric/imon/imon_vfd.o
/home/eric/imon/imon_vfd.c:34:26: error: linux/config.h: No such file or directory
/home/eric/imon/imon_vfd.c:43:35: error: linux/devfs_fs_kernel.h: No such file or directory
/home/eric/imon/imon_vfd.c: In function ‘send_packet’:
/home/eric/imon/imon_vfd.c:328: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
make[1]: *** [/home/eric/imon/imon_vfd.o] Error 1
make: *** [_module_/home/eric/imon] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
eric@FamilyRoom:~/imon$ 
```

---

### Post by Pavlo on 2007-12-10
Well I have managed to get the VFD display working in myth.

The steps regarding "Starting LCDproc from boot" have been the steps that I have been confused on.



I added the following line /usr/local/sbin/LCDd -c /home/mythtv/lcd/LCDd.conf to the begining of the init-LCDd.debian file and copied the file it to ./etc/init.d/LCDd.

```


# Make the script executable
[root@host lcdproc-0.5.1]# chmod 755 /etc/init.d/LCDd
The above was done as is without a problem.

]# Add the script to chkconfig
[root@host lcdproc-0.5.1]# chkconfig LCDd --add
update-rc.d LCDd defaults is the command I used.  In fact I am not sure if this did anything

# Tell the machine to start on boot:
[root@host lcdproc-0.5.1]# chkconfig LCDd on
as for the last line I had no clue what needs to be done on mythbuntu.

```

Everything seems to be working but I would like to know about the last two commands.  Now I am trying to resolve the volume knob.

Cheers,
Pav

---

### Post by volkswagner on 2007-12-13
Please help as I do not want to bork my install.  It seems my problem is because this solution is for an older kernel.  I have searched for my problem below.
> 
Thanks for the info. I am sthill struggeling however.

I did have the module-assistand installed so I ran the above command and it created the files in /etc/src

So I edited the command to include my specific kernel and her is what i get. I tried to add switch -B to force the make but i must have used wron syntax
Code:

eric@FamilyRoom:~/imon$ make -C /usr/src/linux-headers-2.6.22-14-generic/ SUBDIRS=$PWD modules
make: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/eric/imon/imon_vfd.o
/home/eric/imon/imon_vfd.c:34:26: error: linux/config.h: No such file or directory
/home/eric/imon/imon_vfd.c:43:35: error: linux/devfs_fs_kernel.h: No such file or directory
/home/eric/imon/imon_vfd.c: In function ‘send_packet’:
/home/eric/imon/imon_vfd.c:328: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
make[1]: *** [/home/eric/imon/imon_vfd.o] Error 1
make: *** [_module_/home/eric/imon] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
eric@FamilyRoom:~/imon$



I see the problem is because of missing linux/config.h, which has been renamed in the newer kernel to linux/autoconfig

I see this fix for 7.04 users

[http://ubuntuforums.org/showthread.php?p=2511814]("http://ubuntuforums.org/showthread.php?p=2511814")

I am not sure if I should apply the patch mentioned in the above post.  It also seems the site has updated the fix.  So what do I do?

---

### Post by volkswagner on 2007-12-30
I did a fresh install and performed these steps

> Originally Posted by mutation View Post
can't help you with the remote problem as i lost mine, but the vfd display, let me see if i can remember what i did,

1. install LCDproc

2. edit LCDd.conf and change driver=imon

reboot and you should be up and running on the display

I also ran the following first not sure if it made a difference

```
sudo apt-get install module-assistant
sudo m-a update,prepare
```

VERY HAPPY TO SEE VFD DISPLAY! THANK YOU!

---

### Post by almightybunghole on 2008-04-28
Hi there,

Having a strange problem with LCDd on Mythbuntu 8.04. I've followed the instructions and compiled/installed LCDproc, without incident. I've edited the scripts, copied them to a sensible location, and if I run the init script then LCDproc starts up.

I then copied the init script to /etc/init.d and used **update-rc.d LCDd defaults** to add the startup scripts - all seemed ok. When I reboot the LCDproc server comes up, and shortly afterwards mythbackend starts and the correct display is shown (the date). 

However about 5 secs later the VFD shows the default LCDproc startup screen and I have to kill mythlcdserver and restart mythbackend to get the display back again.

It's as if the init script is running twice, but I don't see how that could be the case...... :confused:

Thanks.

George

---

### Post by volkswagner on 2008-04-28
I would remove your script.  Check my post previous to yours.  That is all I had to do to get it working.  I did not add any script to etc/init.d.

Of course I am running 7.10.  So there may be a difference.  If you added the script because you did not see VFD activity after boot, you may have needed a second reboot.  My VFD shows display late into the boot process.

---

### Post by Offoffoff on 2008-08-09
Hello! I have the same display as yours - it is part of my SoundGraph Inc. iMON PAD Remote Controller (15c2:ffdc). Everything works fine on my Mythbuntu 8.04.1. I only install packages lcd*. All Myth's menus works but only English symbols and numbers. How to fix encoding? I want to use cyrillic symbols.

---

