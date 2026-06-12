---
title: "[SOLVED] Did ATI Driver &amp;amp; Catalyst  8.9 Install?"
date: 2008-10-12
forum: Multimedia Software
---

### Post by ft23002 on 2008-10-12
Hi All,

Wanted to give the latest ATI drivers & catalyst a try and thinking everything is correct, but when I open catalyst it shows its version, as "2.1". 
Also in the catalyst, it shows "Driver Version 8.53.4"

Note: Had the Hardware Proprietary Drivers ticked (enabled) before installing ati 8.9.
Tried it both ways on new ubuntu installs and it didn't seem to make a difference if this was enabled before the 8.9 install, the results in catalyst and below cli outputs were the same.

Install went without any errors by following the (method#2) instructions found here at.. 

[[COLOR="Blue"]Unofficial ATI Linux Driver Wiki... Ubuntu Hardy Installation Guide[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

1. Do I have the latest drivers installed?
2. Do I have the latest catalyst control center installed?

3. Is it that the installer package is version is 8.9, and nothing installed from it should show this version as the drivers and catalyst themselves have there own version #'s?

Thanks for the help

Outputs:

```
...:~$ lspci -n | grep 0300
01:00.0 0300: 1002:7145
```
```
...:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7979 Release

```
```
...:~$ ls /etc/ati
amdpcsdb          atiogl.xml         control                logo.xbm.example
amdpcsdb.default  authatieventsd.sh  logo_mask.xbm.example  signature

```

[ATTACH]88112[/ATTACH]

---

### Post by porchrat on 2008-10-13
> **ft23002 said:**
> Hi All,

Wanted to give the latest ATI drivers & catalyst a try and thinking everything is correct, but when I open catalyst it shows its version, as "2.1". 
Also in the catalyst, it shows "Driver Version 8.53.4"

Note: Had the Hardware Proprietary Drivers ticked (enabled) before installing ati 8.9.
Tried it both ways on new ubuntu installs and it didn't seem to make a difference if this was enabled before the 8.9 install, the results in catalyst and below cli outputs were the same.

Install went without any errors by following the (method#2) instructions found here at.. 

[[COLOR="Blue"]Unofficial ATI Linux Driver Wiki... Ubuntu Hardy Installation Guide[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

1. Do I have the latest drivers installed?
2. Do I have the latest catalyst control center installed?

3. Is it that the installer package is version is 8.9, and nothing installed from it should show this version as the drivers and catalyst themselves have there own version #'s?

Thanks for the help

Outputs:

```
...:~$ lspci -n | grep 0300
01:00.0 0300: 1002:7145
```
```
...:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7979 Release

```
[ATTACH]88112[/ATTACH]


Let me start by saying yes that is the 8.9 catalyst driver, and what is more it seems to be functioning perfectly :)  Congratulations on that was this your first try?  If so well done, as I mentioned once in a previous thread it took me 3 attempts before I tried that method you linked to and finally sorted my mess out.

Let's try and answer a few of those questions you've posed.

The first I've noticed you have said that catalyst says it is version 2.1.  That version number refers to the "Catalyst Control Center" GUI program that controls the behaviour of the graphics card by "talking" to the driver, not the graphics driver itself.

As for the 8.53.4 version number, you are 100% right, that number is actually the "Driver Version" number.  The driver used is the "fglrx" driver and the one inlcuded in the Catalyst 8.9 install bundle is actually version 8.53.4, while 8.9 is merely the version number of the ENTIRE install bundle that you download from ATI's website.

These differences may seem a little strange at first, but it isn't that strange when you think about it.  When you install that download from ATI it actually installs multiple programs each with their own version numbers.

Hopefully that clears up some of the confusion and I also hope you enjoy your new drivers, I know I am enjoying mine :)

---

### Post by alex.forencich on 2008-10-13
The ATI version numbers are slightly confusing.  I just installed the latest driver (8.9) and the version numbers changed from what they were before.  At first glance it appears that we are running the same versions - OpenGL 2.1.7979, Catalyst Control Center 2.1, and driver version 8.53.4.  I haven't the foggiest where 8.9 fits into all of that, though...

I know it updated something because all my video playback programs started flickering after I updated the driver, I had to mess with my xorg.conf to get everything working properly.  Which is probably what I should have done in the first place, becuase I was trying to solve a dropped frame problem in VLC.  The new driver certainly couldn't hurt, though.

---

### Post by porchrat on 2008-10-13
> **alex.forencich said:**
> The ATI version numbers are slightly confusing.  I just installed the latest driver (8.9) and the version numbers changed from what they were before.  At first glance it appears that we are running the same versions - OpenGL 2.1.7979, Catalyst Control Center 2.1, and driver version 8.53.4.  I haven't the foggiest where 8.9 fits into all of that, though...

I know it updated something because all my video playback programs started flickering after I updated the driver, I had to mess with my xorg.conf to get everything working properly.  Which is probably what I should have done in the first place, becuase I was trying to solve a dropped frame problem in VLC.  The new driver certainly couldn't hurt, though.

As I said above, 8.9 is the version number for the entire package that you download from ATI.  All of the individual programs within that ATI program bundle will have their own individual version numbers.

---

### Post by ft23002 on 2008-10-13
> **porchrat said:**
> Let me start by saying yes that is the 8.9 catalyst driver, and what is more it seems to be functioning perfectly :)  Congratulations on that was this your first try?  If so well done, as I mentioned once in a previous thread it took me 3 attempts before I tried that method you linked to and finally sorted my mess out.

Let's try and answer a few of those questions you've posed.

The first I've noticed you have said that catalyst says it is version 2.1.  That version number refers to the "Catalyst Control Center" GUI program that controls the behaviour of the graphics card by "talking" to the driver, not the graphics driver itself.

As for the 8.53.4 version number, you are 100% right, that number is actually the "Driver Version" number.  The driver used is the "fglrx" driver and the one inlcuded in the Catalyst 8.9 install bundle is actually version 8.53.4, while 8.9 is merely the version number of the ENTIRE install bundle that you download from ATI's website.

These differences may seem a little strange at first, but it isn't that strange when you think about it.  When you install that download from ATI it actually installs multiple programs each with their own version numbers.

Hopefully that clears up some of the confusion and I also hope you enjoy your new drivers, I know I am enjoying mine :)

Thanks so much Porchrat for clearing this up. It is a little confusing the way none of the individual package version numbers relate to the main download version number. When one reads catalyst 8.9 and then seeing 2.1 in the catalyst, it can easily be misunderstood as thinking an older version of catalyst UI actually installed. Same with the drivers, I had seen with the default ATI proprietary driver Ubuntu uses as being 8.6, then seeing 8.53.4 in catalyst UI, I wasn't sure what was installed. Was glad to see a working desktop after the install though. LOL 
Would the download version (currently 8.9) number change if any of its contained packages are updated? How does one know if somethings been updated? Being new to Ubuntu (linux) I'm not sure how often video drivers get updated, but with windows, its like every couple of weeks.

It did go well and without issue, and owe you some of the credit . Had I not seen your thread regarding updating ati drivers, it may not have gone so well. There are a few methods out there, but having read your success with using the method you referred to, decided it was the one to go with. When I noticed you had just updated, figured now was the time.

Yes, the drivers are working well. Haven't tried any on PC Video players, but compiz, screensavers, and general window appearance is much improved. Video on the net using adobe flash player plays good. After playing around with catalyst, the screensavers improvement was easily seen. I really like the "Skyrocket" one. The clouds and stars look much better! The screen does flicker in preview & in the screensaver UI, but when actually used, its fine. Not sure if thats a problem, but it did do this with the older drivers too. Also, at the bottom of the instructions, theres something on Suspend that I should try as Suspend with the original proprietary driver (8.6) didn't work.

Thanks again Porchrat, your a true Ubuntu Friend!

---

### Post by ft23002 on 2008-10-13
> **alex.forencich said:**
> The ATI version numbers are slightly confusing.  I just installed the latest driver (8.9) and the version numbers changed from what they were before.  At first glance it appears that we are running the same versions - OpenGL 2.1.7979, Catalyst Control Center 2.1, and driver version 8.53.4.  I haven't the foggiest where 8.9 fits into all of that, though...

I know it updated something because all my video playback programs started flickering after I updated the driver, I had to mess with my xorg.conf to get everything working properly.  Which is probably what I should have done in the first place, becuase I was trying to solve a dropped frame problem in VLC.  The new driver certainly couldn't hurt, though.

Update: There is problems with playing video on the PC.

What did you do to your xorg.conf, Please Post Fix.

According to [[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=769020&highlight=ati+video+screen+flicker") it is Not the ATI drivers, but something with compiz and how it uses OpenGL. A workaround suggested is to go to: System/Preferences/Appearance /Visual Effects and choose "None". Its by no means a fix as everything in compiz & emerald gets turned off.

Did you correct this issue by doing:

>  Originally Posted by PoopyTheJ  View Post
This fix works for me in watching video, for games just turn off visual effects in appearance while playing and turn them back on when you're done. Anyways to fix the flickering video with ATI cards turn off textured video. **Edit your etc/X11/xorg.conf file with this in the fglrx device section,**

```
Option "TexturedVideo" "off"
```

Restart X and you're watching flicker free video.

I'm running a 3850HD with the Catalyst 8.5's

Please post all changes you made to solve this, thanks Alex.

---

### Post by ft23002 on 2008-10-13
Added the above line to the device section/fglrx and it worked. One does not have to shut down any effects to watch video...COOL!!!

Thanks to PoopyTheJ for posting this better fix.

---

