---
title: "WUSB54GC not Working on 10.04"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by aleherma on 2010-06-17
Hello all,

i recently installed lucid Lynx in my laptop, everything works great except my WUSB54GC (v3) usb wireless adapter, the green light in the usb stick stays off and the OS don't recognize the USB either (i have been using it in WIN7 so i know its not broken) 

reading previous post i tried the following:

[I]sudo gedit /etc/modprobe.d/blacklist.conf

Added a line

blacklist rt2800usb[/I]  

after restart it was recognized but only worked for a little while (with download speeds about 30kbps and disconnecting every 30 min or so ) today it wasn't working at all

I have also tried installing the driver provided by linksys using the "windows  wireless drivers" obtained by  ubuntu software center, no luck there :(


could anyone give me a hand here

thanks for your time

---

### Post by b k on 2010-06-17
> **aleherma said:**
> Hello all,

i recently installed lucid Lynx in my laptop, everything works great except my WUSB54GC (v3) usb wireless adapter, the green light in the usb stick stays off and the OS don't recognize the USB either (i have been using it in WIN7 so i know its not broken) 

reading previous post i tried the following:

[I]sudo gedit /etc/modprobe.d/blacklist.conf

Added a line

blacklist rt2800usb[/I]  

after restart it was recognized but only worked for a little while (with download speeds about 30kbps and disconnecting every 30 min or so ) today it wasn't working at all

I have also tried installing the driver provided by linksys using the "windows  wireless drivers" obtained by  ubuntu software center, no luck there :(


could anyone give me a hand here

thanks for your time

Hi there, I have the exact same linksys Wusb54gc v3 (device ID 1737:0077) - [COLOR=Red]check[/COLOR] this from a Terminal window with:

```
lsusb
```

I have done exactly what you did and my adapter is [COLOR=Blue]working fine[/COLOR].

I suggest that you try to 'undo' what ever you have done after the procedure above before proceeding further as your problem may be something else than conflicting drivers.

Post the outputs of:

```
lsmod
```

```
lshw -C network
```

```
iwconfig
```

You may wish to transfer the outputs above to a text file first and then transfer the contents of the file to your working computer (with a internet connection) for posting back on this forum.

Thanks.

PS : some people also[COLOR=Red] in addition[/COLOR] to adding *blacklist rt2800usb *also add another two lines:

blacklist rt2x00usb
blacklist rt2x00lib

to the blacklist.conf file

---

### Post by aleherma on 2010-06-17
thanks for the answer, after  i got it working the only changes i made were installing a couple of games and audio software



> alex@alex-laptop:~$ lsusb
Bus 002 Device 002: ID 0458:002e KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 1737:0077 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
as far as i can tell the usb is detected 


> alex@alex-laptop:~$ lsmod
Module                  Size  Used by
ndiswrapper           184677  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_conexant    22577  1 
joydev                  8708  0 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               9961216  41 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
soundcore               6620  1 snd
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
led_class               2864  1 sdhci
ricoh_mmc               2923  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_nforce2             5199  0 
agpgart                31724  1 nvidia
vga16fb                11385  1 
vgastate                8961  1 vga16fb
k8temp                  3024  0 
psmouse                63245  0 
serio_raw               3978  0 
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
forcedeth              49556  0 
sata_nv                19440  2 
pata_amd                8766  0 
-----------------------------------

> 
alex@alex-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
tried to sudo but got no output


----------------------------------------

alex@alex-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



---------------------------------------


going to try adding the 2 other lines , posting results in a while

Thanks a lot!!!!!!!!


edit: no luck adding both lines after reboot

---

### Post by b k on 2010-06-17
Hi there what I can tell at the moment is that you somehow have ndiswrapper installed.

> alex@alex-laptop:~$ lsmod
Module                  Size  Used by
[COLOR=Red]ndiswrapper[/COLOR]           184677  0 
binfmt_misc             6587  1 

What happens is that we normally would use the [COLOR=Red]native[/COLOR] driver (within Ubuntu OS) - rt2870 for this particular wireless adapter.

If this is not possible, then we install [COLOR=Red]ndiswrapper [COLOR=Black](and then use the [COLOR=Red]windows driver[/COLOR] for the wireless adapter).[/COLOR][/COLOR]

We choose one [COLOR=Red]OR[/COLOR] the other (not both)

May I suggest that you 'uninstall' the [COLOR=Red]ndiswrapper

[COLOR=Black]Reboot

and see what happens.

[COLOR=Red]Check[/COLOR] within the blacklist.conf file to make sure that [COLOR=Red]there is no[/COLOR] blacklist rt2870 line in there.

Thanks and post back.


[/COLOR][/COLOR]

---

### Post by aleherma on 2010-06-17
edit: i think i installed ndiswrapper for windows wireless drivers

uninstalled using 

sudo aptitude purge ndiswrapper

unfortunately im still not able to 'see' the usb or detect wireless conections

this is how my black list looks like 

> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00libThank you

---

### Post by b k on 2010-06-17
Hi again, try shutting down the computer, then remove the wireless adapter, then reboot, after that plug in the wireless adapter again - any difference.

If still unsuccessful, post the output of* lsmod* ,* lshw -C network* , and *ifconfig* again,


Sorry typo error

---

### Post by aleherma on 2010-06-17
no luck :(

> alex@alex-laptop:~$ lsmod
Module                  Size  Used by
ndiswrapper           184677  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_conexant    22577  1 
joydev                  8708  0 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               9961216  41 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd                    54148  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
led_class               2864  1 sdhci
agpgart                31724  1 nvidia
ricoh_mmc               2923  0 
soundcore               6620  1 snd
i2c_nforce2             5199  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
k8temp                  3024  0 
psmouse                63245  0 
serio_raw               3978  0 
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
pata_amd                8766  0 
sata_nv                19440  2 
forcedeth              49556  0 
lshw -C network // no output again

> alex@alex-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:7f:f6:a8  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe7f:f6a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:283518 (283.5 KB)  TX bytes:46282 (46.2 KB)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

it seems ndiswrapper is still there :S

edit: tried to unistall windows wireless drivers via ubuntu software center, rebooted but still not able to detect it lsmod
still shows ndiswrapper

---

### Post by b k on 2010-06-17
> **aleherma said:**
> no luck :(
 
lshw -C network // no output again
 
 
it seems ndiswrapper is still there :S
 
edit: tried to unistall windows wireless drivers via ubuntu software center, rebooted but still not able to detect it lsmod
still shows ndiswrapper
 
See this link section 5 on how to remove ndiswrapper [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
 
Not sure though if all the commands are valid for Ubuntu 10.04 LTS.
 
Good luck and post back.
 
Try *sudo lshw -C network *instead.

---

### Post by aleherma on 2010-06-17
uninstalling with the previous guide worked like a charm, i am now able to detect and connect to wireless networks, thanks for your help it was really usefull.

 Another question, is there anyway to save the passwords for wireless networks so it doesnt ask for the password every time i try to connect to it , thanks.

---

### Post by b k on 2010-06-17
> **aleherma said:**
> uninstalling with the previous guide worked like a charm, i am now able to detect and connect to wireless networks, thanks for your help it was really usefull.

 Another question, is there anyway to save the passwords for wireless networks so it doesnt ask for the password every time i try to connect to it , thanks.

Congratulations on your success.

If you currently are configure to manually login to your user account at bootup (and [COLOR=Red]don;t want to change[/COLOR] this), but wish to autoconnect to your wireless connection after you have maually login to your user account, then do this:

Go to *System > Preferences > Network Connections*

then select *Wireles*s, *Name* (of your wireless connection). *Edit*

Then tick/check *Connect automatically* and *Available to all users* , *Apply*

Reboot.  That should do the trick.

If you want to configure your computer to [COLOR=Red]both[/COLOR] autologin to user account as well as autoconnect to your wireless network then see post #1 of this link [http://ubuntuforums.org/showthread.php?p=2776815#post2776815](http://ubuntuforums.org/showthread.php?p=2776815#post2776815)

Hope the info is useful.

---

### Post by Zammin on 2010-07-11
> **b k said:**
> [COLOR=Red][COLOR=Black]

[COLOR=Red]Check[/COLOR] within the blacklist.conf file to make sure that [COLOR=Red]there is no[/COLOR] blacklist rt2870 line in there.

[/COLOR][/COLOR]

I follow your thread, but you say "make sure there is "no" blacklist rt2870 ..... " is not work for me.. for I just have to add those 3 lines (after trying just add 2 lines that not work for me), then reboot and linksys WUSB54GC works automagically..

blacklist rt2800usb  
blacklist rt2x00usb
blacklist rt2x00lib

Anyway thank you so much  for the solution for this linksys wireless usb adapter..

---

### Post by TheCpaptain on 2010-07-18
Hello all,

I believe I have the exact same problem as posted in this thread, the thing is though that I am a [COLOR=Blue]complete beginner[/COLOR] when it comes to Linux.

I am using Ubuntu 10.04 LTS on my stationary comp, which also has Windows 7 in addition (though linux has its own partial space). I installed Ubuntu quite recently, and I had some great difficulties getting my [COLOR=Black]WUSB300N[/COLOR] adapter to work, and I sat many hours with people from the support forum, but to no success.

Eventually I bought the Linksys [COLOR=Blue]WUSB54GC Adapter[/COLOR], since I read somewhere that it should work fine.

I've tried a couple of other threads on this, but as it seems, they've been on older versions of Ubuntu, and I haven't been successful in getting it to work.

Now I have (to the fullest extent of my knowledge) undone all the modifications i've done previously, and I now need to test something else, hence this post.

I really need some [COLOR=Blue]step by step instructions on what to do[/COLOR]. I'm not completely unfamiliar with the Terminal by now, but I don't understand what you mean when you say add a line or so (that is how to do that). I would really appreciate getting help in this matter.

Thanks in advance

---

