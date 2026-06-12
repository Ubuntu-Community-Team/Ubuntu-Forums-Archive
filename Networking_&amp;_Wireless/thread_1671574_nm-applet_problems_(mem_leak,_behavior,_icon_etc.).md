---
title: "nm-applet problems (mem leak, behavior, icon etc.)"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by argued.logic on 2011-01-20
Ubuntu 10.10 with latest updates
manually added ppa:s such as awn-trunk etc

Acer Notebook (i3 370m, ATI 5470mhd, 3Gb RAM etc)
Internet con. through Nokia 5630 HSDPA - usb

I ve noticed the network-manager starting having problems 4-5 days ago when 
I logged in for a usual session having my comp connected to 40#LCD @ 1080p.
The icon theme (have Faenza Dark as standard) was reverted to gnome standard
and a new volume icon/controller started in the notification area. So I searched for
any info I could find and that brought me to nm-applet mem leak info and bugg-
reports. I logged out from the session and once I logged in all was well. You would 
think so right :?

So here is the problem I have.

1: nm-applet --sm-disable starts at loggin BUT after 6-7h is non-responsive
     eating up massive 250+ Mb of RAM
2: nm-applet lacks the indicators of signal-strength as it used to have
3: nm-applet is a part of  indicator-applet 0.4.6 (used to be separated in Notification Area 2.30.2)
* see first 2 attached images

killall nm-applet works as expected 
```
~$ ps -ef | grep nm-applet
root      5229  5164  0 12:02 pts/0    00:00:03 nm-applet --sm-disable
```

sudo nm-applet --sm-disable in terminal starts new nm-applet
as it should in notification area with some messages
```
(nm-applet:5229): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nm-applet:5229): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

```
* see last 2 attached images

Now, this way it stays connected and responsive as far as I see forever
without the mem-leak issue but as soon as I logout the session its all 
back to the state 1.
What can I do about this?
I am currently looking at different wm:s and options but I do like my
gnome the way it is and would like to see a solution to the problem instead of running away from it.

btw the NetworkManager Applet is v. 0.8.3 and I have tried to disable it
from the startup applications but it re-enabled it self.

---

### Post by argued.logic on 2011-01-21
Bumping up my thread with additional info...
My only solution so far to my issue is removing following
*Indicator Applet
*Indicator Applet Session
and only keeping Notification area since nm-applet starts and keeps it self
active for 7-8h+ (consuming around 50-60mb RAM) is somewhat a step
forward. Any ideas or help greatly appreciated.

---

### Post by grahammechanical on 2011-01-21
I do not think that this is a network issue but a Desktop environment issue. Last year I had something weird happening to my desktop. Sometimes on boot up the icons would be different and I would need to re-select my chosen theme.

When did you last re-install and format the disc? I think that overtime and with the changes (improvements) that come with each upgrade, you get a collection of configuration files that sometimes cause conflicts.

Last October I re-installed and formatted the Ubuntu partition and the home partition. Now I have enhanced appearance effects. That was something else that I had a problem with.

I have decided that a clean sweep from time to time is useful. Do not forget to backup everything you want to keep.

Regards.

---

### Post by Endracion on 2011-01-21
Just thought I'd add that I have the exact same problem and I also happen to use the same theme. No direct solution yet though.

---

### Post by argued.logic on 2011-01-21
> **grahammechanical said:**
> I do not think that this is a network issue but a Desktop environment issue. Last year I had something weird happening to my desktop. Sometimes on boot up the icons would be different and I would need to re-select my chosen theme.

When did you last re-install and format the disc? I think that overtime and with the changes (improvements) that come with each upgrade, you get a collection of configuration files that sometimes cause conflicts.

Last October I re-installed and formatted the Ubuntu partition and the home partition. Now I have enhanced appearance effects. That was something else that I had a problem with.

I have decided that a clean sweep from time to time is useful. Do not forget to backup everything you want to keep.

Regards.

This is fairly new set-up since december and  fresh install of 10.10 so those issues I ve been 
reading about people having from up-grading couldn't be the case here. One another thing
that comes back in my thoughts is that having this comp running for 2 users (1 with hdmi out-put and another purely native resolution) this problem doesnt seem to involve the later.
I do have the option of re-install and even try another wm as I mentioned, but being the tech-oriented guy I am, I still prefer finding a solution. Thanks for sharing your experience tho.

> **Endracion said:**
> 
Just thought I'd add that I have the exact same problem and I also happen to use the same theme. No direct solution yet though.

I would think this is an issue effecting a lot of us and there are plenty of bug-reports out there so lets just hope for a "quick-fix" even tho there s no such thing as quick-fix  :shock:

---

### Post by beruic on 2011-01-21
Have you submitted to this bug?
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/684599](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/684599)

---

### Post by beruic on 2011-01-21
Quick fix: install indicator-network, and disable nm-applet. Works for me, but indicator-network is not as user friendly and feature rich as nm-applet.

---

### Post by beruic on 2011-01-21
Read the bug btw. There's more info.

---

### Post by argued.logic on 2011-01-21
> **beruic said:**
> Read the bug btw. There's more info.

Thank you for your reply.
That is the main bug-report I ve been reading and with your additional info
from today I have one question. My network-manager-gnome is in deed the
one from ppa:elementaryart... 0.8.2+git.20101123t161608.f143e76-0ubuntu1
[I]so what I am asking is how did you downgraded to the default one?
Will I be able to do the same considering I only have access to one network
connection and I presume some packages will be needed to download after the
process of removing the 0.8.2+git version takes place?

[/I]Never mind that - I ve found my way but for those who wonder...
Open up Synaptic Package Manager and look for network-manager-gnome
If you want to downgrade it to default 0.8.1+git.20100809t190028.290dc70-0ubuntu3
the mark the 0.8.2 version then choose Package and Force Version... from the menu.
Once there select the 0.8.1 version and hit apply...

I ll be monitoring this and see what it does on my comp. Thanks again Beruic!

---

### Post by beruic on 2011-01-21
Sounds good. Throw updates at the bug from now on if they are relevant :)

---

### Post by argued.logic on 2011-01-21
> **beruic said:**
> Sounds good. Throw updates at the bug from now on if they are relevant :)
Yes thank you.
After one hour things are looking as they should even tho I ve had one crash of the NetworkManager Applet, it sits steady at 7.5Mb usage. *fingers crossed*

---

### Post by beruic on 2011-01-21
Mine is at 5 now and has been for some time. Do you have many networks near you? I have 14 besides my own.

---

### Post by argued.logic on 2011-01-21
> **beruic said:**
> Mine is at 5 now and has been for some time. Do you have many networks near you? I have 14 besides my own.
All between 8-12 depending of the time of the day. Do you think that effects nm-applet as well?

---

### Post by argued.logic on 2011-01-23
All seems to be well here, nm-applet stable @ 4-5 mb after 11-12h use.

---

### Post by draki on 2011-02-03
> **argued.logic said:**
> Thank you for your reply.
That is the main bug-report I ve been reading and with your additional info
from today I have one question. My network-manager-gnome is in deed the
one from ppa:elementaryart... 0.8.2+git.20101123t161608.f143e76-0ubuntu1
[I]so what I am asking is how did you downgraded to the default one?
Will I be able to do the same considering I only have access to one network
connection and I presume some packages will be needed to download after the
process of removing the 0.8.2+git version takes place?

[/I]Never mind that - I ve found my way but for those who wonder...
Open up Synaptic Package Manager and look for network-manager-gnome
If you want to downgrade it to default 0.8.1+git.20100809t190028.290dc70-0ubuntu3
the mark the 0.8.2 version then choose Package and Force Version... from the menu.
Once there select the 0.8.1 version and hit apply...

I ll be monitoring this and see what it does on my comp. Thanks again Beruic!

Thanks - that seems to have worked for me too

---

### Post by argued.logic on 2011-02-08
> **draki said:**
> Thanks - that seems to have worked for me too

:cool: cheers

---

