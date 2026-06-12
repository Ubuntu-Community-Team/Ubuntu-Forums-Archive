---
title: "sound in tvtime saa7134"
date: 2009-10-24
forum: Multimedia Software
---

### Post by hrisolit on 2009-10-24
Hello.

I need your help, i have a tv card saa7134 i have good image but nou sound, i have tryed what i found on the internet but still no solution.

If somebody has a solution it will be great to hear it, i just moved from windows so please give me solutions for dummies.

Thank you verry much.

---

### Post by thusgaard on 2009-11-14
you probably solved your problem, but if not, try looking at the ALSA MIXER. It has been the killer on all of my systems.

---

### Post by Damon68 on 2009-11-22
I have the saa7131 card and had the exact same problem, I tried as many programs as I could find, as well as days of googling and fiddling and still had the same problem.

My card is up and running now, although I'm running PCLinuxOS 2009.2 (KDE 4.3.3)

I can tell you that in the gnome and xfce versions of both Ubuntu and PCLinuxOS I would not get sound, I tried KDE on a whim (always been a user of gnome or xfce).

The base install of PCLinux has I believe KDE 3.5, and I've upgraded now to 4.3.3, no problems with sound in either versions.

I know this is not much help in the long run but it does give you at least a couple choices, try installing Kubuntu (I'm assuming your running gnome), failing that maybe think about giving PCLinuxOS a install and see if you have the same luck as myself.

Either way good luck :)

Damon

---

### Post by Mze on 2009-11-22
[SAA7130 TV tuner card under Linux. How To]("http://sites.google.com/site/jobinau2/saa7130basedtvtunercardunderlinux")

---

### Post by hansheijmans on 2010-02-26
> **Mze said:**
> [SAA7130 TV tuner card under Linux. How To]("http://sites.google.com/site/jobinau2/saa7130basedtvtunercardunderlinux")

I've got a similar card wich provides sound output on Windoze *without *any cable connected to the line-in of my sound card. Unfortunately no sound can be heard using TVtime on Karmic :confused:

---

### Post by Uncle Spellbinder on 2010-02-26
> **hansheijmans said:**
> I've got a similar card wich provides sound output on Windoze *without *any cable connected to the line-in of my sound card. Unfortunately no sound can be heard using TVtime on Karmic :confused:
This is a known problem with TVTime. Not just with saa7131/4, but with other cards. 

See: [http://ubuntuforums.org/showthread.php?t=1320515](http://ubuntuforums.org/showthread.php?t=1320515)

and: [https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/472770?comments=all](https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/472770?comments=all)

---

### Post by hansheijmans on 2010-03-01
> **Uncle Spellbinder said:**
> This is a known problem with TVTime. Not just with saa7131/4, but with other cards. 
 
See: [http://ubuntuforums.org/showthread.php?t=1320515](http://ubuntuforums.org/showthread.php?t=1320515)
 
and: [https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/472770?comments=all](https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/472770?comments=all)
 
Just read the conversations on launchpad. I hope, but do not expect so, that 10.04 will solve the issue. Maybe a complete uninstall of pulseaudio? I'm afraid that I will end up losing all audio (I'm using S/PDIF connected to home theatre, analog out to speaker set).
 
Are there any Ubuntu/TVtime developers reading these threads?

---

### Post by Uncle Spellbinder on 2010-03-01
> **hansheijmans said:**
> Just read the conversations on launchpad. I hope, but do not expect so, that 10.04 will solve the issue. Maybe a complete uninstall of pulseaudio? I'm afraid that I will end up losing all audio (I'm using S/PDIF connected to home theatre, analog out to speaker set).
 
Are there any Ubuntu/TVtime developers reading these threads?

All I know is that this is a real issue and I've tried in 10.04 Alpha 3 with the same results, no sound in TVTime. 

A bug has been filed ages ago, which has yet to be assigned to anyone. Numerous threads have been created on this issue both here and other forums.

Seems it's just being ignored. 

A real shame, as TVTime worked flawlessly on this machine in Jaunty and previous Ubuntu versions

---

### Post by hansheijmans on 2010-03-02
> **Uncle Spellbinder said:**
> All I know is that this is a real issue and I've tried in 10.04 Alpha 3 with the same results, no sound in TVTime. 
 
A bug has been filed ages ago, which has yet to be assigned to anyone. Numerous threads have been created on this issue both here and other forums.
 
Seems it's just being ignored. 
 
A real shame, as TVTime worked flawlessly on this machine in Jaunty and previous Ubuntu versions
 
Actually I couldn't get any sound from xawtv as well. I haven't tried MythTV yet, because I wasn't able to install this terribly complex piece of software (have tried it about 4 times). I don't need frontends, backends, MySQL servers etc. just to watch TV.
 
Maybe we should file a bug report again to get someone's attention?

---

### Post by jis4joe on 2010-11-22
Been fighting this one all weekend.  Searching, reading, trying, reading, searching,... no luck.  Anybody got this figured out?  with confidence in their solution?

---

### Post by hansheijmans on 2011-01-07
> **jis4joe said:**
> Been fighting this one all weekend.  Searching, reading, trying, reading, searching,... no luck.  Anybody got this figured out?  with confidence in their solution?

Anyone ?????????

---

### Post by BicyclerBoy on 2011-01-07
Can you please explain what your tuner device is ?
The exact model name ?

lspci
dmesg | grep dvb

I guess it is a dvb-t tuner card ?
A dvb-t card streams out digital data mpeg2-ts that matches the requested pid.
The audio is contained in the datastream, the dvb-t card does not alter the datastream.

You may not have support for LATM_AAC LOAS that is common with dvb-t & H264AVC

By the way..
Once you start using delayed TV viewing you'll understand MythTV.
If you want a complete media centre box then MythTV &/or XBMC are standout apps.

---

### Post by hansheijmans on 2011-01-17
> Can you please explain what your tuner device is ?
The exact model name ?
Hi, sorry for my late reaction. I'm not able to issue the commands right now (it's actually my dad's pc) but I know it's an Asus My Cinema P7131 analog TV tuner card.
Last week I had to reinstall Ubuntu 10.04 after a failed upgrade to Maverick and installed tvtime as well, but tvtime doesn't start at all. It pops up and then disappears again.

As soon as I'm able to I will issue the commands (within a few days).

Thanks!

---

