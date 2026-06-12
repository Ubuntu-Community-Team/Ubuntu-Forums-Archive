---
title: "Broadcom 4306 Issue"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by MBWoessner on 2010-06-13
I started using Ubuntu a few months ago and went through all the initial headaches that are associated with getting my wireless card working.  I was finally able to get everything stable and working automatically each time I started my computer, and then BOOM!, motherboard went out and I was dead in the water.  I transferred my hard drive and wireless card to a new system, hoping that everything would pick up where I left off, but no such luck.  I'm back to square one with no working wireless connection.

I've looked all over the internet and on these forums, but I still can't get it working.  I think the biggest issue is that, unlike most people asking about this issue, I've already installed all the required pieces and got it working, but now the pci card is on a different motherboard and a different location.  I don't know how to correct this issue to an information would be greatly appreciated.

A couple pieces of information that I know about

lspci

01:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

iwconfig

wlan0     IEEE 802.11bg   ESSID:""
             Mode:Managed   Frequency:2.412 GHz   Access Point: Not-Associated
             Tx-Power=0 dBm
             Retry   long  limit:7      RTS thr:off     Fragment thr:off
             Power Management:off
             Link Quality:0   Signal level:0   Noise level:0
             Rx invalid nwid:0   Rx invalid crypt:0   Rx invalid frag:0
             Tx excessive retries:0   Invalid misc:0   Missed beacon:0

Also, when I go to System>Administration>Hardware Drivers, Broadcom B43 wireless driver is listed and it also mentions fwcutter, but I get an error message when I try to activate it.

Sorry, installation of this driver failed.
Please have a look at the log file for details: /var/log/jockey.log

Any help?

---

### Post by purelinuxuser on 2010-06-13
Hmm... post the output of
```
lshw -c network
```

You can try to perform the following steps to get the wireless working again:

[LIST=1]
[*]Plug into Ethernet for an Internet connection
[*]Open Synaptic and install b43-fwcutter
[*]During the installation you will get a prompt with a checkbox: "Automatically download and install firmware?" make sure it is **checked**
[*]Restart the computer
[/LIST]

---

