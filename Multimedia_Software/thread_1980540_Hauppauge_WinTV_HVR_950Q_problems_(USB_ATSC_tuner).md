---
title: "Hauppauge WinTV HVR 950Q problems (USB ATSC tuner)"
date: 2012-05-15
forum: Multimedia Software
---

### Post by fixitdude on 2012-05-15
I just got a USB stick ATSC tuner, a Hauppauge HVR 950Q

I've read a lot of posts and tried a lot of things.

I know this device works because a friend with a XP laptop let me install it on that and I was watching TV with it at the same location as I am testing it on Ubuntu. (details at the end of this post)

Why doesn't this just work as easy as it does on XP ?

If you are here because you are having problems the answer may be simple, get a better antenna. I have had luck on "weaker" channels (picture cut out) by taking a wire and bending it so it's different lengths, finding the right length isn't easy when the silly programs don't tell you signal strength.

It seems these wonderful new digital things need a super good STRONG signal. I saw somewhere on the net that it said that you need at least 40% signal strength, whatever that means. Does anyone go by db anymore? Is it really that complicated to use a standard?

One other thing, you have to have a USB 2.0 port to use this thing. Check that.

w_scan tells me the signal is "OK", but that doesn't help....

w_scan -f a -c US -X

57000: 8VSB(time: 00:07) (time: 00:10) signal ok:
8VSB f=57000 kHz

The next thing after finding some signals, it goes back to those it found and tries to decode the signal.

tune to: 8VSB f=57000 kHz
(time: 03:05) Info: PAT filter timeout
Info: VCT(terrestrial) filter timeout

Like people know what PAT and VCT are?

Anyone reading this because they are trying this, use a ap called "kaffine" is worth trying, it has a built in scanner (that will crash if you press the button three times) and it may find some channels, mine did after several crash and re-tries. But then NO PICTURE, just blank nothing.

Programs to try:

kaffine <<< BEST YET!
tvtime
xine
vlc
mplayer ( and the supporting front ends, sheesh.... WTF? )
me-tv
vdr <<< records stuff after you get it working

And search for "dvb" in synaptic to find programs that may help.

Oh, and your device is not /dev/video0 anymore....

Try /dev/dvb/adapter0/frontend0


dmesg looks like this...

```

[4734544.736374] au0828: i2c bus registered
[4734545.026675] tveeprom 5-0050: Hauppauge model 72241, rev D3F0, serial# 6403456
[4734545.026681] tveeprom 5-0050: MAC address is 00-0D-FE-61-B5-0A
[4734545.026686] tveeprom 5-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[4734545.026690] tveeprom 5-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[4734545.026694] tveeprom 5-0050: audio processor is AU8522 (idx 44)
[4734545.026698] tveeprom 5-0050: decoder processor is AU8522 (idx 42)
[4734545.026701] tveeprom 5-0050: has no radio
[4734545.026704] hauppauge_eeprom: hauppauge eeprom: model=72241
[4734545.063622] au8522 5-0047: creating new instance
[4734545.063626] au8522_decoder creating new instance...
[4734545.068849] tuner 5-0061: chip found @ 0xc2 (au0828)
[4734545.105357] xc5000 5-0061: creating new instance
[4734545.110273] xc5000: Successfully identified at address 0x61
[4734545.110276] xc5000: Firmware has not been loaded previously
[4734545.111271] au8522 5-0047: attaching existing instance
[4734545.156545] xc5000 5-0061: attaching existing instance
[4734545.161519] xc5000: Successfully identified at address 0x61
[4734545.161523] xc5000: Firmware has not been loaded previously
[4734545.161530] DVB: registering new adapter (au0828)
[4734545.161535] DVB: registering adapter 0 frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[4734545.162028] Registered device AU0828 [Hauppauge HVR950Q]
[4734740.822486] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 2)
[4734740.849449] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on TV encoder (output 2)
[4734740.849455] [drm] nouveau 0000:01:00.0: Output TV-1 is running on CRTC 1 using output B

```

 cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

(system all updated as best as I could)

---

### Post by jmore9 on 2012-05-15
You can try linuxtv.org they have a lot of info on getting tuners working with linux.  They also tell which ones work with linux which ones need a little work to work and which ones do not work,

A lot of good info on that site.

---

### Post by fixitdude on 2012-05-15
I guess I should point to some of the links I've been to...

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q)

"The digital side of the device is supported under Linux since kernel 2.6.26. Analog support was merged into the mainline v4l-dvb tree on March 18, 2009."

Confirmed on this chart:
[http://www.linuxtv.org/wiki/index.php/ATSC_USB_Devices](http://www.linuxtv.org/wiki/index.php/ATSC_USB_Devices)

And of course as you can see by the dmesg, the driver is loaded for this thing.

"scan" produces this, and this is my problem:

scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB 
scanning /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 57028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 63028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 69028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 69028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!


What is happening is it tunes to a "good" frequency "57028615:8VSB" but then has a problem with something like decoding the stream "filter timeout pid 0x0000" the last lines "tuning failed!!!" are when there is no signal.

It's the same thing with w_scan.

I tried "scan /usr/share/dvb/atsc/us-NTSC-center-frequencies-8VSB" with the same results.

I've tried lots of combinations of things.

I was even messing with creating a channels.conf file from the data I got from the one good scan, which is contained in a database in .kaffine and you can extract it as follows:

sqlite3 sqlite.db "select * from Channels"

I was going to write a simple perl script to do it but then ran into the xine problem of formatting the proper format for the file, sheesh what a mess that thing is:

SOMETVCH:57028615:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_AUTO:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:0:1

You want to figure that out?

That's as close as I came by manually trying to make the file and it doesn't work on xine, it just sits there frozen. It doesn't even ask you for a device, so I don't know if it even knows there is a device.

mplayer doesn't like that file at all. I don't know what it really wants.

This is such a mess.

---

### Post by fixitdude on 2012-06-10
And more...

```

So the next idea is to get the latest drivers and install them on my existing system.

sudo apt-get install git-core libproc-processtable-perl patchutils libdigest-sha1-perl
git clone git://linuxtv.org/media_build.git
cd media_build/
./build

You can then do a:

make install

Or if you are like me and don't want to mess up everything, because this will install everything and it's mother all over the place....

I copied only the drivers I needed to where they need to be (make a copy of the original drivers just in case you want to put them back)...

Here's where they are....
/lib/modules/YOUR-KERNAL-VERSION-HERE/kernel/drivers/media/dvb/frontends/au8522.ko
/lib/modules/YOUR-KERNAL-VERSION-HERE/kernel/drivers/media/common/tuners/xc5000.ko
/lib/firmware/dvb-fe-xc5000-1.6.114.fw     <<< this is from dvb-firmwares.tar.bz2 and didn't need to be changed

media_build/linux/drivers/media/common/tuners    <<< xc5000.ko source code is here in case you want to look

cp media_build/v4l/au8522_common.ko /lib/modules/2.6.32-32-generic/kernel/drivers/media/dvb/frontends/au8522.ko

cp media_build/v4l/xc5000.ko /lib/modules/2.6.32-32-generic/kernel/drivers/media/common/tuners/xc5000.ko

These are loaded automagically when you plug in your USB stick so all should be well...


```

What happened? 

I did this:

w_scan -f a -c US -X

And it showed all the channels properly!!

But still no picture using ANY TV watching program available.

Well, at least something happened that gives me hope.

---

### Post by fixitdude on 2012-06-14
I installed Ubuntu 12.04 on another computer and confirmed that the 950Q works on that, so I am going to do the LONG FRUSTRATING upgrade on my main box to 12.04 wish me luck!

Who, other than total geeks want to deal with this crap anyway?

---

### Post by fixitdude on 2013-04-24
In case anyone finds this from google search, I wanted to update it and say that it's been working pretty good for almost a year now and I am using the below perl script I posted to automatically record programs by keywords.

"Perl Script Digital Video Recorder for you"
[http://ubuntuforums.org/showthread.php?t=2009778](http://ubuntuforums.org/showthread.php?t=2009778)

The driver for atsc_epg (it gets the schedule off the air) will get stuck once and a while and lock up the machine for some reason and it seems like once a month, then I just reboot. If I reboot sooner than that then it doesn't seem to happen so it's probably a small memory leak and I do restart that computer in that period anyway most of the time.

You can reset the main driver from a root terminal as below if you need to, I have a script that automatically does it before it tries to get the EPG and that seems to work good. You may not need to do that but I posted the script anyway at the link above. Hope it helps someone. I really enjoy having it record things so I can watch them when I have the time, it's great, so thanks to all the driver developers who made it possible! 

```

sleep 1
/sbin/modprobe -r au0828
sleep 2
/sbin/modprobe au0828

```

---

