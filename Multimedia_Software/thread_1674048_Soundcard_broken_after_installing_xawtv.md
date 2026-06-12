---
title: "Soundcard broken after installing xawtv"
date: 2011-01-23
forum: Multimedia Software
---

### Post by LFS-Nr-3305 on 2011-01-23
Hi,
after installing xawtv, and after using mencoder with the following:```

mencoder -tv norm=PAL-60:driver=v4l2:width=720:height=576:input=1:alsa:fps=25 tv:// immediatemode=1 -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf pp=lb/ha/va/dr,hqdn3d,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1500:vrc_maxrate=8000:vbitrate=7000:keyint=15:acodec=mp2:abitrate=192:aspect=16/10 -o capture.mpg
```
my sound device is broken. 
I used to listen to Sound after calling 
```
alsamixer -D hw:1
```
but now alsamixer terminates with "Error while opening mixer device" (Fehler beim Öffen des Mixer-Gerätes): No such file or directory.
In Ubuntu I had to use System/Settings/Sound additionally and make the settings, but now there is no more device listed under "hardware". 

As I can not afford buying a new pc, nor a separate tv or CD player, which until now I did via my PC, I would be very grateful if somebody could help me! Is there some way how I could check if the Sound Chip on my board is still working and it is an Ubuntu problem? I did not know that installing or using software could damage my hardware.

Ubuntu Version is 10.04 LTS.

cat: /proc/asound/version: No such file or directory

root@A-64:~# lspci | grep -i audio 
05:05.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)

root@A-64:~# lsusb 
(...)
Bus 003 Device 003: ID 0d8c:0201 C-Media Electronics, Inc. CM6501

Is there a way to re-install the sound system? I think something killed the kernel module(s) necessary for sound.
----------------------------------
Edit: I did
 ```

root@A-64:~# modprobe -l | grep snd |grep bt87
kernel/sound/pci/snd-bt87x.ko
root@A-64:~# modprobe snd-bt87x
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.

```
And my TV-Card is back (Ubuntu believes it is one of the soundcards):
```

root@A-64:~# cat /proc/asound/cards
 1 [Bt878          ]: Bt87x - Brooktree Bt878
                      Brooktree Bt878 at 0xfcfff000, irq 18

```
Now, how can I get my Onboard-Soundchip CM6501 back?

Edit 2:
I did
```

modprobe -l | grep snd | grep usb

kernel/sound/usb/snd-usb-audio.ko
kernel/sound/usb/snd-usb-lib.ko
kernel/sound/usb/usx2y/snd-usb-usx2y.ko
kernel/sound/usb/usx2y/snd-usb-us122l.ko
kernel/sound/usb/caiaq/snd-usb-caiaq.ko

```
and
```

root@A-64:~# modprobe snd-usb-audio
root@A-64:~# E: module-alsa-card.c: Failed to find a working profile.
E: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="2" name="usb-0d8c_PnP_Audio_Device-00-default" card_name="alsa_card.usb-0d8c_PnP_Audio_Device-00-default" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.

```
and
```

root@A-64:~# modprobe snd-usb-lib
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.

```
and the result is:
```

 1 [Bt878          ]: Bt87x - Brooktree Bt878
                      Brooktree Bt878 at 0xfcfff000, irq 18
 2 [default        ]: USB-Audio - PnP Audio Device        
                      PnP Audio Device         at usb-0000:00:02.1-4, full speed

```
Ok,my onboard sound card is back ... sort of. Previously, I could set up lots of analog and digital Modes, now I have in System/Settings/Sound only "Analog Stereo Input". But honestly spoken, I can not understand the warnings after modprobe. At least, alsamixer is working again :-)

Nice I can listen to "Line in" as before. Would be nicer if I could listen to my music files on HDD or CD-Player with totem or GMPlayer as was the case before?!

Edit 3:

Okay,

```
killall pulseaudio

```
did it - the option "analog stereo duplex" does shown again in System/Settings (or Preferences? in German it's "Einstellungen") - Sound, together with lots of others I never needed, so I can listen to mp3 Music from my HDD and to CD again.

Thanks to anybody who read my question and maybe the Solution helps somebody else who has the same problem.

Edit 4:
Okay, after next Re-Boot sound hardware has disappeared again and this time "killall pulseaudio" does'nt help any more. 
When trying video capture with xawtv, of course it will break with "oss: open /dev/dsp1: No such file or directory" (or whatever sound device I am configuring, dsp, dsp1, dsp2 - none of them do now show under /dev/).

After 10 years of Linux use, I will go back to windows in the long run ... this problem alone, unsolved, already stole me two days when I should have tried to earn my living :-(

Edit 5: Okay, this time insmod /lib/modules/2.6.32-28-generic/kernel/sound/usb/snd-usb-audio.ko did the trick. (Warning: if you have the same problem, your module file probably will be in an other place corresponding to your actual kernel version. And even though the problem may apply to other hardware, this problem is connected to the Onboard-sound-chip CM6501 on asus and asrock boards).
Don't know why modprobe snd-usb-audio doesn't work since the last time. Still unaceptable to have to do configuration each time new if I want to have sound ... maybe entering the driver in /etc/modules will work?

---

