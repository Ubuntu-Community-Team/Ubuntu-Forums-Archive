---
title: "My 8.10 experience so far"
date: 2008-11-06
forum: Mythbuntu
---

### Post by fatmonk on 2008-11-06
_**Background**_

Bits and pieces of linux experience in the past and quite a lot of unix experience of various flavours (SCO, Solaris etc), but a couple of months ago was told about MythBuntu as a Media hub option.

Tried the live CD of 8.04 and was very impressed with Ubuntu as a basic OS, it was so fast on the machine I tried it on, and 'it just worked' (as hasbeen said so many times before).

So, off I went to buy the various bits of hardware I wanted to build a backend / frontend combo that would sit comfortably in my hifi stack in the living room and not look (or sound) out of place.

I was making some progress with 8.04, but having serious problems getting S/PDIF out to work off my motherboard, and having no joy whatsoever with getting the remote control to work. As for the LCD/VFD screen on my case, I didn;t get as far as trying to set that up - although people reported that it worked after a struggle on their systems.

Then last weekend after a session on IRC and in the forums trying to get the remote working I ended up with a pretty poorly box. Disk errors on boot, no access to the tuner card, slow, odd behaviour of the OS on the whole and in Myth.

I thought I'd left these problems behind with Windows!

After trying and failing to reinstall with 8.04 (it didn't like my wireless card or video card in the case while I installed!). So pulling hardware out and trying again I got somewhere but nowhere near a 'working' system that I was happy to start configuring Myth-wise.

So I decided to download 8.10 and see where that went....

_**8.10 experience**_

The install was as smooth as ever. I had an oddity first install though when I selected to use the TV out on my video card. The system rebooted in low graphics mode. When I then opened nVidia settings to try to tweak the settings I lost the menu bar at the top of the screen completely and the the screen stretched vertically - odd. Only option was to pull the power and try again. This time I left the TV out disabled and all went well.

_**First problem - MythWeb**._

I selected a standard MythBuntu install with all plugins, and to be honest I prefer MythWeb to the on screen programme guide, so was keen to have that working anyway. BUT when the system asked me for a password for Mythweb, the dialog saying it was settings MythWeb security froze and wouldn't progress beyond about 95%. Not a major problem, but it seem sthere is a problem with MCC setting a MythWeb password in general.

When I connected to MythWeb I was also suprised to see most of the icons across the top of the screen had gone. I was left with just the TV icon and the settinsg icon, then the search box. All of the others that were there on my 8..04 install had gone. Hmm. Needs more investgation, but that seems odd to me.

_**Next nVidia**_ (I've tried 173 and 177 drivers).

Well, a lot has been written about the problems with nVidia settings and xorg.conf. Suffice to say I had all of those problems, and the fix for the seg fault and being unable to write a new xorg.conf file for me was to remove /etc/X11/xorg.conf then run sudo nvidia-xconfig and then sudo nvidia-settings. Always then run nvidia-settings as root (su) in future, as you shoudl anyway, and the saving of xorg.conf is sorted.

BUT that's not the end of my nVidia woes.

I am wholy unable to configure a cloned TV-out with nvidia-settings now. It worked perefctly in 8.04, but the GUI just behaves very very oddly now. When I select to enable TV out and set it to clone, the LCD montor config changes to an odd 300x480 (or something equally odd and 'portrait'). I can reset those parameters and get everything looking about right in the GUI with abit of fiddling, but the image of the displays isn't quite as it was in 8.04. In 8.04 I am 99% sure that the image of the screen showed both the TV out and the LCD device in the screen when it was set to clone. Now what happens is that the config appears to hide the TV behind the LCD! Rather than a clone its just a second screen in the same virtual position, but behind the LCD and I never actually get the TV out on the TV... I say never, I occasionaly get a flicker of the desktop or the nVidia logo when restarting X, but nothing permanent and nothing when I reboot.

No TV out makes the Mythbox a bit useless for me. That's priority number one fix for me, so I'll be trying a manual edit of xorg.conf next.

_**Remote control**._

Well I've had some sucess with this in 8.10. More than I had in 8.04 anyway. It needs a lot more work, but at least I have been able to drive the Myth GUI from the Hauppage remote supplied with the Nova-T 500 which I hadn't managed before. Key presses didn;t always do what was expected, but its a start. Now just to get that working with the built in Soundgraph IR receiver. That could be fun. Getting a working remote is priority number two.

_**Software / updates repositories**._

This one a bit of an annoyance seeing as there seem to be so many little issues with 8.10. When I run the update manager I get a whole bunch of errors.

The Mythbuntu website still lists the repository info for weekly builds for Hardy, but I tried adding for intrepid as well (modifying references to hardy to intrepid). This doesn't work, but that's propbably down to my incompetence. The fact that the other repositories throw errors as well is a bit more worrying.

Again, this is something I need to look into as I guess potentially some of my issues could be fixed pretty quickly in updates.

_**WiFi network key niggle**._

Now this is quite possibly down to me clicking a cancel button during the initial connection to my WiFi. I was asked to set up a default key ring and I didn't. I think this is a new thing in MythBuntu 8.10 and I was quite happy with the box remembering my WiFi key the way it did on 8.04. Except it doesn't. In 8.10 it seems to rely on this key ring thing. (Please correct me if I'm wrong about this.) Unfortunately, now if the unit is rebooted I am asked to enter the user password in order to unlock the default keyring to allow the WiFi to connect (I don't have to re-enter the key, just provide the user password). If I don't do this in time, I even lose the network connect icon on the top menu bar.

That's another one for me to look into in an effort to make the box more user friendly.

_**Then there's the CD tray unload bug**._

I think I've found instructions for solving this one in the forums, and its now a recognised bug, I believe. The fix I found is in this thread [https://bugs.launchpad.net/ubuntu/+source/eject/+bug/280931](https://bugs.launchpad.net/ubuntu/+source/eject/+bug/280931) but I haven't had a chance to try it yet.

And that's about where I am at. I've got the TV tuner working fine, so if I get the TV out and remote working at least the box is usable. But as you can see I have quite a few other thyings to sort out before the box is really fit for general use.

Another thing I did notice though was that I don't think the seperate media mount point was created when my disk was formatted under the standard install. I believe the whole disk has been used as boot/OS and media combined... not 100% sure about this, but at a first glance with df -k it looks that way.

If anyone has any pointers as to quick fixes for any of the problems listed I'd be inetersetd to know. Otherwise I'd be interested to know general experiences of others with 8.10 - ie what you've managed to get working and what's causing problems (will give me a clue as to what problems I should expect to encounter next!).

-FM

---

### Post by tgm4883 on 2008-11-06
> **fatmonk said:**
> _**Background**_

Bits and pieces of linux experience in the past and quite a lot of unix experience of various flavours (SCO, Solaris etc), but a couple of months ago was told about MythBuntu as a Media hub option.

Tried the live CD of 8.04 and was very impressed with Ubuntu as a basic OS, it was so fast on the machine I tried it on, and 'it just worked' (as hasbeen said so many times before).

So, off I went to buy the various bits of hardware I wanted to build a backend / frontend combo that would sit comfortably in my hifi stack in the living room and not look (or sound) out of place.

I was making some progress with 8.04, but having serious problems getting S/PDIF out to work off my motherboard, and having no joy whatsoever with getting the remote control to work. As for the LCD/VFD screen on my case, I didn;t get as far as trying to set that up - although people reported that it worked after a struggle on their systems.

Then last weekend after a session on IRC and in the forums trying to get the remote working I ended up with a pretty poorly box. Disk errors on boot, no access to the tuner card, slow, odd behaviour of the OS on the whole and in Myth.

I thought I'd left these problems behind with Windows!

After trying and failing to reinstall with 8.04 (it didn't like my wireless card or video card in the case while I installed!). So pulling hardware out and trying again I got somewhere but nowhere near a 'working' system that I was happy to start configuring Myth-wise.

So I decided to download 8.10 and see where that went....

_**8.10 experience**_

The install was as smooth as ever. I had an oddity first install though when I selected to use the TV out on my video card. The system rebooted in low graphics mode. When I then opened nVidia settings to try to tweak the settings I lost the menu bar at the top of the screen completely and the the screen stretched vertically - odd. Only option was to pull the power and try again. This time I left the TV out disabled and all went well.

_**First problem - MythWeb**._

I selected a standard MythBuntu install with all plugins, and to be honest I prefer MythWeb to the on screen programme guide, so was keen to have that working anyway. BUT when the system asked me for a password for Mythweb, the dialog saying it was settings MythWeb security froze and wouldn't progress beyond about 95%. Not a major problem, but it seem sthere is a problem with MCC setting a MythWeb password in general.

When I connected to MythWeb I was also suprised to see most of the icons across the top of the screen had gone. I was left with just the TV icon and the settinsg icon, then the search box. All of the others that were there on my 8..04 install had gone. Hmm. Needs more investgation, but that seems odd to me.

_**Next nVidia**_ (I've tried 173 and 177 drivers).

Well, a lot has been written about the problems with nVidia settings and xorg.conf. Suffice to say I had all of those problems, and the fix for the seg fault and being unable to write a new xorg.conf file for me was to remove /etc/X11/xorg.conf then run sudo nvidia-xconfig and then sudo nvidia-settings. Always then run nvidia-settings as root (su) in future, as you shoudl anyway, and the saving of xorg.conf is sorted.

BUT that's not the end of my nVidia woes.

I am wholy unable to configure a cloned TV-out with nvidia-settings now. It worked perefctly in 8.04, but the GUI just behaves very very oddly now. When I select to enable TV out and set it to clone, the LCD montor config changes to an odd 300x480 (or something equally odd and 'portrait'). I can reset those parameters and get everything looking about right in the GUI with abit of fiddling, but the image of the displays isn't quite as it was in 8.04. In 8.04 I am 99% sure that the image of the screen showed both the TV out and the LCD device in the screen when it was set to clone. Now what happens is that the config appears to hide the TV behind the LCD! Rather than a clone its just a second screen in the same virtual position, but behind the LCD and I never actually get the TV out on the TV... I say never, I occasionaly get a flicker of the desktop or the nVidia logo when restarting X, but nothing permanent and nothing when I reboot.

No TV out makes the Mythbox a bit useless for me. That's priority number one fix for me, so I'll be trying a manual edit of xorg.conf next.

_**Remote control**._

Well I've had some sucess with this in 8.10. More than I had in 8.04 anyway. It needs a lot more work, but at least I have been able to drive the Myth GUI from the Hauppage remote supplied with the Nova-T 500 which I hadn't managed before. Key presses didn;t always do what was expected, but its a start. Now just to get that working with the built in Soundgraph IR receiver. That could be fun. Getting a working remote is priority number two.

_**Software / updates repositories**._

This one a bit of an annoyance seeing as there seem to be so many little issues with 8.10. When I run the update manager I get a whole bunch of errors.

The Mythbuntu website still lists the repository info for weekly builds for Hardy, but I tried adding for intrepid as well (modifying references to hardy to intrepid). This doesn't work, but that's propbably down to my incompetence. The fact that the other repositories throw errors as well is a bit more worrying.

Again, this is something I need to look into as I guess potentially some of my issues could be fixed pretty quickly in updates.

_**WiFi network key niggle**._

Now this is quite possibly down to me clicking a cancel button during the initial connection to my WiFi. I was asked to set up a default key ring and I didn't. I think this is a new thing in MythBuntu 8.10 and I was quite happy with the box remembering my WiFi key the way it did on 8.04. Except it doesn't. In 8.10 it seems to rely on this key ring thing. (Please correct me if I'm wrong about this.) Unfortunately, now if the unit is rebooted I am asked to enter the user password in order to unlock the default keyring to allow the WiFi to connect (I don't have to re-enter the key, just provide the user password). If I don't do this in time, I even lose the network connect icon on the top menu bar.

That's another one for me to look into in an effort to make the box more user friendly.

_**Then there's the CD tray unload bug**._

I think I've found instructions for solving this one in the forums, and its now a recognised bug, I believe. The fix I found is in this thread [https://bugs.launchpad.net/ubuntu/+source/eject/+bug/280931](https://bugs.launchpad.net/ubuntu/+source/eject/+bug/280931) but I haven't had a chance to try it yet.

And that's about where I am at. I've got the TV tuner working fine, so if I get the TV out and remote working at least the box is usable. But as you can see I have quite a few other thyings to sort out before the box is really fit for general use.

Another thing I did notice though was that I don't think the seperate media mount point was created when my disk was formatted under the standard install. I believe the whole disk has been used as boot/OS and media combined... not 100% sure about this, but at a first glance with df -k it looks that way.

If anyone has any pointers as to quick fixes for any of the problems listed I'd be inetersetd to know. Otherwise I'd be interested to know general experiences of others with 8.10 - ie what you've managed to get working and what's causing problems (will give me a clue as to what problems I should expect to encounter next!).

-FM

Some of the problems may be db tables that need to be repaired, mysql linux doesn't like it when you just pull the power, so don't do that.

The icons at the top of mythweb are only there if the plugins are installed.

Also, you will get more help if you post the output of things like df -k rather than just say they look weird.  What is weird to you might make perfect sense to me.

---

### Post by ghuber on 2008-11-06
What worked for me to get past the nvidia problems was this:
I replaced the xorg.conf file with the xorg.conf.failsafe that is in that directory.

Then I installed envy from the repositories.   Envy then downloaded the 173 drivers and configured the xorg.conf file for me.

Worked great and was quick and easy.

I also enabled the extra repositories but I don't know if that is required to get envy. 

G

---

### Post by fatmonk on 2008-11-07
> **tgm4883 said:**
> Some of the problems may be db tables that need to be repaired, mysql linux doesn't like it when you just pull the power, so don't do that.

The icons at the top of mythweb are only there if the plugins are installed.

Also, you will get more help if you post the output of things like df -k rather than just say they look weird.  What is weird to you might make perfect sense to me.

Hi tgm4883,

I know that pulling the power on a linux box is not good in general, especially when something like MySQL is running as there will be stuff which hasn't been written from from teh cache to the disk which could lead to corruption. Howeve these were absolute last resorts due to the OS not responding to anything.

The worst situation was when the screen stretched vertically (the mythbuntu logo was vertically stretched and in the middle of the screen), the top menu bar was missing and the mouse would not pass beyond the edge of the physical screen (ie it wasn't a panning desktop). Right click didn't work either so there was no way to bring up the menu to restart or even bring up a terminal to sbin halt.

Is there a key combination in Ubuntu that will open a terminal or open the desktop menu?

(As I said, I have plenty of unix experience and a fair bit of linux experience from a few years ago, but I am new to Ubuntu and so keep finding new shortcuts to add to my quivver).

Regarding posting output from command, I normally would, but I'm nowehere near my box at the moment and I wanted to post my experience so far just to get a feel of whether others had gone through similar things with 8.10.

The disk partitioning issue will all change next week anyway, as I've just ordered a 160GB disk to put in the box as a system disk (and to hold my music and photos), leaving the 500GB for recordings. That means that next week I'll go for a fresh install again - and hopefully get things back that I've got working so far like my S/PDIF out!

Regarding MythWeb, I had all plugins installed as per the default installation and yet only the two icons were there. No weather icon, no radio icon, and I can't remember what the others were under the 8.01 install.

Once I'm back in front of the box I can get more specific info (hopefully some time thsi weekend).
-FM

---

### Post by fatmonk on 2008-11-07
> **ghuber said:**
> What worked for me to get past the nvidia problems was this:
I replaced the xorg.conf file with the xorg.conf.failsafe that is in that directory.

Then I installed envy from the repositories.   Envy then downloaded the 173 drivers and configured the xorg.conf file for me.

Worked great and was quick and easy.

I also enabled the extra repositories but I don't know if that is required to get envy. 

G


Ghuber,

Thanks for this. I'd had a look at the Envy website and wondered if that might help.

Will certainly give that a go as well once I get back in front of my box.

Cheers,

FM

---

