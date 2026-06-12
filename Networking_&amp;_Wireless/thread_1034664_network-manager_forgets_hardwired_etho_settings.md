---
title: "network-manager forgets hardwired etho settings"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by Effcook on 2009-01-08
I just installed Ubuntu 8.10 on a machine that has run previous versions
of Ubuntu.  I'm attempting to set up a hard-wired ethernet connection
with a permanent address for this box.

After a few tries with the network-manager GUI, I managed to get the
hard wired connection to use the correct address (under IPv4 Settings)
and everything works fine.
Then I rebooted the machine and it forgot everything I entered.
I tried this several times just to make sure it was repeatable.

The two check-boxes for Connect automatically and System setting are
checked.  Does anybody have a clue what I'm doing wrong here?
I changed the Connection name to Hardwired eth0, that also seems
to disappear.

I find it somewhat amusing that what used to be one of the most basic
configuration steps for installing a new OS has become buried so deeply
under all of the DHCP and wireless configuration details.

---

### Post by hardyn on 2009-01-08
its a bug in network manager... well documented too  (i found out first hand just as you did).

its on the launchpad... hopefully it will be fixed for next release

---

### Post by Effcook on 2009-01-08
Ok, I "fixed" the problem by uninstalling network-manager and network-manager-gnome
then added the usual neworking info to /etc/network/interfaces and /etc/resolv.conf.
Problem solved well enough for me, thanks.

---

### Post by oygle on 2009-01-09
I haven't tried it yet, but seems a workaround at [http://bigbrovar.wordpress.com/2008/12/18/how-to-share-your-internet-connection-on-ubuntu/](http://bigbrovar.wordpress.com/2008/12/18/how-to-share-your-internet-connection-on-ubuntu/) ??

---

### Post by doberry on 2009-01-19
I got around this issue by doing the following.

My box has multiple ethernet cards. I plugged one in, and verified which it was by running ifconfig and checking for the sent dhcp packets. Once I had done this, I went into the manager, copied the mac for that card, and added a new connection. I then unchecked the connect automatically and system boxes, rechecked them, and added the mac. Then I added the static info I use. That forced it to ask for my root level access password. This saved my settings and upon reboot allowed my box to keep its settings and browse.  :)

But I really wish the issue did not exist in the first place.

---

### Post by BLTicklemonster on 2009-02-08
> **doberry said:**
> I got around this issue by doing the following.

My box has multiple ethernet cards. I plugged one in, and verified which it was by running ifconfig and checking for the sent dhcp packets. Once I had done this, I went into the manager, copied the mac for that card, and added a new connection. I then unchecked the connect automatically and system boxes, rechecked them, and added the mac. Then I added the static info I use. That forced it to ask for my root level access password. This saved my settings and upon reboot allowed my box to keep its settings and browse.  :)

But I really wish the issue did not exist in the first place.

I can't network worth a flip. I wonder if this is my problem, because in networking tools, I can't configure eth0 because it says

The interface does not exist
Check that it is correctly typed and that
it is correctly supported by your system.

Exactly what all did you do, step by step so I don't miss anything?

Oh, and I tried 

sudo ifconfig eth0 up

to no avail...

Thanks.

---

### Post by drewbert on 2009-02-10
I've run into this issue on 2 computers at home within 3 days.....my wife's machine lost connectivity on saturday mine today.....tried the fixes but to no avail.....any help would be great....

---

### Post by BLTicklemonster on 2009-02-19
Yay me.

I've since reinstalled ubuntu on a new hard drive I just got. Recently I was told that perhaps one of my problems I've had networking was that I was using an onboard lan, so I got a spare nic out and put that in the computer, disabled the onboard in the bios, booted up, and it would not connect. So I figured what the heck, turned off the machine, took the new card out, turned the lan back on in the bios, and voila!!! no network, no internet, and the only thing showing up in network tools is modem settings, and I don't even have a modem. ifconfig lo is the only thing that returns anything. No eth* works at all. Now I'm stuck totally, and the only thread here that came close to matching my problem was never resolved.
[http://ubuntuforums.org/showthread.php?t=843608](http://ubuntuforums.org/showthread.php?t=843608)

I get the same thing he does in the screen cap he posted doing ifconfig lo btw.

Anybody got any ideas? Remove networking in synaptic, and use the install cd to install it back again, maybe?

---

### Post by WizOfOz on 2009-03-28
Found this in a similar post.


 check your    /etc/network/interfaces file and make sure the only settings in 8.10 are:

auto lo
iface lo inet loopback

Save it and then reboot.  I had a working network connection (sometimes) and my Network Manager showed an orange triangle.  I saved the new config and rebooted and everything works!:guitar:

---

