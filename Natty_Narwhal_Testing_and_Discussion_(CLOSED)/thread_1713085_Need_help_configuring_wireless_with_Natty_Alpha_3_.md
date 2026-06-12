---
title: "Need help configuring wireless with Natty Alpha 3 running live"
date: 2011-03-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ClientAlive on 2011-03-23
Hi all,
 
Could someone please help me? I'm kinda new to using forums and I had an issue I wasn't sure where I should post. Since it has to do with Ubuntu 11.04 Alpha 3 (Natty Narwahl) I didn't know if I should post somewhere where they are talking about Natty or somewhere where they are talking about what my issue is.
 
Last night I posted in another thread where they were talking about Natty and this [http://ubuntuforums.org/showthread.php?p=10591404#post10591404](http://ubuntuforums.org/showthread.php?p=10591404#post10591404) is the link to that thread. Now I'm not so sure I shouldn't have started a new thread here. Sorry.
 
Any help would be much appreciated.
 
Thanks
Jake

---

### Post by uRock on 2011-03-25
Moved to Natty Narwhal Testing and Discussion.

---

### Post by cariboo on 2011-03-25
It would help if you told us what wireless chipset your system uses, if you don't know, open a terminal and type:

```
lspci | grep Network
```

the output should look something like this:

```
lspci | grep Network
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```

---

### Post by ClientAlive on 2011-03-25
I'm working on it right now cariboo907. I just got back from work and I was sooo tired I had to get some more rest. I'm up and I'll have a new post up here in a little bit. Thank you. 
 
Jake
:)

---

### Post by ClientAlive on 2011-03-25
Ok. Here we go. I ran "lspci | grep Network" and it's result can be seen in the attachment. I also ran "ifconfig", "iwconfig", "lsmod", and "dmesg". If any of that information is useful let me know and it is available.

By the way - I don't know if this makes any difference in what is displayed in terminal but internet does work for me when plugged in with ethernet cable. When I ran most of those listed above the ethernet cable was in fact plugged in.

Thanks again.

Jake

PS: Figured out how to copy and paste info from the terminal. Thank God! Silly thing, I was trying to use the [hotkeys?] the time before this and the terminal won't let you do that. Right click works.

---

### Post by cariboo on 2011-03-25
You probably need an ethernet connection to install the drivers you need, I'm very sure that you need the firmware-b43-installer, to get your device to work, I have the same chipset in one of my systems in my shop, I'll check tomorrow and post back.

---

### Post by nm_geo on 2011-03-25
> **ClientAlive said:**
> Ok. Here we go. I ran "lspci | grep Network" and it's result can be seen in the attachment. I also ran "ifconfig", "iwconfig", "lsmod", and "dmesg". If any of that information is useful let me know and it is available.

By the way - I don't know if this makes any difference in what is displayed in terminal but internet does work for me when plugged in with ethernet cable. When I ran most of those listed above the ethernet cable was in fact plugged in.

Thanks again.

Jake

PS: Figured out how to copy and paste info from the terminal. Thank God! Silly thing, I was trying to use the [hotkeys?] the time before this and the terminal won't let you do that. Right click works.

+1 on what cariboo told you.  Have you tired to install any wireless drivers with the ethernet cable attached? 
I would think you could go to Synaptic and install the firmware-b43-installer and the b43-fwcutter. Or open a terminal and use 
```
sudo apt-get install firmware-b43-installer
```then 
```
sudo apt-get install b43-fwcutter
```By the way, you can just copy the terminal output between the  brackets.

Another good one for us to see would be 
```
sudo lshw -C network
```Here is mine 
```
*-network               
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:c1:24:e5
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5752-v3.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:efcf0000-efcfffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7d:c5:67:29
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-7-generic firmware=410.2160 ip=192.168.1.102 link=yes multicast=yes wireless=IEEE 802.11bg

```Our wireless chips are in the same family.

---

### Post by ronacc on 2011-03-25
wouldn't he need to be running from an install to do that not the live cd , or don't they need a reboot to be activated .

---

### Post by nm_geo on 2011-03-25
> **ronacc said:**
> wouldn't he need to be running from an install to do that not the live cd , or don't they need a reboot to be activated .

Yes you are right ronacc.  I have got the b43 working when using a live USB in Lucid and Maverick but as soon as I shutdown and rebooted it was obviously not installed just working in memory. I really did not think about the OP saying running live vs installed but I see the OP is running on live CD or USB now.

---

### Post by ClientAlive on 2011-03-26
Thanks guys.
 
cariboo907, ronacc and nm_geo I'll make a quick attempt at getting those drivers installed and see if I can get my wireless working with live 'CD' first them I'll probably go ahead with the install. I've been flirting with the idea for a few days now since I know I can get internet while plugged in. This way, I can do whatever tweaks or installs I need to, to get up n' running. I'll also see if I can get Windows back on my desktop for now so if something happens to this machine while I'm working on it I'll still be able to communicate with ya' all. :D
 
nm_geo I'm in Windows right now. I'll have to reboot into Ubuntu in a min here and I'll get the rudown from "sudo lshw -C network" and add it as an attachment. Btw, no, I haven't specifically gone out for any drivers with the ethernet cable plugged in - unless you consider my response a couple times to the pop up that says "restricted drivers available". I went to the app "additional drivers" and told it to get it. Afterwards it said the driver was enabled so I guess if it has to go on the internet to get it it was successful. I've used this o/s live both with and without it and I can't tell any differnce. I think it was a graphics driver it was talking about if I remember correctly.
 
I have to let you all know that this whole business may take me a while so it may be a while before I can get back here. Prob most of the day tomorrow (providing nothing else comes up to take me away from it).

nm_geo: if our chips are in the same family does that make us brothers? :)
 
Peace out for now all. I'm gonna get that attachment on here then time to hit the sack for this kid.
 
All my best to ya'
Jake

----------------------------------

One last question I have before looking for that b43 installer that was mentioned. In the results of "sudo lshw -C network" I saw an entry under "network 1" that made me wonder if I don't already have that driver. Here is the copy and paste of that line: "configuration: driver=b43-pci-bridge latency=64". Is the "installer" something different than what that entry is saying? It also said something like 'network disabled' (near the last part I think). Could I need to enable it or something?

Thanks

---

### Post by nm_geo on 2011-03-26
You might be able to get the wireless working with the live CD, but it will not be persistent only on that session. In other words, when you shutdown and reboot the wireless will not be working.  You do have the b43 driver listed and looks like the firmware is still needed.

It will be easier to get your wireless working after you install Natty 11.04 to your hard-drive and use the ethernet cable to get the updates that are numerous daily.  In my opinion you could install Lucid 10.04 or Maverick 10.10 and have a lot less daily updates, but if you want 11.04 installed that okay too.

---

### Post by ClientAlive on 2011-03-27
Well I dbaned my drive and got Natty installed. Everything seems to be working fine but I had a heck of a time finding the driver earlier. I'll have to look for it tomorrow.

Jake

---

### Post by cariboo on 2011-03-27
I'd suggest clicking the Application icon, and typing **syn** in the search box then click the Synaptic Package Manager icon, then once synaptic is open type b43 in the quick search box.

---

### Post by ClientAlive on 2011-03-27
Well I downloaded b43-fwcutter following the way you said cariboo907 (post #13) but after it installed I'm a little confused about a couple things.

I found this web page: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) that talks about doing what we're talking about and it mentions needing to " . . .either remove or unload the broadcom-wl driver first prior to using b43 . . ." I don't know how to do that though.

Also, don't I need to actually run b43-fwcutter or is everything done already by just downloading it? There is another link in the page mentioned above: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access") and about half-way down, under the heading: "b43 - Internet access", there is a picture of some gui for fwcutter. this makes me think that I do need to run the thing, have it fetch the driver and install it in the right place/ way for me. How to do this though? I looked for b43-fwcutter in applications and I tried through 'additional drivers' but didn't see it in either place.

Also, is there a way to double check if it is installed properly after running it?

Finally, do I need to do another thing or two after the above? Namely - Enable the device or something along those lines? Configure the wireless account (like with my MAC address and password or something like that)? Restart? Don't restart?

In the meantime I'm going to keep looking for the answers with google and see how far (if any) I can get.

Thanks guys.

Jake
:)
----------------------

One last thing: do I also need to get "firmware b43 installer?" So, 'Installer' and 'fwcutter'?

---

### Post by ClientAlive on 2011-03-27
I've been trying to make sure I'm fully updated too by typing "sudo apt -get update" but am getting: "sudo: apt: command not found" returned in terminal. Does version 11.04 use different commands or something? Could it just be a bug?

Jake

---

### Post by cariboo on 2011-03-27
The way to find out if the driver is installed is to open a terminal and type:

```
sudo lshw -C network
```

You have an extra space in your apt-get command, that's why it didn't work.

---

### Post by ClientAlive on 2011-03-27
Thanks cariboo907. I still don't  understand how to run the fwcutter I downloaded what I mean is to 'launch' it), whether I need to get  the installer also, etc and I'm having a heck of a time finding that  info via google. When I downloaded it it just installed it or whatever  and that was it. No interface opened up, no selections to be made or  prompts to be answered. I had looked for it in all the places I knew and diddn't see a way to launch it. I was just able to find via a search of my installed programs through 'software center' but there doesn't look like a way to launch from that app. If this was mentioned in this thread before and I  just missed it I'm sorry. I'll look back through this thread very  carefully again to see if I missed something.

Thanks

---

### Post by ClientAlive on 2011-03-27
I got it. Wireless is working and it wasn't as difficult as I had feared. Just so new to this and I did miss something cariboo907 instructed me on. It was the installer I needed. It does just install and there is nothing to launch or do after that.

Thanks so much for all your help guys. Sorry I was so dumb about it all.

Sincerely,
Jake

:popcorn:

---

### Post by cariboo on 2011-03-27
I'm glad you got wireless working, we were all new users at one time, and I know I made a lot of mistakes when I first started using Linux. 

Things have gotten to the point where almost any one can install and setup a linux distribution, no matter what their skill level, especially with all the help available via the internet.

---

### Post by ClientAlive on 2011-03-30
Thanks for making me feel welcome cariboo907. Sorry been away so long.

Jake

---

### Post by nm_geo on 2011-03-30
Excellent Jake now we are brothers LOL.

---

