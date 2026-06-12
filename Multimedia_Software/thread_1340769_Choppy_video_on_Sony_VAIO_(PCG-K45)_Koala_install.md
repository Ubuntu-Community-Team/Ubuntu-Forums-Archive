---
title: "Choppy video on Sony VAIO (PCG-K45) Koala install"
date: 2009-11-28
forum: Multimedia Software
---

### Post by ganjiz on 2009-11-28
Hello,
Before I start let me say, I'm totally new to Ubuntu, if you're kind enough to reply please post detailed steps and paths for command execution recommendations.

I'm trying to view a DVD video on this laptop and the video starts out ok and then becomes so choppy that it actually stops playing.  When I issue the top command I see Totem (MPlayer) is using maybe 40-60% of the cpu and Pulseaudio is using 15-30%.  
> 
Tasks: 139 total,   2 running, 137 sleeping,   0 stopped,   0 zombie
Cpu(s): 76.5%us, 10.2%sy,  0.0%ni,  0.0%id,  0.0%wa, 11.4%hi,  1.9%si,  0.0%st
Mem:    444116k total,   438396k used,     5720k free,    30172k buffers
Swap:  1301224k total,   164916k used,  1136308k free,   170660k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2274 gangiz  20   0  223m  52m  31m S 41.1 12.1   0:15.44 totem              
 1491 gangiz  20   0  167m  14m  13m S 23.9  3.3   1:32.41 pulseaudio         
 1849 gangiz  20   0  468m 111m  20m R 20.5 25.6  10:26.02 firefox            
 1099 root      20   0  219m  27m 7548 S  6.9  6.4   3:01.53 Xorg               
 1938 gangiz  20   0 39760 5848 4008 S  1.8  1.3   0:03.74 gnome-terminal     
 1500 gangiz  20   0 15692 1676 1264 S  1.2  0.4   0:14.37 at-spi-registry    
 2272 gangiz  20   0  2468 1176  884 R  1.2  0.3   0:00.60 top                
 1496 gangiz  20   0  7588 2188 1196 D  0.9  0.5   0:01.30 gconfd-2           
   26 root      15  -5     0    0    0 S  0.3  0.0   0:04.39 kswapd0            
  347 root      15  -5     0    0    0 D  0.3  0.0   0:00.24 kjournald2         
 1568 gangiz  20   0  3164  376  312 S  0.3  0.1   0:01.48 syndaemon          
 1605 gangiz  20   0 31632 3676 2096 S  0.3  0.8   0:15.21 compiz.real        
    1 root      20   0  2528  732  516 S  0.0  0.2   0:01.55 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.12 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0 
I attempted to install the new ATI Catalyst 9.8 driver package based on info from this site:
[URL="http://www.webupd8.org/2009/08/amd-catalyst-98-released-how-to-upgrade.html"]http://www.webupd8.org/2009/08/amd-catalyst-98-released-how-to-upgrade.html
[/URL]and no change after finishing the install and rebooting...

Are there any suggestions for commands I can use to identify the cause of the performance issue?  Any assistance would be much appreciated.

Regards.

---

### Post by ikacer on 2009-11-29
did you try using the drivers from
System -> Administration -> Hardware Drivers ?

Also, does this only happen when playing videos, or does it also happen with other graphics intensive processes like games?

Edit:

one more thing, could you post part of the output of
```
lspci -v
```

just post the section for your graphics card. It should start with 'VGA compatible controler' or something like that.

---

### Post by ganjiz on 2009-11-29
Surprisingly the Hardware Drivers window is empty (screen shot attached.)

I don't have any high graphic need games installed...  I tried the pre installed chess game and it's working fine... the normal visual effects setting seem to be working fine as well.

> 
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
    Subsystem: Sony Corporation Device 8175
    Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 4
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    I/O ports at a000 [size=256]
    Memory at e0300000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at e0320000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeon, radeonfb


Let me know what else I can provide.  
Appreciate the reply, Thank you.

---

### Post by ikacer on 2009-11-29
It looks like you have a card which ATI no longer supports. This means their proprietary driver (the one you installed) won't work. You should use the open source driver as it still has support for many older cards. Here's a link to a page detailing how to do this: [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

One thing you might have trouble with is uninstalling the catalyst driver you installed. This might be difficult because you didn't use the package management system to install it.

On Linux it is generally a bad idea to download and run an installer like you would in Windows (its a bad idea in windows too, but that's how its done anyway). If you need to install something in Linux, use the Synaptic Package Manager or if its not available there use a '.deb' file. If it's something you are compiling, use 'checkinstall', which will create a .deb file. If you always do this, then you will easily be able to undo any changes you make.

Because of how you installed your driver, I have no way of knowing what changes the installer made to your system, what effects those changes will have, or how to undo those changes.

---

### Post by ganjiz on 2009-11-29
hmm.  I attempted to follow the instructions on that page and interesting enough I have no /etc/X11/xorg.conf file at the moment and I also don't have the xorg-driver-fglrx package installed.  Seems like my attempt to install the updated ATI Radeon Driver did not work as expected...

Also when I run the "glxinfo | grep vendor" command, I get SGI as the listed client glx vendor string... I believe it should be ATI.
> 
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.


I also checked used "ls /usr/lib/xorg/modules/drivers/" and noticed a number of .so files (similar to dll's in windows per a google search) in particular radeon_drv.so and ati_drv.so...
> 
apm_drv.so        geode_drv.so       r128_drv.so           tdfx_drv.so
ark_drv.so        i128_drv.so        radeon_drv.so         tfp410.so
ati_drv.so        i740_drv.so        rendition_drv.so      trident_drv.so
ch7017.so         intel_drv.so       s3_drv.so             tseng_drv.so
ch7xxx.so         ivch.so            s3virge_drv.so        v4l_drv.so
chips_drv.so      mach64_drv.so      savage_drv.so         vesa_drv.so
cirrus_alpine.so  mga_drv.so         sil164.so             vmware_drv.so
cirrus_drv.so     neomagic_drv.so    siliconmotion_drv.so  voodoo_drv.so
cirrus_laguna.so  nv_drv.so          sis_drv.so            ztv_drv.so
fbdev_drv.so      openchrome_drv.so  sisusb_drv.so


I got to the above directory by checking the /var/log/Xorg.0.log file which is attached for reference.

Thanks for the information in your post.  I'll certainly follow that recommendation going forward.

---

### Post by ganjiz on 2009-11-29
Attachment
 > **ganjiz said:**
> ...


I got to the above directory by checking the /var/log/Xorg.0.log file which is attached for reference.

....

---

### Post by ikacer on 2009-11-30
I'm no expert on this, but I'll try to help as much as I can.

First off, the xorg-driver-fglrx package would only be marked as installed if you installed using the package manager, so its ok that that's not marked as installed. Also, the xorg.conf file, I think, doesn't exist on a new install, so that's nothing to worry about if its not there. You can make one if you want.The glxinfo output is normal, I think.

The open ati driver that you need should be on your system by default when you installed, and should have worked from the time you installed Ubuntu. If you didn't notice anything get worse after installing the new driver, then the open source driver is either still working, or never worked in the first place. If it's not working then your graphics would seem choppy when doing anything from scrolling in a webpage or playing a game. If it seems smooth then it is probably working.

I'll address your problem playing a dvd later. For now lets just make sure your graphics driver is set up and working.

I recommend you take a look here:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver")
If you follow the "fully remove -fglrx and reinstall -ati from scratch" section, it should undo any changes to your settings that the installer made, although it probably won't uninstall the driver.

For your xorg.conf file, it shouldn't be necessary as the settings are done automatically, but if you want you could make one to manually specify the graphics card settings. You would do this by creating a file /etc/X11/xorg.conf with any setting you would like to set. But this should be necessary.

Restart after you do these so they take effect.

Next, do this "testing the driver" section:
[https://help.ubuntu.com/community/RadeonDriver#Testing%20The%20Driver]("https://help.ubuntu.com/community/RadeonDriver#Testing%20The%20Driver")

If it passes then your driver is working.

I know this doesn't answer your original question about the dvd. I'll see if I can help you out with that too, but right now I'm out of time, so I'll post that later.

---

### Post by ikacer on 2009-11-30
There are a lot of things that could be causing your troubles with the DVD. I know a lot of people have had troubles with pulse audio in the past, so that may be it.

A good media player to try is SMPlayer, which is an excellent frontend for MPlayer. You can get it here:
[http://smplayer.sourceforge.net/downloads.php?tr_lang=en]("http://smplayer.sourceforge.net/downloads.php?tr_lang=en")
Just add the two launchpad PPAs to your software sources, and install SMPlayer using the Symantic Package Manager. One of the PPAs is for SMPlayer, and with the other the author maintains up to date versions of MPlayer.
I also recommend you install VLC as an alternative media player.

Try running your DVD with these two programs and see if it will work. (note: smplayer doesn't have dvd menu support) If not try changing some of the settings. I recommend keeping the video output driver on xv and trying a some different audio drivers. I've had some troubles with playback freezing when using ALSA in SMPlayer since switching to Karmic, so watch out for that.

Other than that, just fiddle around with the settings and let me know if that fixes is

---

