---
title: "Hauppauge WinTV-HVR 930c (usb, DVB-T/C + analog)"
date: 2009-11-08
forum: Multimedia Software
---

### Post by rbvf1 on 2009-11-08
Hiya
 
I´ve just received the in the title mentioned and have no idea where to start to get it to work.
 
I´m using Ubuntu 9.10 and my plan is to use MythTV.
 
The device is working on Windows 7 on another computer. (though the software that came with the Hauppauge device is almost as bad as Windows Media Centre)
 
I´ve searched the forums, but can´t find any posts with the same USB device.

---

### Post by rbvf1 on 2009-11-09
If you need more information I could possibly get it from the Windows 7 machine where this WinTV-HVR 930c USB device works.

---

### Post by rbvf1 on 2009-11-11
I´ve read somewhere that it might have "Micronas drx-k" chip. Dunno if that´s any help

---

### Post by steefjeqv on 2009-11-11
Hey,

Easiest way to check if it works is to install Kaffeine (mediaplayer based on Xine).

If your usb stick is recognized then Kaffeine should show a Digital TV icon.

I would suggest using VDR in stead of MythTV.
Of course this depends on your personal taste, but VDR in my opinion is a much leaner, easier to use package.
There's a nice ppa put together by gda & hotzenplotz from the VDR Portal which will give you a fully functional digital HDTV system.

[http://www.linuxtv.org/vdrwiki/index.php/Main_Page]("http://www.linuxtv.org/vdrwiki/index.php/Main_Page")

[https://launchpad.net/~the-vdr-team/+archive/vdr-ubuntu-karmic]("https://launchpad.net/~the-vdr-team/+archive/vdr-ubuntu-karmic")

Greetings,
Steven

---

### Post by rbvf1 on 2009-11-11
Thanks for the reply, I´ll try out Kaffeine today when I get home.
 
Is there any other way to test if the device is recognized?

---

### Post by steefjeqv on 2009-11-11
Hi,

You can check dmesg for loading the necessary modules (terminal) :

sudo dmesg | grep dvb

also

sudo lsmod

The following command (terminal) will also give usefull info :

sudo lsusb

Greetings,
Steven

---

### Post by rbvf1 on 2009-11-12
Thanks for the help Steven

Kaffeine does show a Digital TV icon, but I can´t select any devices in the channels window. (I don't know if this tells me that my device is there or not)

as for VDR, after installing it and some of the cool sounding plugins, I get an error message that reads as follows: 
vdr: error while reading '/var/lib/vdr/commands.conf.'
vdr: error while reading '/var/lib/vdr/reccmds.conf.'
vdr: error while reading '/var/lib/vdr/timercmds.conf.'
vdr: no primary device found - using first device!

dmesg | grep dvb shows nothing

"lsusb" shows me a Hauppauge device with the ID   2040:1605

I could post the result of lsmod and dmesg if you think it will help the diagnosis?  =)

---

### Post by steefjeqv on 2009-11-12
Hi,

1. Look for /dev/dvb/adapter1/frontend0. If this is available then your DVB device is recognized.
 
2.Kaffeine has a channel scan function.
Go to menu : DVB - configure DVB. 

3. VDR needs a frontend, so you'll need to install the xineliboutput-plugin.
Then make sure vdr is running with the following command :

sudo /etc/init.d/vdr restart

Then start your frontend with following command : vdr-sxfe

4. Try scanning for a signal with w_scan. First install it :

sudo apt-get install w-scan 

First shutdown VDR : sudo /etc/init.d/vdr stop 

Then run the following command (for DVB-T) :

sudo w_scan -c DK        

Greetings,
Steven

---

### Post by rbvf1 on 2009-11-16
there is no /dev/dvb unfortunately

---

### Post by rbvf1 on 2009-11-17
alas, according to [this TerraTec site]("http://linux.terratec.de/tv_en.html") the driver for the chip has not been GPL´ed, and is therefore not supportet in linux
 
Googling around lead me to believe that the Hauppauge WinTV-HVR 930c uses this EM2884 chip
 
hopefuly the manifacturer will release the source at some point (and on that happy day, I won´t need Windows for watching TV,... although on that same day, the devil might wear ice-skates to work) :(

---

### Post by steefjeqv on 2009-11-17
Hi,

Sad that you can't use this good piece of hardware.

It's mainly the Micronas part that's closed down I believe. 

Greetings,
Steven

---

### Post by rbvf1 on 2009-11-18
I´ll just have to use Widows for watching TV then.
Untill Micronas gets things sorted out.
 
 
Thanks for all the help Steven =)

---

### Post by beschu on 2012-01-01
The thread has been not updated for 2 years. 

The stick seems to be supported now! ;)

Please see:

[http://linuxtv.org/wiki/index.php/Hauppauge#DVB_Products]("http://linuxtv.org/wiki/index.php/Hauppauge#DVB_Products")

[http://comments.gmane.org/gmane.linux.drivers.video-input-infrastructure/41252]("http://comments.gmane.org/gmane.linux.drivers.video-input-infrastructure/41252")

[http://www.spinics.net/lists/linux-media/msg41530.html]("http://www.spinics.net/lists/linux-media/msg41530.html")

Please give me a feedback if it is working on your systems. On my machine it is not working yet, although I have downloaded the firmware and copied it to /lib/firmware.

---

### Post by Amatøren on 2012-01-04
I can't my Hauppauge WinTV-HVR 930 to work on Ubuntu 11.10 :(

```
epg@EPG-server:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 2040:1605 Hauppauge 
epg@EPG-server:~$ 

``````
epg@EPG-server:~$ dmesg | grep dvb
[   27.244604]     53c91373bdd74f7e11d2726046a90b986c1ed650 [media] dvb: remove the extra parameter on get_frontend
[   27.252053]     53c91373bdd74f7e11d2726046a90b986c1ed650 [media] dvb: remove the extra parameter on get_frontend
[   27.411416]     53c91373bdd74f7e11d2726046a90b986c1ed650 [media] dvb: remove the extra parameter on get_frontend
[   30.100045] em28xx #0: Successfully loaded em28xx-dvb
[   30.100049] Em28xx: Initialized (Em28xx dvb Extension) extension
epg@EPG-server:~$ 

```Kaffeine don't see the DVB-T only the DVB-C part

```
epg@EPG-server:~$ sudo w_scan -c NO
w_scan version 20110616 (compiled for DVB API 5.3)
using settings for NORWAY
DVB aerial
DVB-T Europe
frontend_type DVB-T, channellist 4
output format vdr-1.6
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
    /dev/dvb/adapter0/frontend0 -> DVB-C "DRXK DVB-C": specified was DVB-T -> SEARCH NEXT ONE.
    /dev/dvb/adapter0/frontend1 -> DVB-T "DRXK DVB-T": good :-)
Using DVB-T frontend (adapter /dev/dvb/adapter0/frontend1)
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.5
frontend 'DRXK DVB-T' supports
INVERSION_AUTO
QAM_AUTO
TRANSMISSION_MODE_AUTO
GUARD_INTERVAL_AUTO
HIERARCHY_AUTO
FEC_AUTO
FREQ (47.12MHz ... 865.00MHz)
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
Scanning 7MHz frequencies...
177500: (time: 00:02) 
184500: (time: 00:04) 
191500: (time: 00:07) 
198500: (time: 00:09) 
205500: (time: 00:12) 
212500: (time: 00:14) 
219500: (time: 00:17) 
226500: (time: 00:19) 
Scanning 8MHz frequencies...
474000: (time: 00:22) 
482000: (time: 00:24) 
490000: (time: 00:27) 
498000: (time: 00:29) 
506000: (time: 00:32) 
514000: (time: 00:34) 
522000: (time: 00:37) 
530000: (time: 00:39) 
538000: (time: 00:42) 
546000: (time: 00:44) 
554000: (time: 00:47) 
562000: (time: 00:49) 
570000: (time: 00:52) 
578000: (time: 00:54) 
586000: (time: 00:57) 
594000: (time: 00:59) 
602000: (time: 01:02) 
610000: (time: 01:04) 
618000: (time: 01:07) 
626000: (time: 01:09) 
634000: (time: 01:12) 
642000: (time: 01:14) 
650000: (time: 01:17) 
658000: (time: 01:19) 
666000: (time: 01:22) 
674000: (time: 01:24) 
682000: (time: 01:27) 
690000: (time: 01:29) 
698000: (time: 01:32) 
706000: (time: 01:34) 
714000: (time: 01:37) 
722000: (time: 01:39) 
730000: (time: 01:42) 
738000: (time: 01:44) 
746000: (time: 01:47) 
754000: (time: 01:49) 
762000: (time: 01:52) 
770000: (time: 01:54) 
778000: (time: 01:57) 
786000: (time: 01:59) 
794000: (time: 02:02) 
802000: (time: 02:04) 
810000: (time: 02:07) 
818000: (time: 02:09) 
826000: (time: 02:12) 
834000: (time: 02:14) 
842000: (time: 02:17) 
850000: (time: 02:19) 
858000: (time: 02:22) 

ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!
epg@EPG-server:~$ 

```Any help here...?
:confused:

---

### Post by radek82 on 2012-01-14
HI guys,
wondering if anyone can point me to a tutorial on how to install the drivers for 930c witch comes from the linuxtv?

---

### Post by fwendt on 2012-03-04
> **radek82 said:**
> HI guys,
wondering if anyone can point me to a tutorial on how to install the drivers for 930c witch comes from the linuxtv?

I'm trying to follow the discussion here: [http://www.spinics.net/lists/linux-media/msg41610.html](http://www.spinics.net/lists/linux-media/msg41610.html) in order to end up with a dmesg log like here: [http://hg.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-930C](http://hg.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-930C)

but haven't really got anywhere yet - one thing is clear: with Ubuntu 11.10 64-bit, this thing doesn't run out of the box (I did get a DVB-T USB-card working with tvheadend yesterday, it's just that I want to use DVB-C).

---

### Post by fixitdude on 2012-05-13
> **Amatøren said:**
> Any help here...?
:confused:

I just started messing with a USB stick too...

The w_scan shows that it seems to be there and have a driver loaded, so that's good. The problem is that it's not picking up any signals on the frequencies for your country (as I understand it so far).

You want to make sure you have a good antenna and strong signal.

I made another post about all my frustration with installing this silly thing. It should be a lot simpler than this.

Try kaffine because it seemed to pick up my local station's IDs but I still can't get any video.

Search for "dvb" in synaptic and try whatever you think may help you figure this out.

And the program "scan" is stupid. What a waste of programming time.

---

### Post by Morten ML on 2012-05-15
Hi all

I have made a tutorial here: [http://ubuntuforums.org/showthread.php?p=11938491#post11938491]("http://ubuntuforums.org/showthread.php?p=11938491#post11938491")

But what just occurred to me is that there are more than one version of the 930c-not-HD. 

Please see "Why I chose the 520e, the 930c and not the 930c-HD" in my tutorial for more info.

@Amatøren I have the 930c model 1279 working in 11.10 mythbuntu. And if you are in luck you also have Yousee as a provider. then you can follow my every step in the tutorial.

Best regards
Morten

---

