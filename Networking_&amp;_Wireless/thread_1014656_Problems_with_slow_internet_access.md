---
title: "Problems with slow internet access"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by cshard on 2008-12-18
Ever since installing Ubuntu 8.04, I have been experiencing extremely slow internet speeds no matter if I am simply downloading update and software packages, or if I'm surfing the internet.

I dual boot with win XP on the same PC and the difference in speeds are worlds apart - on Ubuntu, I get barely 7-15 kb/s - yet with XP, I regularly get speeds of 40-300 kb/s for the exact same tasks. If I turn on Firestarter, when in Ubuntu, the speeds slow down even more, but in this case, I'm aware of what is slowing the connection.

A few details about my current build of Ubuntu - as mentioned, I'm using 8.04 and I've downloaded all current updates. As I've just started using Linux, I've barely scratched the surface of the OS and haven't done any special modifications other than downloading software packages that caught my eye in Synaptic. I also have not modified any settings in terms of opening any ports nor changed anything in Firestarter.

What can I do to optimise my connection speeds? I'd like to play around Ubuntu more, but when my internet speeds stay at such lethargic levels, I can't even read up solutions to problems I encounter without firing up my XP laptop side by side.

---

### Post by bromix on 2008-12-18
Try running this in a terminal

```
sudo iwconfig wlan0 (or your network device) rate 54M
```

That solved it for me

---

### Post by cybrsaylr on 2008-12-18
It also my be an IPv6 issue.
This[ thread ]("http://ubuntuforums.org/showthread.php?t=1014549")deals with that.

---

### Post by cshard on 2008-12-20
Many thanks, both of you. Took me a while to get the time to sit down and try this out but anyway...

@bromix: I haven't tried your solution yet because I have a question before using that command. If my inference is correct, that command is meant to speed up some setting in the configuration of my wireless adapter. Can you point me towards something I can read up on it? Also, what command should I use to revert it back to the previous state?

@cybrsaylr: I made the changes to the ipv6 settings and it has definitely sped up my internet access speed. However, my Package Manager is still as slow as heck when downloading updates, even when I use my country's local update servers. I'm still getting speeds of 2-8 kb/s (or 5562 bytes on the display)

Is there any other setting I can modify on my PC to speed this up, or is this a case of having to be dependent on choosing the correct server to get updates from?

edit: Almost forgot to add something. Multitasking downloading files and updates seems to be an effort in futility. My internet speed is definitely fast enough to handle more than one download at a time, but even after changing the ipv6 settings, I can't download, say the tar.gz file for Blender at the same time as getting package updates without both suddenly losing all speed and failing. 

At least Blender was still downloading at 5.0 kb/s but an update package downloading at the same time failed completely. Is there anything I can change to get this working?

---

### Post by Baldrick_NZ on 2008-12-22
> **bromix said:**
> Try running this in a terminal

```
sudo iwconfig wlan0 (or your network device) rate 54M
```

That solved it for me

Thanks for this, it seemed to work immediately then signal drops back a fe seconds later. I re-apply the above and the signal springs back again for a few secs.

Any ideas how I can make it stay longer?

Seems to be on the right track tho...

Merry Christmas to one and all!

---

### Post by cshard on 2008-12-30
I haven't had much time to troubleshoot Ubuntu recently, but  seems like there hasn't been much response to this thread since the last set of advice, so I'm just bumping it up.

Basically:
1. What does the command "sudo iwconfig wlan0 rate 54M" do and if I want to reverse the settings, what should I type in?

2. How can I effectively multitask downloading activities without my speeds dropping to a snail's pace and failing? Downloading updates is already extremely slow, and trying to do more than one task on the internet is currently futile.

3. Is there anything more I can do to speed up downloading updates?

---

### Post by cb34 on 2008-12-30
not that i know really anything about internet and all that, if mine were slow like yours, i would probably also be here askin for help, but first thing that comes to mind, even though there shouldn't really be anything in the background using the internet or listening with a server.. try running this command to have a look at what if anything is using internet.. do this when you're not cruisin the net or doing any downloading so you can see what's goin on.. then gotta research about each port you find, IF you find anything interesting.
```

netstat -atu

```
a=all t=tcp u=udp - what those flags mean

also check, maybe you have more than firestarter on, maybe you have ufw firewall on with some rules slowin you down(sudo ufw status).. or somethin in IPTABLES main rules are wrong.. i dont really know, just throwin you some ideas if maybe it's not only the connection settings, but something somewhere blocking you or limiting your speeds or ports.

good luck.. and sorry i cant be of much help.
conky is cool to have running on your screen giving you realtime info. ;)

---

