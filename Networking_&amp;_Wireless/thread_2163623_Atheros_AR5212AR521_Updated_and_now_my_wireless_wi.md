---
title: "Atheros AR5212/AR521: Updated and now my wireless will not work."
date: 2013-07-19
forum: Networking &amp; Wireless
---

### Post by bmavbeard on 2013-07-19
Ok, I have looked and looked and looked on the forums trying to find a solution.  Either it was way too complicated, I didn't trust the information (not this forum :) , or it was outdated.  So I am in DESPERATE need of help.

Here is some information. I have a desktop not a laptop so no kill switch commands will help me I don't think.

A long time ago I installed a Netgear Wireless PCI adapter (not a usb but the card that comes with the antenna on the back and you permanently install to the computer)

It worked right out of the box with jaunty (as far as I can remember)

I recently came back to ubuntu and had to update from every version since jaunty up to 12.04 LTS version.  Shew, that was a lot of work and you may say I should have did a fresh install but I couldn't (I currently I have a hard drive that is partitioned and windows is on part of it so a fresh install is just not going to work right now).

Now, I cannot get my wireless to do anything (if this helped it stopped working on the first update after jaunty).  I can only connect with a ethernet chord :(

One thing that searching through the forums taught me was how to look up 

   sudo lshw -C network

I will post that at the bottom.  Also I learned that the driver that is supposed to work is something like aht5k and I even though I have Netgear it is really Atheros ar5212/5213

I came across something about MadWireless (or something like that) but after all the warnings I am afraid to go there.  Something about it doesn't update/etc.  I have seen lots of conflicting information on posts about killswitches so I am terrified to try that now.

Can someone please help me?  Also, please notice I have very little beans.  I am a noob.  I can open a terminal.  I can use a gui.  I need help on almost anything else.  I hope that one day when I get better I can help other people too.

Ok, here is the information:

   
sudo lshw -C network
   *-network:0 UNCLAIMED    
        description: Ethernet controller
        product: AR5212/AR5213 Wireless Network Adapter
        vendor: Atheros Communications Inc.
        physical id: 1
        bus info: pci@0000:01:01.0
        version: 01
        width: 32 bits
        clock: 33MHz
        capabilities: pm bus_master cap_list
        configuration: latency=64 maxlatency=28 mingnt=10
        resources: memory:feaf0000-feafffff
   *-network:1
        description: Ethernet interface
        product: 82562EZ 10/100 Ethernet Controller
        vendor: Intel Corporation
        physical id: 8
        bus info: pci@0000:01:08.0
        logical name: eth0
        version: 02
        serial: 00:11:11:a1:fb:f4
        size: 100Mbit/s
        capacity: 100Mbit/s
        width: 32 bits
        clock: 33MHz
        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=172.16.0.8 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
        resources: irq:20 memory:feaef000-feaeffff ioport:ddc0(size=64)
 

I hope that gives someone enough to work with.  3 days and I finally decided google searches were not going to help me.

---

### Post by carl4926 on 2013-07-19
let us see
```
lspci -nnk | grep -iA2 net
```

---

### Post by bmavbeard on 2013-07-19
> **carl4926 said:**
> let us see
```
lspci -nnk | grep -iA2 net
```

Here is what I got (I deleted the part that referred to my computer name - didn't think you needed that).  Is it going to work now?

~$ lspci -nnk | grep -iA2 net
01:01.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212/AR5213 Wireless Network Adapter [168c:0013] (rev 01)
    Subsystem: Netgear Device [1385:5e00]
    Kernel modules: ath5k
01:02.0 Modem [0703]: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI [8086:1080] (rev 04)
--
01:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)
    Subsystem: Dell Dimension 3000 [1028:019d]
    Kernel driver in use: e100
~$ ^C
~$

---

### Post by carl4926 on 2013-07-19
Is it possible you previously used madwifi?
I found
[http://wiki.debian.org/ath5k](http://wiki.debian.org/ath5k)

---

### Post by bmavbeard on 2013-07-19
> **carl4926 said:**
> Is it possible you previously used madwifi?


I am 98% sure I didn't unless that is what came standard with jaunty (Is that possible?)  On the off chance that I did is there a way to know that I did (a directory maybe I could check?)  I used dash and I looked around I am pretty sure I have never used this.  I talked about it earlier becuase I was afraid to use it.  Please forgive me but just a noob and not sure how to check.

> **carl4926 said:**
> [http://wiki.debian.org/ath5k](http://wiki.debian.org/ath5k) 

I found this yesterday and looked and looked and looked and I couldn't do anything on this page to help me.  I didn't do the steps after madwifi because I don't think I ever used that.

Thanks for the reply

---

### Post by carl4926 on 2013-07-19
I take it then the wireless didn't work in the live session.

---

### Post by bmavbeard on 2013-07-19
> **carl4926 said:**
> I take it then the wireless didn't work in the live session.

This makes me think you think I am using a cd.  I don't have a live CD for 12.04 (I guess I could make one with an iso...) I do have one for Jaunty somewhere (that is old aint it!).  Isn't that what is meant by live session (running from cd)?  Sorry, all these terms I don't have down 100%.  If it helps, I have it installed on the hard drive.  It is a dual boot machine with xp in the other partition.  Now, if the question is does my wireless work on Ubuntu, no.  It does on Windows XP.  (It seems that there are some things just way easier on Windows still but I am really trying to get better at Ubuntu.)  Thanks for all the help.

---

### Post by carl4926 on 2013-07-19
Reason I ask is:

1. You said you upgraded from Jaunty > 12.04 step by step - this concerns me

2. I know you are installed. But most people try the Live CD. And it's not unheard of for wireless to work live and then not post install.

I would like to know if 12.04 wireless works from a live cd, so if you can, download it, burn it and boot it up?
Because I feel confident the result will be good.

---

### Post by bmavbeard on 2013-07-20
> **carl4926 said:**
> Reason I ask is:

1. You said you upgraded from Jaunty > 12.04 step by step - this concerns me

2. I know you are installed. But most people try the Live CD. And it's not unheard of for wireless to work live and then not post install.

I would like to know if 12.04 wireless works from a live cd, so if you can, download it, burn it and boot it up?
Because I feel confident the result will be good.


I get it now!  Great idea.  I was thinking I needed to probably do a fresh install anyway this will let me see if that will work.  I will try it and give a holler when I hear.  Pretty smart thinking.

---

