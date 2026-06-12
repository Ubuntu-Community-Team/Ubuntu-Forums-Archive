---
title: "which is the best driver for Ati Radeon HD 3650 512MB?"
date: 2009-01-21
forum: Multimedia Software
---

### Post by zika on 2009-01-21
Ubuntu Intrepid, Phenom X3, ATI Radeon HD 3650 512MB.
I'm currently using ATI driver version 8.561 with Catalyst 8.12.
I keep reading about open-source drivers but I am unsure if they would support this card based on R600 (as far as I know).
on__ [http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-ati/](http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-ati/) I see open-source drivers with versions higher that those I got when upgraded to Intrepid, (RC + all updates) but I do not even know which of these drivers to try. I surely do not want to end up with blank screen ... ;) should I revert to open-source drivers or should I stay with this "restricted" ... what do You suggest? it works OK with these drivers, not with great speed in compiz but metacity is quicker than me ...
just a thought.

---

### Post by TVMA on 2009-01-21
I'm in a similar boat. I have the HD4850 and have had the same delimma. One thing too is, is that I often times have to tweak settings to keep my screen from flickering when using the ATI restricted drivers. I can go set "Vblank" in compiz general settings, and I have also set (no Xv) for X settings. This solves the ficker problem only for totem, still have issues with VLC and such.

From what I understand, people using Nvidia restricted drivers don't really have any of the issues ATI users have?

I'm curious to know if using the open source drivers would help eliminate these problems. Also, gaming sucks using ATI drivers as well, especially if you are using Wine / Crossover Gaming.. ugh..

Any input regarding the open source drivers would be great. I fear they don't offer 3D support though?

Thanks,..

---

### Post by Melcar on 2009-01-21
There is "blinking" all across the board (when using desktop composition).  All open source drivers suffer from it and fglrx suffers from it.  It has more to do with the way X is set up.  Nvidia drivers bypass X, so they are not susceptible to these problems.  
The ATI open source drivers are great for 2D accel and basic 3D accel on most cards (2D/3D on 5rxx and before cards, 2D only on newer cards).  They are only opengl1.3 and half as fast as fglrx (on a good day), so if you are seeking pure 3D performance these are not for you.  They are good for watching Xv accelerated videos, running composite managers like Compiz, and running most Linux games (forget about Wine since that needs full opengl2.1 compliance), as well as being overall more stable.

---

### Post by HavocXphere on 2009-01-21
afaik the Open-source ones will soon support 3d on the new cards. ATI released some or other docu pack that is supposed to help with that.

Can't wait for the dri2 thing...supposedly its going to fix the flicker bug.:popcorn:

---

### Post by zika on 2009-01-21
> **Melcar said:**
> There is "blinking" all across the board (when using desktop composition).  All open source drivers suffer from it and fglrx suffers from it.  It has more to do with the way X is set up.  Nvidia drivers bypass X, so they are not susceptible to these problems.  
The ATI open source drivers are great for 2D accel and basic 3D accel on most cards (2D/3D on 5rxx and before cards, 2D only on newer cards).  They are only opengl1.3 and half as fast as fglrx (on a good day), so if you are seeking pure 3D performance these are not for you.  They are good for watching Xv accelerated videos, running composite managers like Compiz, and running most Linux games (forget about Wine since that needs full opengl2.1 compliance), as well as being overall more stable.
great! I do not play 3D games, I need them for just the stuff You mentioned. what do You suggest for my card? (HD 3650) to uninstall ATI driver and use what? should I just un-check restricted driver in System->Administration->Hardware or should I uninstall ATI driver by ```
sudo sh ./fglrx-uninstall.sh
``` since I've installed it that way? what am I going to be left with once I've uninstalled it? what about new versions of open-source drivers on "teormodvolden"'s site ... ?

or should I just be at peace with what I have right now and wait for JJ?

---

### Post by Melcar on 2009-01-21
The HD3650 is a r6xx based chip, which doesn't really have a 2D engine.  Most acceleration is done with the 3D engine (even video playback), so the driver would be of no help to you at this moment, unless you plan on using X11 output on your video players.  Further, you won't be able to use Compiz or any of that stuff.  Fglrx is still the best drive for that card for now.  If you still wan to use it, Ubuntu already has both radeon and radeonhd installed by default, so all you would need to do after uninstalling fglrx is rebuild X and edit xorg.conf to use the driver:


```
sudo dpkg-reconfigure xserver xorg
sudo gedit /etc/X11/xorg.conf

# add the "Driver" line to your "Device" section

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeonhd"
EndSection
```

[http://www.x.org/wiki/radeonhd]("http://www.x.org/wiki/radeonhd")


For fglrx uninstallation, use the uninstall script only if you installed the driver with ATI's install script (the one you get from their site).  If you used Ubuntu to install the drivers, just uncheck the box in the hardware drivers menu.

---

### Post by zika on 2009-01-21
thank You very much. I'll just leave everything as it is. to be honest I have everything working reasonably well but every now and then I get the urge to "fix" things, to be honest. thank You once more.

---

### Post by Blue Beard on 2009-01-21
I have used both the radeon and radeonhd drivers in jaunty alpha 3 on a HD3450.  IMO, they are both as good as the flgrx driver.

Configuring two monitors with xrandr simplifies xorg.conf and I have had xrandr --auto work perfectly once.  There are still bugs with recognizing the card on a fresh install.

Status of the features in the drivers is available at [http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

The future looks good for the open source drivers.

---

### Post by TVMA on 2009-01-21
So I also have an Nvidia 8600 GT, would I actually get better 3d / gaming performance using that with the restricted drivers than I would using my ATI HD4850 with the ati drivers?

I'm guessing ..probably.. yeah?

---

### Post by oregonbob on 2009-01-21
I'll have to jump on this list too. I have a new HP m9400f with AMD X4 9750 and an ATI Radeon 3650 HD video card. With stock Intrepid config it does OK, bot no compiz features. I installed the latest ATI Radeon HD 3XXX downloaded from ATI 3 days ago. Then I couldn't stand to watch a video, screen flickers white every time mouse is moved or any screen activity.

Also, I just did automatic updates, it installed 80 of them and said I had to reboot. When I reboot the entire screen was garbled and unreadable. I reboot recovery, restored Intrepid driver and I can function now.

I would like to know of a good card that does everything for less thasn, say $250.00. Is there a perfect working card/model? I have always had bad luck with video cards and linux--for the past 10 years.

---

### Post by Melcar on 2009-01-21
> **oregonbob said:**
> I'll have to jump on this list too. I have a new HP m9400f with AMD X4 9750 and an ATI Radeon 3650 HD video card. With stock Intrepid config it does OK, bot no compiz features. I installed the latest ATI Radeon HD 3XXX downloaded from ATI 3 days ago. Then I couldn't stand to watch a video, screen flickers white every time mouse is moved or any screen activity.

Also, I just did automatic updates, it installed 80 of them and said I had to reboot. When I reboot the entire screen was garbled and unreadable. I reboot recovery, restored Intrepid driver and I can function now.

I would like to know of a good card that does everything for less thasn, say $250.00. Is there a perfect working card/model? I have always had bad luck with video cards and linux--for the past 10 years.


If you really want to be able to use Compiz and accelerate video playback at the same time, nvidia is the only way to go at he moment.  I really should not discuss this, but the next set of ATI drivers will start to address the "blinking" with video playback and Compiz (starting with 9.1 if they can work out the kinks), so not everything is bad for ATI users.
Keep in mind that most of these problems are being caused by the xserver and not the drivers, so no one can really do anything about it except the guys developing X.  

> **TVMA said:**
> So I also have an Nvidia 8600 GT, would I actually get better 3d / gaming performance using that with the restricted drivers than I would using my ATI HD4850 with the ati drivers?

I'm guessing ..probably.. yeah?


The HD4850 card will run circles around the 8600 when it comes to raw 3D.  The nvidia card will, however, give you better video playback with composite managers (i.e Compiz).

---

### Post by markbuntu on 2009-01-22
If intel had not monkeywrenched dri2 last summer we would not be having this problem anymore. 

In any case, dri2 will be out very soon and that is what ati and compiz have been waiting for rather than spend a lot of time on temporary kludgy fixes that will need to be unwound and tossed in the trash when the next xserver is released.

Anyway, I am quite happy with my HD3650 and can live without compiz when I want to watch a video.

---

### Post by zika on 2009-01-23
> **markbuntu said:**
> Anyway, I am quite happy with my HD3650 and can live without compiz when I want to watch a video.
+1
the only two things that I use compiz for are negative of the current window (to compensate for bad color choice on certain web pages) and I love the possibility to switch between work-spaces with scroll mouse button. videos are fine even with compiz once I've managed to route the output to X11 on all players.

---

### Post by zika on 2009-01-28
my experience (not bad, to the contrary) might be useful to someone ...[I][B]
8.10-64-bit:[/B][/I]
several minutes ago I've updated (not intentionally but I was just following the orders ... :)) my kernel to 2.6.27-11-generic via Synaptic. everything went well. finally I've got rid of ATI proprietary driver but not at my will ... :wink: this new kernel doesn't work with that driver? even if I check driver in Hardware_drivers I get into the mess of a screen after reboot. so I'm staying with, ... nothing I guess since my xorg.conf now looks like:```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection 
```I'm not complaining, videos work, everything works, even faster, except of compiz and such stuff which I really do not use anyway. but, what happened ... :wink:

do I have to change anything now? which driver am I using now, anyway ...?

**update1:** on a laptop (HP 530) with (I think) Intel v-chip it updated without a glitch. so, it's just the collision between kernel and ATI driver[B].
update2:[/B] I've removed ATI driver with *sh ./fglrx-uninstall.sh* and removed all traces of fglrx through synaptic. even though **Melcar** say:*Ubuntu already has both radeon and radeonhd installed by default *on my machine radeonhd is not installed and radeon is. should I install radeonhd and enable it through xorg.conf with the line *Driver "radeonhd"*? I'm kind of stummied because (apart from compiz) all the stuff works (videos etc.) ... so, to say, I do not need help I need some kind of explanation and guidance ... ;) I do not want to install fglrx if I do not need to, and, uncommon for me, I am not sure if I want to change anything while all the stuff is working ...
** update3:** installed radeonhd and added corresponding line to xorg.conf. it doesn't work. uninstalled radeond. changed line into radeon and it works. it seems it is slower than without that line. but with radeon I have glx direct rendering and without it I do not have glx at all. the question remains: what am I using when there is no driver line in xorg.conf and why is that faster for all the stuff I need?
is activating fglrx advised?[B]
update4:[/B] I've edited my xorg.conf in accordance with the page suggested in this thread to:```
Section "Device"
    Identifier    "Configured Video Device"
        Driver          "radeon"
        Option "AccelMethod" "XAA"
 # XAA/EXA
        Option "AccelDFS"    "1"
 # 1/0 On for PCIE, off for AGP
 # Manpage: Use  or  don't  use accelerated EXA DownloadFromScreen hook
 # when possible.
        Option "GARTSize" "64"
 # 0-64 Megabytes of gart (system) memory used.
 # Wrongly defaults to 8MB sometimes, see your logfile.
 # Bigger seems better.
        Option "EnablePageFlip" "1"
 # 1/0 Increases 3D performance substantially
 # seemingly in XAA mode only
        Option "ColorTiling" "1"
 # 1/0 Increases 3D performance substantially
 # affected stability only positively on my system
EndSection

Section "DRI"
        Group        "video"
        Mode         0660
EndSection

Section "Module"
        Load            "glx"
        Load            "dri"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
``` any comments would be appreciated.[B]

update5:[/B] this xorg.conf gives better stability and speed:```
Section "Device"
    Identifier    "Configured Video Device"
        Driver          "radeon"
        Option "AccelMethod" "EXA"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```**update6:** a new day and a new sub-version of kernel. :) I have no regrets, I've learned a lot and still did not install fglrx ... ;) in [http://ubuntuforums.org/showpost.php?p=6633172&postcount=12](http://ubuntuforums.org/showpost.php?p=6633172&postcount=12) made a good point why I should not do that yet, or, at least, consider using "official" version ...


**conclusion:** speedy appearance of a new sub-version of kernel shows what was wrong. to be clear: me. I shouldn't have jumped and applied updates so quickly. but, what would be a good rule: to wait for how long and how to differentiate between updates several days old and those that came today? without regrets and with more knowledge that yesterday morning I'm moving on ... :)

was this at the end a dkms issue? I do not have it installed. looking at the logs that is the difference between yesterday's and today's 2.6.27-11generic (14 and 25). should I install it or is it there by default? would dkms transfer ATI driver installed outside of apt-get, aptitude and synaptic to a new kernel?

---

