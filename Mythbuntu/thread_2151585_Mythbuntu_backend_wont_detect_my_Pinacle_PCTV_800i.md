---
title: "Mythbuntu backend wont detect my Pinacle PCTV 800i tuner card. I'm completely stumped"
date: 2013-06-05
forum: Mythbuntu
---

### Post by jimmyclyde1983 on 2013-06-05
So I've been bashing my  head against a wall on this all day nearly. I have installed the  firmware for this card as well as the the latest v4l-dvb drivers through  Mercurial. When I go into the backend to set up my capture card it  keeps giving me the "Probed info: Failed to Open" when set to analog-V4L  or anything else for that matter.
  The video device is blank by default and the VBI device is set to  /dev/vbi0 by default and this is something I'm wondering about too. (How  do I find my tuner card's actual location?)
  I haven't even got to the audio configuration yet. From what little  I've tried I haven't been able to get ALSA to work at all either. This  is really depressing and I'm about to just give up. :(
  Here is the relevant dmesg output: [http://pastebin.com/uaFngVME](http://pastebin.com/uaFngVME)[1] 
  Here is the relevant lspci output: [http://pastebin.com/ERxfTk3p](http://pastebin.com/ERxfTk3p)[2] 
  If anyone could help me at all I would greatly appreciate it.
  EDIT: If there is any pertinent information that I've forgotten please let me know.

---

### Post by BicyclerBoy on 2013-06-08
That card has had built-in kernel support for ages..
[http://linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29](http://linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29)

Are you sure you have not messed up the v4l-dvb build.
Can you reboot into a std kernel/liveDVD of mythbuntu & check the dmesg output.

If you intend to use DVB tuner then there is no audio config. The card outputs (digitally) mpegts streams.

The logs show mythbackend crashing & re-spawning or is it that you trying to run "mythtv-setup"?

Mythbuntu uses a wrapper script around the real mythbackend executable but it should stop via upstart..
sudo service mythtv-backend stop
mythtv-setup -v all

---

### Post by jimmyclyde1983 on 2013-06-09
I think I did in fact mess up the v4l-dvb build... Going back I realized that I was getting an error message on the make: [http://pastebin.com/8DmyV6au](http://pastebin.com/8DmyV6au)

make[2]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /home/james/v4l-dvb/v4l/tuner-xc2028.o
In file included from <command-line>:0:0:
/home/james/v4l-dvb/v4l/config-compat.h:1249:1: fatal error: include/linux/version.h: No such file or directory
compilation terminated.

This is where it starts to mess up.

---

### Post by BicyclerBoy on 2013-06-09
I think the mercurial packages are ancient..
They have been using git for some time..

If your build failed then the install should have not succeeded. But anything is possible..
And it is very odd that mythbackend is crashing..

[http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)
Try the basic approach..

Or just re-install the kernel package & forget building the dvb module.

---

### Post by jimmyclyde1983 on 2013-06-09
Speaking from ignorance, is there anything I need to do as far as removing the driver files before I retry with git instead?

---

### Post by jimmyclyde1983 on 2013-06-10
I don't understand why this is so effing difficult. I give up. I know I'm not the best at this but it shouldn't be this hard to make work. I followed the wiki guide. Did everything linuxtv.org said to do to install v4l-dvb drivers on here [http://git.linuxtv.org/media_tree.git](http://git.linuxtv.org/media_tree.git). Only to find out that gcc wasn't installed by default as well as mercurial or git. After figuring all this out, following ALL the steps as far as the make and make install, (through git instead of mercurial)  the only thing I ended up having was 4 hours of wasted time watching drivers compile for... god knows what, an entire image of something maybe, who knows it certainly took long enough, and 10 gigs of wasted hard drive space. I GIVE UP! This is stupid... I hate feeling like I can't accomplish this but **** this ****.

---

### Post by BicyclerBoy on 2013-06-10
With hindsight you'll have to agree it was self inflicted..
You never needed to build the v4l drivers..

It does not require GB of space..my dvb-vl4 folder is < 40MB..builds in minutes..
You must have ended up building the whole kernel..that's not required, the modules are loaded on existing kernel using DKMS..

MythTV is about 1.5GB but that is because of the external packages included..

Building any driver with a kernel space component is not be be undertaken lightly..
You can just boot the previous kernel from grub & then wipe the broken kernel away with synaptic etc.

The std *buntu system & every linux box has a c compiler, you just don't get all the build tools & dev packages & headers etc..because most people don't need them.
The prerequisites for building packages can be determined & installed from the package manager system & in the case of dvb-v4l, are listed on the linuxtv site..

---

### Post by jimmyclyde1983 on 2013-06-10
Yeah... not agreeing with you on that one. This shouldn't have been made  so ridiculously complicated just to get a tv tuner card to work  properly.

---

