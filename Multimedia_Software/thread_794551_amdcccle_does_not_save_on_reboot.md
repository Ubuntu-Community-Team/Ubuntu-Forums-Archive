---
title: "amdcccle does not save on reboot??"
date: 2008-05-14
forum: Multimedia Software
---

### Post by no_hup on 2008-05-14
I'm totally freakin out to get my 2 monitors to work as big desktop or whatever similar to XP "span desktop to this monitor"
Actually, in various ways I managed to do it in fedora4, slackware, kubuntu and ubuntu 7. Sometimes it was ready to go (just a click to enable) sometimes I had to hardcode the xorg.conf.

Now I have tried kubuntu8 kde4 and no way, after 3-4 trials everything is so compromised that I need to reinstall the os and I gave up with kde.

I'm more lucky with ubuntu8, but it happens that when I run amdcccle (catalyst control center) I configure successfully the bigdesktop (apart from a 5mm stripe ontop of the 2nd monitor that remains jerky) and it asks me to reboot to take effect. When I do no changes are made! Also the same amdcccle detects the same previous clonemode setup!

So frustrated, I compared xorg.conf before and after the "apply settings" of amdcccle and no changes at all were made. I tried running amdcccle from root but same result.

At present moment I simply do not reboot and keep my correclty bigdesktop setup with the crappy wallpaper stripe on 2nd monitor.

P.S: I tried at dozens and dozens of times to use " --screen-layout=left" setting or similar for aticonfig, but always at xserver restart I get the bigdesktop but window manager won't get load, every application got no window frame, and many buttons returns error. So I abandoned that path.

Is there anyone that already fixed this issue? Thanks :confused:

---

### Post by NS2-10 on 2008-08-23
Same problem here! Please help!

---

### Post by JonTheJester1337 on 2008-08-28
I am having the same problem. Whether I run it as root through terminal or from my main menu, it never saves xorg.conf to apply changes on reboot.

Thoughts on how to build an xorg.conf from the settings it applies? Anyone know how to coax it into actually saving?

---

### Post by TheTank on 2008-09-10
Similar problems, but my changes hold!
But from my xorg.conf, they should not be. Really strange.

---

### Post by markbuntu on 2008-09-10
Screen configuration is a user session setting so, once you set up your screens you should do a System/Preferences/Save Session otherwise you may end up with your previous session setting which is default for cloned screen.

---

### Post by pacanukeha on 2008-09-16
There is no Save Session option.

The nearest equivalent is

System | Preferences | Sessions | Session Options
and then click
"Remember Currently Running Applications"
will give you a "Your session has been saved." message. This certainly implies that it is only about currently running applications rather than any display settings, and in fact when I tried it, it *did* save my applications and did *not* save my Big Desktop options. Same for the September 17, 2008 release of the driver 

*edited last sentence*

---

### Post by give.away on 2008-09-26
Hello,

same problem here.
Cannot remove pairmode permanently and cannot persuade my graca to boot in the correct resolution.

I can manually set the resolution at amdcccle, but it is saved only for the current X-session. Is there perhaps a possibility to write a script?

Thanks in advance,
GA

P. S. Saving the session doesn't work either.

---

### Post by cjaeger on 2008-10-12
This worked for me: after using amdcccle to set the monitors the way I wanted them, I clicked "ok" to close amdcccle, and then went to System->Preferences->Screen Resolution, verified that it showed the resolution that I wanted, and clicked apply. This time, the settings survived an X restart.

I haven't had the patience yet to verify that this is reproducible.

---

### Post by latev on 2008-10-28
For some reason I was so sure there would be a command line utility in Linux for switching displays :(
I was so disappointed with the crappy control center from ATI - it has no cmd line options support and yes - it does NOT modify the xorg file - the aticonfig is supposed to do that. So my guess is that it stores its settings elsewhere
In my case after every little change I made in the control center it asks me to reboot /is this a micro$oft trojan horse?/ however certain changes are applied immediately without the need for an X reset. 
Still looking for a way to automate the process via bash scripts
and finally I should mention that I managed to get my monitor at 1280x1024 and my TV at 1024x768 at the same time. This turns out is not what I thought it would be, because in this setup the ATI driver seems to be very unstable - vlc in full screen mode reverts back to my monitor screen and trying to rotate the cube /switching desktops/ while playing video on my TV crashes X and I have to do a reboot.

Linux AMD64 2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64 GNU/Linux
02:00.0 VGA compatible controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series]
02:00.1 Display controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] (Secondary)

---

### Post by markbuntu on 2008-10-28
aticonfig is the command line for controlling the fglrx driver. Use aticonfig --help for options. The driver is very much a work in progress so many features are not yet in the Catalyst Control Center gui but are expected to be included as the driver progresses.

As far as xorg.conf is concerned, Xorg is in the process of removing xorg.conf entirely. It will not be avialable in future releases of X starting with 7.4. Configuration is being automated with options confined to the drivers themselves and their configuration utilities.

---

### Post by latev on 2008-10-28
All right markbuntu, 
could you please provide some support on one of the very first thing a user would like to do on a freshly installed system - configure the displays, in my case a monitor and a TV.
So far the CCC has been totally worthless for me and the aticonfig utility seems to be trying to write a xorg file each time I try to reconfigure my settings. All I really need is a simple command to turn the TV on and OFF, or to switch between TV and the monitor.
/hopefully without having to reboot each time/
And the funny thing is that according to my experience the configuration file seems to be ignored anyways - as you already mentioned. So - what am I missing here, how's the correct way to think about all that?
Also - do you have any idea where the fglrx settings are stored?

---

### Post by latev on 2008-10-28
I think I found an answer to my question

tl@AMD64:~$ aticonfig --enable-monitor tv --resolution=0,800x600

switches the TV on and disables the monitor, the right resolution is applied as well

tl@AMD64:~$ aticonfig --enable-monitor tmds2i --resolution=0,1280x1024

turns the TV off and the monitor ON

According to the aticonfig:
"Dynamic Display Management Options:
  Following options will not change the config file. They are
  used for querying driver, controller and adaptor information.
  These options will be effective immediately. Other options on 
  the same command line will be ignored."

There's TWO wrong statements here:
1) aticonfig is trying to change my xorg file
tl@AMD64:~$ aticonfig --enable-monitor tmds2i
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

this is not much of an issue as I'm not using it with root privileges so changing the xorg file is not going to succeed

2) The second parameter is still processed, contrary to what the utility says - ie the resolution is changed as well

Hope the above spares somebody the 2-3 hours I spent on this

---

### Post by markbuntu on 2008-10-28
You should file a bug report about that with ati since it is certainly something they should know about. 

The actual file that aticonfig writes to is:

/etc/ati/amdpcsdb 

It is not a file that can be edited by hand.

---

### Post by latev on 2008-10-28
I'm sorry, I was too quick to brag about finding the right solution

It worked the first couple of times and then stopped - it's totally messed up now! Never seizes to amaze me how they manage to turn something as easy as switching between various displays into such a nightmare!

What happens now is after I enable/disable the tv and tmds2i displays the resolutions are messed up and it won't allow me to go more than 1024x768. Besides that the picture on my monitor is positioned randomly each time, sometimes at the very top of the screen leaving me with a black portion covering more than 80% of the screen

One last thing I'd like to try before completely giving up again and waiting another year for things to get fixed up /this is my 3rd or 4th attempt for the last 5 years to switch to Linux/ would be to somehow store 2 copies of the amdpcsdb file - a working version for the TV and for the monitor and my script will then consist of overwriting the main file with the stored copies.
The question now becomes how to initiate an update of the settings without a reboot or X reset. I know this can be done, because amdccc does it, however it has no cmd line support


One thing I forgot to mention - I looked at the permissions and looks like the amdpcsdb is uneditable by anyone besides root. How come than the amdccc uitility manages to update it ?!

---

### Post by markbuntu on 2008-10-29
Did you use the autodetect function in CCC when the monitor and tv are both connected and turned on?
Did it correctly identify your tv amd monitor and give you choices for available resolutions?

Are you using the latest 8.10 driver?
There were some problems with tv detection in earlier drivers but that should be fixed now. Switching monitors off and on and changing them around too often can cause a crash with older drivers expecially if one of them is a tv but that too should be fixed.

Also, aticonfig should be run as root. It is not a user utility but an administrator utility. The user utility is CCC.

---

### Post by drelyn86 on 2008-10-29
try uninstalling and reinstalling fglrx with both monitors connected. Also check your resolution settings in Preferences and look for something that is double the width of each monitor. For example, I have both monitors at 1280x1024, so my resolution is set at 2560x1024.

---

### Post by latev on 2008-10-29
I sort of got it working for now.../I think/
For a complete explanation of what I've done so far see this post
[http://ubuntuforums.org/showthread.php?p=6059401#post6059401](http://ubuntuforums.org/showthread.php?p=6059401#post6059401)

The ccc utility identifies my attached displays properly and besides the annoying message each time asking me to reboot manages my screens ok. The problem with that is I cannot automate it, there's no way I can make a script using ccc, so it's totally useless for me. It also makes my TV going crazy for the 30 seconds during startup.

The aticonfig utility works for me without running it as root - at least for the switching between tv and monitor part. I'd prefer it running that way actually, so it doesn't modify my xorg file

Anyways thanks for the support guys, I'm moving on to solving issue No 3 out of 100 probably!

---

### Post by bernecky on 2008-11-01
I just installed the production release of Ubuntu 8.10, with the
fglrx proprietary drivers, as defined by Ubuntu - no trips to the
ATI web site needed.

Things work MUCH better than before, so I thank all the people
who made that possible.

I found the dual-head settings to be settable via amdcccle,
except that they disappear over a reboot. I've just tried
the "save session" trick described earlier in this thread,
but have not rebooted yet, so can't say if that works or not.

BTW, is aticonfig officially dead now?

---

### Post by latev on 2008-11-01
why should aticonfig be dead?! I think that's the main utility the other one is just for the kids to play with. Are you saying it's not included in ubuntu 8.10 ?!

Anyways I'm curious - do suspend/resume work on your machine after the update? Did they work before?

---

### Post by peakshysteria on 2008-11-01
I haven't myself upgraded yet. I'm still on 8.0.4.1 with a smooth working 8.9 version of the ATI driver. I haven't upgraded because I'm not to thrilled about breaking things (not sure what will happen to my current driver during an update). I still haven't connected my LCD tv to my pc so I can't really check if there is an overlay function in the ATI CCC like in windows. In my windows days I always used the overlay function. Then my better half could work on the pc while I kicked back on the couch watching my favorite shows from the very same machine (or vice versa). VLC was always hidden behind her browser (or other apps) but the overlay function always showed it's content fullscreen on the tv. If you find this option I recommend it since it by far is the best option (though I have my doubts if this option is available in linux yet for some strange reason. Absolutely the one and only thing I miss from the windows days).

---

### Post by Mike-dev-random on 2008-11-19
> **cjaeger said:**
> This worked for me: after using amdcccle to set the monitors the way I wanted them, I clicked "ok" to close amdcccle, and then went to System->Preferences->Screen Resolution, verified that it showed the resolution that I wanted, and clicked apply. This time, the settings survived an X restart.

I haven't had the patience yet to verify that this is reproducible.

This worked for me.  Settings were also retained after reboot.  Thanks!

---

### Post by ctardi on 2008-11-30
> This worked for me: after using amdcccle to set the monitors the way I wanted them, I clicked "ok" to close amdcccle, and then went to System->Preferences->Screen Resolution, verified that it showed the resolution that I wanted, and clicked apply. This time, the settings survived an X restart.

I haven't had the patience yet to verify that this is reproducible.
Worked for me as well, Thanks!

---

### Post by reverseninja on 2008-12-06
Same here, made my changes in the ATI CCC, then opened up screen resolution and hit save there and presto, it works.  Hello solution!  Thanks!

---

### Post by Ed Elmo on 2008-12-09
> **cjaeger said:**
> This worked for me: after using amdcccle to set the monitors the way I wanted them, I clicked "ok" to close amdcccle, and then went to System->Preferences->Screen Resolution, verified that it showed the resolution that I wanted, and clicked apply. This time, the settings survived an X restart.

I haven't had the patience yet to verify that this is reproducible.

It worked for me also. Thanks very much.

---

### Post by pfourtz on 2008-12-15
> **cjaeger said:**
> This worked for me: after using amdcccle to set the monitors the way I wanted them, I clicked "ok" to close amdcccle, and then went to System->Preferences->Screen Resolution, verified that it showed the resolution that I wanted, and clicked apply. This time, the settings survived an X restart.

I haven't had the patience yet to verify that this is reproducible.

Worked for me too. I had to change the resolution to a random In Sys Prefs value though, but after restarting X the dual screen was functioning properly.

Thanks a lot cjaeger!

---

### Post by BFG on 2009-03-19
> **cjaeger said:**
> This worked for me: after using amdcccle to set the monitors the way I wanted them, I clicked "ok" to close amdcccle, and then went to System->Preferences->Screen Resolution, verified that it showed the resolution that I wanted, and clicked apply. This time, the settings survived an X restart.



Also worked for me on 8.10

A true fix for amdcccle not saving on reboot. Many thanks.

It seems crazy that ATI can't do the save and simply doing the Ubuntu
System / Preferences / Screen Resolution.
and clicking "Apply" without changing anything, makes the amdcccle setting take.

Is this an ATI bug or by design?

---

### Post by Amaroq on 2011-01-13
I'd say it's bad design on Ubuntu's part. The ATI Catalyst Control Center works like a charm and saves settings when I use it on Windows. It's when I do it on Ubuntu that the settings don't take. And I've had so many problems with Ubuntu not properly supporting AMD's fglrx driver it's just not even funny anymore. Every time I upgrade X, bam! Broken display drivers, unusable system, because the new version of X doesn't support the already existing ATI fglrx driver anymore and ATI now has to create a new fglrx that works with it.

If the Ubuntu devs want to inconvenience those users of theirs who prefer to use proprietary graphics drivers, that's fine. If they -want- to force fglrx users to go for a month+ at a time without proprietary graphics every time X gets an upgrade, that's fine. But don't blame ATI for problems Ubuntu causes. I hate to see the blame go in the wrong direction.

But anyway, after I typed the above two paragraphs, I looked at the aticonfig's help text (aticonfig -h) and I think I found the answer.

The problem I was having is that monitor 2 is on the left side of monitor 1, but Ubuntu was treating my monitors as if 2 was to the right of 1. So it was really annoying that the settings I set in amdcccle (even with administrative permissions) were lost upon restarting or even upon opening programs in wine, and upon opening the monitors dialogue and hitting apply.

Here's what I did to fix it:
```
sudo aticonfig --initial=dual-head --screen-layout=left --xinerama=on --effective=startup
```

Obviously I wanted --screen-layout=left because my second monitor was to the left of my first. And I wanted xinerama on so I'd get two X's, one for each monitor, and so windows could be dragged across monitors. I think what may have made the difference was the --effective=startup flag. For those of you who have tried an aticonfig --initial and found that your settings weren't saved, try adding --effective=startup and see how that works. I didn't experiment without it, but it made my settings save through restarts, and now changes I make in amdcccle after I did this save through restarts as well.

---

### Post by setzergabbiani on 2011-02-22
I just experienced the same problem and discovered what was happening.

In fact, amdcccle was saving a Xorg.conf file, but it was saving the file on the folder that it was ran.
When I closed amdcccle I was at my home folder and saw many copies of xorg.conf (I rand amdcccle lots of times trying to discover why it wasn't saving my xorg.conf), so I deleted them all and just did cd /etx/X11 followed by a sudo amdcccle and everything worked :)

---

### Post by Noxa on 2011-10-25
Great [setzergabbiani]("http://ubuntuforums.org/member.php?u=499290"), that finally made it work in 11.10 :)
There's a typo though, it's cd /et**c**/X11.

---

