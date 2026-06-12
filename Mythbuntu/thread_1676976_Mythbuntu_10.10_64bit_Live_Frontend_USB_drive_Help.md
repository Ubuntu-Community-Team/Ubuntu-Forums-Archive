---
title: "Mythbuntu 10.10 64bit Live Frontend USB drive Help needed"
date: 2011-01-28
forum: Mythbuntu
---

### Post by newbie02 on 2011-01-28
So I bought a CUBE N3
[http://www.giada.cc/chanpinzhongxin/minipc/cube%20series/2009-11-04/3.html](http://www.giada.cc/chanpinzhongxin/minipc/cube%20series/2009-11-04/3.html)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856176002](http://www.newegg.com/Product/Product.aspx?Item=N82E16856176002)

Based on a reviewer from newegg who stated they had "mythTV booting off a flash drive. I installed MYTHBUNTU 10.10 on a 2gig flash drive. Bootup could be faster BUT once booted I do not notice any real lag."

I have search everywhere but I'm unable to figure this out.
My goal is to use usb thumb drive and boot into mythfrontend.
Here is the process I followed

System->Admin->Startup Disk creator
   Erase flash drive select mythbuntu 10.10 64bit iso then select 1.2GB for reserved extra space. I thought this is where any changes are saved for mythbuntu.

Once completed I insert the USB drive and power up the N3. It boots off the usb drive initially. I choose try CD then end up at a desktop.
With two icon in the upper left install mythbuntu and Live cd.
I select live cd and get the basics of the frontend up and connect to mythtv server.

However If I try to reboot the usb stick is no longer appears to be boot-able from the device. Also I can not get into bios usb key board doesn't attach in time for f1 to force the N3 into the bios.

I retest my creation process and used Disk creator again but after first boot I can not reboot the usb drive. I also tried this with ubuntu 10.10 ISO and this too only powered up once.

Any ideas?
Thanks
Newbie02

---

### Post by nickrout on 2011-01-28
I don't think you can install to the same media your are installing from. Use two usb sticks, or a cd to boot from and a usb stick to install to.

---

### Post by newbie02 on 2011-01-28
I was wondering about that so I went out and bought a second usb stick on the way home.

I will update after my new attempt. 
Thanks
Newbie02

---

### Post by newbie02 on 2011-01-29
That was it. Mythbuntu installed itself to the second thumb drive just fine. Now just tring to get audio working. alsamixer crashes.
Thanks
Newbie02

---

### Post by newbie02 on 2011-01-29
So I allowed mythbuntu to update itself and reboot then alsamixer was
working. 

So for my alsamixer screen
Master=100
PCM=100<>100
Front=100<>100
Mic=MM 0<>0
Mic Boos=0<>0
S/PDIF=00
S/PDIF D=MM
S/PDIF 1=00

exit alsamixer. Then do

sudo alsactl store 0  <- this will save your alsamixer settings

Lets test audio now.

aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav

I heard audio out of tv..

then  nano ~/.asoundrc
add the following
    defaults.pcm.device 3


Add nfs 
sudo apt-get install nfs-common

added server in fstab
192.168.xxx.xxx:/remote/path /yourlocal/mount_pt nfs ro,auto 0 0

reboot all devices playing default will use defaults.pcm.device 3 for audio output now and remote file system is mounted on start.

Final setup in myth
_**Video**_
VDPAU drivers ... didn't need to worry current nvidia drivers had this.
Note the latest from nvidia does have some VDPAU fixes.

However I did need to setup the
Setup->Tv settings->playback ...screen 3/8
set playback profile to VDPAU Normal( fixes 1080p stuttering).

_**Audio setup**_
not sure I need to do this but I did
In setup->Generel under Audio system
set Audio output device to plughw:0,3

_**Setup videos**_
Setup->Media Settings->Video Settings->Generel ..screen 1/4
Directories that hold video: /yourlocal/mount_pt


That is it. The Cube N3 is up and running. Works great for a ion with a flash drive as harddrive and 2GB of ram. But it does take about 3 minutes to power up full. But once it powers up it works great. It has a fan but I cant hear it ;)  

Newbie02

---

