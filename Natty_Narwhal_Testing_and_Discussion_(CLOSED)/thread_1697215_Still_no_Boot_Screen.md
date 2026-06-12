---
title: "Still no Boot Screen"
date: 2011-02-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jennybrew on 2011-02-28
Is anyone else still without a boot screen ?
All I am currently getting is a blank, black, screen. Prior to today's updates the blank screen was purple coloured!
Even more worrying, **especially for a test  / alpha system,** is the total lack of feedback during boot. Surely, if its not currently possible to show the Ubuntu screen, an hour glass or similar could show?

---

### Post by PaulW2U on 2011-02-28
> **jennybrew said:**
> Is anyone else still without a boot screen ?
All I am currently getting is a blank, black, screen. Prior to today's updates the blank screen was purple coloured!
I'm not seeing a consistent boot screen. Sometimes it's just a blank screen prior to the logon screen. At other times it's "Ubuntu 11.04" in small text on a background of the correct colour. At other times I see that text on a bright purple background followed by text scattered over the upper half of the screen. I'm leaving it a while before I try to submit a bug report.

---

### Post by cariboo on 2011-02-28
I'm seeing a boot screen with nvidia-current and Intel i915 here. It's only there for a very short while on the nvidia system. If I remember correctly only the first two dots change color.

---

### Post by Harry33 on 2011-02-28
> **jennybrew said:**
> Is anyone else still without a boot screen ?
All I am currently getting is a blank, black, screen. Prior to today's updates the blank screen was purple coloured!
Even more worrying, **especially for a test  / alpha system,** is the total lack of feedback during boot. Surely, if its not currently possible to show the Ubuntu screen, an hour glass or similar could show?

You should tell us a bit of your setup.
Like:
- graphics card model and the driver used?
- any extra PPA's in sources.list?
- is your setup fully upgraded/updated?

---

### Post by afoglia on 2011-02-28
I too often do not get a usplash screen.  Unfortunately, more often now, it's not booting at all.  I'm running a Core i5 with integrated graphics and the laptop has an discrete ATI Radeon HD 5650 as well.  The corresponding kernel modules are i915 and radeon.  I'm using the integrated graphics.

---

### Post by garvinrick4 on 2011-02-28
> **jennybrew said:**
> Is anyone else still without a boot screen ?
All I am currently getting is a blank, black, screen. Prior to today's updates the blank screen was purple coloured!
Even more worrying, **especially for a test  / alpha system,** is the total lack of feedback during boot. Surely, if its not currently possible to show the Ubuntu screen, an hour glass or similar could show?
Are your graphic drivers hitting before mountall?
```
sudo -i
```
```
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash 
update-initramfs -u 
```
```
exit
```
```
sudo reboot
```

---

### Post by Harry33 on 2011-03-01
> **afoglia said:**
> I too often do not get a usplash screen.  Unfortunately, more often now, it's not booting at all.  I'm running a Core i5 with integrated graphics and the laptop has an discrete ATI Radeon HD 5650 as well.  The corresponding kernel modules are i915 and radeon.  I'm using the integrated graphics.

Actually usplash was used with Karmic, after that Plymouth has been in use instead.

---

### Post by teachop on 2011-03-01
Honestly, I have not seen a completely functioning boot screen in Ubuntu for a year, and that is on a number of different hardware platforms.  The only time I see it work is booting on a Live CD.  It does no harm, and I just figure it will sort out eventually.

---

### Post by jennybrew on 2011-03-01
Garvinrick4:
Thats exactly the thought I had initially but, unfortunately,that doesnt seem to be the cause.
 
I believe the culprit is a package known as Plymouth which has proved a problem for
up to 50 % of systems on various distros.
 
However, I am surprised it is giving problems on this test machine which also runs
 10.04 and 10.10, both of which use Plymouth, without any problems.
 
I can only surmise there has been a significant change to the Plymouth package for 11.04.
 
Perhaps someone could confirm this is the case.
 
Harry33: Thanks for the reply but you seem to have not to have read my post properly.
Your answers are always helpful 
 
Many Thanks

---

### Post by afoglia on 2011-03-01
> **Harry33 said:**
> Actually usplash was used with Karmic, after that Plymouth has been in use instead.

Sorry.  I've been using linux and Debian/Ubuntu for so long, it's hard to keep track of the changes, especially the purely cosmetic ones.

> **jennybrew said:**
> Garvinrick4:
Thats exactly the thought I had initially but, unfortunately,that doesnt seem to be the cause.
 
I believe the culprit is a package known as Plymouth which has proved a problem for
up to 50 % of systems on various distros.
 
However, I am surprised it is giving problems on this test machine which also runs
 10.04 and 10.10, both of which use Plymouth, without any problems.
 
I can only surmise there has been a significant change to the Plymouth package for 11.04.

I don't think it's plymouth.  I still have problems booting in the recovery mode, which, if it's anything like it was in the usplash days, won't hide the boot messages with a pretty picture.  Also, judging by the version numbers, there hasn't been any major changes to plymouth.  It's based off the same debian package, albeit with a bunch more ubuntu patches.

In my case I'm nearly certain it's a ATI driver issue, at least in my case.  AT least that's the impression I get from [the thread I started]("http://ubuntuforums.org/showthread.php?p=10508131").

---

### Post by jennybrew on 2011-03-01
This is all very interesting but doesnt address the reason why on a single machine (mine)

Ubuntu 10.04 shows the splash screen properly ..this is Plymouth

Ubuntu 10.10 shows the splash screen properly ... this is Plymouth

Ubuntu 11.04 does not show the splash screen and also shows no user feedback during the boot process.

Has the ATI driver changed between 10.10 and 11.04?

Has Plymouth changed between 10.10 and 11.04?

---

### Post by afoglia on 2011-03-01
> **jennybrew said:**
> This is all very interesting but doesnt address the reason why on a single machine (mine)

Ubuntu 10.04 shows the splash screen properly ..this is Plymouth

Ubuntu 10.10 shows the splash screen properly ... this is Plymouth

Ubuntu 11.04 does not show the splash screen and also shows no user feedback during the boot process.

I had the exact same experience on my laptop.

> Has the ATI driver changed between 10.10 and 11.04?

Yes.  From 1:6.13.1-1ubuntu5 to 1:6.14.0-0ubuntu2.  There was a new upstream release.

> Has Plymouth changed between 10.10 and 11.04?

Yes.  From 0.8.2-2ubuntu5 to 0.8.2-2ubuntu17.  So there were ~12 changes made by the Ubuntu packagers.  Here is the [changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/p/plymouth/plymouth_0.8.2-2ubuntu17/changelog").  I'm not familiar enough with plymouth to know if any of them are big changes.

Your error might not be related to mine.  What videocard do you have?  Is it relatively new, or older and likely to have better support?  If it's an older card, or better supported one, you're probably right.

---

### Post by Kirk M on 2011-03-02
Here's my experience with no (Plymouth) boot screen since I installed Alpha 2 (see signature for PC specs):


[LIST]
[*]Saw no boot screen after initial install of Natty, just blinking cursor until login screen.
[*]Installed updates, rebooted, still only blinking cursor during boot until login.
[*]Installed "Recommended" Nvida driver (270.29)-- no change during boot up. Same as above.
[*]Installed "Startup Manager" and set boot splash to 1024x768 @24 bit color.
[*]Blank screen during boot up for approx 5-7 seconds (no blinking cursor this time), Plymouth boot screen flashed up for approx 2 seconds then screen went blank for approx 1 sec and the login screen appeared.
[/LIST]
Overall boot times to Login screen don't vary (quite fast actually--nice!) no matter what changes I make. So Natty is still in the alpha stage? And there's weirdness going on? How terribly unusual. :lolflag:

---

### Post by Harry33 on 2011-03-02
> **Kirk M said:**
> Here's my experience with no (Plymouth) boot screen since I installed Alpha 2 (see signature for PC specs):
...
:

Kirk, you are still able to boot completely to gdm and X. :D
The issue is that you did not actually see plymouth graphics during post grub phase.
I can tell that is not so uncommon at all during these alfa days.

I have one Intel setup, where I rarely see Plymouth during boot, but I see Plymouth during every shut down. Plymouth is also seen after updates that trigger initscript, but only during the first (slow) boot. What I do see on every boot, however, is the grub background.

Then, I have one ATI setup where I always see Plymouth, but only for ~1 sec or so, otherwise grub backround.

In my NVidia setup I see Plymouth for ~2 secs immediately after grub background, but the whole booting process is very fast, only a bit over 10 secs from grub to X (with autologin enabled).

---

### Post by jennybrew on 2011-03-02
> **Kirk M said:**
> 
So Natty is still in the alpha stage? And there's weirdness going on? How terribly unusual. :lolflag:

Given that sort of patronising response Im less and less certain of the wisdom of posting anything at all on these forums.
But here goes:
My motive for starting the thread was to ascertain if the problem is due to a bug or whether its simply down to current progress. If the former is the case it needs to be reported as such. If the latter, then it doesn't need reporting.

Clearly thats worth a sarcastic comment.     * sigh* 


It also seems as if some of today's posts (not mine) have been removed. I thought Harry33 and Afoglia are both helpful posters. ...: ..
 Edit:  I can see what you have done Cariboo ... makes sense :)

---

### Post by cariboo on 2011-03-02
I merged those post with afoglia's other two threads, as they had nothing to do with this thread, they were about afoglia's inabiltiy to boot in recovey mode or to boot at all. They are still available [here]("http://ubuntuforums.org/showthread.php?t=1696890")

---

### Post by Kirk M on 2011-03-02
> **Harry33 said:**
> Kirk, you are still able to boot completely to gdm and X. :D
The issue is that you did not actually see plymouth graphics during post grub phase.
I can tell that is not so uncommon at all during these alfa days.

I have one Intel setup, where I rarely see Plymouth during boot, but I see Plymouth during every shut down. Plymouth is also seen after updates that trigger initscript, but only during the first (slow) boot. What I do see on every boot, however, is the grub background.

Then, I have one ATI setup where I always see Plymouth, but only for ~1 sec or so, otherwise grub backround.

In my NVidia setup I see Plymouth for ~2 secs immediately after grub background, but the whole booting process is very fast, only a bit over 10 secs from grub to X (with autologin enabled).

Pretty much similar experiences. No complaints whatsoever at this stage, just reporting my particular experience since no one has the exact same hardware setup the more experiences that are posted about a certain problem the better.

---

### Post by Kirk M on 2011-03-02
> **jennybrew said:**
> Given that sort of patronising response Im less and less certain of the wisdom of posting anything at all on these forums.
But here goes:
My motive for starting the thread was to ascertain if the problem is due to a bug or whether its simply down to current progress. If the former is the case it needs to be reported as such. If the latter, then it doesn't need reporting.

Clearly thats worth a sarcastic comment.     * sigh* 


It also seems as if some of today's posts (not mine) have been removed. I thought Harry33 and Afoglia are both helpful posters. ...: ..
 Edit:  I can see what you have done Cariboo ... makes sense :)

My apologizes, I did not mean that last bit of my post as sarcastic or patronizing. Please forgive an old software tester/geek his sense of humor. :oops:

---

### Post by afoglia on 2011-03-03
> **jennybrew said:**
> My motive for starting the thread was to ascertain if the problem is due to a bug or whether its simply down to current progress. If the former is the case it needs to be reported as such. If the latter, then it doesn't need reporting.

[...]

It also seems as if some of today's posts (not mine) have been removed. I thought Harry33 and Afoglia are both helpful posters. ...: ..
 Edit:  I can see what you have done Cariboo ... makes sense :)

I'm fine with Cariboo moving of my posts out, especially since I fear our bugs are different.  (I still think my boot is too long, and I have boot screen/plymouth issues, but I have bigger problems that the former might merely be a symptom of.)

Anyway, trying to offer some help on your problem...

Looking at [your boot chart]("http://ubuntuforums.org/showpost.php?p=10440613&postcount=12"), your boot is taking longer than most, probably because the read rate is much slower than others.  How old is your computer?  Is your boot drive SATA or PATA?

This won't solve why there's no boot screen, but it might alleviate the problem.

And on the off chance it is related to mine problem, what kernel and driver version are you using?  Do you have any other kernel versions installed?

---

### Post by Kirk M on 2011-03-04
I was checking my system logs today in the "Log viewer" and I found this bit towards the end of todays initial boot up of Natty.

```
Mar  4 16:03:53 Natty-679-DX4822 gdm-simple-slave[1186]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Mar  4 16:03:53 Natty-679-DX4822 acpid: client connected from 1189[0:0]
Mar  4 16:03:53 Natty-679-DX4822 acpid: 1 client rule loaded
Mar  4 16:03:54 Natty-679-DX4822 acpid: client connected from 1189[0:0]
Mar  4 16:03:54 Natty-679-DX4822 acpid: 1 client rule loaded
Mar  4 16:03:55 Natty-679-DX4822 gnome-session[1213]: WARNING: Could not launch application 'libcanberra-ready-sound.desktop': Unable to start application: Failed to execute child process "/usr/bin/canberra-gtk-play" (No such file or directory)
Mar  4 16:03:55 Natty-679-DX4822 gdm-session-worker[1236]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Mar  4 16:03:56 Natty-679-DX4822 gdm-simple-greeter[1233]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.1/gtk/gtkwidget.c:5687: widget not within a GtkWindow
```(**Note:** *Everything before this was the usual hardware initializations you might see during boot up. This is the only  section that I thought might be related tro Plymouth.*) 

Now I haven't had time to look deeply into this but perhaps someone else might find a clue in this somewhere as to the lack of a Plymouth boot screen? By the way. Sound works okay and the login screen is correct. It's during the normal boot up that the screen is blank for several seconds, then about 2 secs worth of Plymouth and then the login screen appears.

---

### Post by Harry33 on 2011-03-04
> **Kirk M said:**
> I was checking my system logs today in the "Log viewer" and I found this bit towards the end of todays initial boot up of Natty.

```

...
Mar  4 16:03:55 Natty-679-DX4822 gnome-session[1213]: WARNING: Could not launch application 'libcanberra-ready-sound.desktop': Unable to start application: Failed to execute child process "/usr/bin/canberra-gtk-play" (No such file or directory)
...

```

Now I haven't had time to look deeply into this but perhaps someone else might find a clue in this somewhere as to the lack of a Plymouth boot screen? By the way. Sound works okay and the login screen is correct. It's during the normal boot up that the screen is blank for several seconds, then about 2 secs worth of Plymouth and then the login screen appears.

I bet you do not hear system-ready sound (the drums) nor the login sound.
Otherwise sound may work OK.
This is due to the bug in libcanberra (bug#718805).

---

### Post by Kirk M on 2011-03-04
> **Harry33 said:**
> I bet you do not hear system-ready sound (the drums) nor the login sound.
Otherwise sound may work OK.
This is due to the bug in libcanberra (bug#718805).

Ah, you're right. Thanks for reminding me. I meant to put that in but it totally slipped my mind. It's the age thing you know. :)

---

### Post by Harry33 on 2011-03-05
> **Kirk M said:**
> Ah, you're right. Thanks for reminding me. I meant to put that in but it totally slipped my mind. It's the age thing you know. :)

Yes I just mentioned it because I have been looking into this a bit and I been following the migration of the canberra-gtk-play (the executive that plays system-ready and login sound) from libcanberra-gtk0 (GTK+2) to libcanberra-gtk3-0 (GTK+3) and back again.

But looking at your log, you have some problems with gdm.
This, however, does not impact on Plymouth. Plymouth is loaded much earlier than gdm.
Loading Plymouth is more a grub and kernel KMS issue.

---

### Post by Kirk M on 2011-03-05
> **Harry33 said:**
> Yes I just mentioned it because I have been looking into this a bit and I been following the migration of the canberra-gtk-play (the executive that plays system-ready and login sound) from libcanberra-gtk0 (GTK+2) to libcanberra-gtk3-0 (GTK+3) and back again.

But looking at your log, you have some problems with gdm.
This, however, does not impact on Plymouth. Plymouth is loaded much earlier than gdm.
Loading Plymouth is more a grub and kernel KMS issue.

I'll admit that I'm not that heavy in this particular area. Considering that this is an unmodified install (from Alpha 2) which has updated in the usual way I expect this these problems are probably pretty common for most testers? I have installed the latest Nvida driver of course and I do see a few seconds of Plymouth before the login screen. By the way, I noticed there were several updates to canberra packages today and now the drums are sounding when the login screen appears. That's a bit of progress anyway.

---

### Post by jerrylamos on 2011-03-05
> **Kirk M said:**
> I'll admit that I'm not that heavy in this particular area. Considering that this is an unmodified install (from Alpha 2) which has updated in the usual way I expect this these problems are probably pretty common for most testers? I have installed the latest Nvida driver of course and I do see a few seconds of Plymouth before the login screen. By the way, I noticed there were several updates to canberra packages today and now the drums are sounding when the login screen appears. That's a bit of progress anyway.

From many bruises I find updates from say Alpha 2 is NOT the same as an Alpha 3 install.  Somewhere alopng the lines the updates to the updates get all snarled up and it is just not worth my time to unravel it.

So I do a new install when every milestone comes by, or even oftener. Typically I'll use the latest CD Daily Build at about the time of say Alpha 3 because I can use zsync.

My opinion, if a much updated Alpha isn't working, ditch it and do a new install.

Good luck,

Jerry

---

### Post by Harry33 on 2011-03-05
> **jerrylamos said:**
> From many bruises I find updates from say Alpha 2 is NOT the same as an Alpha 3 install.  Somewhere alopng the lines the updates to the updates get all snarled up and it is just not worth my time to unravel it.
So I do a new install when every milestone comes by, or even oftener. Typically I'll use the latest CD Daily Build at about the time of say Alpha 3 because I can use zsync.
My opinion, if a much updated Alpha isn't working, ditch it and do a new install.
Good luck,
Jerry

The bottom line is that even though your first installation media would have been Lucid Lynx (10.04) like in one of my setups I have, you could have upgraded it package by package (not by dist-upgrade, that is way more complicated to retain fresh) and after you would have a fully upgrated Natty, it would be exactly the same as fresh Natty-alfa3 install with todays latest updates.

But, I admit, it is not an easy task to upgrade from let's say Maverick to Natty by only changing the file sources-list by replacing the word maverick with the word natty.

You must pay attention to all ABI changes. This may easily create a dependency hell in your setup. Names of the packages change and the old packages should be deleted and so on. And you do need Synaptic to all this and to understand the "dependency-world of Ubuntu".

But during any development phase, one must pay attention to the settings in /home/user/ directory. Sometimes it is even better to fully clean problematic settings to recover the correct operation.

I haven't done a single system-wide re-installation since Lucid days.

However, I do have one setup with the latest release version (right now Maverick Merkaat, 10.10) and I do have a live-USB around (Maverick too) in case of chrooting.

---

### Post by Kirk M on 2011-03-06
> **jerrylamos said:**
> From many bruises I find updates from say Alpha 2 is NOT the same as an Alpha 3 install.  Somewhere alopng the lines the updates to the updates get all snarled up and it is just not worth my time to unravel it.

So I do a new install when every milestone comes by, or even oftener. Typically I'll use the latest CD Daily Build at about the time of say Alpha 3 because I can use zsync.

My opinion, if a much updated Alpha isn't working, ditch it and do a new install.

Good luck,

Jerry

Heh, well I downloaded and burned the Natty 11.04 alpha 3 build and attempted to do a clean install (with formatting to ext4) into the test partition where Natty alpha 2 resided (sda2). Unfortunately, Ubuquity kept crashing at the same place during install (half way through "Installing system" after all files were copied and all packages were downloaded) on three different install attempts. This didn't happen with alpha 2 so there's obviously something wrong with Ubiquity in alpha 3. Possibly relating to manually specifying partitions.

I've since wiped this test partition (sda2) and reformatted to ext4 using Gparted from my Linux Mint Debian Edition install and will download the .iso again on the chance I got  a bad download the first time.

---

