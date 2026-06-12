---
title: "Unfathomable default settings in Mythbuntu"
date: 2008-11-17
forum: Mythbuntu
---

### Post by mfearby on 2008-11-17
After using Mythbuntu seriously for several weeks now, I'm beginning to become quite frustrated with continuing amazement at default settings I'm finding - sometimes on a daily basis.

For example, just now I was both watching and recording a TV programme (that I had scheduled yesterday) and all was working fine. All of a sudden the screen begins to fade to black leaving just a white mouse pointer! Could it have been a blank screen saver? I adjusted the volume on my mceusb remote but the screen remained black, but I could still hear the audio. Not even clicking the mouse or pressing something on the keyboard would get around it. I ended up switching to my TV's internal digital tuner to keep watching it. Afterwards, I Ctrl-Alt-F1'd and did a shutdown -r. 

On reboot I found that it continued recording OK. So why is there apparently a screen saver set on a distribution whose sole purpose is to be a media center where one does not want the programme being viewed replaced faded out to black to save the screen? Having to change this yourself is just plain stupid for a media center. If anything, you should have to seek out and enable this crazy feature that belongs on desktop PCs.

Just briefly, other bizarre default values I've come across and had to fix myself after searching for solutions are as follows:

Volume up/down on my remote (mceusb) doesn't repeat like every other normal remote. You have to configure this yourself or keep pressing the button repeatedly to achieve the same result.

The shutdown command doesn't actually power off when you shutdown (that is, after you've found the option to at least show the shutdown/restart options when exiting MythTV). I had to change it to "sudo halt -p" to actually tell it to power off... "Yes, Exit and Shutdown" normally means just that. It doesn't mean go as far as a flashing cursor so that you have to open the TV cabinet to press the power switch.

Unless you edit the corresponding X config file using "sudo nano", adjusting the X resolution isn't remembered between reboots because the NVidia icon isn't started with root privileges off the xfce menu. Admittedly, this is a proprietary driver, but it is one offered to me by Mythbuntu. It should be plainly obvious that a screen-resolution changer's settings should be remembered between reboots, so why can't the file permissions be relaxed or the thing started as root? This is a media center, it's not a public kiosk machine that every man and his dog is going to be getting at.

IP details manually entered using the icon at the top-right of the screen aren't retained during reboots. It will set an IP for the current user's login, but it won't retain it. Again, why should one have to keep entering the IP for a media center that should be so "set and forget"?

I'm not at the stage where I regret formatting Vista, but I have to say that I'm having to intervene with Mythbuntu just as much as I had to with Vista, and that's not exactly what I expected from the Linux community. If Mythbuntu keeps presenting me with stupid surprises, I may just have to bite the bullet and sell myself back to Microsoft, and nobody wants that.

Please.... use some sane defaults in the next release.

thanks

---

### Post by uncle hammy on 2008-11-17
> **mfearby said:**
> For example, just now I was both watching and recording a TV programme (that I had scheduled yesterday) and all was working fine. All of a sudden the screen begins to fade to black leaving just a white mouse pointer! Could it have been a blank screen saver? I adjusted the volume on my mceusb remote but the screen remained black, but I could still hear the audio. Not even clicking the mouse or pressing something on the keyboard would get around it. I ended up switching to my TV's internal digital tuner to keep watching it. Afterwards, I Ctrl-Alt-F1'd and did a shutdown -r. 

On reboot I found that it continued recording OK. So why is there apparently a screen saver set on a distribution whose sole purpose is to be a media center where one does not want the programme being viewed replaced faded out to black to save the screen? Having to change this yourself is just plain stupid for a media center. If anything, you should have to seek out and enable this crazy feature that belongs on desktop PCs.

I have yet to have the screen saver kick in on my machine anytime other than after true inactivity.  I have never had it kick in during any viewing.

> Volume up/down on my remote (mceusb) doesn't repeat like every other normal remote. You have to configure this yourself or keep pressing the button repeatedly to achieve the same result.

Volume up/down is simply a key stroke emulation that when used elsewhere, a repeating behavior would be very undesirable.  You want it to repeat, many don't...who's correct?

> The shutdown command doesn't actually power off when you shutdown (that is, after you've found the option to at least show the shutdown/restart options when exiting MythTV). I had to change it to "sudo halt -p" to actually tell it to power off... "Yes, Exit and Shutdown" normally means just that. It doesn't mean go as far as a flashing cursor so that you have to open the TV cabinet to press the power switch.
Yes, Exit and Shutdown has always worked for me with no extra configuration on my frontends.  The options is not available by default on backends...who wants to accidentally shut down their backends?

> Unless you edit the corresponding X config file using "sudo nano", adjusting the X resolution isn't remembered between reboots because the NVidia icon isn't started with root privileges off the xfce menu. Admittedly, this is a proprietary driver, but it is one offered to me by Mythbuntu. It should be plainly obvious that a screen-resolution changer's settings should be remembered between reboots, so why can't the file permissions be relaxed or the thing started as root? This is a media center, it's not a public kiosk machine that every man and his dog is going to be getting at.

Agree wholeheartedly on this one.  It almost seems criminal to have to manually edit a config file for screen settings in this day and age.

> IP details manually entered using the icon at the top-right of the screen aren't retained during reboots. It will set an IP for the current user's login, but it won't retain it. Again, why should one have to keep entering the IP for a media center that should be so "set and forget"?
Don't know what version of Mythbuntu you're using, but in 8.10 with Network Manager 0.70, this is apparently a bug that the manager doesn't seem to save any settings that are applied to it. [http://ubuntuforums.org/showthread.php?t=969873](http://ubuntuforums.org/showthread.php?t=969873)

---

### Post by ghuber on 2008-11-17
The screen saver I think is a bug.  I've been using Mythbuntu since 7.10 and have never had it not come out of screen saver mode.  I am currently running 8.10 and I paused a TV show and had it fade to black with just the mouse showing.  It would NOT wake up.  I Hit play on the remote.  hit exit.  Grabbed the keyboard hit keys, moved the mouse.  Nothing would wake it up.  Rebooted.

I don't know what the cause of this is or how to reproduce it.  It has only happened once in the last week but it happened just like on your machine.

:confused:

Geoff

---

### Post by superm1 on 2008-11-17
> 
Agree wholeheartedly on this one.  It almost seems criminal to have to manually edit a config file for screen settings in this day and age.

Please file a bug against the nvidia-settings package to include a wrapper script that launches it as root.

If you launch it out of MCC, it will launch as root already.

---

### Post by mfearby on 2008-11-17
> **uncle hammy said:**
> I have yet to have the screen saver kick in on my machine anytime other than after true inactivity.  I have never had it kick in during any viewing.

I guess what I'm getting at is that the screen saver should be disabled by default. A screen saver interrupting TV viewing is just silly.

> **uncle hammy said:**
> Volume up/down is simply a key stroke emulation that when used elsewhere, a repeating behavior would be very undesirable.  You want it to repeat, many don't...who's correct?

With proper values, like delay, it can be set to repeat after a typical period of time, like every other volume button on a remote control known to man. The whole point of a Mythbuntu installation is to get a media center. Usage of a media center typically involves adjusting the volume a lot more than whatever other use there is for the volume buttons.

> **uncle hammy said:**
> Yes, Exit and Shutdown has always worked for me with no extra configuration on my frontends.  The options is not available by default on backends...who wants to accidentally shut down their backends?

On my install I had to add the -p to actually get it to power down. Maybe my Gigabyte G31MX-S2 mobo is a little strange, but if a -p didn't adversely affect other people, then it may as well be included by default. In my case I have a combined backend and frontend, so in this situation, the shutdown options should be made available. I would suggest this would be where most people start out using MythTV.

> **uncle hammy said:**
> Agree wholeheartedly on this one.  It almost seems criminal to have to manually edit a config file for screen settings in this day and age.

I hope this is just sarcasm. If not, then Mythbuntu is seen as one of the leading MythTV distros and I expected most things to be easy.

> **uncle hammy said:**
> Don't know what version of Mythbuntu you're using, but in 8.10 with Network Manager 0.70, this is apparently a bug that the manager doesn't seem to save any settings that are applied to it. [http://ubuntuforums.org/showthread.php?t=969873](http://ubuntuforums.org/showthread.php?t=969873)

I'm using 8.10 with updates as of 24 hours ago. I did find a network program (community maintained) in Synaptic that allows me to enter values that are retained (though it has lost my DNS settings at least once already).

---

### Post by superm1 on 2008-11-17
> **mfearby said:**
> I guess what I'm getting at is that the screen saver should be disabled by default. A screen saver interrupting TV viewing is just silly.

It should never interrupt your tv viewing.  Only menus and paused TV.  Have you added any applications to your install?  There are a few known ways to break this, but I'd like to hear what you've done differently.


> 
With proper values, like delay, it can be set to repeat after a typical period of time, like every other volume button on a remote control known to man. The whole point of a Mythbuntu installation is to get a media center. Usage of a media center typically involves adjusting the volume a lot more than whatever other use there is for the volume buttons.
File a bug against mythbuntu-lirc-generator attaching the lircrc that you saw better and explain it.  We'll see what's doable.

> 
On my install I had to add the -p to actually get it to power down. Maybe my Gigabyte G31MX-S2 mobo is a little strange, but if a -p didn't adversely affect other people, then it may as well be included by default. In my case I have a combined backend and frontend, so in this situation, the shutdown options should be made available. I would suggest this would be where most people start out using MythTV.
Use the hal script to shutdown:
/usr/share/mythtv/myth-halt.sh

It's set as the default behavior for shutting down your system from the mythtv menu itself.


> 
I hope this is just sarcasm. If not, then Mythbuntu is seen as one of the leading MythTV distros and I expected most things to be easy.
Look, this is just a bug with nvidia-settings that wasn't reported.  It was tested via launching nvidia-settings via mcc which launches as root.  File the bug on nvidia-settings and it can get fixed.

[http://bugs.launchpad.net/ubuntu/+source/nvidia-settings]("http://launchpad.net/ubuntu/+source/nvidia-settings")

--------------

The constructive feedback is most appreciated.  When you come across bugs, make sure developers are made aware.  It's difficult to go through hundreds of posts to sort out bugs that people are having versus complaints or praises.  This is why it's most effective to get the bugs on the bug trackers.

---

### Post by laga on 2008-11-20
Regarding the screen saver:

It is useful to blank the screen after a certain amount of inactivity to prevent burn-in on plasma screens etc. The screen saver will only kick in in the menus or when video is paused. If that doesn't work or if it doesn't come back when pushing a button on the remote, then that's a bug.

---

### Post by mfearby on 2008-11-21
> **ghuber said:**
> The screen saver I think is a bug.  I've been using Mythbuntu since 7.10 and have never had it not come out of screen saver mode.  I am currently running 8.10 and I paused a TV show and had it fade to black with just the mouse showing.  It would NOT wake up.  I Hit play on the remote.  hit exit.  Grabbed the keyboard hit keys, moved the mouse.  Nothing would wake it up.  Rebooted.

I don't know what the cause of this is or how to reproduce it.  It has only happened once in the last week but it happened just like on your machine.

:confused:

Geoff

Sometimes just knowing that the problem is on somebody else's system at least makes me realise I haven't done anything strange.

---

### Post by mfearby on 2008-11-21
> **superm1 said:**
> It should never interrupt your tv viewing.  Only menus and paused TV.  Have you added any applications to your install?  There are a few known ways to break this, but I'd like to hear what you've done differently.

The only software I've installed is to enable the "Ubuntu Desktop" role in MCC, install Konversation, and to install the gnome network settings manager since the one at the top-right of the screen doesn't remember the IP I enter.

> **superm1 said:**
> Use the hal script to shutdown:
/usr/share/mythtv/myth-halt.sh

It's set as the default behavior for shutting down your system from the mythtv menu itself.

Do you mean the XFCE "Applications > Quit" menu? Because the default option when using the exiting-with-shutdown option from the MythTV frontend is to just run "halt"

---

### Post by superm1 on 2008-11-21
> **mfearby said:**
> The only software I've installed is to enable the "Ubuntu Desktop" role in MCC, install Konversation, and to install the gnome network settings manager since the one at the top-right of the screen doesn't remember the IP I enter.

Well nothing in there should have broken it...Are you logging into a gnome or an xfce session when it happens?


> 
Do you mean the XFCE "Applications > Quit" menu? Because the default option when using the exiting-with-shutdown option from the MythTV frontend is to just run "halt"
If this is a "new" master backend install, and the default for your mythtv shutdown menu option is halt, that's a bug.  Please file it against the mythtv package.

---

### Post by mfearby on 2008-11-21
> **superm1 said:**
> Look, this is just a bug with nvidia-settings that wasn't reported.  It was tested via launching nvidia-settings via mcc which launches as root.  File the bug on nvidia-settings and it can get fixed.

[http://bugs.launchpad.net/ubuntu/+source/nvidia-settings]("http://launchpad.net/ubuntu/+source/nvidia-settings")

Somebody already [filed it]("https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/200868") as a bug, it seems.

---

### Post by Caps18 on 2008-11-21
I'm not a  big fan of the screen saver either.  Or at least make it something that people have to turn on.  It was easy to turn off, but I changed my display settings and it's back on again.  It still works fine, but it is a little annoying.  

I have my system running all the time, but turn off the monitor.  When I turn on the monitor, I would like to see the menu, not a black screen until I hit a button.

---

### Post by tgm4883 on 2008-11-21
> **Caps18 said:**
> I'm not a  big fan of the screen saver either.  Or at least make it something that people have to turn on.  It was easy to turn off, but I changed my display settings and it's back on again.  It still works fine, but it is a little annoying.  

I have my system running all the time, but turn off the monitor.  When I turn on the monitor, I would like to see the menu, not a black screen until I hit a button.

You would be in the minority then.  Most prefer to have it the other way.  The old saying "better safe than sorry" applies here.  I'd rather have the default setting annoy a few users and save someones TV rather than make you happy and cause someone burn-in.

To the OP, the default for shutdown is that if the backend in installed, then to make it harder to completely shutdown the system.  The reason for this is that your scheduled recordings won't record if your machine is off.  This is easily fixed by changing a setting in the frontend menu.  As to your complaint about why is there a screen saver on a distro whose primary function is a media center?  Well I think what sums that up the best is this quote "The only software I've installed is to enable the "Ubuntu Desktop" role in MCC"  If you want the system to be a media center why are you installing Ubuntu Desktop?

---

### Post by mfearby on 2008-11-22
> **tgm4883 said:**
> To the OP, the default for shutdown is that if the backend in installed, then to make it harder to completely shutdown the system.  The reason for this is that your scheduled recordings won't record if your machine is off.  This is easily fixed by changing a setting in the frontend menu.  As to your complaint about why is there a screen saver on a distro whose primary function is a media center?  Well I think what sums that up the best is this quote "The only software I've installed is to enable the "Ubuntu Desktop" role in MCC"  If you want the system to be a media center why are you installing Ubuntu Desktop?

I installed the Ubuntu Desktop role in the hope that I might get some more items on the XFCE menu -i.e., more system-configuration type things. I'm not an Ubuntu user (my main desktop is Mandriva where the Mandriva Control Center is pretty darn nice) so I assumed this might give me some more GUIs for doing common system administration type things. I was mistaken.

---

### Post by mfearby on 2008-11-22
> **Caps18 said:**
> I'm not a  big fan of the screen saver either.  Or at least make it something that people have to turn on.  It was easy to turn off, but I changed my display settings and it's back on again.  It still works fine, but it is a little annoying.  

I have my system running all the time, but turn off the monitor.  When I turn on the monitor, I would like to see the menu, not a black screen until I hit a button.

Maybe, instead of a black screen, they could have some sort of Mythbuntu logo moving around the screen, in 5-second increments between positions, like a lot of TVs seem to do.

---

### Post by tgm4883 on 2008-11-22
> **mfearby said:**
> I installed the Ubuntu Desktop role in the hope that I might get some more items on the XFCE menu -i.e., more system-configuration type things. I'm not an Ubuntu user (my main desktop is Mandriva where the Mandriva Control Center is pretty darn nice) so I assumed this might give me some more GUIs for doing common system administration type things. I was mistaken.

Well when you install a metapackage like Ubuntu-Desktop, it pulls in lots of things and that is where the screensaver and dpms settings probably got overridden.  

You already have the Mythbuntu Control Centre as well as the XFCE control panel installed, what system administration things are you trying to do?

---

### Post by mfearby on 2008-11-22
> **tgm4883 said:**
> Well when you install a metapackage like Ubuntu-Desktop, it pulls in lots of things and that is where the screensaver and dpms settings probably got overridden.  

You already have the Mythbuntu Control Centre as well as the XFCE control panel installed, what system administration things are you trying to do?

I wanted to see if I'd get a program to check the firewall as well as Samba shares. I keep getting strange "NTFS tree disconnect" errors when using smbclient to mount shares on my Mythbuntu machine. I was also hoping to get a GUI to manage my IP address since the network icon at the top-right ignores what I enter. In the end, enabling Ubuntu Desktop didn't give me a network GUI; I had to install gnome-network or something like that (from memory).

---

### Post by tgm4883 on 2008-11-22
> **mfearby said:**
> I wanted to see if I'd get a program to check the firewall as well as Samba shares. I keep getting strange "NTFS tree disconnect" errors when using smbclient to mount shares on my Mythbuntu machine. I was also hoping to get a GUI to manage my IP address since the network icon at the top-right ignores what I enter. In the end, enabling Ubuntu Desktop didn't give me a network GUI; I had to install gnome-network or something like that (from memory).

I know what you are trying to do.  My point is that before you rant about "Unfathomable default settings in Mythbuntu", think for a minute that it might actually be something that you did that caused it.

---

### Post by mfearby on 2008-11-30
> **tgm4883 said:**
> I know what you are trying to do.  My point is that before you rant about "Unfathomable default settings in Mythbuntu", think for a minute that it might actually be something that you did that caused it.

Mea culpa. I confess :-)

---

### Post by maniaq on 2009-04-02
I'm totally with you!

I've had this thing running for about a week now and I'm pulling my hair out over these crappy Mythbuntu settings.

To think I broke a perfectly functioning KDE and installed something so useless and counterproductive - just because it had "myth" in front of the name...

I figured better have something lightweight for a quick bootup (my DVR boots up in 9 seconds) and I don't really need something as meaty as KDE but damned if this aint so much worse - mythPOS if you ask me!

---

### Post by tgm4883 on 2009-04-02
> **maniaq said:**
> I'm totally with you!

I've had this thing running for about a week now and I'm pulling my hair out over these crappy Mythbuntu settings.

To think I broke a perfectly functioning KDE and installed something so useless and counterproductive - just because it had "myth" in front of the name...

I figured better have something lightweight for a quick bootup (my DVR boots up in 9 seconds) and I don't really need something as meaty as KDE but damned if this aint so much worse - mythPOS if you ask me!

Well thats constructive.

---

