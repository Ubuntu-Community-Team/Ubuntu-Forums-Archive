---
title: "Latest round of updates borked my install..."
date: 2010-09-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by crjackson on 2010-09-13
Well it finally happened.  The latest round of updates has me running in low graphics mode now.  I'm not really sure which package or setting is the culprit just yet..

A reboot found my old ATI 9600 powered emachines notebook with vertical stripes on the screen.

---

### Post by ranch hand on 2010-09-13
I find this VERY interesting.  I just did this evenings updates on all my 10.10 installs and upgraded my throw away.

It is not screwed but the resolution is strange.  Stretched horizontally.  Not much but you can see it.

What is weird is that I came back here and pulled up synaptic to look at the packages again.  When I upgraded the throw away they looked pretty harmless.  Here I found only one package that appears to have to do with graphics, one I noticed and ignored on the throw away.

I ignored it because it is xserver-xorg-video-intel.  Like you, I am on ATI.  WTF?

---

### Post by crjackson on 2010-09-13
Well, I purged my x-swat PPA thinking a graphics package may have been pulled in from there, but it was a bust.  Still tinkering...

---

### Post by crjackson on 2010-09-13
Humm having no luck otherwise, and wanting to try the daily build...  I'm downloading now.

---

### Post by ranch hand on 2010-09-13
I need to look at the packages again.  The resolution on the monitor settings is what is screwed on mine and it is not the intel driver as it is the same on a second intall that did not get the driver update.

---

### Post by kansasnoob on 2010-09-13
How long had you gone between updates?

The only thing I saw recently from Xorg should have only effected Intel:

xserver-xorg-video-intel (2:2.12.0-1ubuntu3) to 2:2.12.0-1ubuntu4

Could you use the terminal, either through a chroot:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

or from booting into recovery mode and post the output of:

```
lspci | grep VGA
```

Maybe if we know the exact GPU info we can help figure something out :)

---

### Post by ronacc on 2010-09-13
just for info , I'm not seeing that here on my nvidia installs .

---

### Post by crjackson on 2010-09-13
Downloaded the daily and did a clean install.  All went well (except the crappy install dialogue and the slidshow talking about packages like F-Spot that are no longer included).  

Installed 72 updates and my it borked my install.  Running in low graphics mode again...

```
charles@charles-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
charles@charles-laptop:~$ 
```

---

### Post by ranch hand on 2010-09-13
I update twice a day.  I do not have the problem that crack has but something  messed with my screen res on two different installs.  

One had the intel update the other not.

Beats me hollow.

We are both on ATI, mine is a bunch newer than his.  I am on OSS drivers.

I think this has got to be related.

---

### Post by setherd on 2010-09-14
ATI x300 vid card here and I am screwed. when it should come to a login screen it's a blank white screen.
I can login to a virtual terminal but if I go back to ctrl-alt-f7 it locks everything up.


seth@seth-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]

---

### Post by crjackson on 2010-09-14
> **setherd said:**
> ATI x300 vid card here and I am screwed. when it should come to a login screen it's a blank white screen.
I can login to a virtual terminal but if I go back to ctrl-alt-f7 it locks everything up.


seth@seth-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]

boot into the recovery kernel and select fail-safe x / safe graphics mode.  You should be able to use your system until it's sorted out.

---

### Post by Reiger on 2010-09-14
Have you guys tried booting without KMS (radeon.modeset=0) ?

---

### Post by crjackson on 2010-09-14
> **Reiger said:**
> Have you guys tried booting without KMS (radeon.modeset=0) ?

I haven't tried that yet.

---

### Post by Kiek on 2010-09-15
I installed Xubuntu 10.10 on a laptop with a radeon RV350. KMS+X does not work for me. I have the nice VT switching, but starting X wont work.
Failsafe X does not work either.

I'll append the result of startx later

radeon.modeset=0 gives me an X desktop, but everything looks washed out and performance is bad.

[PHP]
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
[/PHP]

[PHP]
startx
X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.35-21-generic #31-Ubuntu SMP Mon Sep 13 22:39:43 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
Build Date: 08 September 2010  09:03:27AM
xorg-server 2:1.9.0-0ubuntu5 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep 15 16:20:51 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) VESA: Kernel modesetting driver in use, refusing to load
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
giving up.

xinit:  No such file or directory (errno 2):  unable to connect to X server

xinit:  No such process (errno 3):  Server error.

[/PHP]

---

### Post by karmila on 2010-09-15
I have this problem too, my screen became blurry after some updates (I don't know which one). I'm using nvidia.

Oh yes, I only use driver from repository. No beta driver.

---

### Post by tormod on 2010-09-15
Please make sure bug reports are filed. Use the ubuntu-bug command if you can.

---

### Post by karmila on 2010-09-15
Upgrading kernel and nvidia beta driver from ppa but still no luck.

---

### Post by karmila on 2010-09-15
> **tormod said:**
> Please make sure bug reports are filed. Use the ubuntu-bug command if you can.

Yes I want to, but I don't know which package that should filed for bug report.  :(

---

### Post by tormod on 2010-09-15
> **karmila said:**
> Yes I want to, but I don't know which package that should filed for bug report.  :(
ubuntu-bug helps you with that.

---

### Post by tormod on 2010-09-15
I just now tried today's daily CD on a Radeon X700 and there was no problem. It can be an upgrade issue. Can you please test a daily CD (using a USB stick of course :) ) To figure out what goes wrong, it is better if you have filed a bug since then all relevant log files will be attached.

---

### Post by up2early on 2010-09-15
Same issue here, blank white screen when it get to log in screen. If I hit enter, to open password box for default user, then type in the password, it properly loads. 

mike@mike-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]

---

### Post by VMC on 2010-09-15
> **up2early said:**
> Same issue here, blank white screen when it get to log in screen. If I hit enter, to open password box for default user, then type in the password, it properly loads. 

mike@mike-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]

When I had the "blank white screen", adding "radeon.nomodeset=0" fixed that issue.

---

### Post by up2early on 2010-09-15
> **VMC said:**
> When I had the "blank white screen", adding "radeon.nomodeset=0" fixed that issue.

Thanks alot for the help, but where is this added?

---

### Post by jerrylamos on 2010-09-15
> **up2early said:**
> Thanks alot for the help, but where is this added?
To try out, at the initial Grub boot screen enter
e
then go down to the line that starts
linux
at the end of the line it should say
quiet splash
change that to 
quiet radeon.modeset=0
then do
Ctrl-x

If that boots up O.K., then do 
sudo gedit /etc/default/grub
enter password
go to the line that says quiet splash
replace that with quiet radeon.modeset=0
save
sudo update-grub
then reboot....

Note I don't have any use for the splash screen.  It takes a little bit of processor time and offers no info. From time to time there's an X windows bug in splash besides.  Boot up is pretty quick anyway, just wait some seconds with a blank screen with a blinking cursor at top left.  If it is going to come up it will quickly.

Jerry

---

### Post by up2early on 2010-09-15
That did it! Thank's for everyone help.

---

### Post by crjackson on 2010-09-15
> **jerrylamos said:**
> To try out, at the initial Grub boot screen enter
e
then go down to the line that starts
linux
at the end of the line it should say
quiet splash
change that to 
quiet radeon.modeset=0
then do
Ctrl-x

If that boots up O.K., then do 
sudo gedit /etc/default/grub
enter password
go to the line that says quiet splash
replace that with quiet radeon.modeset=0
save
sudo update-grub
then reboot....

Note I don't have any use for the splash screen.  It takes a little bit of processor time and offers no info. From time to time there's an X windows bug in splash besides.  Boot up is pretty quick anyway, just wait some seconds with a blank screen with a blinking cursor at top left.  If it is going to come up it will quickly.

Jerry

Well, this got me to the new wallpaper and then a hard freeze with a mouse cursor showing (but not working).

Booted back into fail-safe and got updates.  No difference after updates with new xorg server core.

---

### Post by crjackson on 2010-09-15
> **up2early said:**
> Same issue here, blank white screen when it get to log in screen. If I hit enter, to open password box for default user, then type in the password, it properly loads. 

mike@mike-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]

This does nothing for me.

---

### Post by tormod on 2010-09-16
> **VMC said:**
> When I had the "blank white screen", adding "radeon.nomodeset=0" fixed that issue.

Ahem, that is not "fixing an issue" :) It is a workaround to get a working X, yes. But kernel modesetting (KMS) is supposed to work and we should make sure it works out of the box. Pretty soon, running without KMS will be considered not supported.

Has no one filed a bug report yet, really? Would be sad if 10.10 ships with this.

---

### Post by karmila on 2010-09-16
My problem is the same with ranch hand's.

I didn't get white strip on my screen or something that obvious but it just out of focus, blurry.

Yesterday, i tried to file a bug but then i canceled it because i didn't know the right word to explain this kind of bug. If somebody file the bug let me know and i will confirm it.

---

### Post by tormod on 2010-09-17
> **karmila said:**
> Yesterday, i tried to file a bug but then i canceled it because i didn't know the right word to explain this kind of bug.
If you have a digital camera, attaching a picture to the bug report can help a lot.

---

### Post by crjackson on 2010-09-17
I still can't boot.  Todays daily build still has the same problem with nothing but vertical stripes.  I'm starting to think I'll end up passing up this release.  I hope I'm wrong...

---

### Post by ktp on 2010-09-17
did you try removing your /etc/X11/xorg.conf if you have one to see if it boots with defaults?

---

### Post by crjackson on 2010-09-18
> **ktp said:**
> did you try removing your /etc/X11/xorg.conf if you have one to see if it boots with defaults?

Mine doesn't have one.  It's still screwed up even after the new kernel and updates.

---

### Post by crjackson on 2010-09-19
Maverick still now working on this machine.  I'm thinking of going back to 8.10 where I believe this video card is properly supported by the Proprietary driver from ATI.

I'd like to see some speed on this thing again.

---

### Post by tormod on 2010-09-19
> **crjackson said:**
> I'd like to see some speed on this thing again.To start, where are the bug reports?

---

### Post by crjackson on 2010-09-19
> **tormod said:**
> To start, where are the bug reports?

[Here]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/643118")

---

### Post by crjackson on 2010-09-19
Well, Gutsy Gibbon (7.10) list the proprietary driver in the Hardware Drivers (jockey-gtk) application so I'm leaning towards that version.  It's old but it should be quick.  Hardy didn't list the anything in jockey so I'm guessing that's when the driver stopped being supported.  For some reason though I thought it was supported thought 8.04 or 8.10 but I guess I was wrong.

---

### Post by 23meg on 2010-09-19
> **crjackson said:**
> Well, Gutsy Gibbon (7.10) list the proprietary driver in the Hardware Drivers (jockey-gtk) application so I'm leaning towards that version.  It's old but it should be quick.  Hardy didn't list the anything in jockey so I'm guessing that's when the driver stopped being supported.  For some reason though I thought it was supported thought 8.04 or 8.10 but I guess I was wrong.

I suggest troubleshooting your problem via some other means in a supported stable release if you can't get it to work with Maverick, since Ubuntu 7.10 has reached EOL and is unsupported.

---

### Post by crjackson on 2010-09-19
Well, I can't remember which release it was that I last used the proprietary driver, but it's been slow ever since then...

I can run Lucid but it's graphically slow.  Same goes for Karmic and Jaunty (although they are much faster than Lucid, but not even close to Gutsy).  I thought I had proprietary support through 8.10 (which would be great) but since it doesn't show up in jockey I guess I was wrong.  Same goes for 8.04.

Even if I get Maverick working, it's doubtful that my old video card will have any kind of pep like it did in 7.10.

---

### Post by jerrylamos on 2010-09-19
> **crjackson said:**
> I still can't boot.  Todays daily build still has the same problem with nothing but vertical stripes.  I'm starting to think I'll end up passing up this release.  I hope I'm wrong...
cjackson,

I haven't read all the posts, however have you tried on the boot grub screen doing
e
then move the cursor down to the linux line that ends in
quiet splash
and changing it to 
quiet radeon.modeset=0
then to boot do
Ctrl-x
You should get a black screen with blinking cursor at the top left for 10 or 20 seconds, then the screen should flicker, then presently a pointer appears followed by the gdm......

Works for me on my two ati machines from time to time depending on the state of the Ubuntu updates.

If it helps, then when booted do
sudo gedit /etc/default/grub
make the same change to the line with quiet splash to 
quiet radeon.modeset=0
save
quit
sudo update-grub
patience here
sudo reboot

Works for me sometimes when the Ubuntu ati driver is screwed up.  
splash sometimes causes trouble also

Jerry

---

### Post by crjackson on 2010-09-19
> **jerrylamos said:**
> cjackson,

I haven't read all the posts, however have you tried on the boot grub screen doing
e
then move the cursor down to the linux line that ends in
quiet splash
and changing it to 
quiet radeon.modeset=0
then to boot do
Ctrl-x
You should get a black screen with blinking cursor at the top left for 10 or 20 seconds, then the screen should flicker, then presently a pointer appears followed by the gdm......

Works for me on my two ati machines from time to time depending on the state of the Ubuntu updates.

If it helps, then when booted do
sudo gedit /etc/default/grub
make the same change to the line with quiet splash to 
quiet radeon.modeset=0
save
quit
sudo update-grub
patience here
sudo reboot

Works for me sometimes when the Ubuntu ati driver is screwed up.  
splash sometimes causes trouble also

Jerry

Yes I tried that, it didn't work for me,

---

### Post by crjackson on 2010-09-19
> **jerrylamos said:**
> cjackson,
Works for me sometimes when the Ubuntu ati driver is screwed up.  
splash sometimes causes trouble also

Jerry

If you have this issue can you confirm the [bug report]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/643118") so it will get some attention?

---

### Post by tormod on 2010-09-20
> **crjackson said:**
> If you have similar issues can you confirm the [bug report]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/643118") so it will get some attention?

If you have *similar* issues, please file a **new** bug! Only if you have the same chipset and the exact same symptoms you should comment on an existing bug. I believe this thread has accumulated a bunch of issues that are not related. Of course there is a chance there is one common underlying issue behind them but until that has been proved, we have to treat them individually.

---

### Post by jerrylamos on 2010-09-20
> **tormod said:**
> If you have *similar* issues, please file a **new** bug! 

tormod:

Yes, when I get a failures that will repeat and haven't killed Ubuntu too bad to get data, I file launchpad bugs. 

On occasion when someone posts having trouble I give suggestions on a workaround that has worked for me and others, and sometimes it is even of help to them.  I do post existing bug #'s for a problem if it seems to be applicable.  I didn't post any bug #'s here because I didn't see a match to the ati bugs (!) I've had.

Jerry

---

### Post by tormod on 2010-09-20
> **jerrylamos said:**
> tormod:

Yes, when I get a failures that will repeat and haven't killed Ubuntu too bad to get data, I file launchpad bugs. 

On occasion when someone posts having trouble I give suggestions on a workaround that has worked for me and others, and sometimes it is even of help to them.  I do post existing bug #'s for a problem if it seems to be applicable.  I didn't post any bug #'s here because I didn't see a match to the ati bugs (!) I've had.
Jerry, that's great and why we have the forums.

My comment was directed towards the guys here who experience troubles. They should not post on crjackson's bug report. Their own issues have to be reported.

If X does not work out-of-the-box in a clean installation or from a live CD, it is a issue that we should try to fix, at the best before 10.10 is released. If a recent update caused trouble for many people, it is a lot more serious issue, but this is hard to judge from a few forum comments.

---

### Post by tormod on 2010-09-20
> **setherd said:**
> ATI x300 vid card here and I am screwed. when it should come to a login screen it's a blank white screen.
I can login to a virtual terminal but if I go back to ctrl-alt-f7 it locks everything up.


seth@seth-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
Did this happen after updating mesa from 7.8 to 7.9? Can you please test the Beta CD (which has 7.8 ) and update libgl1-mesa-dri and libgl1-mesa-glx (plus whatever dependencies) on it?

---

### Post by tormod on 2010-09-20
General hint to everybody: /var/log/dpkg.log keeps track of all package updates so you can compare the timestamps in it with the day things broke.

---

### Post by crjackson on 2010-09-20
> **tormod said:**
> Did this happen after updating mesa from 7.8 to 7.9? Can you please test the Beta CD (which has 7.8 ) and update libgl1-mesa-dri and libgl1-mesa-glx (plus whatever dependencies) on it?

The Beta CD works fine with all the packages mentioned here upgraded.

---

### Post by crjackson on 2010-09-20
> **tormod said:**
> General hint to everybody: /var/log/dpkg.log keeps track of all package updates so you can compare the timestamps in it with the day things broke.

Thanks for this.  I'll be referring to this thought-out.

---

### Post by crjackson on 2010-09-20
I just did a clean install of the BETA with NO updates.  Tell how to proceed next to track this down.

There are 425 updates and a partial upgrade wanting to be installed.  I won't install anything until someone with more Savvy points me in the right direction to track this bugger down.

---

### Post by Rasa1111 on 2010-09-20
well,
 stay away from the "partial upgrade"
it will bork you good, (it did me, anyhow). lol

today was the first day i allowed any updates to go through since i reinstalled after partial upgrade borked me.. 

everything seems normal..
other than i have no sound now. :lol:

 Ive noticed a number of things a little 'off''..
maybe i should just make my own thread... lol

---

### Post by sdowney717 on 2010-09-20
if it is finally going on the beta, why not just wait till the final release to finish upgrading?

---

### Post by Rasa1111 on 2010-09-20
> **sdowney717 said:**
> if it is finally going on the beta, why not just wait till the final release to finish upgrading?

wise advice. <3

---

### Post by 23meg on 2010-09-20
> **sdowney717 said:**
> if it is finally going on the beta, why not just wait till the final release to finish upgrading?

> **Rasa1111 said:**
> wise advice. <3

Wise advice? The goal and whole point of this forum is to help people test and improve the development branch into the best final release possible; not to help them keep their installation working at all costs (that's what stable releases and other support forums are about). How do you expect the OP to do that without updating to the latest state of Maverick? 

That a two-week old milestone release is running fine doesn't mean there's nothing going wrong; two weeks is an eternity in Ubuntu development.

---

### Post by Rasa1111 on 2010-09-21
wise advice~
in that he finally got beta working again,
and if s[he] is not well versed in testing/submitting bugs, 
it just might be easier on them to test it, and not go above ones abilities to fix something, should something really go 'wrong'. 

Im not against "testing"..
 I am "testing" 10.10 myself for the first time testing a release before final. 

 I was just adding what I thought was good advice for n00bs. 
But like i said, Im also a noob in this, so if I was wrong, my apologies. 

 no harm meant dude.. lol

> That a two-week old milestone release is running fine doesn't mean there's nothing going wrong; two weeks is an eternity in Ubuntu development.

 Yeah, I understand that.
and have been keeping track of "my own bugs" i find. 
thanks.

---

### Post by ktp on 2010-09-21
and only reason op as gone back to beta is because he wants to find the bug, which broke his system after some upgrade.

I say, if you have /var/log/dpkg.log from old install, then make education guess based on the date and what was installed.  Either that or very slow and painful process or looking through each update's changelog and and see what was changed when.

---

### Post by tormod on 2010-09-21
> **crjackson said:**
> The Beta CD works fine with all the packages mentioned here upgraded.

The question was originally directed to setherd :)

Setherd, it would be good if you file a bug report, like crjackson did.

---

### Post by crjackson on 2010-09-26
Okay, had a family emergency and was away for a few days.  I had good instructions on getting logs to help track down the bugger.  When I got back I couldn't get anything to work. It would boot and I couldn't access the partition.  I can only guess one of the kids decided to help out while I was gone.

Bottom line...  I reinstalled the beta.  Then I started to install the updates in groups of 1-5 packages and rebooting EVERY time.  I finally found that installing the following 4 packages gave me the broken desktop that I though was caused by xorg.

```

Commit Log for Sun Sep 26 18:27:14 2010


Upgraded the following packages:
gnome-orca (2.31.90-0ubuntu1) to 2.31.92-0ubuntu1
gnome-power-manager (2.31.90-0ubuntu5) to 2.31.92-0ubunntu1
gnome-settings-daemon (2.30.2-0ubuntu5) to 2.31.92-0ubuntu1
gnome-sudoku (1:2.31.90-0ubuntu1) to 1:2.31.92-0ubuntu1

```

I have posted the information on launchpad in the bug report.  Now I just hoping someone can tell me (without starting all over again) how to determine the EXACT package causing the problem, and what action to take from there.

common sense tells me it's not gnome-sudoku so that would bring it down to three.  I'm guessing it's the gnome-settings-daemon or the gnome-power-manager.  

That's where I'm at with this for now...

---

### Post by ktp on 2010-09-26
You can look at the changelog for each version and also try to force install of older/newer version to see if fixes the issue:

[https://launchpad.net/ubuntu/maverick/+source/gnome-settings-daemon](https://launchpad.net/ubuntu/maverick/+source/gnome-settings-daemon)
[https://launchpad.net/ubuntu/maverick/+source/gnome-power-manager](https://launchpad.net/ubuntu/maverick/+source/gnome-power-manager)

---

### Post by crjackson on 2010-09-26
In synaptic, I went to packages>force version but I couldn't fine any other versions available.  How do I find the other versions to force so I can put my finger on the exact package?

Based on the change logs, I'm guessing the offending package is gnome-settings-daemon.  It makes many references to RANDR and display settings, so I think this must be the one.  Now if I can figure out how to take it back the version in the beta to confirm we'll have it nailed as the trouble maker.

---

### Post by ktp on 2010-09-26
I don't think you will be able to force it via synaptic. 

You can download the version for the links I posted before. Click the version you want, then pick the build arch (64-bit or 32-bit) and you should be able to download the deb for that version under "Built files".  You can use dpkg to install/downgrade it.  Probably not the best way but should work.

---

### Post by crjackson on 2010-09-28
As it turns out the buggy package is for sure the gnome-settings-daemon.  I wasn't able to make the broken install work properly by downloading a deb with a different version, but I was able to break an install simply by updating this package.

Further, another clean install of the beta and then version locking the gnome-settings-daemon kept it alive even after all other updates were applied.

I'm guessing I should file a new [**[COLOR="Blue"]bug report[/COLOR]**]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649534") on this package.

Thanks for all the help and advice.

---

### Post by ranch hand on 2010-09-28
All I can say is great work.  Your efforts may very well make this version better.

---

### Post by crjackson on 2010-09-28
> **ranch hand said:**
> All I can say is great work.  Your efforts may very well make this version better.

I hope it gets fixed before the release.  I've uploaded logs from both working and non-working installs.

It's working okay with the older version locked package right now, but if I didn't have a copy of the beta cd I wouldn't even be able to install from a live desktop. I haven't tried the alternate installer, that would probably work, and then I'd have to boot to a command line and install the older package to get a desktop.  It's a heck of a bug to have on an install cd.

---

### Post by ranch hand on 2010-09-28
You have to admit that is what makes testing so much FUN.

---

### Post by ktp on 2010-09-28
> **crjackson said:**
> As it turns out the buggy package is for sure the gnome-settings-daemon.

Nice...at least the bug is narrowed down to a package.  Lets hope dev can get this fixed ASAP.

> **ranch hand said:**
> You have to admit that is what makes testing so much FUN.

It sure does...at least for me.  It's even better when it's fixed. :)

---

### Post by crjackson on 2010-09-29
> **ranch hand said:**
> You have to admit that is what makes testing so much FUN.

Yup, and that's how "I" learn...

---

### Post by crjackson on 2010-09-29
> **ktp said:**
> Nice...at least the bug is narrowed down to a package.  Lets hope dev can get this fixed ASAP.



It sure does...at least for me.  It's even better when it's fixed. :)

I'm not really expecting it to be fixed in time.  At least I know how to work around it if I have to.

---

### Post by sdowney717 on 2010-09-29
What is different about your hardware than other systems which dont have this problem?

---

### Post by crjackson on 2010-09-29
> **sdowney717 said:**
> What is different about your hardware than other systems which dont have this problem?

It's older, it has a ATI Mobility Radeon 9600.  The bug has been pinned down to a change in the gnome-settings-daemon that triggers a bug in the radeon driver.

---

### Post by tormod on 2010-10-05
Thanks to crjackson's bug report, his and many other "wrong/broken resolution at startup" issues are going to be fixed, if not before the 10.10 release, soon thereafter. It turned out a number of more or less independent bugs built up to this:
[LIST=1]
[*]the X server sometimes adds a broken modes (but does not choose it)
[*]gnome-settings-daemon has its own way of choosing modes (sometimes not the preferred one of the X server, and therefore sometimes the broken one)
[*]a recent change in gnome-settings-daemon to always turn on external screens triggered g-s-d to reselect modes at startup
[/LIST]
and voilà...

So g-s-d will be fixed to let the X server's choice alone unless the user selects something else. Hopefully it can later be improved to make better choices as well, in accordance to the X server's preferred selection. Then obviously we have to fix the X server to not add broken modes, which can be really delicate stuff and may have to wait for "Natty".


EDIT: This bug was fixed in the package gnome-settings-daemon - 2.32.0-0ubuntu2

---

### Post by ktp on 2010-10-05
> **crjackson said:**
> It's older, it has a ATI Mobility Radeon 9600.  The bug has been pinned down to a change in the gnome-settings-daemon that triggers a bug in the radeon driver.

can you try the latest gnome-settings-daemon (2.32.0-0ubuntu2)?  I think this should fix your issue.  Since you were having similar issue with live cd, if I remember correctly, you might want to get tomorrows daily build and test it out.

---

