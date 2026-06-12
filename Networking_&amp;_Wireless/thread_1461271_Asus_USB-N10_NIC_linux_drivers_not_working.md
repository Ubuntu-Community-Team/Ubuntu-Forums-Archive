---
title: "Asus USB-N10 NIC linux drivers not working"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by DarKK_MessiaH on 2010-04-24
Hi all, I was hoping for some advice to overcome a driver issue I'm having. I've followed the guide to installing the drivers through the terminal (I'm a linux newb btw) and am returned with this logging info:

```
samuel@samuel-desktop:~/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/samuel/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.o
/home/samuel/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c: In function ‘rtl8192_usb_probe’:
/home/samuel/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12317: error: ‘struct net_device’ has no member named ‘open’
/home/samuel/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12318: error: ‘struct net_device’ has no member named ‘stop’
/home/samuel/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12319: error: ‘struct net_device’ has no member named ‘tx_timeout’
/home/samuel/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12320: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/samuel/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12321: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/samuel/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12322: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/samuel/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12323: error: ‘struct net_device’ has no member named ‘get_stats’
/home/samuel/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12324: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/samuel/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.o] Error 1
make[1]: *** [_module_/home/samuel/Desktop/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2

```

I've had a rummage around the forums etc and have an idea that the error relates to the version of the Linux kernel I'm running. Apparently version 2.6.31 removes support for the old net_device api.

I'm running Ubuntu 9.10.

Is there anyway I can still use this device or do I have to wait for updated drivers from Asus?

---

### Post by gpecke on 2010-05-18
I tried several approaches to this.
1/ Tried to compile Asus linux driver. This will not make against later kernel because
    of changes to the net calls. It did'nt seem worth patching the file core.c to the new 
   format.

2/ Tried using the staging kernel drivers in kernel 2.6.34-rc7 after patching in the usb-id
   etc. . Unfortunately it was not easily possible to find the  right firmware files to install.
 
3/ The last approach, which worked with no problems at all , was to download the
    file RTL8192SU_usb_linux_v2.6.0006.20100511.zip from the Ralink site.
    This file extracted with unzip and tar  and then compiled with "make" and
    "make install" with no  fiddling required at all! The module is called 8172u 

:)

    The adapter works nicely, and has been quite sensitive and reliable so far....
    Especially considering how small it is.

---

### Post by Rayve on 2010-06-17
gpecke,

You, sir/ma'am, are a genius.  Couldn't figure out why the driver that came with the disk wouldn't install.  I've got the new driver downloaded now, except it doesn't want to work...

It completely freezes my computer whenever I try to "sudo insmod 8712u.ko" as it says in the instructions.  As in, I can't even Ctrl+Alt+F1 to a VT.  No mouse movement, no keyboard input, nothing.  I have to do a hard reboot.

I did "make", and then tried "make install" but it wouldn't work.  The instructions say "./clean" which does nothing and then "insmod 8712u.ko" which is where I'm stuck.

Any thoughts?

Edit: I also found this link through another post here, [http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html](http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html), but my computer again froze after the "sudo modprobe 8712u".  This time, I couldn't even finish the boot up process in normal or recovery kernel until I removed the dongle from my USB port.  

I will try modprobe without the dongle plugged in and see if that works, but... :(  I hate all this cold rebooting.

Edit 2: Okay, unplugging it and running modprobe works... however, whenever I plug it in, it freezes my system again instantly.  Unplugging it does not restore use, I have to reboot with the dongle unplugged to get things back in order.  /sigh

A bug or am I missing a fix somewhere?

Edit3: Found this post ([http://art.ubuntuforums.org/showthread.php?p=9252137](http://art.ubuntuforums.org/showthread.php?p=9252137)) which was rather helpful, so will update with relevant questions there.  Will post back if I get it working.

---

### Post by gpecke on 2010-06-27
I am using kernel 2.6.34-rc7 which I compiled myself on that pc, and made sure that all kernel symbols/headers etc were correct.
The ralink wifi package made and compiled ok aganst that kernel version.
My suspicion is that ralink have been updating their package against the mods made to the kernel net calls.
I would suspect that your module hung the kernel because of a version mismatch.
Hopefully the ralink driver (working version) will be included in the kernel soon.
If you are completely stuck, I'll email you the .config I used for the kernel, or the compiled .debs for kernel ,headers and 8712u.ko for that matter. 
Ill check this thread again in a few days.

---

### Post by GlowingApple on 2010-11-17
> **gpecke said:**
> The last approach, which worked with no problems at all , was to download the file RTL8192SU_usb_linux_v2.6.0006.20100511.zip from the Ralink site.

Just thought I'd post a thank you for this!  I just bought the ASUS USB-N10, got it home, and was disappointed to see the latest online drivers (from ASUS) fail to compile.  The Ralink driver compiles easily and my wireless adapter is now working well!

---

### Post by gunterhausfrau on 2011-01-10
ok, maybe I am being a nitwit, do you have a link for the ralink site? I go to what I think is the site, but they don't seem to have anything for 8192.

---

### Post by PatchesTheCaveman on 2011-01-11
I think he meant Realtek, not Ralink:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

---

### Post by gunterhausfrau on 2011-01-11
that makes sense. Ok, got the file, and was following the instructions from Samiux. I was able to most of the way, but got stuck at the make install. Up to this point, no errors that I noticed.

sudo make install
cp: cannot stat `/autoconf_rtl8712_usb_linux.h': No such file or directory
install -p -m 644 8712u.ko  /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.35-22-generic
root@blacktop:/home/gunter/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111# 

or should I just be doing the unmod'd Makefile? 

are there instructions for the linux challenged?

---

### Post by PatchesTheCaveman on 2011-01-12
You ran *make* before that right?

It looks like it might have completed.  Try running:
```
sudo modprobe rtl8712u
```

If that doesn't give you an error.  See if your wireless works.  If not, run:
```
dmesg | grep -i rtl
```
and copy/paste the output.

---

### Post by gunterhausfrau on 2011-01-12
yep, make worked without error, and the file that it says not found looks to be there. I'll try your suggestion and get back. Thanks for the help, I really don't want to go back to windows (tried clean install of windows and was able to get the hardware to work, then back to clean ubuntu and having problems)

---

### Post by chili555 on 2011-01-12
> **PatchesTheCaveman said:**
> You ran *make* before that right?

It looks like it might have completed.  Try running:
```
sudo modprobe rtl8712u
```

If that doesn't give you an error.  See if your wireless works.  If not, run:
```
dmesg | grep -i rtl
```
and copy/paste the output.I think patches means:```
sudo modprobe 8712u
dmesg | grep 8712
```Please see:> install -p -m 644 [COLOR="Red"]8712u[/COLOR].ko /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/In contrast to most other Realtek drivers, this one has no rtl or r. Undoubtably, just to keep patches and me guessing!

---

### Post by gunterhausfrau on 2011-01-12
holy cow, the thing that wouldn't die. I was able to run without the rtl and finished with no errors. Still no wireless, no errors, but no wireless. lsusb sees it. Tried rebooting (old habit) still nothing.

I've been using the suggestions from Samiux's blog, changes to the Makefile and all. 

I really appreciate the help.

---

### Post by PatchesTheCaveman on 2011-01-13
Please copy/paste the output of:
```
lsmod
dmesg | grep -i 8712
```

---

### Post by gunterhausfrau on 2011-01-13
ok, here you go. I also did the grep with 8192 as that is that actual chipset (but also did the 8712, as that what what you asked for, but there was no output)

thanks.

gunter@blacktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
i915                  290938  2 
snd_intel8x0           25632  2 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
thinkpad_acpi          67659  0 
drm_kms_helper         30200  1 i915
snd_seq_midi            4588  0 
8712u                 301910  0 
joydev                  8735  0 
pcmcia                 35973  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
nsc_ircc               18252  0 
drm                   168054  2 i915,drm_kms_helper
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0 
r8192s_usb            287340  0 
irda                  178938  1 nsc_ircc
intel_agp              26360  2 i915
parport_pc             26058  1 
yenta_socket           21518  0 
led_class               2633  1 thinkpad_acpi
pcmcia_rsrc            10566  1 yenta_socket
nvram                   6342  1 thinkpad_acpi
crc_ccitt               1351  1 irda
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
eeprom_93cx6            1345  1 r8192s_usb
snd                    49006  12 snd_intel8x0,snd_ac97_codec,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
psmouse                59033  0 
shpchp                 29886  0 
agpgart                32011  2 drm,intel_agp
serio_raw               4022  0 
output                  1883  1 video
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
e100                   30356  0 
usbhid                 36882  0 
floppy                 54311  0 
mii                     4425  1 e100
hid                    67742  1 usbhid
gunter@blacktop:~$ dmesg | grep -i 8712
gunter@blacktop:~$ dmesg | grep -i 8192
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.150266] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.150279] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[   19.613387] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   19.877578] Linux kernel driver for RTL8192 based WLAN cards
[   21.075202] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   21.189975] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
gunter@blacktop:~$

---

### Post by PatchesTheCaveman on 2011-01-13
Run:
```
sudo ln -s /lib/firmware/RTL8192SE/ /lib/firmware/RTL8192SU
sudo modprobe -r r8192s_usb
sudo modprobe r8192s_usb
```

Give it another shot.  If that fails, run these commands and copy/paste:
```
dmesg | grep -i rtl
```

---

### Post by gunterhausfrau on 2011-01-13
WOOT!
it works! I really was at the end, tonight I was going to reformat and go back to that other operating system. Very relieved.

Now, if I can ask one more question. What did we just do? I'd like to understand vs. just fix.

Thanks much.

---

### Post by PatchesTheCaveman on 2011-01-14
Many wireless cards need some programming (called "firmware") loaded into them to work.  For reasons unknown, Ubuntu didn't include the firmware for that particular card it in the directory it needed to be in.  Luckily, the firmware for the very similar RTL8192SE chipset also works with your card's RTL8192SU chipset.  

So, you just created a what is called a "symbolic link" pointing whatever looks in the RTL8192SU directory to the RTL8192SE directory.  You could have also just copied the files, but doing that way ensures that you get any updates to the RTL8192SE firmware should they be installed.

Glad to hear everything's working now.  :-D

---

### Post by Xanth on 2011-01-22
Hello I'm having some difficulty installing these drivers on Ubuntu 10.10.

When I type "sudo make install" :
Makefile:11: /config: No such file or directory
make: *** No rule to make target `/config'.  Stop.

I'm not sure what's going on... (if I don't use sudo..):
install -p -m 644 8712u.ko  /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/
install: cannot create regular file `/lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/8712u.ko': Permission denied
make: *** [install] Error 1

Thanks.

Edit: Bah, just sucked it up and used ndiswrapper...

---

### Post by lee500 on 2011-01-26
Hi, I`m a newbie and have installed Ubuntu 10.10 and been having fun and games installing (or trying to!) whilst lurking and reading all the different replies and help, 
someone posted earlier about mdseg ... tried it and the drivers flew in!!! thankyou.
 
Only trouble is, that although the N10 dongle is active, it will not link up to my Belkin router by adding another PC .... something about different systems viz:-
==============================================================================================================
[FlashConfig]
TEXT=The wizard cannot automatically configure your network settings on the version of Windows that is running on this computer.\r\n\r\nDo you want to print your network settings so that you can enter them manually for this computer?
TITLE=Wireless Network Setup Wizard.
==============================================================================================================
 
The N10 dongle is running with lights and the connection is made to my router but it just will not accept the generated pass code and keeps requesting to input passcode..
 
I have two other pc`s linked up using add pc but one is using w7 and the other plus main is XP ...... they flew in - HELP.....:mad:.
 
Lee.

---

