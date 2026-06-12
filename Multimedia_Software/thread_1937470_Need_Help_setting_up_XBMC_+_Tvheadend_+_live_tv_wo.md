---
title: "Need Help setting up XBMC + Tvheadend + live tv working with my Hauppauge PVR-350"
date: 2012-03-07
forum: Multimedia Software
---

### Post by ledzepjes on 2012-03-07
I Need Help setting up XBMC + Tvheadend + live tv working with my Hauppauge PVR-350 tv card, which the TV card was working with CSMonkey TV Remote before the installation, so I know the TV Card still works, I dual boot with Win 7 and it works with Media Center as well. My TV died, and want to get XBMC with TVHeadend setup so that I can distribute the TV signal to all my PC's in the house, I just choose this setup with XBMC with Tvheadend after reading 

[http://xbmc.org/](http://xbmc.org/)
 and
[http://wiki.xbmc.org/index.php?title=Installing_XBMC_for_Linux](http://wiki.xbmc.org/index.php?title=Installing_XBMC_for_Linux)

I then ran the commands for "Ubuntu 10.04, 10.10, 11.04 & 11.10 - PRE XBMC Eden  11.0 (testing)

1 sudo add-apt-repository ppa:alexandr-surkov/xbmc-pvr
2  sudo apt-get update
3 sudo apt-get install xbmc tvheadend

all from site:
[http://www.loggn.de/ubuntu-xbmc-repository-10-1-dharma-und-11-0-eden-mit-und-ohne-pvr](http://www.loggn.de/ubuntu-xbmc-repository-10-1-dharma-und-11-0-eden-mit-und-ohne-pvr)
       (translated into english):
[http://translate.google.com/translate?sl=auto&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fwww.loggn.de%2Fubuntu-xbmc-repository-10-1-dharma-und-11-0-eden-mit-und-ohne-pvr]("http://translate.google.com/translate?sl=auto&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fwww.loggn.de%2Fubuntu-xbmc-repository-10-1-dharma-und-11-0-eden-mit-und-ohne-pvr")

I setup the permissions for TVHeadend on the [http://localhost:9981](http://localhost:9981) page and added admin and my user account in the ACL and then added that permission in XBMC as well, if you don't setup user permissions TVHeadend will complain with an Access Denied error when you run XBMC.

Now my problem is I can't get the Live TV to show, and when I installed tvheadend it uninstalled vlc and I can no longer install vlc cause it complains saying package dependencies are incompatible with vlc?

I am running Ubuntu 10.10 with xbmcubuntu 2.11 with latest Tvheadend  2.13, when I go to [http://localhost:9981/extjs.html](http://localhost:9981/extjs.html)  and click TV adapters and I then see only 2 tabs, General and Services and not Multiplexes. In  General tab I click on adapters and I see my tv card (Hauppauge WinTV  PVR-350 ivtv PCI:0000:01:08.0), Multiplexers tab is missing? In the  documentation ([https://www.lonelycoder.com/tvheadend/documentation](https://www.lonelycoder.com/tvheadend/documentation))  it says to click on General Tab and then "Add DVB Network by location"  and then the adapter should be populated with multiplexes, but "Add DVB  Network by location" isn't an option either. It's my understanding that without scanning for multiplexes it won't "know" the TV channels.

:-(


My goal is to properly setup XBMC on my desktop with the PVR-350 and Ubuntu 10.10 and broadcast and watch the TV channels on my other computers, both windows 7 media center and Ubuntu with XBMC or VLC.

Am I making this harder than it needs to be? is there an easier way to stream my Live TV channels from the Hauppauge PVR-350 in Ubuntu to all my other computers on the home network or do I have to purchase a HDHomerun to do that? I'm trying really hard to avoid having to purchase another piece of equipment.

---

### Post by BicyclerBoy on 2012-03-08
I never used tvheadend but noticed this:
"Analog TV
    Using the Video4Linux2 API. Currently, only PAL is supported."

Your PVR-350 is an analogue tuner card with onboard mpeg2 encoder..is uses the IVTV driver..it is not a DVB tuner card, there are no multiplexes to scan.

The user in video group?

cat /dev/video0 > some_file.mpg or similar..
Does this work?

---

### Post by ledzepjes on 2012-03-13
I'm trying to find two things,
 
1) a list of all supported hardware by Tvheadend
2) and a way to make my Hauppauge pvr-350 tv card work with tvheadend
 
... since I've been struggling and can't seem to get it to work with mythtv, and myth's interface seems to be very clunky imho
 
I've got ivtv driver installed and working and the pvr-350 which outputs all my basic cable tv channels using the csmonkey remote ([http://blog.csmonkey.com/2007/07/csmonkey-tv-remote.html?z#!/2007/07/csmonkey-tv-remote.html](http://blog.csmonkey.com/2007/07/csmonkey-tv-remote.html?z#!/2007/07/csmonkey-tv-remote.html) , [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/) ) and vlc, I can change channels with my mouse on the on-screen csmonkey remote and watch tv on my one computer that has the pvr-350, just can't use my media center remote like I'd hope to be able to do with a proper setup of xbmc or watch from any computer in the house, I really prefer the inerface of xbmc, not to mention tvheadend would allow me to distribute the channels to all my computers either running windows 7 media center or xbmc on ubuntu, or possibly xbmc/ubuntu on rasbery pi or similar low power device

---

### Post by ledzepjes on 2012-03-13
@BicylcerBoy
 
and for me, I have a web cam installed on /dev/video0, my pvr-350 is on /dev/video1
so I used
 
cat /dev/video1 > somefile.mpg
 
and that works using vlc, can watch the mpg as it's being recorded
just went to /home/user directory and opened somefile.mpg with vlc

---

### Post by BicyclerBoy on 2012-03-13
Your problem is with TVheadend & I can't help with that..

XBMC has an interface to mythbackend (<=0.24 only).

The raspberry pi has no ram or CPU power, less than first atom.
If CrystalHD support is any indication, I wouldn't rely on any on-going support from Broadcom. Without the video h/w working, the thing is junk.
The GPU has no shader performance so decode only.

IMO The best low power (& hi efficiency) ITX uses mobile CULV iCPU & GPU chipsets..

---

