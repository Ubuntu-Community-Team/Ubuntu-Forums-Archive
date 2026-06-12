---
title: "Bluetooth is pooched"
date: 2010-08-26
forum: Multimedia Software
---

### Post by BloodyIron on 2010-08-26
Hi, I'm trying to get the Playstation 3 remote to work with my mythbuntu implementation. At first my bluetooth device worked just fine, as in it showed up but i didn't complete configuration of it, but now I have caused my bluetooth daemon to not start when I tell it.

Part of my problem is there are so many different howto's on how to do this, and quite a few of them are no longer relevant due to ubuntu version updates.

The daemon stopped working after following the instructions in this howto:

[http://wiki.xbmc.org/?title=HOW-TO_Setup_PS3_BD_Remote](http://wiki.xbmc.org/?title=HOW-TO_Setup_PS3_BD_Remote)

The issue is that I didn't read the important part: "I didn't need to patch 4.63 to get BD working on ubuntu 10.04 ". Which would have saved me the headache I'm in now.

I followed the second part of his first section to update with the patched version of bluez:

```
sudo apt-get purge bluez
sudo echo deb http://ppa.launchpad.net/kitlaan/ppa/ubuntu jaunty main >> /etc/apt/sources.list
sudo echo deb-src http://ppa.launchpad.net/kitlaan/ppa/ubuntu jaunty main >> /etc/apt/sources.list
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6F7177CC
sudo apt-get update
sudo apt-get install bluez

```Since then I have tried many different ways to purge and do complete removals of all things bluetooth on my system and full reinstallations of the same parts. However the daemon still does not start.

I also have not gone further in that particular howto as it seemed pointless as bluetooth is now not functional.

Tailing the /var/log/messages does not output a message, and I cannot find a log just yet, but I am not sure if I am looking in the right place.

At this point I am out of ideas as I cannot find a post on the internet covering this issue.

Please help me.

---

### Post by tripolitan on 2010-08-26
Couldn't help but notice this:
[http://ppa.launchpad.net/kitlaan/ppa/ubuntu](http://ppa.launchpad.net/kitlaan/ppa/ubuntu) jaunty main

are you using Jaunty or lucid?

---

### Post by BloodyIron on 2010-08-26
> **tripolitan said:**
> Couldn't help but notice this:
[http://ppa.launchpad.net/kitlaan/ppa/ubuntu](http://ppa.launchpad.net/kitlaan/ppa/ubuntu) jaunty main

are you using Jaunty or lucid?

Lucid, 10.04. As such I put Lucid in the repo name, as the article suggested. I have since removed those repos and the auth key.

---

### Post by BloodyIron on 2010-08-27
I have fixed this problem, the daemon was running elsewhere in another pid, as such prevbenting me from properly starting it.

Please close this thread, or something like that.

---

