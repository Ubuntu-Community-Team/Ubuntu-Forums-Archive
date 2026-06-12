---
title: "Network Manager System Setting?"
date: 2011-08-30
forum: Networking &amp; Wireless
---

### Post by mikeym on 2011-08-30
Hi,

I've a problem that my system is not connecting until I've logged in and therefore a couple of the more sensitive services I am running such as *mediatomb* and *Knockd* are failing to load during boot. I was about to try and figure out how to set up networking manually when I noticed that Network Manager is supposed to have a setting called "System Setting" that does this for you ([https://help.ubuntu.com/community/NetworkManager0.7#User Settings and System Settings](https://help.ubuntu.com/community/NetworkManager0.7#User Settings and System Settings)). 

This is supposed to be from Version 0.7, but for some reason my version 0.8.4 does not have this setting.

Is there something I'm missing?

---

### Post by Enigmapond on 2011-08-30
There never has been a "System Settings". If you are trying to edit your connections, do just that. Right-click on the icon/edit connections then tab/select which connection you want to edit and go. You will be able to manually all the network info.

They refer to system settings at the bottom showing you that path where these options are saved.

---

### Post by mikeym on 2011-08-30
> **Enigmapond said:**
> There never has been a "System Settings".

The [screenshot]("https://help.ubuntu.com/community/NetworkManager0.7?action=AttachFile&do=get&target=ipv4_wired.png") on the linked documentation page would beg to differ. 

Erm.. no that's not what the problem is. I want the system to connect to my only wired connection as soon as the system starts as part of my *init* sequence, as 2 of my daemons / services (in Ubuntu vernacular) fail to start without an established connection. That is exactly what the "System Setting" is described as being for in the [Linked Docpage]("https://help.ubuntu.com/community/NetworkManager0.7#User Settings and System Settings"). Since something has obviously changed, or I have missed an undescribed step, I would like to know what the accepted way of configuring your system in such a way on Ubuntu currently is?

---

### Post by Enigmapond on 2011-08-30
I don't mean to be rude but did you do as I instructed and manually enter the network info, tick CONNECT AUTOMATICALLY, reboot and see if it worked?

---

### Post by mikeym on 2011-08-30
> **Enigmapond said:**
> I don't mean to be rude but did you do as I instructed and manually enter the network info, tick CONNECT AUTOMATICALLY, reboot and see if it worked?

That was not what you said. You posed the slightly more patronising and less informative "Right click, enter networking details" (paraphrased). But I'm really not picking a fight and do appreciate that anyone takes the time to write responses to these kind of questions.

So, I tested your suggestion and found out I was wrong in my initial post. The settings I had originally and the ones I tried entering manually following your suggestion both had "Available to all users" ticked. I've tested it by pinging my machine and both sets of settings connect me at boot. So my question was wrong. That said the 2 networking services (*mediatomb* and *knockd*) are still failing to load on boot. So there is some problem with the way I have my networking or services set up.

---

### Post by praseodym on 2011-08-30
Hi,

until Maverick there was a file named:

```
/etc/NetworkManager/nm-system-settings.conf
```

There is a value "false":


```
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
```
which can be renamed in "true". "false" means that the NM ignores interfaces configured in the **/etc/network/interfaces**, and the NM connects only at login. So, if you want to have "wake-on-XXX" you put a manual config into that file with "true":

```
auto lo
iface lo inet loopback

#example for DHCP and LAN
auto eth0
iface eth0 inet dhcp
```
The first thing you can try is with "false" to put only

```
auto eth0
```

additionally into the **interfaces**

---

### Post by mikeym on 2011-08-30
**praseodym** thanks. Though one step ahead of you. 

Just tested it with *managed=false* (which it already was) and with:

**/etc/network/interfaces**```

auto eth0
iface eth0 inet dhcp

```

The *managed=false* setting now seems to reside in **/etc/NetworkManager/NetworkManager.conf**. But the "System Settings" I was talking about earlier wasn't this file but an actual checkbox in the *nm-applet* that appears to have been removed or perhaps exchanged for "Available to all users". 

Anyway these settings didn't help matters with *knockd*. I've done a bit more research though. I had overcome the problem with *mediatomb* but had forgotten exactly how I had done it. Initially I had added it as a "Startup Application" when I logged in, as advised on the [mediatomb FAQ Ubuntu section]("http://mediatomb.cc/dokuwiki/faq:faq#how_do_i_make_mediatomb_start_automatically"). I had however forgotten that this had been fixed with [a patch]("https://bugs.launchpad.net/ubuntu/+source/mediatomb/+bug/212441/comments/17") to mediatomb (that I now believe had made it's way into the repos). 

The patch apparently updated the **/etc/init.d/mediatomb** script with an *Upstart* script **/etc/init/mediatomb**. And has fixed the problem for me for mediatomb. 

I've just checked *knockd* and it is indeed using a **/etc/init.d/knockd** script. This does seem to be more of a service issue than a networking one. I don't really know enough about the specifics of how Ubuntu manages its services and the order in which they are run, but my guess is that *knockd* also needs to be updated to an *Upstart* script to be loaded properly.

---

### Post by mikeym on 2011-08-31
I've submitted a bug report for knockd along with an upstart script that fixes the problem for me but is likely to have errors as I don't know enough about writing upstart scripts. ([https://bugs.launchpad.net/ubuntu/+source/knockd/+bug/837954](https://bugs.launchpad.net/ubuntu/+source/knockd/+bug/837954))

---

