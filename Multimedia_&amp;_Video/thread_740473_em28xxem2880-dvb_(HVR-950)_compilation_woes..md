---
title: "em28xx/em2880-dvb (HVR-950) compilation woes."
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by Sastraxi on 2008-03-30
Hey all,

Upgraded to Hardy, went smooth as silk. Now the only issue remaining (apart from the dreadful power consumption) is to get my Hauppauge HVR-950 working once more.

I attempted the steps described in the infamous lunapark article ([http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html](http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html)) but they do not seem to work for Hardy. Specifically...

```
cameron@vienna:/lib/firmware/v4l-dvb-experimental$ sudo make
[sudo] password for cameron: 
make -C /lib/firmware/v4l-dvb-experimental/v4l 
make[1]: Entering directory `/lib/firmware/v4l-dvb-experimental/v4l'
creating symbolic links...
make -C /lib/modules/2.6.24-12-generic/build SUBDIRS=/lib/firmware/v4l-dvb-experimental/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-12-generic'
  CC [M]  /lib/firmware/v4l-dvb-experimental/v4l/flexcop-pci.o
In file included from /lib/firmware/v4l-dvb-experimental/v4l/flexcop-common.h:23,
                 from /lib/firmware/v4l-dvb-experimental/v4l/flexcop-pci.c:10:
/lib/firmware/v4l-dvb-experimental/v4l/dvb_frontend.h:42:33: error: media/v4l_dvb_tuner.h: No such file or directory
In file included from /lib/firmware/v4l-dvb-experimental/v4l/flexcop-common.h:23,
                 from /lib/firmware/v4l-dvb-experimental/v4l/flexcop-pci.c:10:
/lib/firmware/v4l-dvb-experimental/v4l/dvb_frontend.h:165: error: field 'tuner_ops' has incomplete type
make[3]: *** [/lib/firmware/v4l-dvb-experimental/v4l/flexcop-pci.o] Error 1
make[2]: *** [_module_/lib/firmware/v4l-dvb-experimental/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-12-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/lib/firmware/v4l-dvb-experimental/v4l'
make: *** [all] Error 2
```

... I'm not exactly sure where the problem lies. Has anyone gotten this card (and its digital capabilities that work flawlessly in the 2.6.22 kernel, in gutsy OR hardy) working with Hardy and the 2.6.24 kernel?

---

### Post by gekkio on 2008-04-05
It's a known problem when compiling em28xx with kernels >= 2.6.24.

I managed to get my em2880-dvb working by using this patch from the em28xx mailing list:
[http://mcentral.de/pipermail/em28xx/2008-April/001481.html](http://mcentral.de/pipermail/em28xx/2008-April/001481.html)
It's a very simple Makefile patch, but it worked for me.

Hope it helps!

---

### Post by tuku on 2008-04-08
I have exactly the same problem.  The link does not have the patch anymore, its just has the .obj file.
Where can I find the patch.
thanks

---

### Post by gekkio on 2008-04-08
The obj file IS the patch file, it's just named weirdly.

Just download the obj file and patch the source with
```
patch -p0 < v4l-dvb-kernel-Makefile-2.6.24.obj
```

---

### Post by GaryAitcheson on 2008-04-10
Many thanks for your help.

---

### Post by xens on 2008-04-14
Thanks it solved the problem for me!

I can't figure out why the em28xx driver isn't bundled with hardy, it's been a long time since this driver exists.

---

### Post by ayellen on 2008-04-24
Could someone please walk me through the specific steps of how to apply this patch?

Thanks.

---

### Post by dkscudder on 2008-04-24
I have been wrestling with this problem for several months.  I've gotten mine working, so I thought I'd throw my 2 cents in . . .

I'm using Hardy 64.  I'm pretty sure the patch mentioned above is already in the hg mcentral.de kernel and experimental repositories so it shouldn't be needed.  However, just typing "make" still fails.  So instead I type
```
make LINUXINCLUDE="-I`pwd`/linux/include -I`pwd`/v4l -Iinclude -include include/linux/autoconf.h"
```
which compiles nicely.

Then there is installing.  If I do "make install" Ubuntu won't boot after the next reboot.  It looks like HAL crashes.  I'm pretty sure this is a bug that only affects 64 bit systems using kernel 2.6.24.  I'm not smart enough to figure out what's going on exactly or how to fix it, so I use an ugly work around.  Every time I boot up, I run the following command in a terminal:
```
cd /lib/firmware/v4l-dvb-experimental/;sudo make load;sudo /etc/init.d/mythtv-backend restart
```
and BANG -- It works like a charm.  Obviously the last part isn't necessary if you don't use myth.

If someone knows of a better way I'm all ears.  Hopefully these bugs will be fixed soon at the code level.

---

### Post by bawilson2 on 2008-04-25
I'd like to second a request for help here.  I tried and couldn't get things working either with the same setup.  I've given up and switched back to 7.10 but would love to move up to 8.04 if somebody were able to figure this one out.

---

### Post by bawilson2 on 2008-04-25
> **dkscudder said:**
> I have been wrestling with this problem for several months.  I've gotten mine working, so I thought I'd throw my 2 cents in . . .

I'm using Hardy 64.  I'm pretty sure the patch mentioned above is already in the hg mcentral.de kernel and experimental repositories so it shouldn't be needed.  However, just typing "make" still fails.  So instead I type
```
make LINUXINCLUDE="-I`pwd`/linux/include -I`pwd`/v4l -Iinclude -include include/linux/autoconf.h"
```
which compiles nicely.

Then there is installing.  If I do "make install" Ubuntu won't boot after the next reboot.  It looks like HAL crashes.  I'm pretty sure this is a bug that only affects 64 bit systems using kernel 2.6.24.  I'm not smart enough to figure out what's going on exactly or how to fix it, so I use an ugly work around.  Every time I boot up, I run the following command in a terminal:
```
cd /lib/firmware/v4l-dvb-experimental/;sudo make load;sudo /etc/init.d/mythtv-backend restart
```
and BANG -- It works like a charm.  Obviously the last part isn't necessary if you don't use myth.

If someone knows of a better way I'm all ears.  Hopefully these bugs will be fixed soon at the code level.

I'd like to second a request for help here.  I tried and couldn't get things working either with the same setup.  I've given up and switched back to 7.10 but would love to move up to 8.04 if somebody were able to figure this one out.

---

### Post by gekkio on 2008-04-26
> **dkscudder said:**
> 
I'm using Hardy 64.  I'm pretty sure the patch mentioned above is already in the hg mcentral.de kernel and experimental repositories so it shouldn't be needed.  However, just typing "make" still fails.

It's not there yet, so I recommend that you use the patch on the mailing list. The patch fiddles with include directories, so it might just do the same things you're doing but I urge you to use the patch just to be sure.

> **ayellen said:**
> Could someone please walk me through the specific steps of how to apply this patch?


Here are the exact steps to install the driver on Hardy (works on my 64-bit installation, should work on 32-bit too):
```

hg clone http://mcentral.de/hg/~mrec/v4l-dvb-experimental
cd v4l-dvb-experimental
wget http://mcentral.de/pipermail/em28xx/attachments/20080402/b43e9afe/v4l-dvb-kernel-Makefile-2.6.24.obj
patch -p0 < v4l-dvb-kernel-Makefile-2.6.24.obj
make
sudo make install

```
+ install firmware using instructions from [http://mcentral.de/wiki/index.php5/Em2880#Installation]("http://mcentral.de/wiki/index.php5/Em2880#Installation")
And reboot.

> **dkscudder said:**
> 
Then there is installing.  If I do "make install" Ubuntu won't boot after the next reboot.  It looks like HAL crashes.  I'm pretty sure this is a bug that only affects 64 bit systems using kernel 2.6.24.
I assume your card is a USB DVB-T card. Does your system crash when it is not plugged in and you boot into Ubuntu?
Also, please note that this driver will break other v4l drivers (for example, my webcam's uvcvideo driver which is bundled in linux-ubuntu-modules-... package), so if you have a webcam or other potential v4l devices, you could try unplugging them.
I'm using Hardy 64-bit and the drivers works for me so there must be something specific in your system that causes the problems. I'll gladly help with isolating the problem.

---

### Post by msrinath80 on 2008-04-26
Hi there,

I followed your instructions step by step. During the make part I get these warnings and after make install the audio module refuses to load with similar warnings in dmesg. I'm using Hardy 32 bit. Any pointers?

--- snippet---

  LD [M]  /lib/firmware/v4l-dvb-experimental/v4l/dvb-usb-gl861.o
  LD [M]  /lib/firmware/v4l-dvb-experimental/v4l/dvb-usb-au6610.o
  LD [M]  /lib/firmware/v4l-dvb-experimental/v4l/dvb-usb-digitv.o
  LD [M]  /lib/firmware/v4l-dvb-experimental/v4l/dvb-usb-cxusb.o
  LD [M]  /lib/firmware/v4l-dvb-experimental/v4l/dvb-usb-ttusb2.o
  LD [M]  /lib/firmware/v4l-dvb-experimental/v4l/dvb-usb-dib0700.o
  LD [M]  /lib/firmware/v4l-dvb-experimental/v4l/dvb-usb-opera.o
  LD [M]  /lib/firmware/v4l-dvb-experimental/v4l/dvb-usb-af9005.o
  LD [M]  /lib/firmware/v4l-dvb-experimental/v4l/dvb-usb-af9005-remote.o
  CC [M]  /lib/firmware/v4l-dvb-experimental/v4l/pluto2.o
  Building modules, stage 2.
  MODPOST 199 modules
WARNING: "snd_pcm_lib_ioctl" [/lib/firmware/v4l-dvb-experimental/v4l/em28xx-audio.ko] undefined!
WARNING: "snd_pcm_period_elapsed" [/lib/firmware/v4l-dvb-experimental/v4l/em28xx-audio.ko] undefined!
WARNING: "snd_pcm_hw_constraint_integer" [/lib/firmware/v4l-dvb-experimental/v4l/em28xx-audio.ko] undefined!
WARNING: "snd_card_register" [/lib/firmware/v4l-dvb-experimental/v4l/em28xx-audio.ko] undefined!
WARNING: "snd_pcm_set_ops" [/lib/firmware/v4l-dvb-experimental/v4l/em28xx-audio.ko] undefined!
WARNING: "snd_pcm_new" [/lib/firmware/v4l-dvb-experimental/v4l/em28xx-audio.ko] undefined!
WARNING: "snd_card_new" [/lib/firmware/v4l-dvb-experimental/v4l/em28xx-audio.ko] undefined!
WARNING: "snd_card_free" [/lib/firmware/v4l-dvb-experimental/v4l/em28xx-audio.ko] undefined!
  CC      /lib/firmware/v4l-dvb-experimental/v4l/adv7170.mod.o
  LD [M]  /lib/firmware/v4l-dvb-experimental/v4l/adv7170.ko
  CC      /lib/firmware/v4l-dvb-experimental/v4l/adv7175.mod.o
  LD [M]  /lib/firmware/v4l-dvb-experimental/v4l/adv7175.ko
  CC      /lib/firmware/v4l-dvb-experimental/v4l/b2c2-flexcop-pci.mod.o
  LD [M]  /lib/firmware/v4l-dvb-experimental/v4l/b2c2-flexcop-pci.ko
  CC      /lib/firmware/v4l-dvb-experimental/v4l/b2c2-flexcop-usb.mod.o

--- snippet---

---

### Post by asdf46 on 2008-04-26
I'm running hardy and mine wont let me  boot after installing the driver. It doesn't matter if I have the tuner plugged in or not. It hangs saying loading hardware driver fail and then * Loading manual drivers then nothing.

I have no idea where to go with this from here.

Any help on this would be great.

Thanks,
asdf46

---

### Post by tdailey on 2008-04-26
> **gekkio said:**
> It's not there yet, so I recommend that you use the patch on the mailing list. The patch fiddles with include directories, so it might just do the same things you're doing but I urge you to use the patch just to be sure.



Here are the exact steps to install the driver on Hardy (works on my 64-bit installation, should work on 32-bit too):
```

hg clone http://mcentral.de/hg/~mrec/v4l-dvb-experimental
cd v4l-dvb-experimental
wget http://mcentral.de/pipermail/em28xx/attachments/20080402/b43e9afe/v4l-dvb-kernel-Makefile-2.6.24.obj
patch -p0 < v4l-dvb-kernel-Makefile-2.6.24.obj
make
sudo make install

```
+ install firmware using instructions from [http://mcentral.de/wiki/index.php5/Em2880#Installation]("http://mcentral.de/wiki/index.php5/Em2880#Installation")
And reboot.


I assume your card is a USB DVB-T card. Does your system crash when it is not plugged in and you boot into Ubuntu?
Also, please note that this driver will break other v4l drivers (for example, my webcam's uvcvideo driver which is bundled in linux-ubuntu-modules-... package), so if you have a webcam or other potential v4l devices, you could try unplugging them.
I'm using Hardy 64-bit and the drivers works for me so there must be something specific in your system that causes the problems. I'll gladly help with isolating the problem.
I'm also having problems on Hardy 64 on my Acer Aspire 5100.  I did a fresh install and loaded the proprietary drivers for ATI and Broadcom hardware, did apt-get build-essential, then followed gekkio's exact steps.  System won't boot with tuner plugged in, but will without it.  If I plug in the tuner after boot, keyboard locks up but mouse still works - requires hard restart.  I'm going to try a fresh install without the proprietary drivers and see what happens.

---

### Post by msrinath80 on 2008-04-26
I did not want to bring this up but I have no choice. I just tried the Fedora 9 Preview release live CD and plugged the WinTV HVR 950 in it and to my amazement all drivers were automagically loaded. All it mentioned was that it could not load the firmware file. Once I copied the *.fw file to /lib/firmware, I installed tvtime and within a minute or so I am watching TV again! I will most probably switch to Fedora once Fedora 9 is finally released in about 17 days.

---

### Post by bawilson2 on 2008-04-26
> **tdailey said:**
> I'm also having problems on Hardy 64 on my Acer Aspire 5100.  I did a fresh install and loaded the proprietary drivers for ATI and Broadcom hardware, did apt-get build-essential, then followed gekkio's exact steps.  System won't boot with tuner plugged in, but will without it.  If I plug in the tuner after boot, keyboard locks up but mouse still works - requires hard restart.  I'm going to try a fresh install without the proprietary drivers and see what happens.

I had the same problem but found that if I did "modprobe em2880-dvb" before I plugged in the tuner the keyboard didn't freeze up and the tuner actually worked.  I just wasn't able to boot with the tuner plugged in.

---

### Post by bawilson2 on 2008-04-26
> **msrinath80 said:**
> I did not want to bring this up but I have no choice. I just tried the Fedora 9 Preview release live CD and plugged the WinTV HVR 950 in it and to my amazement all drivers were automagically loaded. All it mentioned was that it could not load the firmware file. Once I copied the *.fw file to /lib/firmware, I installed tvtime and within a minute or so I am watching TV again! I will most probably switch to Fedora once Fedora 9 is finally released in about 17 days.

I believe the reason it works in Fedora is because they're using the 2.6.25 kernel.  If Ubuntu would provide an easy way to do that I don't think we'd have a problem but I really don't want to try to build and install my own kernel.

---

### Post by msrinath80 on 2008-04-27
> **bawilson2 said:**
> I had the same problem but found that if I did "modprobe em2880-dvb" before I plugged in the tuner the keyboard didn't freeze up and the tuner actually worked.  I just wasn't able to boot with the tuner plugged in.

When you say that the tuner worked did both audio and video work?

---

### Post by bawilson2 on 2008-04-27
> **msrinath80 said:**
> When you say that the tuner worked did both audio and video work?

Yes, I was able to get the audio and video to work.  I tried tuning to stations using mplayer and everything was ok.  Unplugging the tuner each time I wanted to reboot just wasn't an acceptable solution for me.

---

### Post by teethdood on 2008-04-27
My bootup is also stuck at hald. Before I fiddle some more, I would like to know if the S-Video input work or not. I have a cable box so I will live without the OTA channel functions. I hope things get resolved soon. Thanks

---

### Post by msrinath80 on 2008-04-27
Still no go for me. While video works audio causes an 'Oops' in dmesg. I guess this has something to do with different alsa versions in the kernel and outside it.

---

### Post by KyleBrandt on 2008-04-27
Just added another vote for frozen boot (after patching with the above method).  Didn't follow the one step at a time troubleshooting method to get my machine back up, but here is what I did.

Rebooted to older kernel, added em28xx to /etc/modprobe.d/blacklist, and unplugged the device.  

I am running Hardy which was upgraded from feisty and the version before that.  I had previously compiled the driver on feisty.

---

### Post by teethdood on 2008-04-27
Sorry if I seem to hi-jack this thread. I got xawTV to display analog channels as well as S-video (PCTV HD Pro stick, same chip as HVR-950), no audio however. I'm looking for the file 
v4l-scripts-usbaudio_setup.sh
but can't seem to find it anywhere, maybe one of you have it. Please post the link if possible. Thanks

---

### Post by gekkio on 2008-04-28
Seems like no-one else has the driver successfully working but me.
However, I haven't used my DVB-T in a while, so I might get the crashes too now. It worked a month ago but it's possible that some HAL update or something has broken the driver and causes those crashes.

I think the reason for these crashes is that the driver contains a v4l version that differs from the kernel version. If I could isolate the em28xx driver and compile it with the kernel version of v4l, it could work.
I'll investigate this when I have some free time.

---

### Post by TuxCrafter on 2008-05-04
Ubuntu gets worser and worser, when violation Linux standard base kernel setup, if they worked togheter with debian and fedora things could be come a lot better:

I updated my installation guide that should make it able to install the drivers, but its not a very nice way of doing things:
[http://mcentral.de/wiki/index.php5/Installation_Guide](http://mcentral.de/wiki/index.php5/Installation_Guide)

---

### Post by ichatter231 on 2008-05-04
> **gekkio said:**
> The obj file IS the patch file, it's just named weirdly.

Just download the obj file and patch the source with
```
patch -p0 < v4l-dvb-kernel-Makefile-2.6.24.obj
```

So I typed this in the terminal and I have no idea what's going on. It wants to know which file to patch, as I suppose it should.

What file am I patching, and how do I do so? (command-by-command if possible)

Thanks!

---

### Post by bawilson2 on 2008-05-04
> **ichatter231 said:**
> So I typed this in the terminal and I have no idea what's going on. It wants to know which file to patch, as I suppose it should.

What file am I patching, and how do I do so? (command-by-command if possible)

Thanks!

There are other issues going on beyond just compiling the driver.  Unless somebody else can say different I believe it requires building a new kernel.  You may want to hold off until there's a little easier solution then that.

---

### Post by winterequinox on 2008-05-04
Just to add my 2 cents.  I followed gekkio's instructions from post nr 10 of this thread, and have the same experience as others:  The machine won't boot if the hvr-950 is plugged in.  If I plug it in after the boot, the keyboard stops working (but the mouse still works, I can click on the menu items to shut the machine down.)  If I 'modprobe em2880-dvb' and then plug in the hvr-950. it works and I can watch a dvb broadcast with xine.  It's a 64 bit AMD machine BTW. (My final problem is finding something I want to watch, but that's not for this forum.)

---

### Post by bawilson2 on 2008-05-05
I had a bit of time today so I tried compiling a new kernel.  I stepped up the Hardy kernel to 2.6.25.  Once I did that, I was able to compile the v4l-dvb-experimental drivers without any issue.  It looks like the patch to the makefile has been added to the repository.  Things worked 100%.  Not exactly an easy solution but there are guides out there to do each step.  It just takes a little time.

---

### Post by msrinath80 on 2008-05-07
> **TuxCrafter said:**
> Ubuntu gets worser and worser, when violation Linux standard base kernel setup, if they worked togheter with debian and fedora things could be come a lot better:

I updated my installation guide that should make it able to install the drivers, but its not a very nice way of doing things:
[http://mcentral.de/wiki/index.php5/Installation_Guide](http://mcentral.de/wiki/index.php5/Installation_Guide)

100% true. This is one of the reasons why I will be switching to Fedora 9 in a week. The WINTV HVR 950 works out of the box in F9. Goodbye Ubuntu!

Edit: For all those interested, I have been able to get the WINTV HVR-950 working using the instructions from the lunapark6 website in Debian (testing). So far thumbs up for Debian and Fedora!

---

### Post by tr7110 on 2008-05-07
I have a TX1000 with AMD X2 TL66 CPU's I originally installed Gutsy 7.10 AMD did mods to get sound and network to work as well as Touchscreen. I have a HVR-950 and built the driver as per lunapark Feisty instructions, installed meTV and everything worked fine. Using TV Time I have no sound (as expected). Did an upgrade to Hardy the HVR-950 didn't work so rebuilt the driver using the patch mentioned earlier. after doing the modprobe em2880-dvb tuner worked fine. Did a reboot and pluged in the HVR, lost keyboard functions but the mouse/touchpad still works and meTV said no Tuner but TV Time does recognize the HVR. Reboot again, do a sudo modprobe em2880-dvb. Plug in HVR everything works fine. But in order to use the HVR I must do a sudo modprobe em2880-dvb after each reboot. If I do a modprobe -l em* right after reboot and then again after doing the modprobe em2880-dvb the results are the same. 

Also can't get touchscreen to work in Hardy but thats for another thread.

---

### Post by swheatley on 2008-05-08
I'm having similar difficulties. My setup:

[LIST]
[*]MythBuntu 8.04, 32-bit x86, fresh install
[*]2 x HVR-950 USB HDTV Tuners
[*]1 x PVR-500 PCI Dual Analog Tuner
[/LIST]

I've tried the official instructions, the Lunapark instructions, and installing 2.6.25 via the Master Kernel Thread instructions. None of these seemed to really do the trick. The 2.6.25 kernel was closest, with the devices being detected without audio and without being recognized as DVB devices in MythTV. I've spent about 6 hours so far and just want to watch some TV. I'll probably be switching back to Beyond TV for a few weeks while I wait for an official 2.6.25 kernel.

---

### Post by bawilson2 on 2008-05-08
> **swheatley said:**
> I'm having similar difficulties. My setup:

[LIST]
[*]MythBuntu 8.04, 32-bit x86, fresh install
[*]2 x HVR-950 USB HDTV Tuners
[*]1 x PVR-500 PCI Dual Analog Tuner
[/LIST]

I've tried the official instructions, the Lunapark instructions, and installing 2.6.25 via the Master Kernel Thread instructions. None of these seemed to really do the trick. The 2.6.25 kernel was closest, with the devices being detected without audio and without being recognized as DVB devices in MythTV. I've spent about 6 hours so far and just want to watch some TV. I'll probably be switching back to Beyond TV for a few weeks while I wait for an official 2.6.25 kernel.

I have a similar setup using a Ubuntu 8.04 64bit fresh install.  Updated the kernel to 2.6.25 using the same instructions.  I found that it worked if you used the v4l-dvb-experimental drivers and then did 

modprobe em28xx
modprobe em2880-dvb

Worked without a hitch in MythTv.  Let me know if you're seeing problems.  It worked for me.

---

### Post by tattrat on 2008-05-13
> **gekkio said:**
> 
I managed to get my em2880-dvb working by using this patch from the em28xx mailing list:
[http://mcentral.de/pipermail/em28xx/2008-April/001481.html](http://mcentral.de/pipermail/em28xx/2008-April/001481.html)


This link seems to be dead, does anyone know if the file is available elsewhere?

---

### Post by bawilson2 on 2008-05-13
> **tattrat said:**
> This link seems to be dead, does anyone know if the file is available elsewhere?

The patch is no longer needed if you download the v4l-dvb-experimental driver.

---

### Post by swheatley on 2008-05-13
Thanks bawilson2. I tried again with 2.6.25, but when I tried to build v4lexperimental I got the following error:

> make[2]: Entering directory `/usr/src/linux-2.6.25'
  CC [M]  /home/swheatley/v4l-dvb-experimental/v4l/bt866.o
/home/swheatley/v4l-dvb-experimental/v4l/bt866.c:304: error: unknown field 'usage_count' specified in initializer
/home/swheatley/v4l-dvb-experimental/v4l/bt866.c:305: warning: missing braces around initializer
/home/swheatley/v4l-dvb-experimental/v4l/bt866.c:305: warning: (near initialization for 'bt866_client_tmpl.dev')
make[3]: *** [/home/swheatley/v4l-dvb-experimental/v4l/bt866.o] Error 1
make[2]: *** [_module_/home/swheatley/v4l-dvb-experimental/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.25'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/swheatley/v4l-dvb-experimental/v4l'
make: *** [all] Error 2


Any thoughts?

---

### Post by msrinath80 on 2008-05-13
Yea, switch to Fedora 9. It detects the WinTV HVR 950 out of the box! No more building drivers from experimental repositories.

---

### Post by bawilson2 on 2008-05-13
> **swheatley said:**
> Thanks bawilson2. I tried again with 2.6.25, but when I tried to build v4lexperimental I got the following error:



Any thoughts?

Yeah, sorry I'd forgotten about that.  It came up in two or three places with an error like that.  I commented out the line each time it showed up. So open  up the v4l-dvb-experimental/v4l/bt866.c file and change line 304 from

         .usage_count = 0

to be
        //.usage_count = 0

Like I said there were two or three other places where that same problem showed up, I just don't remember where they were.  Don't be afraid to ask questions.  I do have it working with digital tv OTA for Mythtv.

---

### Post by tattrat on 2008-05-14
I was not getting anywhere with this, so I decided to try from scratch on a clean hardy install.

It didn't seem to work, at first, but after two reboots, the green light on my device was illuminated. SO I did a dmesg | grep em2 and got this result:

```
brendan@testbed:~$ dmesg | grep em2
[   44.819089] em28xx v4l2 driver version 0.0.1 loaded
[   44.819128] em28xx new video device (0ccd:0042): interface 0, class 255
[   44.819131] em28xx: device is attached to a USB 2.0 bus
[   44.819133] em28xx: you're using the experimental/unstable tree from mcentral.de
[   44.819135] em28xx: there's also a stable tree available but which is limited to
[   44.819137] em28xx: linux <=2.6.19.2
[   44.819138] em28xx: it's fine to use this driver but keep in mind that it will move
[   44.819140] em28xx: to http://mcentral.de/hg/~mrec/v4l-dvb-kernel as soon as it's
[   44.819142] em28xx: proved to be stable
[   44.819145] em28xx #0: Alternate settings: 8
[   44.819146] em28xx #0: Alternate setting 0, max size= 0
[   44.819148] em28xx #0: Alternate setting 1, max size= 0
[   44.819150] em28xx #0: Alternate setting 2, max size= 1448
[   44.819152] em28xx #0: Alternate setting 3, max size= 2048
[   44.819154] em28xx #0: Alternate setting 4, max size= 2304
[   44.819156] em28xx #0: Alternate setting 5, max size= 2580
[   44.819158] em28xx #0: Alternate setting 6, max size= 2892
[   44.819160] em28xx #0: Alternate setting 7, max size= 3072
[   45.285351] input: em2880/em2870 remote control as /devices/virtual/input/input10
[   45.540784] em28xx-input.c: remote control handler attached
[   45.570244] em28xx #0: i2c eeprom 00: 1a eb 67 95 cd 0c 42 00 50 12 5c 03 6a 32 9c 34
[   45.570253] em28xx #0: i2c eeprom 10: 00 00 06 57 46 07 00 00 00 00 00 00 00 00 00 00
[   45.570260] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 31 00 b8 00 14 00 5b 00 00 00
[   45.570268] em28xx #0: i2c eeprom 30: 00 00 20 40 20 6e 02 20 10 01 00 00 00 00 00 00
[   45.570275] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   45.570282] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   45.570289] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 32 03 43 00 69 00
[   45.570297] em28xx #0: i2c eeprom 70: 6e 00 65 00 72 00 67 00 79 00 20 00 48 00 79 00
[   45.570304] em28xx #0: i2c eeprom 80: 62 00 72 00 69 00 64 00 20 00 54 00 20 00 55 00
[   45.570311] em28xx #0: i2c eeprom 90: 53 00 42 00 20 00 58 00 53 00 00 00 34 03 54 00
[   45.570319] em28xx #0: i2c eeprom a0: 65 00 72 00 72 00 61 00 54 00 65 00 63 00 20 00
[   45.570326] em28xx #0: i2c eeprom b0: 45 00 6c 00 65 00 63 00 74 00 72 00 6f 00 6e 00
[   45.570333] em28xx #0: i2c eeprom c0: 69 00 63 00 20 00 47 00 6d 00 62 00 48 00 00 00
[   45.570341] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   45.570348] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   45.570355] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   45.572625] tuner 0-0061: chip found @ 0xc2 (em28xx #0)
[   47.087207] em28xx #0: V4L2 VBI device registered as /dev/vbi0
[   47.088916] em28xx #0: V4L2 device registered as /dev/video0
[   47.088919] em28xx #0: Found Terratec Hybrid XS
[   47.088934] em28xx audio device (0ccd:0042): interface 1, class 1
[   47.088944] em28xx audio device (0ccd:0042): interface 2, class 1
[   47.088964] usbcore: registered new interface driver em28xx
[   47.237608] em2880-dvb.c: DVB Init
[   48.495316] DVB: registering new adapter (em2880 DVB-T)
[   55.433930] em28xx-video.c: Switching device from DVB-T to analogue mode
```

Undaunted, I quickly installed me-tv, and fired it up. Blow me, it just got on and tuned all the channels, very quickly in fact.

So, I was able to watch TV; well sort of. The problem is, that about every 3 seconds, the screen goes to white, very quickly, with the end effect rather like flickering. It is similar to what happens with google, which I understand is caused by the ATI proprietary drivers and not google earth.

Is the same same for this, or is the problem in me-tv, or the drivers for the dvb tuner or what? Is it a question of installed codecs (this is a pretty vanilla installation, as thus far I have only installed what has been necessary to get this card going.

Thanks in advance for any ideas.

---

### Post by winterequinox on 2008-05-28
If I could figure out how to start a new thread, I would, but I can't.  This thread's topic is close enough I guess.

OK, so I'm the kind of guy who every now and then builds up a new computer, buying motherboards, memory, cpu chips etc as necessary, and recycling what I can from old broken down ones.  Right now I can almost get 3 computers running simultaneously (not enough power supplies and video cables to go around).  I have some old TV capture cards based on the bttv chips, a hauppage HVR-950 dvb usb dongle, using an em2880 chip, and a pchdtv-3000 PCI based dvb card using a conexant chip.  I can get one of my old bttv capture cards to work in gutsy gibbon, and I've gone and set up one system with gutsy gibbon just to use it since I think I may still want to digitize some old VHS tapes.  I can't get anything bttv working in hardy heron.

I had both dvb devices working in hardy heron, though the HVR-950 you had to first patch, then modprobe before you even plugged it in as a usb device.  The pchdtv was actually working pretty good.  Then I got the notice about upgrading the kernel.  I did that on one system and none of my video devices works on that anymore!  I'm keeping one computer un-upgraded just to be able to use it for dvb reception, just as I'm keeping one system at gutsy gibbon just to be able to use the old bttv devices.

I think ubuntu folks and video4 linux folks need to have a conversation.

Thanks for listening.
PS
It's 3 weeks since I posted the above.  I feel guilty because my post may seem more like a rant than I intended in the heat of the moment of frustration.  I realize it's a very big job maintaining ubuntu, and there are limits to how well the linux kernel folks, and the video4linux folks, and the ubuntu folks can coordinate their efforts.  Keeping hvr-950 owners happy may not be everybody's top priority.  On the other hand, feedback is necessary.  I think around kernel version 2.6.26 the issues with the em2880 chipset are supposed to have be resolved and made a part of the standard kernel, so hopefully, when that gets integrated into the ubuntu releases, things will work.  As I write this, my ubuntu linux kernel is at 2.6.24-19.  I realize there are ways to jump ahead to a more cutting edge kernel, but since I want a 'standard' release and update, I am choosing to wait.

---

### Post by jmw86069 on 2008-06-08
I second the frustrations described here. I followed 100 sets of instructions, and got things working piece by piece, then BOOM an Ubuntu kernel update ruined it all. Would be nice to know, "Hey don't upgrade the kernel if you think *any* of the 100 steps of installs for all your tools may not be perfectly freaking compatible with it.

Two examples of questionable "progress":

1) Very many people's TV cards have stopped working. Isn't that a red flag saying "Do not release new kernel." What's the benefit of a new kernel if you can't use your tools any more??

2) Very many people's ffmpeg doesn't work any more. Isn't *that* a red flag, aren't there a few people out there using ffmpeg??

I mean, I still love Ubuntu, I'm just not speaking to her right now I'm so mad. If/when there's a fix, I'll be among those of us trying to help link to the specific steps.

---

### Post by msrinath80 on 2008-06-08
I went through the same frustration with Hardy a month ago. Then I switched to Feodra 9 and my TV card was detected out of the box. There have been three kernel updates so far on Fedora 9. My HVR 950 is still working like a charm :-)

---

### Post by jmw86069 on 2008-06-10
Hey, haven't you posted like 15 times that you like Fedora 9? We get it, you love Fedora. Great, wonderful.

Why are you posting it so many times on Ubuntuforums.org? Anyway, if somehow the stability of Fedora9 drivers can help me run Ubuntu, please let me know.

---

### Post by mrothwell on 2008-06-10
I've read this thread, and see that patches are needed, change of Kernel, etc...  It appears that some have the 950 working with 8.04.  Could someone document from beginning to end what is needed to get the 950 working.

Thanks.

---

### Post by bawilson2 on 2008-06-10
I have it working but as far as I know the only way to do it is rebuilding your kernel.  Not neccisarly an easy task.  If you're comfortable doing that, I can put together a how-to but if that's more than you'd like to get into I'm not going to take the time to do it.

---

### Post by kirkster86 on 2008-06-11
> **bawilson2 said:**
> I have it working but as far as I know the only way to do it is rebuilding your kernel.  Not neccisarly an easy task.  If you're comfortable doing that, I can put together a how-to but if that's more than you'd like to get into I'm not going to take the time to do it.

I would appreciate knowing how to do this. I have tried several times to get the hvr 950 working with 8.04, but have been unsuccessful to get both audio and video working. I was able to get video working, but without sound, so it is useless to me.

---

### Post by kirkster86 on 2008-06-11
> **msrinath80 said:**
> I went through the same frustration with Hardy a month ago. Then I switched to Feodra 9 and my TV card was detected out of the box. There have been three kernel updates so far on Fedora 9. My HVR 950 is still working like a charm :-)

Also, in my frustration to just get the HVR 950 working I temporarily switched to Fedora 9 just to see if it would work out of the box and eliminate any further frustration. It didn't so I switched back to Ubuntu.

---

### Post by jmw86069 on 2008-06-11
I too would be happy to rebuild the kernel given some steps to follow. There are many how-to guides out there, but I'm not smart enough to know how they fit with the various kernel and driver versions available. I'd really appreciate your guidance since you have it up and running!

---

### Post by mrothwell on 2008-06-11
This is a play system at this point, and if I mess something up, I'll just re-load.  

So, yes, I would like the instructions.

Thank you.

---

### Post by bawilson2 on 2008-06-11
> **mrothwell said:**
> This is a play system at this point, and if I mess something up, I'll just re-load.  

So, yes, I would like the instructions.

Thank you.
I'm working on them now to make sure everything still works the same.  When I verify it all I'll post it.

---

### Post by bawilson2 on 2008-06-11
Ok, let me first state that there can be a lot of problems in each step. Everybody has different hardware so there could be tons of different things going on when a kernel upgrade.  I'll help with what I can but I'm by no means an expert here.  I just really enjoy watching HTDV with Mythtv.  I am only using this for OTA digital signals so I don't know how to get things to work with other inputs, if possible at all.  

Step 1 - Upgrade your kernel to 2.6.25

Upgrade your kernel to 2.6.25.5.  I had it working with 2.6.25.2 and just got it working with 2.6.25.5.  Follow the instructions here:

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

Gotchas that I ran into when doing that were with High Definition sound.  See the Q&A on the Master Kernel Thread for that one.  Loading the new nvidia driver was also kind of a pain.  Since that doesn't apply to everybody I'll leave it out for now.

Step 2 - Download the Firmware

Change Directory
[INDENT]cd /lib/firmware[/INDENT]
Download the firmware 
[INDENT]wget http://konstantin.filtschew.de/v4l-firmware/firmware_v3.tgz[/INDENT]
Extract it
[INDENT]tar xvzf firmware_v3.tgz[/INDENT]

Step 3 - Build the drivers

Change do your home directory
[INDENT]cd ~[/INDENT]
Download the V4L drivers
[INDENT]hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-experimental](http://mcentral.de/hg/~mrec/v4l-dvb-experimental)[/INDENT]
Change to the v4l-dvb directory 
[INDENT]cd v4l-dvb-experimental/[/INDENT]
Modify two files.  Comment out the following lines:
v4l/bt866.c line 304
v4l/ks0127.c line 767

That should take the lines from looking like:
[INDENT].usage_count = 0[/INDENT]
to like this:
[INDENT]//.usage_count = 0[/INDENT]

Then run
[INDENT]make[/INDENT]
and
[INDENT]sudo make install [/INDENT]

Reboot the computer and then try running
[INDENT]sudo modprobe em2880-dvb[/INDENT]

That's all I did.  Sorry it isn't nearly as neat as some guides.  I don't have a lot of time.  Let me know if there are any problems and I'll help as I can.

---

### Post by jmw86069 on 2008-06-12
I'm still going through the "build the kernel" step... but my question is about the firmware. I thought the Pinnacle HD Pro USB (and by same chipset the 950) required firmware v4 and not v3? I'll use what worked for you, but wanted to check that point.

Thank you for taking time to describe what worked for you!

---

### Post by bawilson2 on 2008-06-12
The Pinnacle HD Pro does use the version 4 firmware.  That is actually what I have so I used the version 4.  The Ubuntu Wiki says that the em28xx chipset requires different firmwares depending on the device.  I just switched the instructions to version 3 since that's what the wiki suggested for the HVR-950, which this thread is supposed to be about.

For more info:

[https://wiki.ubuntu.com/em28xx](https://wiki.ubuntu.com/em28xx)

---

### Post by mythtvbvntv on 2008-06-19
Has anyone (else) tried the updated V4L drivers mentioned here:

  [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_HVR-950](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_HVR-950) 

Based on that page (& the lunapark6/techpark6 page), after installing 8.04 & updating to 2.6.24-19-generic, I took the following steps:

# apt-get install mercurial linux-headers-$(uname -r) linux-source build-essential

# cd /lib/firmware

# wget [http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip)

# unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys

# hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

# v4l-dvb/linux/Documentation/video4linux/extract_xc3028.pl

# cd v4l-dvb

# make

# make install

# reboot


I hope this helps!

---

### Post by jmw86069 on 2008-06-24
I'll say I tried to rebuild the kernel, but it started throwing weird errors throughout the process, and I was too skeered to follow through with it!

I did however follow the instructions listed in post 53 (above) and they worked smoothly for 2.6.24-19-generic. I second the vote for following those instructions in absence of other reasonable options. The em28xx drivers are apparently not ready for 2.6.24-19-generic, and I'm not sure everyone needs them.

My issue, if you can call it that now, was that the pinnacle IR remote wasn't working.

I highly recommend an RF MCE remote! I got the "KeySpan RF MCE remote for Vista" from Amazon for something like $35. Omg, using RF is awesome, no line of sight issues, works from the other room, oh it's great. Plus it has buttons that are (1) all recognized by the drivers, and (2) come close to covering the many functions available in MythTV, mplayer, VLC, etc. I started wondering why I was trying so hard to use the Pinnacle remote? Yeah it should work, and if you're travelling you'd want it to work without having to carry something else around, so I get that. But if you can find room for an MCE remote, the buttons are much more useful IMHO, and the drivers work fairly well.

---

### Post by msrinath80 on 2008-06-25
> **kirkster86 said:**
> Also, in my frustration to just get the HVR 950 working I temporarily switched to Fedora 9 just to see if it would work out of the box and eliminate any further frustration. It didn't so I switched back to Ubuntu.

Did you copy the firmware to /lib/firmware in F9 before plugging in your card?

---

### Post by raphy3 on 2008-06-28
> **mythtvbvntv said:**
> Has anyone (else) tried the updated V4L drivers mentioned here:

  [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_HVR-950](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_HVR-950) 

Based on that page (& the lunapark6/techpark6 page), after installing 8.04 & updating to 2.6.24-19-generic, I took the following steps:

# apt-get install mercurial linux-headers-$(uname -r) linux-source build-essential

# cd /lib/firmware

# wget [http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip)

# unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys

# hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

# v4l-dvb/linux/Documentation/video4linux/extract_xc3028.pl

# cd v4l-dvb

# make

# make install

# reboot


I hope this helps!


Did you get analog audio working this way?
I haven't got analog audio working yet because apparently a bug in the Ubuntu kernel prevents the snd-usb-audio driver from being built when the em2880 driver gets built in the v4l tree.

---

### Post by granicus on 2008-06-29
> **gekkio said:**
> It's not there yet, so I recommend that you use the patch on the mailing list. The patch fiddles with include directories, so it might just do the same things you're doing but I urge you to use the patch just to be sure.



Here are the exact steps to install the driver on Hardy (works on my 64-bit installation, should work on 32-bit too):
```

hg clone http://mcentral.de/hg/~mrec/v4l-dvb-experimental
cd v4l-dvb-experimental
wget http://mcentral.de/pipermail/em28xx/attachments/20080402/b43e9afe/v4l-dvb-kernel-Makefile-2.6.24.obj
patch -p0 < v4l-dvb-kernel-Makefile-2.6.24.obj
make
sudo make install

```
+ install firmware using instructions from [http://mcentral.de/wiki/index.php5/Em2880#Installation]("http://mcentral.de/wiki/index.php5/Em2880#Installation")
And reboot.


I assume your card is a USB DVB-T card. Does your system crash when it is not plugged in and you boot into Ubuntu?
Also, please note that this driver will break other v4l drivers (for example, my webcam's uvcvideo driver which is bundled in linux-ubuntu-modules-... package), so if you have a webcam or other potential v4l devices, you could try unplugging them.
I'm using Hardy 64-bit and the drivers works for me so there must be something specific in your system that causes the problems. I'll gladly help with isolating the problem.

Gekkio,

I'm having what appears to be the same problem as above, but am having a problem getting the patch to work.  I've been trying other solutions I've found on the web to the 2880 issue, and I won't rule out problems with conflicts between the various things I've tried today.  I believe I've gotten back to the original v4l drivers as packaged with the Hardy kernel, but as I'm still fairly new to Linux, I would appreciate a bit of instruction there as well.

Back to the problem at hand, when I run the patch I get the following output:

```
patching file v4l/Makefile
Hunk #1 FAILED at 142.
1 out of 1 hunk FAILED -- saving rejects to file v4l/Makefile.rej

```

Obviously this is not what is supposed to happen.  I just upgraded to Hardy (2.6.24-19) today from Gutsy.  Any suggestions?  Thanks.

-Granicus

---

### Post by bawilson2 on 2008-06-30
> **granicus said:**
> Gekkio,

I'm having what appears to be the same problem as above, but am having a problem getting the patch to work.  I've been trying other solutions I've found on the web to the 2880 issue, and I won't rule out problems with conflicts between the various things I've tried today.  I believe I've gotten back to the original v4l drivers as packaged with the Hardy kernel, but as I'm still fairly new to Linux, I would appreciate a bit of instruction there as well.

Back to the problem at hand, when I run the patch I get the following output:

```
patching file v4l/Makefile
Hunk #1 FAILED at 142.
1 out of 1 hunk FAILED -- saving rejects to file v4l/Makefile.rej

```

Obviously this is not what is supposed to happen.  I just upgraded to Hardy (2.6.24-19) today from Gutsy.  Any suggestions?  Thanks.

-Granicus

The instructions you're trying to follow are outdated.  The patch is no longer required if you're using the experimental repositories.  Last I heard the drivers won't work with the 2.6.24 kernel.  If you're going to use those instructions you have to upgrade the kernel.  I have it working using the 2.6.25 kernel.  My suggestion would be to try the instructions in post 53 here.  I haven't tried them but that seems like the easiest way to get this tuner working at this time.

---

### Post by granicus on 2008-06-30
> **bawilson2 said:**
> The instructions you're trying to follow are outdated.  The patch is no longer required if you're using the experimental repositories.  Last I heard the drivers won't work with the 2.6.24 kernel.  If you're going to use those instructions you have to upgrade the kernel.  I have it working using the 2.6.25 kernel.  My suggestion would be to try the instructions in post 53 here.  I haven't tried them but that seems like the easiest way to get this tuner working at this time.

Yeah, I saw those instructions in post 53 after my post and tried them.  They got me up and running, but still not perfect.  I'm able to run the scan channels and view them in MPlayer (with audio, although some channels the audio isn't percetly synched right).  In MythTV itself, the tuner setup recognizes the HVR-950 correctly and the channel scan picks up all the channels in my area.  However, when I go to LiveTV it says it cannot get a channel lock on any of the channels.  

Unsure where to go from here.  I'm not opposed to rebuilding the kernel, but as I am fairly new to Linux (had this box running on 7.10 since December) I would need some help making sure I don't screw things up and can restore back to the old kernel if needed.

Any suggestions?

---

### Post by bawilson2 on 2008-06-30
> **granicus said:**
> Yeah, I saw those instructions in post 53 after my post and tried them.  They got me up and running, but still not perfect.  I'm able to run the scan channels and view them in MPlayer (with audio, although some channels the audio isn't percetly synched right).  In MythTV itself, the tuner setup recognizes the HVR-950 correctly and the channel scan picks up all the channels in my area.  However, when I go to LiveTV it says it cannot get a channel lock on any of the channels.  

Unsure where to go from here.  I'm not opposed to rebuilding the kernel, but as I am fairly new to Linux (had this box running on 7.10 since December) I would need some help making sure I don't screw things up and can restore back to the old kernel if needed.

Any suggestions?

If you're able to view the channels in mplayer then there isn't a problem with the drivers.  It sounds like the problem is probably with your MythTv setup.  Do you have the tuner set as a "DVB DTV capture card" in the tuner setup?  You might also see if there is anything telling in the mythtv logs when you try to start the live tv.

---

### Post by granicus on 2008-06-30
> **bawilson2 said:**
> If you're able to view the channels in mplayer then there isn't a problem with the drivers.  It sounds like the problem is probably with your MythTv setup.  Do you have the tuner set as a "DVB DTV capture card" in the tuner setup?  You might also see if there is anything telling in the mythtv logs when you try to start the live tv.

That was my thought.  I've had it set up as a DVB DTV capture card.  In fact, those setting stayed from the pre-upgrade setup I had.  I also tried removing all capture cards and re-defining.

I'll have to check the logs when I get home to see what is going on.

---

### Post by granicus on 2008-06-30
> **bawilson2 said:**
> If you're able to view the channels in mplayer then there isn't a problem with the drivers.  It sounds like the problem is probably with your MythTv setup.  Do you have the tuner set as a "DVB DTV capture card" in the tuner setup?  You might also see if there is anything telling in the mythtv logs when you try to start the live tv.

Okay, I went in and verified settings.  I didn't change anything, but when I went back into the frontend to run LiveTV to capture logfile information, I actually received signal lock and saw picture.  However, the picture froze after about one second of playback.  Here are the logs.  I have removed a lot of extraneous WriteAudio: Buffer Underrun errors to be concise.

UPDATE:  Okay, good news is that MythTV is now definitely recognizing and locking on the signal.  If I set a program to record in the schedule, it appears to record fine.  Playback works just as if I were watching TV straight from antenna.  The issue described above only seems to be with trying to watch LiveTV.  In fact, even if the video freezes while watching LiveTV, the recorded stream plays back perfectly fine.  Strange, since I have an AMD 5600+ CPU, 2 GB memory, and an ATI HD 2600 Pro 512 MB video card.  System resources shouldn't be an issue.  Again, LiveTV mostly worked fine before the upgrade from 7.10 to 8.04, so my inclination is it is just a settings issue somewhere.

UPDATE 2:  Okay, apparently it working was not a permanent thing.  After being shut down overnight, I have just been informed that it cannot get channel lock again.

mythfrontend.log:
```
2008-06-30 21:03:24.225 TV: Attempting to change from None to WatchingLiveTV
2008-06-30 21:03:24.225 Using protocol version 40
2008-06-30 21:03:25.368 New DB connection, total: 3
2008-06-30 21:03:25.369 Connected to database 'mythconverg' at host: localhost
2008-06-30 21:03:25.378 NVP: Disabling Audio, params(-1,2,44100)
2008-06-30 21:03:25.435 DPMS Deactivated 
2008-06-30 21:03:25.457 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2008-06-30 21:03:25.505 OSD Theme Dimensions W: 640 H: 480
2008-06-30 21:03:25.636 TV: Changing from None to WatchingLiveTV
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 720 x 576
2008-06-30 21:03:25.638 Realtime priority would require SUID as root.
2008-06-30 21:03:25.717 Video timing method: USleep with busy wait
2008-06-30 21:03:27.787 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
yadifdeint: size changed from 720 x 576 -> 1920 x 1088
2008-06-30 21:03:28.112 AFD: Opened codec 0x7f546e2f0790, id(MPEG2VIDEO) type(Video)
2008-06-30 21:03:28.112 AFD: codec AC3 has 6 channels
2008-06-30 21:03:28.113 AFD: Opened codec 0x7f546e2eec00, id(AC3) type(Audio)
2008-06-30 21:03:28.418 Opening audio device 'default'. ch 2(2) sr 48000
2008-06-30 21:03:28.418 Opening ALSA audio device 'default'.
2008-06-30 21:03:28.465 mixer unable to find control Master 1
2008-06-30 21:03:28.475 NVP: Enabling Audio
2008-06-30 21:03:32.433 WriteAudio: buffer underrun
...
2008-06-30 21:03:32.564 WriteAudio: buffer underrun
2008-06-30 21:03:32.607 [mpeg2video @ 0x7f549745f5b0]invalid mb type in P Frame at 52 47
2008-06-30 21:03:32.610 [mpeg2video @ 0x7f549745f5b0]Warning MVs not available
2008-06-30 21:03:32.621 WriteAudio: buffer underrun
...
2008-06-30 21:03:35.108 WriteAudio: buffer underrun
2008-06-30 21:03:35.149 [mpeg2video @ 0x7f549745f5b0]Warning MVs not available
2008-06-30 21:03:35.157 WriteAudio: buffer underrun
...
2008-06-30 21:03:38.207 WriteAudio: buffer underrun
2008-06-30 21:03:40.271 [mpeg2video @ 0x7f549745f5b0]00 motion_type at 25 2
2008-06-30 21:03:40.272 [mpeg2video @ 0x7f549745f5b0]00 motion_type at 6 17
2008-06-30 21:03:42.136 [mpeg2video @ 0x7f549745f5b0]00 motion_type at 40 10
2008-06-30 21:03:42.141 [mpeg2video @ 0x7f549745f5b0]00 motion_type at 58 46
2008-06-30 21:03:42.142 [mpeg2video @ 0x7f549745f5b0]Warning MVs not available
2008-06-30 21:03:43.661 [ac3 @ 0x7f549745f5b0]delta bit allocation strategy reserved
2008-06-30 21:03:43.661 [ac3 @ 0x7f549745f5b0]error parsing the audio block
2008-06-30 21:03:45.767 WriteAudio: buffer underrun
...
2008-06-30 21:03:46.433 WriteAudio: buffer underrun
2008-06-30 21:03:46.472 TV: Attempting to change from WatchingLiveTV to None
2008-06-30 21:03:46.474 WriteAudio: buffer underrun
2008-06-30 21:03:46.665 TV: Changing from WatchingLiveTV to None
2008-06-30 21:03:46.672 DPMS Reactivated.
Destroying SipFsm object 

```

Thanks for all your help.  it really is appreciated.

---

### Post by bawilson2 on 2008-07-01
> **granicus said:**
> Okay, I went in and verified settings.  I didn't change anything, but when I went back into the frontend to run LiveTV to capture logfile information, I actually received signal lock and saw picture.  However, the picture froze after about one second of playback.  Here are the logs.  I have removed a lot of extraneous WriteAudio: Buffer Underrun errors to be concise.

UPDATE:  Okay, good news is that MythTV is now definitely recognizing and locking on the signal.  If I set a program to record in the schedule, it appears to record fine.  Playback works just as if I were watching TV straight from antenna.  The issue described above only seems to be with trying to watch LiveTV.  In fact, even if the video freezes while watching LiveTV, the recorded stream plays back perfectly fine.  Strange, since I have an AMD 5600+ CPU, 2 GB memory, and an ATI HD 2600 Pro 512 MB video card.  System resources shouldn't be an issue.  Again, LiveTV mostly worked fine before the upgrade from 7.10 to 8.04, so my inclination is it is just a settings issue somewhere.

UPDATE 2:  Okay, apparently it working was not a permanent thing.  After being shut down overnight, I have just been informed that it cannot get channel lock again.

Thanks for all your help.  it really is appreciated.

I'm afraid that I'm not sure what's going on there.  You may have to try to find some more specific help with regards to Mythtv.  I have Mythtv up and running but that wasn't an error that I encountered at all.

---

### Post by bigdawgte on 2008-07-04
I am a noob. This post is not about compilation, but apparently I am not yet permitted to make new posts, as a noob.  I too am having trouble installing an HVR-950 - actually, an HVR-980, or EyeTV Hybrid (Mac OS X)- a nearly identical piece of hardware to the Hauppage.  However, my trouble in installing is because of the method of installation in linux.  The method recommended by everyone in Ubuntu (and otherwise) requires to "hg clone" to [http://mcentral.de/hg/~mrec/v4l-dvb-kernel](http://mcentral.de/hg/~mrec/v4l-dvb-kernel).  I have been trying to do this step for two days now and the site is unavailable.  How can it be that with hardware this popular, the entire world has to go to the back porch of this one guy and get what they need out of the back door from a brown paper bag? And is this news to the linux community?  I found [this article]("http://www.makomk.com/index.php/2008/03/16/v4l-dvb-experimental-and-v4l-dvb-makomk-are-dead/"), which states: "In case you haven’t noticed, both Markus’ v4l-dvb-experimental and my v4l-dvb-makomk are slowly dying." If this is the only way this hardware can be installed, can't anything be done about it?  Why isn't this important?  Yes, I know its free - and that may be the problem - absence of market forces to drive action.  Because whatever IS driving innovation in Ubuntu/linux, IMHO and experience, is not nearly rational (I could sing a song of woe about trying to install Ubuntu on two of my machines, but what would be the point?)

---

### Post by msrinath80 on 2008-07-05
> **bigdawgte said:**
> I am a noob. This post is not about compilation, but apparently I am not yet permitted to make new posts, as a noob.  I too am having trouble installing an HVR-950 - actually, an HVR-980, or EyeTV Hybrid (Mac OS X)- a nearly identical piece of hardware to the Hauppage.  However, my trouble in installing is because of the method of installation in linux.  The method recommended by everyone in Ubuntu (and otherwise) requires to "hg clone" to [http://mcentral.de/hg/~mrec/v4l-dvb-kernel](http://mcentral.de/hg/~mrec/v4l-dvb-kernel).  I have been trying to do this step for two days now and the site is unavailable.  How can it be that with hardware this popular, the entire world has to go to the back porch of this one guy and get what they need out of the back door from a brown paper bag? And is this news to the linux community?  I found [this article]("http://www.makomk.com/index.php/2008/03/16/v4l-dvb-experimental-and-v4l-dvb-makomk-are-dead/"), which states: "In case you haven&#8217;t noticed, both Markus&#8217; v4l-dvb-experimental and my v4l-dvb-makomk are slowly dying." If this is the only way this hardware can be installed, can't anything be done about it?  Why isn't this important?  Yes, I know its free - and that may be the problem - absence of market forces to drive action.  Because whatever IS driving innovation in Ubuntu/linux, IMHO and experience, is not nearly rational (I could sing a song of woe about trying to install Ubuntu on two of my machines, but what would be the point?)

Hi there,

Not sure about those repos dying, but if I were to guess I'd say they are being obsoleted as all relevant drivers are being made part of the stock kernel source. For instance, I use Fedora 9 which comes with a 2.6.25.* kernel. When I plug my HVR 950 in, Fedora 9 instantly recognizes it and all necessary modules are loaded automatically. Then all I have to do is fire up mplayer or tvtime and I am good to go.

---

### Post by TuxCrafter on 2008-07-05
After reading so many post about these old installation methods i want to post this message again:

A few notes:

I am not a developer on this project, i only did some documentation, and tried to help the developer use better development strategies so his work can be included upstream.

The problem the developers work is a nasty fork of the mainstream system. This problem makes it necessary to manually compile the drivers. On debian sid this takes me 10 minutes time with every new kernel release.

With ubuntu this is something different because ubuntu also does something very nasty splitting parts of the kernel with different source versions etcetra (audio is separated). You can either remove the ubuntu kernel with a normal debian kernel or manually recomplile a ubuntu or mainstream kernel or make the ubuntu developers change there strategy so the use mainstream LSB kernel compile and distribution methods.

This is the installation documentation wiki website:
[http://mcentral.de/wiki/index.php5/Installation_Guide](http://mcentral.de/wiki/index.php5/Installation_Guide)

I attached my documentation that i use to install things in less then 10 minutes in debian sid.

And to everybody, yes i know this is not a pretty thing, thinks should be better, but sadly this is not the case. I hope this helps some people to get things working, you can also try switching to debian.

---

### Post by TuxCrafter on 2008-07-05
> **msrinath80 said:**
> Hi there,

Not sure about those repos dying, but if I were to guess I'd say they are being obsoleted as all relevant drivers are being made part of the stock kernel source. For instance, I use Fedora 9 which comes with a 2.6.25.* kernel. When I plug my HVR 950 in, Fedora 9 instantly recognizes it and all necessary modules are loaded automatically. Then all I have to do is fire up mplayer or tvtime and I am good to go.

.. and this is not true for everybody, you are using the mainstream code, there is also a big fork with the new drivers that have more features and better audio support. Be aware not to mix up the to because they are so different. I do hope the developers of both forks can merge together again, previous attempts to do this have failt sadly.

---

### Post by msrinath80 on 2008-07-05
> **TuxCrafter said:**
> .. and this is not true for everybody, you are using the mainstream code, there is also a big fork with the new drivers that have more features and better audio support. Be aware not to mix up the to because they are so different. I do hope the developers of both forks can merge together again, previous attempts to do this have failt sadly.

So far, I know for a fact that the WINTV HVR 950 hybrid TV stick and the Pinnacle HDTV Pro Stick 800e work out of the box with Fedora 9. They both use the firmware file xc3028-v27.fw which needs to be copied to /lib/firmware.

---

