---
title: "Update Manager freezes while updating BE 12.04.1 v0.25"
date: 2012-12-06
forum: Mythbuntu
---

### Post by 4partee on 2012-12-06
Mythbuntu 12.04.1

Did a fresh install of BE only and in a VirtualBox VM. Rebooted as directed.

Update manager(UM) button is blinking, click it and let it do 192 updates.

Close UM.

Run UM and check.  No new updates. Close UM.

Run MCC, repositories, and check activate box, click apply,apply. Close MCC.

Run UM and check.  click and let it do 11 updates.  Click details to watch progress. Downloads OK. Then freezes.

Detail message box shows:
Preconfiguring packages ...
X
the cursor at position X is not blinking.

Had the same freeze on my live FEBE bare metal system while trying to fix the pvr-150 problem that was recently fixed at mythtv.org. I reproduced the behavior in both by the above steps on the separate bare metal system and a VM on a separate system.  

What next?

John

---

### Post by nickrout on 2012-12-06
> **4partee said:**
> Mythbuntu 12.04.1

Did a fresh install of BE only and in a VirtualBox VM. Rebooted as directed.

Update manager(UM) button is blinking, click it and let it do 192 updates.

Close UM.

Run UM and check.  No new updates. Close UM.

Run MCC, repositories, and check activate box, click apply,apply. Close MCC.

Run UM and check.  click and let it do 11 updates.  Click details to watch progress. Downloads OK. Then freezes.

Detail message box shows:
Preconfiguring packages ...
X
the cursor at position X is not blinking.

Had the same freeze on my live FEBE bare metal system while trying to fix the pvr-150 problem that was recently fixed at mythtv.org. I reproduced the behavior in both by the above steps on the separate bare metal system and a VM on a separate system.  

What next?

JohnWhat next? Follow the avice I gave you in the other thread and update via the command line. You may get a better error message, if there is in fact an error.

---

### Post by 4partee on 2012-12-06
> **nickrout said:**
> What next? Follow the avice I gave you in the other thread and update via the command line. You may get a better error message, if there is in fact an error.

OK.

```
gelmjw@be12041:~$ sudo apt-get update
[sudo] password for gelmjw: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
gelmjw@be12041:~$ 

```

This is because the of the frozen UM.

I once tried closing UM at this point by clicking on the close button where the message was not responding so I chose the force button.  When I restarted UM it had the partial upgrade message and I chose partial to proceed.  The result was I did not get the fix. 

I now have a new install with a frozen UM. 

So how would you like me to kill the frozen UM?

Or, would you prefer I reinstall and use the cli commands after MCC?

John

---

### Post by nickrout on 2012-12-06
xkill should work to close it, or sudo kill from the commandline. Then use the apt-get commands.

Is it frozen or just doing stuff?

---

### Post by AlecJ on 2012-12-06
Had the same problem, it is just doing stuff.
My old IBM laptop with a pentium 3, took about 45mins to complete last update a few days ago.

My worries are, will this hardware become useless with the latest software, at what point do you "say no more update's"  as I have no plans (or pennies) to upgrade the laptop???

---

### Post by 4partee on 2012-12-06
> **nickrout said:**
> xkill should work to close it, or sudo kill from the commandline. Then use the apt-get commands.

Is it frozen or just doing stuff?

It is frozen, no cpu or i/o in top.  When I wake the system from screensaver, the screens are blank with no refresh at all. No progress bar of details.

```
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 2,473 kB in 4s (563 kB/s) 
Reading package lists... Done
root@be12041:/home/gelmjw# apt-get upgrade -V
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@be12041:/home/gelmjw# cd /etc/apt/sources.list.d
root@be12041:/etc/apt/sources.list.d# ls -lha
total 12K
drwxr-xr-x 2 root root 4.0K Dec  6 10:50 .
drwxr-xr-x 6 root root 4.0K Dec  6 10:50 ..
-rw-r--r-- 1 root root  132 Dec  6 10:50 mythbuntu-0_25-precise.list
root@be12041:/etc/apt/sources.list.d# cat mythbuntu-0_25-precise.list 
deb http://ppa.launchpad.net/mythbuntu/0.25/ubuntu precise main
deb-src http://ppa.launchpad.net/mythbuntu/0.25/ubuntu precise main
root@be12041:/etc/apt/sources.list.d# mythbackend --version
Please attach all output as a file in bug reports.
MythTV Version : v0.25.3-23-g0b60406
MythTV Branch : fixes/0.25
Network Protocol : 72
Library API : 0.25.20120506-1
QT Version : 4.8.1
Options compiled in:
 linux profile use_hidesyms using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_bindings_php using_crystalhd using_dvb using_firewire using_frontend using_hdhomerun using_ceton using_hdpvr using_iptv using_ivtv using_joystick_menu using_libcec using_libcrypto using_libdns_sd using_libxml2 using_lirc using_mheg using_opengl_video using_qtwebkit using_qtscript using_qtdbus using_v4l2 using_x11 using_xrandr using_xv using_bindings_perl using_bindings_python using_bindings_php using_mythtranscode using_opengl using_vaapi using_vdpau using_ffmpeg_threads using_live using_mheg using_libass using_libxml2
root@be12041:/etc/apt/sources.list.d# 

```

John

---

### Post by nickrout on 2012-12-06
Well you seem to now have the latest version of mythtv-backend (even later than mine yesterday). According to the git commit number in the mythtv version (0b60406) you are now completely up to date. [https://github.com/MythTV/mythtv/commits/fixes/0.25](https://github.com/MythTV/mythtv/commits/fixes/0.25)

Now you should probably test it and report back in the other thread.

---

### Post by 4partee on 2012-12-06
> **nickrout said:**
> Well you seem to now have the latest version of mythtv-backend (even later than mine yesterday). According to the git commit number in the mythtv version (0b60406) you are now completely up to date. [https://github.com/MythTV/mythtv/commits/fixes/0.25](https://github.com/MythTV/mythtv/commits/fixes/0.25)

Now you should probably test it and report back in the other thread.

Yes, I will do that, on one condition.

You will record a ticket in launchpad regarding this problem with the UM freeze.  :)

I'll be watching for your link in here. 

John

---

### Post by nickrout on 2012-12-06
For heaven's sake you really are being idiotic now. I have no problem with update manager because I don't use it. If you have a problem with it, you report it. But bear in mind the other post here that claims they had a similar problem which was just caused by update manager taking a long time to do it's thing, so you might in fact be barking up the wrong tree.

I am merely pointing out that having gone through about 4 pages of posts with you yesterday because you didn't have mythbuntu repos activated, I would have thought you would be happy that you now have your system updated and were in a position to test the supposed fix to your PVR problem AND post back in the RIGHT thread about whether or not it works for you. But no, you seem to have some point to make about launchpad, the details of which are going way over everyone elses head, including mine.

Frankly I don't give a damn whether your system works, I hjust try to help people on here, I don't expect your silly responses. You implied yesterday that I had some malice in my posts > how do I know who you are?  and > If you are going to have principles, you must be willing to put your big boy pants on and deal with problems.

With people like you around, I am surprised anyone helps out.

---

### Post by AlecJ on 2012-12-06
Good Rant!
Very Big Bang Theory..

---

### Post by 4partee on 2012-12-06
> **alecj said:**
> good rant!
Very big bang theory..

x2!

---

