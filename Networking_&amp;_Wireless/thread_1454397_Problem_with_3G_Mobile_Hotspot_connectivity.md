---
title: "Problem with 3G Mobile Hotspot connectivity"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by ohiomoto on 2010-04-14
I just got Verizon Mobile Palm Pre Plus and set up the 3G Mobil Hotspot.  I'm able to connect to the hotspot with Ubuntu 9.10, Win XP and Win 7 without a hitch using WPA/WPA2 Personal or Open connections.  Service is slow on XP, but not bad on Win 7 and Ubuntu.  

The problem is that when using Ubuntu, the Pre is constantly connecting and disconnecting the computer, but Ubuntu shows a solid connection at all times.  Running windows 7 on the same machine works fine.  

EDIT:  I solved the problem in 9.10 by removing my wireless backports module as stated in post #3, but it looks like the problem will be back with 10.04 as noted in post #4.  A workaround is presented in post #2. 

[B]EDIT:  This looks like it is a problem with Palm's Hotspot.

> **cek said:**
> Alright, I think I have a solution to the issue, and I think it's a bug with the Palm Hotspot software.

It's not responding to direct probe requests from a direct packet, the probe request needs to be sent to the broadcast address.

It would be relatively simple to patch this in the kernel to mask the issue, but I'm not sure if that is the "correct" approach.  Likely that will be faster than we can get Palm to address it though...

  Please see the next post for a workaround. I will attempt to keep this thread up to date.  Please post your results. [/B]

---

### Post by ohiomoto on 2010-04-15
Thanks to cek, CodeDonkey, PatrickVogeli and others for thier contributions to this guide,

1. Download [compat-wireless-2.6.32.16.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.32/compat-wireless-2.6.32.16.tar.bz2") from [http://wireless.kernel.org/en/users/Download/stable/](http://wireless.kernel.org/en/users/Download/stable/)
2. Untar it
3. edit ./net/mac80211/mlme.c within the untarred source following Cek's instructions:
> **cek said:**
> ....
Within the source for the wireless drivers, open the file: ./net/mac80211/mlme.c

with gedit (or whatever text editing program you prefer), search for the following:

ieee80211_send_probe_req(sdata, ifmgd->associated->cbss.bssid,

This should lead you to two lines of code that look like this:

```

ieee80211_send_probe_req(sdata, ifmgd->associated->cbss.bssid,
 ssid + 2, ssid[1], NULL, 0);

```

Comment out these two lines of code and replace with the same function call with different arguments, the finished product should look like this:

```

/*
ieee80211_send_probe_req(sdata, ifmgd->associated->cbss.bssid,
 ssid + 2, ssid[1], NULL, 0);
*/
ieee80211_send_probe_req(sdata, NULL, ssid + 2, ssid[1], NULL, 0);

```


4. Go to the compat-wireless-2.6.32.16 folder (the one that was the result of the untar in step 2) in the terminal.

5. Do the following commands in the terminal:

*./scripts/driver-select iwlwifi*
[I]sudo make
sudo make install
sudo make unload

[/I]6. Restart your computer

*If it goes wrong you can undo it by *sudo make uninstall. *

Notes: If step 5 fails, make sure you have your kernel headers installed. 

If that's not enough, you may also need to run this command: 
```
sudo apt-get install build-essential
```

It seems as though the new driver will NOT work if you are using linux-backports-modules-wireless.  Use Synaptic Package Manager to remove it if necessary.

**NEW SOLUTION**
This one worked for me:

> **chiefmanyrabbitguteat said:**
> ohiomoto, I got my 3g hotspot to work using the tutorial found here:
[http://ubuntuforums.org/showthread.php?t=1598930](http://ubuntuforums.org/showthread.php?t=1598930)
(many thanks to SquirrelScript for that)
For everybody's benefit, I've pasted the tutorial below.  Basically, you need to patch an updated version of the driver, and edit a script to install to the appropriate version of the kernel.  This set of instructoins is for Ubuntu 10.10 and derrivitaves.  I'm running 10.10 32 bit.  No promises for 64 bit...
It's pretty easy:
```

wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2
tar -jxf compat-wireless-2010-10-16.tar.bz2
cd compat-wireless-2010-10-16
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo reboot
```

Hope it works - keep us posted.Thanks! Worked great with my 32-bit Lubuntu.

---

### Post by ohiomoto on 2010-04-15
Solved by removing linux-backports modules.

---

### Post by ahbe on 2010-05-03
Hello, I am having the exact same problem. My Palm and Ubuntu were running fine until I upgraded to 10.04, and now it keeps dropping just as you said. I don't have the linux-backports modules installed, at least as far as I can tell. Any suggestions on what to look for now? Thanks.

---

### Post by ohiomoto on 2010-05-03
I'm still using 9.10 so the only clue I can offer is that 10.04 might be using the latest drivers that were in the 9.10 backposrts module.

I don't know enough to be any help, but maybe someone else can shed a little more light on the subject. I'll remove the "solved" tag.

---

### Post by ahbe on 2010-05-04
:( Just and update, I tried installing linux-backports-modules-wireless-generic and linux-backports-modules-wireless-preempt with no success. I have then done a complete fresh install of Ubuntu Lucid 10.04 64-bit. It still does the same thing. The hotspot connection continues to cycle. It worked fine in 9.10. Is there a way to backup to the drivers I was using in 9.10? How can I fix this?

---

### Post by ohiomoto on 2010-05-04
Sounds like the same issue I had with backports on 9.10, but only with the mobile hotspot.  All my other wireless connections worked fine.  It's worked perfectly since I removed the backports.  

I sent a PM so someone who may be able to help out.  I hope it gets sorted out because I'm planning on upgrading to 10.04 soon.

---

### Post by PatrickVogeli on 2010-05-05
hi there.. I don't think I have any solution for you, but still, I'll try.

I assume you are using the Phone as a Wireless Acess Point, not tethering or stuff like that. If that's true, you might want to look into the compat-wireless drivers [http://wireless.kernel.org/en/users/Download/stable/](http://wireless.kernel.org/en/users/Download/stable/)

These should provide newer intel wifi drivers. Or, searching a bit, you could find the older ones which worked fine. After unzipping, you must run scripts/driver-select iwlagn or something similar to select to only build the intel driver (for 5x00 and 1000 devides). After that, the tipical make and sudo install should work. After a reboot you should have different drivers.. If they don't work, sudo make uninstall and go try another file.

I think in the Acer 1810T thread for karmic I explained how to build the compat wireless package.. I'm a bit in a hurry now...

---

### Post by ohiomoto on 2010-05-05
Thanks for chiming in here Patrick!  And yes, we are using the phone as a wireless access point which happens to be the main reason I purchased it.

Here is the Acer 1810T post he's talking about: [http://forum.notebookreview.com/acer/434638-linux-acer-1410-1810tz-1810t.html#post5521789](http://forum.notebookreview.com/acer/434638-linux-acer-1410-1810tz-1810t.html#post5521789)


[QUOTE=PatrickVogeli]
**Wireless power saving:** **Issue:** in kernels from the 2.6.31 series, wireless power saving in intel wireless drivers was dissabled.
**Solution:** *(please, first look at the Alternative Solution below)* install updated drivers. the method I used, is compiling and installing the latest intel wireless drivers from the 2.6.32.2 kernel. To do this, download the latest wireless backports drivers from [here]("http://linuxwireless.org/en/users/Download/stable/#Stable_compat-wireless_releases") (compat-wireless-2.6.32.2.tar.bz2, updated). Unpack them and, to compile and install:
```

cd /to/compat/wireless/folder
scripts/driver-select iwlwifi
make
sudo make install
sudo make unload
sudo modprobe iwlagn

```
[/QUOTE]

---

### Post by ohiomoto on 2010-05-05
Also, would this be considered a bug and would it be an Ubuntu or WebOS bug? 

I would like to see the issue fixed without having to do workarounds.

---

### Post by PatrickVogeli on 2010-05-05
I have no idea... maybe you could fill a bug against the kernel or against the intel drivers. Don't know where to do that, though.

Also I wouldn't know wether it's a Palm bug or an ubuntu one... I'd rather think an ubuntu one.

---

### Post by ohiomoto on 2010-05-06
I tried using my Wireless hotspot today with Ubuntu 10.04 today.  I ran the 64-bit LTS and 32-bit Ubuntu Netbook Remix live from a USB on my Acer AS1410 and my Dell Vostro 1400.  Both laptops have Intel wireless cards.  In all four cases, Ubuntu failed to hold a connection with the Hotspot, but worked fine with my home router.  So the problem is related to the 9.10 backports and 10.04 wireless modules.

---

### Post by ohiomoto on 2010-05-07
Bug reported: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577015](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577015)

---

### Post by cek on 2010-05-11
This appears to be an issue with the wireless subsystem, not with a specific driver.  I'm ha ing the issue with the ath9k driver.

I've got it somewhat working by hacking the mac80211 module - though my fix is definitely a hack - I can keep a connection for about 20 minutes before it drops. I'm using gentoo though, so someone needs to take the actions in the bug report.  It's filed as incomplete so no one will look at it until it's been updated.

---

### Post by cek on 2010-05-12
So, I'm now giving the drivers from [http://wireless.kernel.org/en/users/Download/stable/](http://wireless.kernel.org/en/users/Download/stable/) a go....

Running gentoo-sources 2.6.32-gentoo-r7 with the compat-wireless-2.6.32.11 drivers.  It's a little better, but the problem persists.

Going to have a go with the latest kernel source from git, and the compat-wireless-2.6.34-rc4 drivers.

---

### Post by ohiomoto on 2010-05-12
> **cek said:**
>  I'm using gentoo though, so someone needs to take the actions in the bug report.  It's filed as incomplete so no one will look at it until it's been updated. I'll follow up with it next week, but who marks the bug onfirmed?

---

### Post by cek on 2010-05-12
> **ohiomoto said:**
> I'll follow up with it next week, but who marks the bug onfirmed?

I don't know who is responsible for marking it confirmed.

I've done some additional testing with the latest kernel from git (2.6.34), and the problem persists in the vanilla kernel and with the compat-wireless driver patches.

---

### Post by cek on 2010-05-12
Alright, I think I have a solution to the issue, and I think it's a bug with the Palm Hotspot software.

It's not responding to direct probe requests from a direct packet, the probe request needs to be sent to the broadcast address.

It would be relatively simple to patch this in the kernel to mask the issue, but I'm not sure if that is the "correct" approach.  Likely that will be faster than we can get Palm to address it though...

---

### Post by ohiomoto on 2010-05-13
Nice work.  Check out the the forum at PreCentral.net I have notice other users having problems with the Hot Spot when using Vista, Ipods, and Nitendo DS etc.  Maybe this problem is related and we can get Palm to patch it.

---

### Post by ahbe on 2010-05-13
Hmm... disapointing, but it's good to know what the issue is. It's odd that my Pre works fine on Vista, XP and Ubuntu 9.10 on the same laptop, but Ubuntu 10.04 has problems. My Pre also runs fine on Mac OS X. I understand it's a Palm bug, but still, it's to bad there wasn't an easy work around until it gets patched. Either way, thanks for your help.

---

### Post by cek on 2010-05-14
Since this is likely a buggy implementation in the Palm Hotspot app (and who knows when that will be fixed!), the easiest way to fix this is to download the wireless drivers for your kernel from the compat-wireless link above, patch it (for a workaround), and install the updated modules.

I confirmed that this will work for 10.04 and the Palm Pre.

Download the drivers for your kernel and extract the source code as documented in the link above.

Within the source for the wireless drivers, open the file: ./net/mac80211/mlme.c

with gedit (or whatever text editing program you prefer), search for the following:

ieee80211_send_probe_req(sdata, ifmgd->associated->cbss.bssid,

This should lead you to two lines of code that look like this:

```

ieee80211_send_probe_req(sdata, ifmgd->associated->cbss.bssid,
 ssid + 2, ssid[1], NULL, 0);

```

Comment out these two lines of code and replace with the same function call with different arguments, the finished product should look like this:

```

/*
ieee80211_send_probe_req(sdata, ifmgd->associated->cbss.bssid,
 ssid + 2, ssid[1], NULL, 0);
*/
ieee80211_send_probe_req(sdata, NULL, ssid + 2, ssid[1], NULL, 0);

```

This will address the issue and you're Palm Pre's access point should work for you.

Since this is apparently a bug in the Palm hotspot application it is not likely that a fix will come from the kernel, so this work around appears to be necessary for the time being.

If you have any problems, just drop a note in here and I'll try to help when I can.

---

### Post by ohiomoto on 2010-05-14
Thanks cek.  I'm happy to know that there is at least a work around.  Maybe someone will do a homebrew patch it they think it might help with the Ipoop issues.  :)

---

### Post by chiefmanyrabbitguteat on 2010-07-08
I had the same problem, which was solved by installing the patch.  However, after installing the patched driver, I can no longer access my home network.  My network card sees it, but fails to log on to it.  Any thoughts?

---

### Post by oldjags on 2010-07-19
I hate to say "me too", but my new Palm Pre won't maintain a connection with Ubuntu 10.4 on my Toshiba laptop. If I boot into XP, no problem (aggg).
Has there been a formal problem registered under Ubuntu, or is this really a Palm glitch?
 
Please disregard... I read cek's great reply and will try it.
 
Thanks cek!

---

### Post by ohiomoto on 2010-07-30
I have added the posts related to the workaround cek has presented.  If someone would like to do a step-by-step, that would be great. I'll add it to the top of the thread.

---

### Post by ohiomoto on 2010-07-30
I'm trying to get the workaround working, but it doesn't work with my Hotspot.  I'm wondering if I did it right.  First of all, I'm testing this in Peppermint Ice (a Ubuntu 10.04 based OS). I'm using ICE because my Hotspot works with my UNR 9.10 install so I don't want to play with that one. 

ICE is running the 2.6.32-23-generic kernel.  The closest compat-wireless tar was for 2.6.32.16.  Is this right or should I use a different package?  Also, how do I know what driver is being used?

Thanks in advance.

---

### Post by ohiomoto on 2010-08-08
Anyone?  I could use a little help.  This is the first time I've tried to compile a driver. Maybe I'm doing something wrong.  Thanks.

---

### Post by sf_basilix on 2010-08-12
I second that notion. I would love to know if someone can document the steps on how to compile the kernel/driver, rather than just stating what to do. While it's greatly appreciated, some of us who are not as familiar, but would like to be, with these procedures would greatly appreciate it.

It would also be great if someone could explain how to revert back if it doesn't work. As explained in the above posts, someone did try this and it broke their other connection.  I'm hoping it won't affect the entire system negatively.

I'm struggling with the mobile hotspot on the Verizon Pre Plus and Ubuntu. It seems to work well on any other OS.

Thanks.

---

### Post by CodeDonkey on 2010-08-19
I got my Acer Aspire One running Ubuntu 10.04 Desktop to work with my Palm Pixi.  I followed what OhioMoto put together in the second post, but it was pretty piecemeal and hard to follow.  It took my a couple of tries to get right, so I thought I'd write some explicit instructions describing exactly what I did.

1. Download [compat-wireless-2.6.32.16.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.32/compat-wireless-2.6.32.16.tar.bz2") from [http://wireless.kernel.org/en/users/Download/stable/](http://wireless.kernel.org/en/users/Download/stable/)
2. Untar it
3. edit ./net/mac80211/mlme.c within the untarred source following Cek's instructions:

> Originally Posted by **cek**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9299149#post9299149")                 
                 [I]Since this is likely a buggy  implementation in the Palm Hotspot app (and who knows when that will be  fixed!), the easiest way to fix this is to download the wireless drivers  for your kernel from the compat-wireless link above, patch it (for a  workaround), and install the updated modules.

I confirmed that this will work for 10.04 and the Palm Pre.

Download the drivers for your kernel and extract the source code as documented in the link above.

Within the source for the wireless drivers, open the file: ./net/mac80211/mlme.c

with gedit (or whatever text editing program you prefer), search for the following:

ieee80211_send_probe_req(sdata, ifmgd->associated->cbss.bssid,

This should lead you to two lines of code that look like this:

     Code:
     ieee80211_send_probe_req(sdata, ifmgd->associated->cbss.bssid,
 ssid + 2, ssid[1], NULL, 0); 
Comment out these two lines of code and replace with the same  function call with different arguments, the finished product should look  like this:

     Code:
     /*
ieee80211_send_probe_req(sdata, ifmgd->associated->cbss.bssid,
 ssid + 2, ssid[1], NULL, 0);
*/
ieee80211_send_probe_req(sdata, NULL, ssid + 2, ssid[1], NULL, 0); 
This will address the issue and you're Palm Pre's access point should work for you.

Since this is apparently a bug in the Palm hotspot application it is not  likely that a fix will come from the kernel, so this work around  appears to be necessary for the time being.

If you have any problems, just drop a note in here and I'll try to help when I can.[/I]
4. Go to the compat-wireless-2.6.32.16 folder (the one that was the result of the untar in step 2) in the terminal.

5. Do the following commands in the terminal:
*.scripts/driver-select iwlwifi*
[I]sudo make
sudo make install
sudo make unload

[/I]6. Restart your computer

That's it.  Mine works fine with my palm pixi and fine with any other normal wireless router.  If it goes wrong, as mine did when I was initially trying to figure out what to do, you can undo it by *sudo make uninstall. *

---

### Post by sf_basilix on 2010-09-02
Thanks CodeDonkey!

---

### Post by ohiomoto on 2010-09-03
Thanks CodeDonkey.  That's what I did.  Maybe I just need to try it again a couple of times.  lol

Anyway, I updated post #2.

---

### Post by sf_basilix on 2010-09-15
For anyone following this thread, the latest release of Verizon's webOS 1.4.5 fixed this issue. I am able to connect to 64 bit 10.04 lucid using the palm pre hotspot with no more dropped connections. (everything default, no recompilation necessary)

---

### Post by ohiomoto on 2010-09-16
What the heck???  I didn't fix it for me.  Further more, I haven't been able to get the wireless driver to work either.  My Hotspot still works with 9.10 and I'm guessing that it still works with Windows.  Maybe I need to do a little more testing....

---

### Post by joealanbrooks on 2010-09-16
Edit: These directions aren't working on my EeePC 1001P.  I can't get online at all with the patched driver.

---

### Post by ohiomoto on 2010-09-16
I seem to have it working in Peppermint Ice (a 10.04 derivative).  

I went into synaptic package manager and removed linux-backports-modules-wireless-2.6.32-23-generic.  My Hotspot is now working without drops.  

I don't think I added that package.  It was either there by default with Peppermint Ice or it maybe when I was trying to compile my the patched driver.  I'll go and take a look at my other 10.04 installs (Ubuntu & Peppermint One) and see if I can get them working.

Edit:  Checked Peppermint One.  No backports by default and Hotspot was not working.  I was able to make it work using the patch. I'm pretty sure the PO (Peppermint One) install was clean because I only used it to test the Hotspot.  I have been playing with PI (Peppermint Ice) for a while now and I may have added backports-modules trying to get the Hotspot working.  My guess is that I had loaded the patched driver but it wasn't properly working because of the backports module.  As soon as the modules was removed it worked perfectly.  

I am going to test the fresh Ubuntu Install and might even try with a fresh PI install just to be sure that it works. Also, it should be noted that I have tested 9.10, 10.04, Peppermint One and Peppermint Ice with two different Palm Pre Plus phones.  So I'm pretty sure the WebOS 1.4.5 update didn't fix the problem.  Which is why I want to test a fresh Peppermint Ice install.  Just to be sure.

---

### Post by ohiomoto on 2010-09-16
I was able to get the driver to work in 32-bit 10.04.  Will do a little more testing and update the OP.

---

### Post by ohiomoto on 2010-09-16
> **sf_basilix said:**
> For anyone following this thread, the latest release of Verizon's webOS 1.4.5 fixed this issue. I am able to connect to 64 bit 10.04 lucid using the palm pre hotspot with no more dropped connections. (everything default, no recompilation necessary) I can't get any of my 32-bit 10.04 installs to work with either of my updated Pre Plus phones without he patch.  Maybe there is something different with the 64-bit system?

Edit:  I just downloaded, installed and updated 64-bit 10.04 and it did not work with either of my phones. I had to follow the guide to get it to work.

---

### Post by ohiomoto on 2010-10-28
Need help again.  Trying to make a patched driver for a Lubuntu install.  It's on the 2.6.35-22-generic-pae kernel and I'm using the compat-wirless 2.6.35-1 release.

Everything works fine until I go to unload the driver and I get the following:
```
/Desktop/compat-wireless-2.6.35-1$ sudo make unload 
Stoping bluetooth service..
 * bluetooth is not running
Unloading iwlagn...
FATAL: Module iwlagn not found.
Unloading iwlcore...
FATAL: Module iwlcore not found.
Unloading mac80211...
FATAL: Module mac80211 is in use.
Unloading cfg80211...
FATAL: Module cfg80211 is in use.

```What's happening?

---

### Post by chiefmanyrabbitguteat on 2010-11-07
ohiomoto, I got my 3g hotspot to work using the tutorial found here:
[http://ubuntuforums.org/showthread.php?t=1598930](http://ubuntuforums.org/showthread.php?t=1598930)
(many thanks to SquirrelScript for that)
For everybody's benefit, I've pasted the tutorial below.  Basically, you need to patch an updated version of the driver, and edit a script to install to the appropriate version of the kernel.  This set of instructoins is for Ubuntu 10.10 and derrivitaves.  I'm running 10.10 32 bit.  No promises for 64 bit...
It's pretty easy:
```

wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2
tar -jxf compat-wireless-2010-10-16.tar.bz2
cd compat-wireless-2010-10-16
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo reboot
```

Hope it works - keep us posted.

---

### Post by ohiomoto on 2010-11-10
> **chiefmanyrabbitguteat said:**
> ohiomoto, I got my 3g hotspot to work using the tutorial found here:
[http://ubuntuforums.org/showthread.php?t=1598930](http://ubuntuforums.org/showthread.php?t=1598930)
(many thanks to SquirrelScript for that)
For everybody's benefit, I've pasted the tutorial below.  Basically, you need to patch an updated version of the driver, and edit a script to install to the appropriate version of the kernel.  This set of instructoins is for Ubuntu 10.10 and derrivitaves.  I'm running 10.10 32 bit.  No promises for 64 bit...
It's pretty easy:
```

wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2
tar -jxf compat-wireless-2010-10-16.tar.bz2
cd compat-wireless-2010-10-16
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo reboot
```

Hope it works - keep us posted.Thanks! Worked great with my 32-bit Lubuntu.

The only thing that I had to do is to disable IPv4 for some reason.  Otherwise it seems to be working great. 

I'll add it to the top.

---

### Post by ohiomoto on 2010-11-11
I had to enable IPv4 to get it to work today???  Otherwise it seems to be working great.  Maybe someone can enlighten me?

---

### Post by BobVA on 2010-11-11
Thanks Chief!  The procedure you posted worked for me as well with an Asus eee 900 running 10.10 desktop.  Only problem was losing bluetooth.  I ran the makefile for uninstalling / reverting the bt drivers and that seemed to fix it.

Bob

---

### Post by rbosaz on 2010-12-24
> 
wget [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2)
tar -jxf compat-wireless-2010-10-16.tar.bz2
cd compat-wireless-2010-10-16
wget [http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch](http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch)
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget [http://patches.aircrack-ng.org/channel-negative-one-maxim.patch](http://patches.aircrack-ng.org/channel-negative-one-maxim.patch)
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo reboot


I'm running Ubuntu 10.10 Maverick Meerkat - Release amd64 connected through latest webOS Palm Pre Plus Hotspot.  I was having the same problem and the NEW SOLUTION described above worked great for me!

Thank you all for your help!

---

### Post by ohiomoto on 2011-01-01
Glad it helped.  I used it again on another Lubuntu install and it's working great for me too.

---

### Post by jeff913 on 2011-01-28
Just bought a Palm Pixi and my Ubuntu 10.04 has constant disconnect problem, Win Vista works, my wife's Ubuntu 9.04 works too.

The fix from post 29 works, although there is one warning during the "make" process.

Thank all you technical giants for this forum!!

---

### Post by ohiomoto on 2011-01-30
My Lubuntu just received a kernel upgrade today.  Like always, it broke my patch.  So I tried the latest compat-wireless backports module and it seems to be working!  

My Lubuntu is running 2.6.35-25-generic-pea kernel and I'm using the compat-wireless-2.6.37 wireless backports module.

---

### Post by ohiomoto on 2011-02-07
> **ohiomoto said:**
> My Lubuntu just received a kernel upgrade today.  Like always, it broke my patch.  So I tried the latest compat-wireless backports module and it seems to be working!  

My Lubuntu is running 2.6.35-25-generic-pea kernel and I'm using the compat-wireless-2.6.37 wireless backports module.

Still working great!!

---

### Post by sf_basilix on 2011-04-21
> **chiefmanyrabbitguteat said:**
> ohiomoto, I got my 3g hotspot to work using the tutorial found here:
[http://ubuntuforums.org/showthread.php?t=1598930](http://ubuntuforums.org/showthread.php?t=1598930)
(many thanks to SquirrelScript for that)
For everybody's benefit, I've pasted the tutorial below.  Basically, you need to patch an updated version of the driver, and edit a script to install to the appropriate version of the kernel.  This set of instructoins is for Ubuntu 10.10 and derrivitaves.  I'm running 10.10 32 bit.  No promises for 64 bit...
It's pretty easy:
```

wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2
tar -jxf compat-wireless-2010-10-16.tar.bz2
cd compat-wireless-2010-10-16
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo reboot
```

Hope it works - keep us posted.

So as it turns out, the temporary fix didn't last long and yes it did break.  The above fix worked perfectly for me. I'm running Ubuntu 10.04, 64 bit. So far it seems to be fine. I will add that it did take a while to compile - there are quite a number of files it goes through!

I actually started to attempt the method in post 29, however it spewed an error when I typed in:

"./scripts/driver-select iwlwifi"

It wasn't until after I ran "sudo make unload" from the above method that I realized my laptop's driver is not using iwlwifi. It is instead using "iwlagn" (Dell Latitude e6510). Once I changed it to that, the method in post 29 also compiled.

Thanks for posting the methods step by step - very helpful!

---

### Post by ohiomoto on 2011-04-23
Updated a couple of times to 2.6.35-28-generic-pae and the compat wireless drivers are still working fine for me.  As a matter of fact, I'm using my Palm Hotspot right to post this.

---

### Post by praveen_m on 2012-03-18
> **ohiomoto said:**
> Thanks to cek, CodeDonkey, PatrickVogeli and others for thier contributions to this guide,

1. Download [compat-wireless-2.6.32.16.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.32/compat-wireless-2.6.32.16.tar.bz2") from [http://wireless.kernel.org/en/users/Download/stable/](http://wireless.kernel.org/en/users/Download/stable/)
2. Untar it
3. edit ./net/mac80211/mlme.c within the untarred source following Cek's instructions:


4. Go to the compat-wireless-2.6.32.16 folder (the one that was the result of the untar in step 2) in the terminal.

5. Do the following commands in the terminal:

*./scripts/driver-select iwlwifi*
[I]sudo make
sudo make install
sudo make unload

[/I]6. Restart your computer

*If it goes wrong you can undo it by *sudo make uninstall. *

Notes: If step 5 fails, make sure you have your kernel headers installed. 

If that's not enough, you may also need to run this command: 
```
sudo apt-get install build-essential
```

It seems as though the new driver will NOT work if you are using linux-backports-modules-wireless.  Use Synaptic Package Manager to remove it if necessary.

**NEW SOLUTION**
This one worked for me:

Thanks! Worked great with my 32-bit Lubuntu.
Hi ohiomoto,

I tried your solution for fixing my hotspot issue, but somethings gonna wrong, my wifi connection doesn't work at all now :(. How would i rollback to the earlier configuration.

UPDATE-

gotcha, reinstalled broadcom drivers via synaptic and rebooted, all is well now :)

---

