---
title: "[SOLVED] How to install the Pinnacle PCTV DVB-T 72e Stick"
date: 2009-01-06
forum: Multimedia Software
---

### Post by WitchCraft on 2009-01-06
OK, since it didn't work by default, but I got it working, I thought other people might profit of knowing how to install the Pinnacle 72e DVB-T stick.

The description applies for Debian Lenny (Kernel 2.6.26-1) , but it should work with Ubuntu, too.

First: 
if you do
```

ls /dev/dvb

```
or 
```

ls /dev/d*

```

you will see no such device. This means that the driver is not (yet, Jan. 06 2009) in the Linux kernel, so you have to actually compile and install the driver.


**You will need a 2.6 kernel, 2.4 and 2.2 will not work.**

To see your kernel version:
```

uname -r

```


If you have an old kernel, upgrade:
```

apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-cache search linux-headers
apt-cache search linux-image
sudo apt-get install linux-headers-2.6.26-1-686 linux-image-2.6.26-1-686

```


**Installing the video for Linux device driver:**

Installing the source dependencies and the mercurial code management system:
```

sudo apt-get install mercurial linux-headers-`uname -r` build-essential

```

Downloading the video 4 linux dvb driver sourcecode:
```

cd ~
mkdir sources
cd sources
hg clone http://linuxtv.org/hg/v4l-dvb

```

Compiling the v4l-dvb source code:
```

cd v4l-dvb
make

```

If you get
```

/root/sources/v4l-dvb/v4l/cx25840-core.c:186: error: duplicate 'static'
make[3]: *** [/root/sources/v4l-dvb/v4l/cx25840-core.o] Error 1
make[2]: *** [_module_/root/sources/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.26-1-686'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/root/sources/v4l-dvb/v4l'

```

then do the following:
sudo gedit ~/sources/v4l-dvb/v4l/cx25840-core.c

go to line 186 (or whatever is indicated)

You will find this BUGGY line:
```

#if LINUX_VERSION_CODE >= KERNEL_VERSION(2, 6, 20)
static static void cx25840_work_handler(struct work_struct *work)

```

change this to:
```

#if LINUX_VERSION_CODE >= KERNEL_VERSION(2, 6, 20)
//static static void cx25840_work_handler(struct work_struct *work)
static void cx25840_work_handler(struct work_struct *work)

```

now save, exit gedit.

type make again.

Now it should build correctly.

then type 
```

make install

```

Now you still need to download the firmware from:
```

http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-03-pre1.fw

```

The firmware image will need renaming to 
```

dvb-usb-dib0700-1.20.fw

```
(or whatever the current version is at the moment you compile)

Now you need to copy the firmware image to the correct directory:
On Debian this is:
```

/usr/lib/hotplug/firmware

```

On Ubuntu this is:
```

/lib/firmware 

```

If you don't find the firmware directory for your distro, it might help searching for possibly existing firmware images (you need to run this as UID 0 [= root]):
```

updatedb
locate *.fw

```

and you possibly will see an output like:
```

/usr/lib/hotplug/firmware/dvb-usb-dib0700-1.20.fw
/usr/lib/hotplug/firmware/ipw2200-bss.fw
/usr/lib/hotplug/firmware/ipw2200-ibss.fw
/usr/lib/hotplug/firmware/ipw2200-sniffer.fw

```

Once you have done this, just load the kernel modules you compiled with modprobe.
```

modprobe dvb_usb_dib0700

```
If you don't know how to do this, then just restart your computer (has the same effect - takes longer but is easier).


Done installing the drivers.
Now you need something to actually scan your dvb-t for frequencies, and watching the TV-program.
Kaffeine is THE way to go, but feel free to use something else if you don't like kaffeine (good luck finding something else that really works...).
```

sudo apt-get install kaffeine

```


Now start kaffeine. If you just installed it, click yourself through the initial configs.

Now in the kaffeine menu, select DVB->Channels
Click start scan.
If the scan finished, click "Select All", click "Add Selected", then click "Done".

Now click on Digital TV, and on the left select a channel.
Now that's it, I guess you're intelligent enough to figure out the details on yourself. :KS

---

### Post by WitchCraft on 2010-06-25
With the new Lucid Lynx, if you get:
> 
Cannot find demux plugin for MRL dvbpipe.m2t


Then do the following

```

sudo apt-get remove --purge kaffeine
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install libxine1 libxine1-all-plugins phonon-backend-xine
sudo apt-get install kaffeine 

```

---

### Post by TheMadGeneral on 2011-05-24
Thanks mate it worked a treat for me. Thumbs up to you!

---

### Post by cefn on 2011-10-09
Just a note which might be useful to others. 

Although I thought nothing was working, my PCTV 72e card WAS being detected and was working fine, but I hadn't got decent reception. 

It was hard to tell that everything was in fact functional without a decent aerial. Try going to a friend's house where Digital TV (Freeview) is already working and plug into their aerial for testing.

In my case I hadn't selected the right local DVB-T transmitter group when running the 'scan' utility from dvb-apps, or running Kaffeine [Tvtime was just crashing every time I launched it]. For this reason I was getting no channels at all.

Using Kaffeine, I needed to configure under 'Television' and select the Winter Hill transmitter, not Lancaster, even though I have a Lancaster postcode. Using the [http://www.digitaluk.co.uk/](http://www.digitaluk.co.uk/) transmitter search by postcode, and selecting 'I am in the aerial installation trade' provided me with the names of primary and secondary transmitters to experiment with.

I found on Natty that my Pinnacle PCTV 72e was automatically detected and modules were loaded. The card relies on the dvb-usb-dib7000p module I think. At least it reports itself as a DiB7000 to the 'lsusb' tool. You can prove your card is recognised by running the following from a Terminal console...

dmesg | grep Pinnacle

...which in my case looked like...

cefn@cefn-natty-dell:~$ dmesg | grep Pinnacle
[ 5533.990660] dvb-usb: found a 'Pinnacle PCTV 72e' in cold state, will try to load a firmware
[ 5534.740431] dvb-usb: found a 'Pinnacle PCTV 72e' in warm state.
[ 5534.740717] DVB: registering new adapter (Pinnacle PCTV 72e)
[ 5535.225003] dvb-usb: Pinnacle PCTV 72e successfully initialized and connected

You should also see a folder hierarchy under /dev/dvb/adapter0 which looks like this...

cefn@cefn-natty-dell:~$ ls /dev/dvb/adapter0/
demux0  dvr0  frontend0  net0

So if you have the same, chances are your card is working without having to build any packages from source. 

Instead try choosing different transmitter groups within Kaffeine. After tuning channels I also had to install the libxine1-all-plugins package to get a suitable DVB decoder for Kaffeine, and then everything worked fine.

---

