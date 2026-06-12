---
title: "Atheros AR5007 card help/No wireless connection"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by racie on 2009-02-08
Okay so I've tried this many times before on Hardy Heron 8.04 with no luck.  I noticed some posts about people getting there Atheros AR5007 cards working on Intrepid Ibex 8.10, so I've decided to try that.  Already I noticed one big improvement...

On 8.10, under Hardware Drivers, it says "Support for Atheros 802.11 wireless LAN cards," next to my Nvidia Card stuff which was not there before on 8.04.  It is enabled, but the internet does not work.

I don't know if that is useful or not, but anyway...
When I run:
```
lspci -v|less
```

I get:
```
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Hewlett-Packard Company Device 137a
        Flags: fast devsel, IRQ 19
        Memory at f6000000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel modules: ath_pci

```

Note how Ubuntu thinks my AR5007 Atheros card is an Atheros AR242x.  How do I go about fixing my internet?  The last time I tried, I think I may have screwed up Ubuntu, so step by step will be greatly appreciated.  Thanks.

--Racie

---

### Post by superprash2003 on 2009-02-08
post output of the following
1)lshw -C network
2)iwconfig
3)iwlist scanning

---

### Post by racie on 2009-02-08
For ```
lshw -C network
``` I get:
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:08:7d:34
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.68 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 76:0a:c5:bd:3a:d3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

For ```
iwconfig
``` I get:

```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

For ```
iwlist scanning
``` I get:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

Right now I am using a wired connection to use the internet.

---

### Post by racie on 2009-02-08
Bump.

---

### Post by racie on 2009-02-08
Oh, I forgot to mention that I have the 64-bit version of Ubuntu 8.10.  Can anyone help me?

---

### Post by racie on 2009-02-08
Bump.  Does anyone think this will work or has anyone tried it before?
 [http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/comment-page-3/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/comment-page-3/)

---

### Post by mohitchawla on 2009-02-08
This thread helped me to get my AR5007EG card working. 

[http://ubuntuforums.org/showthread.php?t=964836]("http://ubuntuforums.org/showthread.php?t=964836")

Basically get the latest wireless drivers ( the link's in the thread) and compile them...nothing complicated. :)

---

### Post by racie on 2009-02-08
> **mohitchawla said:**
> This thread helped me to get my AR5007EG card working. 

[http://ubuntuforums.org/showthread.php?t=964836]("http://ubuntuforums.org/showthread.php?t=964836")

Basically get the latest wireless drivers ( the link's in the thread) and compile them...nothing complicated. :)

Thanks for the link.  The first solution does not work and in the second solution, the link does not work.  I was wondering if it was a good idea to try to use this how-to: [http://oesediez.blogspot.com/2008/11/intrepid-atheros-wifi-card-on-compaq.html](http://oesediez.blogspot.com/2008/11/intrepid-atheros-wifi-card-on-compaq.html)

It is the same kind of WiFi card and laptop I have, and most people that commented this seem to have working internet now.  Think I should give it a go?

---

### Post by racie on 2009-02-08
Bump.  Okay, the how-to in my link didn't work for me.  I disabled the "Support for Atheros 802.11 wireless LAN cards" and rebooted, but when I do the first step, which is typing ```

sudo aptitude install linux-backports-modules-intrepid-generic
``` in terminal, I get:
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Can someone *please* help me??

---

### Post by yknivag on 2009-02-08
Hi racie,

I can't help you directly with your problem, I'm guessing you have an HP laptop with the builtin card.  My Dad has the same issue (shows as AR5007 in Windows but AR242x in linux) and his doesn't respond with the normal ath_pci madwifi driver or the new ath5k madwifi driver from backports or ndiswrapper. :(

As for the last problem you have with aptitude unable to get a lock that suggests you have synaptic open or update manager is running.

You could try:

```
ps -e | grep -i "apt"
``` or ```
ps -e | grep -i "syn"
``` to try and find it and then kill it, or you could just shut it down if you can see it ;)

I'll be very interested to know if you do get this card working as I've been trying for some time to help my Dad.

---

### Post by racie on 2009-02-08
> **yknivag said:**
> Hi racie,

I can't help you directly with your problem, I'm guessing you have an HP laptop with the builtin card.  My Dad has the same issue (shows as AR5007 in Windows but AR242x in linux) and his doesn't respond with the normal ath_pci madwifi driver or the new ath5k madwifi driver from backports or ndiswrapper. :(

As for the last problem you have with aptitude unable to get a lock that suggests you have synaptic open or update manager is running.

You could try:

```
ps -e | grep -i "apt"
``` or ```
ps -e | grep -i "syn"
``` to try and find it and then kill it, or you could just shut it down if you can see it ;)

I'll be very interested to know if you do get this card working as I've been trying for some time to help my Dad.

Thanks.  It installed, I rebooted... aaand nothing.  I can now enable or disable wireless, but I don't have a wireless connection.  Any ideas of what I can do?

[COLOR="Blue"]*edit*  Nevermind, it took a minute for it to show up.  Yay.  Thank you![/COLOR]

---

### Post by yknivag on 2009-02-08
> **racie said:**
> [COLOR="Blue"]*edit*  Nevermind, it took a minute for it to show up.  Yay.  Thank you![/COLOR]

Did you get the wireless working?

---

### Post by racie on 2009-02-08
Yep.  I'm using it right now.  How do I edit the title of my thread to post [SOLVED] at the end?

---

### Post by yknivag on 2009-02-08
Great news! If you don't mind me asking, how exactly did you get it to work?

Oh, and you can't mark threads as solved at the moment, there were some issues with the forum database and the function has been removed for a while :(

---

### Post by racie on 2009-02-08
Oh, I used this: [http://oesediez.blogspot.com/2008/11/intrepid-atheros-wifi-card-on-compaq.html](http://oesediez.blogspot.com/2008/11/intrepid-atheros-wifi-card-on-compaq.html)

Remember that this is for Ubuntu version 8.10 (Intrepid Ibex) and NOT Ubuntu version 8.04 (Hardy Heron).  I couldn't get mine to work at all on Hardy and everyone on this page got theirs working, so I thought I'd give it a shot.  Good luck!

---

### Post by yknivag on 2009-02-08
Thanks racie, I'll have another go when I'm next with my Dad's laptop.

Incidently, do you also experience the strange startup behaviour that some people mention in the comments there?

---

### Post by racie on 2009-02-08
Do you mean that Ubuntu gets stuck in the startup?  I have to hold down the enter button for Ubuntu to keep booting.  As far as I'm concerned, other than a petty annoyance, this isn't a major problem.  I just have to remember to hold down the enter key when it boots.  =P

---

### Post by yknivag on 2009-02-08
Yes, that's what I meant. I agree it's petty, and of no real consequence.  It's just baffling! ;)

Really glad you got the wifi working though - gives me hope that I'll be able to fix my Dad's.

---

### Post by racie on 2009-02-08
Hope you have as much luck as I did. :D  Oh, and another thing... this is a solution for Ubuntu version 8.10 (Intrepid Ibex).  I couldn't get the WiFi card to work on previous versions.

---

