---
title: "Cannot access internet with wireless router LinkSys e1200"
date: 2012-09-26
forum: Networking &amp; Wireless
---

### Post by jcmcnch on 2012-09-26
Hi everyone,

This is my first post, so thanks in advance for any help! I'll try to reciprocate down the road when I get more experience! 

I'm having trouble accessing my home wireless network through ubuntu - it was working fine last night, but now it inexplicably stopped working. I can connect to the router fine, but not to the internet. 

I've tried the usual resetting of modems and routers, and throughout all this painful process, I've determined that it seems to be probably a ubuntu-specific problem, since I am able to connect wirelessly through windows vista on the same machine (different partition). 

Confusingly, I'm not even able to connect to the internet plugging my ethernet cable directly to the modem in ubuntu, which is really weird to me and this works fine in Vista.

If anyone can offer any advice on how to troubleshoot this, I'd really appreciate it! Below is the partial output from nm-tool in case it helps. Thanks!

Jesse

nm-tool

- Device: wlan0  [Cisco17945 1] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl4965
  State:             connected
  Default:           yes

---

### Post by jcmcnch on 2012-09-26
OK, so I figured out what the problem was, and I thought I'd post it in case it saves someone else the grief that I had trying to fix it. It turns out that for some reason my VPN client was blocking my connection. I had tried unsuccessfully to connect to my workplace's VPN over wireless earlier in the day, and for some reason, that prevented me from logging onto my home network. All I did was connect to my router, log in to VPN (successfully this time) and bingo! I could connect to the internet and everything! What a waste of time...CISCO!!!:mad:

VPN Client: Cisco AnyConnect

---

### Post by jcmcnch on 2012-09-30
On closer inspection, it appears now that the problem is a bit more complicated than I previously thought. I can now connect to the internet at home, but ONLY when I log into my work VPN. Weird! Does anyone know why this might be? I found this thread that describes the same problem:

[http://ubuntuforums.org/archive/index.php/t-1936686.html](http://ubuntuforums.org/archive/index.php/t-1936686.html)

In case it helps, I am also having trouble connecting to my workplace wired connection too, I have to restart it a couple of times before it kicks in, and I can't seem to connect at all to the workplace VPN from my work's wireless network.

I can still connect to the internet, but it's just weird and irritating, and if anyone can shed some light or give me a sense of why it might not be working, I'd greatly appreciate the help!

---

### Post by jcmcnch on 2012-10-30
OK, finally have something to contribute - I figured it out! Yay! I can connect at home for the first time in over a month without VPN! :guitar::popcorn::KS

Here's what was causing the problem, in case anyone else runs up into this. I use my laptop both at work and at home, and for some reason, the default configuration in /etc/resolv.conf was overwritten with my work DNS servers. When I opened this file, it only showed my work's DNS server and not my ISP's server. Editing it manually did not help because Network Manager just reset it back to the same problem-causing configuration.

So what I did was to try and clear this to default, using a guide I found here:

[http://askubuntu.com/questions/134121/how-to-restore-recreate-etc-resolv-conf-files](http://askubuntu.com/questions/134121/how-to-restore-recreate-etc-resolv-conf-files)

I used both of the command line functions that the user desgua indicated, and now it works like a charm. Thanks desgua!

Can a moderator please mark this as solved? HTH people in the same situation!

---

