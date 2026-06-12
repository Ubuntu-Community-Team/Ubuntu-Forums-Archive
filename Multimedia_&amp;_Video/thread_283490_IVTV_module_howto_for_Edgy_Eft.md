---
title: "IVTV module howto for Edgy Eft"
date: 2006-10-24
forum: Multimedia &amp; Video
---

### Post by Episteme on 2006-10-24
Is there a ivtv module how-to for edgy eft?

I found this: 
[http://ivtvdriver.org/index.php/Howto:Ubuntu](http://ivtvdriver.org/index.php/Howto:Ubuntu)

and a few others, but none for EE. 

Do you know if one exists and where I might find it?

If not, would you be willing to help me write one?

Many thanks

Epi.

---

### Post by the.dude on 2006-10-25
EDIT :: I found a WIKI entry by SuperM1

[https://wiki.ubuntu.com/Install_IVTV_Edgy?highlight=%28ivtv%29]("https://wiki.ubuntu.com/Install_IVTV_Edgy?highlight=%28ivtv%29")

---

### Post by kathyo on 2006-10-26
Well, I'm a fairly new user - have been using Ubuntu for four months now. These forums have been most helpful. As a result, this is my first post because everything else I have been able to solve by searching through the forums. ;) 

Anyway, I tried this howto. I have a Hauppauge PVR-150 card which was working great in Windows, but I haven't gotten close to working in Ubuntu and it's driving me crazy. ](*,) 

I've inserted the driver - sudo modprobe ivtv - and get back:
FATAL: Error inserting ivtv (/lib/modules/2.6.17-10-386/ivtv/ivtv.ko): Unknown symbol in module, or unknown parameter (see dmesg)

So I try dmesg and get all these "lovely" unknown symbols:
[17397270.788000] ivtv: Unknown symbol v4l_compat_translate_ioctl
[17397270.788000] ivtv: Unknown symbol tveeprom_read
[17397270.792000] ivtv: Unknown symbol video_unregister_device
[17397270.792000] ivtv: Unknown symbol video_device_alloc
[17397270.792000] ivtv: Unknown symbol video_register_device
[17397270.792000] ivtv: Unknown symbol video_usercopy
[17397270.792000] ivtv: Unknown symbol tveeprom_hauppauge_analog
[17397270.792000] ivtv: Unknown symbol video_device_release
[17397855.592000] ivtv: Unknown symbol v4l_compat_translate_ioctl
[17397855.592000] ivtv: Unknown symbol tveeprom_read
[17397855.592000] ivtv: Unknown symbol video_unregister_device
[17397855.592000] ivtv: Unknown symbol video_device_alloc
[17397855.592000] ivtv: Unknown symbol video_register_device
[17397855.592000] ivtv: Unknown symbol video_usercopy
[17397855.592000] ivtv: Unknown symbol tveeprom_hauppauge_analog
[17397855.592000] ivtv: Unknown symbol video_device_release
[17401225.240000] ivtv: Unknown symbol v4l_compat_translate_ioctl
[17401225.240000] ivtv: Unknown symbol tveeprom_read
[17401225.240000] ivtv: Unknown symbol video_unregister_device
[17401225.240000] ivtv: Unknown symbol video_device_alloc
[17401225.240000] ivtv: Unknown symbol video_register_device
[17401225.240000] ivtv: Unknown symbol video_usercopy
[17401225.240000] ivtv: Unknown symbol tveeprom_hauppauge_analog
[17401225.240000] ivtv: Unknown symbol video_device_release

Any help on how to fix this and where to go from here would be appreciated. The ultimate goal, like anyone installing IVTV I suppose, is to watch and record TV through the computer. It doesn't necessarily have to be through MythTV, but any suggestions would be great.

Thank you! 
Kathy

---

### Post by superm1 on 2006-10-26
> **kathyo said:**
> Well, I'm a fairly new user - have been using Ubuntu for four months now. These forums have been most helpful. As a result, this is my first post because everything else I have been able to solve by searching through the forums. ;) 

Anyway, I tried this howto. I have a Hauppauge PVR-150 card which was working great in Windows, but I haven't gotten close to working in Ubuntu and it's driving me crazy. ](*,) 

I've inserted the driver - sudo modprobe ivtv - and get back:
FATAL: Error inserting ivtv (/lib/modules/2.6.17-10-386/ivtv/ivtv.ko): Unknown symbol in module, or unknown parameter (see dmesg)

So I try dmesg and get all these "lovely" unknown symbols:
[17397270.788000] ivtv: Unknown symbol v4l_compat_translate_ioctl
[17397270.788000] ivtv: Unknown symbol tveeprom_read
[17397270.792000] ivtv: Unknown symbol video_unregister_device
[17397270.792000] ivtv: Unknown symbol video_device_alloc
[17397270.792000] ivtv: Unknown symbol video_register_device
[17397270.792000] ivtv: Unknown symbol video_usercopy
[17397270.792000] ivtv: Unknown symbol tveeprom_hauppauge_analog
[17397270.792000] ivtv: Unknown symbol video_device_release
[17397855.592000] ivtv: Unknown symbol v4l_compat_translate_ioctl
[17397855.592000] ivtv: Unknown symbol tveeprom_read
[17397855.592000] ivtv: Unknown symbol video_unregister_device
[17397855.592000] ivtv: Unknown symbol video_device_alloc
[17397855.592000] ivtv: Unknown symbol video_register_device
[17397855.592000] ivtv: Unknown symbol video_usercopy
[17397855.592000] ivtv: Unknown symbol tveeprom_hauppauge_analog
[17397855.592000] ivtv: Unknown symbol video_device_release
[17401225.240000] ivtv: Unknown symbol v4l_compat_translate_ioctl
[17401225.240000] ivtv: Unknown symbol tveeprom_read
[17401225.240000] ivtv: Unknown symbol video_unregister_device
[17401225.240000] ivtv: Unknown symbol video_device_alloc
[17401225.240000] ivtv: Unknown symbol video_register_device
[17401225.240000] ivtv: Unknown symbol video_usercopy
[17401225.240000] ivtv: Unknown symbol tveeprom_hauppauge_analog
[17401225.240000] ivtv: Unknown symbol video_device_release

Any help on how to fix this and where to go from here would be appreciated. The ultimate goal, like anyone installing IVTV I suppose, is to watch and record TV through the computer. It doesn't necessarily have to be through MythTV, but any suggestions would be great.

Thank you! 
Kathy

Kathy,

Did you build the modules per the guide on ivtvdriver.org, or per module-assistant directions on the wiki?

Also is this kernel your booted into, the latest kernel you have installed.

---

### Post by kathyo on 2006-10-26
Thanks for your reply. I've actually tried the how to on ivtv website as well as the aforementioned and ran into both ends with each.

I have the latest kernel updates on the system and that was what I was booting into. Currently, I can't even boot into Ubuntu - been having a heck of a day with that! So much for being productive on a day off. :rolleyes:

---

### Post by superm1 on 2006-10-26
Kathy,

Once you are up and running in Ubuntu, let me know and we can try to work through and debug what's going on.

---

### Post by sabelsen on 2006-10-27
Thanks for directing me to this howto. Finally, an ivtv-driver installation made easy. I updated from Dapper to Edgy and the ivtv-driver was the only part that broke.

---

### Post by User_Program on 2006-10-27
WOW this is what I'm talkin about!! Worked great.

---

### Post by planetmn on 2006-10-28
I tried to perform the above Wiki instructions and am having problems from the outset.

I just installed Edgy Eft into the system.  According to Device Manager, it recognizes my PVR150 card.  If I perform a "sudo modprobe ivtv" it comes back with "module ivtv not found"

So I started down the wiki instructions.  The first step "sudo aptitude install ivtv-source devscripts ivtv-utils" starts the package manager, but I receive an error that says:
Couldn't find any package whose name or description matched "ivtv-source"
Couldn't find any package whose name or description matched "ivtv-utils"
No packages will be installed, upgraded, or removed.

Any help would be greatly appreciated.

Thanks,
dave

---

### Post by superm1 on 2006-10-28
Dave,

Can you make sure that you have both universe and multiverse enabled?

---

### Post by planetmn on 2006-10-28
I enabled multiverse and the installation worked.  I ran cat /dev/video0 > test.mpg and it recorded a file.  But, if I open TVTime, I get the following error:
ivtv: invalid argument
cannot open capture device /dev/video0.

Any ideas?

Thanks,
dave

---

### Post by superm1 on 2006-10-28
Dave,

Are you sure tvtime has support for ivtv?  I don't know for sure that it does.  I believe mplayer does, and know for sure myth does.

---

### Post by User_Program on 2006-10-29
Mplayer,Kaffeine,and VLC work great. The media player I use is VLC works great with WinTV PVR cards. 

The only problem I have with using the wintv pvr cards is there is no player that will change channels so you either have to do it through the terminal or use [http://www.kde-look.org/content/show.php?content=29661](http://www.kde-look.org/content/show.php?content=29661) it's a  theme for SuperKaramba as for Gnome users (if you are adventurous) renaming the karaivtv.skz to just "karaivtv" in the zip there is a python program in there and following [http://www.pycage.de/howto_desklets.html](http://www.pycage.de/howto_desklets.html) could produce the same thing.  I think ? 

Has anyone ever made a gdesklet from a karamba theme?

---

### Post by kathyo on 2006-10-29
superm1,

After doing a fresh install of Edgy, I was able to succeed with this howto. Thanks for offering to help, I really appreciate it.

Kathy

---

### Post by superm1 on 2006-10-30
I'm glad to hear the wiki has been working out for everyone.

I added a section to the bottom.  When a kernel update gets released, you may have to rebuild the module depending on how big of a jump in version it is (if the ABI breaks).  When you reboot into the new kernel, if it stops working, just follow those directions.

---

### Post by Zay on 2006-11-02
I tried this guide (the wiki one) and having an error which I don't know how to solve. Everything went without errors untill I ran sudo modprobe ivtv:

> 
FATAL: Error inserting ivtv (/lib/modules/2.6.17.11/ivtv/ivtv.ko): Unknown symbol in module, or unknown parameter (see dmesg)



in the dmesg I found a line:

> 
ivtv : Unknown parameter `ivtv_std`


I had this problem on 6.06 as well. Eventually I just let it rest and now that EE was released I wanted to try it again...

I have a PVR-500.

Anybody got suggestions on how to fix this?

---

### Post by superm1 on 2006-11-02
Sounds like you have some extra things that you added to /etc/modprobe.d or a modprobe.conf that aren't needed.

If you don't remember doing anything like this,
```

cd /etc
grep ivtv -R *

```
This will turn up any files that you have such options put

---

### Post by Zay on 2006-11-02
thanks a lot, it seems to have installed now :)
Now to get mythtv up and running. :D

great guide! :)

---

### Post by LTBP5WD2 on 2006-11-10
I also have the MCE 500 and I have XP MCE on one HD and Ubuntu 6.10 on the other.  Will the firmware mess with the card when it is being used in windows? Is the firmware done to the TV card or is it in the shell?  I still use my XP MCE.   I Installed MythTV but it cannot detect the tv tuner so I guess I need ivTV?

---

### Post by superm1 on 2006-11-10
The firmware is only loaded when the ivtv driver is loaded.  When you boot up into XP MCE, the windows driver (& firmware) will load instead.

You do need to install the ivtv driver for it to work in myth still.

---

### Post by jzmine on 2006-11-16
> **superm1 said:**
> The firmware is only loaded when the ivtv driver is loaded.  When you boot up into XP MCE, the windows driver (& firmware) will load instead.

You do need to install the ivtv driver for it to work in myth still.

superm1: using your howto for edgy intall, is closed captioning expected to work using PVR-150? I read on ivtv.org that an upgrade to 2.6.18 is required. BTW, I installed PVR-150 iaw your howto - it works fine - but CC does not work. I get output on cat /dev/vbi0 to stdout, but don't know how to read it.
Thanks for your reply...

---

### Post by superm1 on 2006-11-16
In all honesty, I haven't tried CC at all.  If ivtvdriver.org indicates 2.6.18 is required, you will have to roll your own kernel to get 2.6.18 - and then you won't be able to use the ivtv driver that is shipping in universe.  You will need one for a 2.6.18 kernel instead.  If CC isn't urgent for you, i'd say hold out until at least feisty.  2.6.19 will be in it, and ivtv will be ready for it.

---

### Post by jzmine on 2006-11-16
> **superm1 said:**
> In all honesty, I haven't tried CC at all.  If ivtvdriver.org indicates 2.6.18 is required, you will have to roll your own kernel to get 2.6.18 - and then you won't be able to use the ivtv driver that is shipping in universe.  You will need one for a 2.6.18 kernel instead.  If CC isn't urgent for you, i'd say hold out until at least feisty.  2.6.19 will be in it, and ivtv will be ready for it.


Thanks for the quick response! Checking with ivtv folks for workaround involving direct read/translate of /dev/vbi0. I will be feisty if I have to wait 6 mos...:twisted: :twisted:

---

### Post by roboguy on 2006-11-25
Hi all,
I'm tearing my hair out here. I have been trying to build the ivtv module using the module assistant method. I managed to build the module (eventually!) but whenever I try modprobing the module I get the following in dmesg

[17186183.272000] ivtv: Unknown symbol v4l_compat_translate_ioctl
[17186183.272000] ivtv: Unknown symbol tveeprom_read
[17186183.272000] ivtv: Unknown symbol video_unregister_device
[17186183.272000] ivtv: Unknown symbol video_device_alloc
[17186183.272000] ivtv: Unknown symbol video_register_device
[17186183.276000] ivtv: Unknown symbol video_usercopy
[17186183.276000] ivtv: Unknown symbol tveeprom_hauppauge_analog
[17186183.276000] ivtv: Unknown symbol video_device_release
[17186346.400000] ivtv: Unknown symbol v4l_compat_translate_ioctl
[17186346.400000] ivtv: Unknown symbol tveeprom_read
[17186346.404000] ivtv: Unknown symbol video_unregister_device
[17186346.404000] ivtv: Unknown symbol video_device_alloc
[17186346.404000] ivtv: Unknown symbol video_register_device
[17186346.404000] ivtv: Unknown symbol video_usercopy
[17186346.404000] ivtv: Unknown symbol tveeprom_hauppauge_analog
[17186346.404000] ivtv: Unknown symbol video_device_release

I'm using Edgy with the 2.6.17-10-generic kernel.
I'd really appreciate any help!

Thanks,
Roboguy

---

### Post by superm1 on 2006-11-25
> **roboguy said:**
> Hi all,
I'm tearing my hair out here. I have been trying to build the ivtv module using the module assistant method. I managed to build the module (eventually!) but whenever I try modprobing the module I get the following in dmesg

[17186183.272000] ivtv: Unknown symbol v4l_compat_translate_ioctl
[17186183.272000] ivtv: Unknown symbol tveeprom_read
[17186183.272000] ivtv: Unknown symbol video_unregister_device
[17186183.272000] ivtv: Unknown symbol video_device_alloc
[17186183.272000] ivtv: Unknown symbol video_register_device
[17186183.276000] ivtv: Unknown symbol video_usercopy
[17186183.276000] ivtv: Unknown symbol tveeprom_hauppauge_analog
[17186183.276000] ivtv: Unknown symbol video_device_release
[17186346.400000] ivtv: Unknown symbol v4l_compat_translate_ioctl
[17186346.400000] ivtv: Unknown symbol tveeprom_read
[17186346.404000] ivtv: Unknown symbol video_unregister_device
[17186346.404000] ivtv: Unknown symbol video_device_alloc
[17186346.404000] ivtv: Unknown symbol video_register_device
[17186346.404000] ivtv: Unknown symbol video_usercopy
[17186346.404000] ivtv: Unknown symbol tveeprom_hauppauge_analog
[17186346.404000] ivtv: Unknown symbol video_device_release

I'm using Edgy with the 2.6.17-10-generic kernel.
I'd really appreciate any help!

Thanks,
Roboguy

Did you possibly try to do this previously from sources?  Or have you tried to use DVB cvs in the past with this kernel?

If so, go and clean up your /lib/modules/2.6.17-10-generic directory before doing this.

If not, attempt to ```
sudo depmod -a
``` and retry.

---

### Post by packetgod on 2006-11-29
So I had the same issues although I only had two lines:

[17231633.208000] ivtv: Unknown symbol tveeprom_read
[17231633.208000] ivtv: Unknown symbol tveeprom_hauppauge_analog

I tried cleaning everything out, as I had indeed had tried to build from source, but I couldn't ever get it to work as I was obviously missing deleting something.  So I switched to the generic kernel and then followed the directions on that wiki and had no problems whatsoever.

Then I went on to resolve the lirc issues which are apparently due to the lirc package having an issue with the hauppauge remote.  So I followed this pages information and used his custom package:

[https://help.ubuntu.com/community/Install_Lirc_Edgy?highlight=%28lirc%29](https://help.ubuntu.com/community/Install_Lirc_Edgy?highlight=%28lirc%29)

Everything is up and happy and working great now.  Now to hook the mythphone into my Asterisk system!

-P>G>>

---

### Post by Panhead Bill on 2006-12-25
When I enter: sudo modprobe ivtv, I get the error: FATAL module ivtv not found.

When I entered: sudo grep ivtv -R * ,  the response was: apt/sources.list:deb [http://dl.ivtvdriver.org/ubuntu](http://dl.ivtvdriver.org/ubuntu) edgy firmware
modules:ivtv

So what seems to be the problem?  up to that point the how to was working.

---

### Post by superm1 on 2006-12-25
> **Panhead Bill said:**
> When I enter: sudo modprobe ivtv, I get the error: FATAL module ivtv not found.

When I entered: sudo grep ivtv -R * ,  the response was: apt/sources.list:deb [http://dl.ivtvdriver.org/ubuntu](http://dl.ivtvdriver.org/ubuntu) edgy firmware
modules:ivtv

So what seems to be the problem?  up to that point the how to was working.
Either you didn't depmod -a, or at some point the m-a command failed - either the updating or the module building.  

Try depmod -a, and try again.  If it still fails then you need to redo the module assistant steps and see if there are any errors in the process.

---

### Post by Panhead Bill on 2006-12-28
m-a failed.  I redid it and the preceding steps - that fixed it.

Thanks

---

### Post by superm1 on 2006-12-28
> **Panhead Bill said:**
> m-a failed.  I redid it and the preceding steps - that fixed it.

Thanks
Wonderful.  Glad this worked :)

---

