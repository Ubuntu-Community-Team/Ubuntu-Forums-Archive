---
title: "Audio intallation issue.. :("
date: 2011-04-01
forum: Multimedia Software
---

### Post by Camaleonte on 2011-04-01
Hi @ all!
First of all sorry for my bad English, I'm Italian..

I'm a newbie in ubuntu and i'm trying to install Ubuntu Netbook Edition (10.10 - x64) in my Asus 1001PXD.
All works fine except the audio.

In this link ([click]("http://www.alsa-project.org/db/?f=9b69a6b6e225560b833e7f31743b206e4ec972fd")) there is the result of "alsa-info.sh" script.

For more information about my attempts, I can tell you that I've  downloaded the newest alsa drivers in Realtek.com site and I've followed  the standard procedure to install it.
I've also tried to add in **/etc/modprobe.d/alsa-base.conf** the string:
"**options snd-hda-intel model=3stack**" but nothing happens. 
The last thing I did was to follow [this]("http://ubuntuforums.org/showpost.php?p=4298894&postcount=24") guide but without any lucky :sad:.

PS: I'm not sure about the video drivers..i've an* [I]Intel*[/I]* Graphics Media Accelerator [I]3150 *[/I]and I didn't install anything because I know that the intel drivers are integrated in the installations of ubuntu..but it seems to me that the graphics isn't "optimal"..can anyone tell me a little more?
**
Thanks in advance..!
Kind regards,
Cama..

---

### Post by Camaleonte on 2011-04-02
Ok..
I've resolved the audio problem with:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```But I'm pretty sure about the lack of the Video drivers..
I think I'm using the standard VESA drivers because the movement isn't fluid.

Has anyone some information about my VideoCard?

Thanks in advance
Cama..

---

### Post by Camaleonte on 2011-04-05
Bump..

---

### Post by lidex on 2011-04-05
This output please:
```
sudo lshw -C display
```

---

### Post by Camaleonte on 2011-04-08
Hi,
Thx for you reply.

This is the output:

```
 
 *-display:0             
       description: VGA compatible controller
       product: N10 Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:f7e00000-f7e7ffff ioport:dc00(size=8) memory:d0000000-dfffffff memory:f7d00000-f7dfffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: N10 Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f7e80000-f7efffff

```

Just another thing: I've noticed that the microphone doesn't work..
Has anyone any suggestion for it?

Regards
Cama..

---

### Post by Yellow Pasque on 2011-04-08
Please run alsa-info script again (your last one was uninformative because no audio driver was loaded).

Also, post /var/log/Xorg.0.log file.

---

### Post by lidex on 2011-04-09
> **Temüjin said:**
> Please run alsa-info script again (your last one was uninformative because no audio driver was loaded).

Also, post /var/log/Xorg.0.log file.

Welcome back.

---

### Post by xaviers67 on 2011-04-09
Hey, you are trying to install the drivers of the audio that are not of your hardware so please follow the below steps for making the audio system ok

First you must find which model of sound card you use, so run this command:

cat /proc/asound/card0/codec#* | grep Codec
It will return model of your sound card(s), for example: "Codec: Realtek ALC260", so your sound card is ALC260.

You should open a file in ALSA documentation. This file is here:

/usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
or if that file does not exist, try:

/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
or check: HD-Audio-Models

You might have followed the manual before this then also you might have got the solution.

---

### Post by Camaleonte on 2011-04-14
> **xaviers67 said:**
> Hey, you are trying to install the drivers of the audio that are not of your hardware so please follow the below steps for making the audio system ok

First you must find which model of sound card you use, so run this command:

cat /proc/asound/card0/codec#* | grep Codec
It will return model of your sound card(s), for example: "Codec: Realtek ALC260", so your sound card is ALC260.

You should open a file in ALSA documentation. This file is here:

/usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
or if that file does not exist, try:

/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
or check: HD-Audio-Models

You might have followed the manual before this then also you might have got the solution.


Hi!
Sorry for the lag of my reply..
In attachment there is the Xorg.0.log..
There ([Click here ;)]("http://www.alsa-project.org/db/?f=5739fd2e7f8d78c67f0c79b252a3cbd0d201bc5d")) is the alsa-info.sh result.

I've tried to find in the documentation wich you have mentioned my codec
```
danny@DannyNetbook:/usr/share/doc/alsa-base/driver$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC269VB
```but i've not found it..!

What can i do now?

Thanx in advance!
Cama..

---

### Post by Yellow Pasque on 2011-04-14
> Sorry for the lag of my reply..
Finally! I've been on the edge of my seat all week waiting to troubleshoot this issue. Unfortunately, I'm not too sure on this one. Maybe you're suffering from this bug: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/697498](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/697498)

---

### Post by lidex on 2011-04-17
@Camaleonte
That is one ugly dmesg.
You have a model switch -"fujitsu"- that needs to be removed for one thing. Edit this:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
save and reboot. Did you install alsa-modules?

---

