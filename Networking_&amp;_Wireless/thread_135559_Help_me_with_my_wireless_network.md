---
title: "Help me with my wireless network"
date: 2006-02-24
forum: Networking &amp; Wireless
---

### Post by ltmon on 2006-02-24
Hi All,

I just bought home a linsys PCI wireless card (WMP54G) and AP (WAP54G) in order to reduce cable clutter in my house.

Unfotunately I'm not getting anywhere.  The AP comes with a wizard setup, which is of course windows only.  I tried to connect to the AP via it's web interface on the default IP address (192.168.1.245), but I keep timing out.  The AP is displaying it's staus LED's correctly, according to the manual, but it's just not on my network.

My router has an "Attached Devices" page on it's setup screen, but this simply lists my computer's IP and no other device.

Anyone with a clue how to debug this?

Is my AP just broken?  I can't even ping it.

Cheers,

L.

---

### Post by andrewsawyer on 2006-02-24
If your AP has a hard connection (cat5), I would suggest connecting through this first to make sure it's all ok.  It may be that it is the card you are having problems with rather than the AP.

Can you show us what is displayed if you type 'ifconfig' into terminal?  This should confirm whether the card is set up in the pc.

---

### Post by ltmon on 2006-02-24
The card seems fine (to my knowledge in any case).  I still am maintaining a wired connection to my router on eth0 (which is how I am able to post this).

I thought that (ignoring my PCI wireless card) that if the AP is on my network I should be able to see it.  Is this a valid assumption?

ifconfig output:

```

eth0      Link encap:Ethernet  HWaddr 00:01:80:4A:6E:50
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::201:80ff:fe4a:6e50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8353 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7521 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1373550 (1.3 MiB)  TX bytes:621775 (607.2 KiB)
          Interrupt:177 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)

```

Note: I have a netgear router and netcomm modem, which could be the cause of the problem.

Thanks,

L.

EDIT:  I just noticed that the ifconfig output I gave you does not contain ra0 (my PCI cards device).  I don't know why it dissapeared... but it did at some stage.  I'm investigating that now.

EDIT AGAIN: I found ra0 by issuing 'sudo ifup ra0'.  My output for 'ifconfig ra0':

```

ra0       Link encap:Ethernet  HWaddr 00:14:BF:78:D1:C7
          inet6 addr: fe80::214:bfff:fe78:d1c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:2 txqueuelen:1000
          RX bytes:115081 (112.3 KiB)  TX bytes:39257 (38.3 KiB)
          Interrupt:201

```

---

### Post by andrewsawyer on 2006-02-24
ra0 is your wireless card?

Can you confirm that if you go to System >> Administration >> Networking that you can see both devices - wired and wireless?  If you can, double check that the Wireless connection is configured and activated.

Looking at the output you have given, it hasn't been allocated an IP address for the AP, nor by the look of it is it even aware of one.  In the wireless card properties (from the menu given above), you will need to enable the connection, plus advise of the SSID of the AP (should be in the manual, or you can set it up by connecting with cat5), as well as any WEP code that you might have set up.

If you add Network Monitor to the gnome-panel, you should be able to set it to display ra0, and you will be able to see at a glance whether it is connecting or not, with a reception quality bar too.

Wireless can be a stumbling block when it comes to Linux, so keep posting and we'll try to get you set up.

---

### Post by ltmon on 2006-02-24
OK, ra0 is active and configured using the default SSID.

As I can't actually connect to my AP to configure the SSID I can't change this off the default.  I have CAT5 from my PC to my router and then from my router to the AP, but this is not allowing me to configure the AP.

Connecting directly from PC to AP does not help either.  I simply cannot get to the AP admin screen.

After a few 'ifup', 'ifdown' plays I got 'ifconfig ra0' to output:

```

ra0       Link encap:Ethernet  HWaddr 00:14:BF:78:D1:C7
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:bfff:fe78:d1c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:423 errors:0 dropped:0 overruns:0 frame:0
          TX packets:417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:2 txqueuelen:1000
          RX bytes:118020 (115.2 KiB)  TX bytes:42596 (41.5 KiB)
          Interrupt:201

```

And what do you know?  It's connected!!!!  I'm sure I did this a dozen times before!

OK, so now I take down my wired connection ('ifdown eth0') and everything is still good.

Unfortunately I still cannot connect to the AP directly to configure it.  Because of this I have the default SSID and no WEP/WPA security.  I _DO NOT_ want to continue using my wireless network in this way :(

It is rather confusing (to me anyway).

L.

---

### Post by andrewsawyer on 2006-02-24
I've just had a quick Google and it looks like you may have to use NdisWrapper on your card.  I found a link to a how-to that uses other drivers, but they cost $15, and why pay for what you can get for free right?

NdisWrapper can be found at [Sourceforge]("http://ndiswrapper.sourceforge.net/"). I also found this how-to to get your specific model of card working with the NdisWrapper.  You can find it [here]("http://www.linuxquestions.org/linux/answers/Networking/Slackware_Installing_Linksys_WMP54G_with_NDISWRAPPER_11").

My girlfriend has the same problem by the look of it, whereby she can connect to the AP but not use it.  She had to use an extra app too.

There are a couple of things about the how-to that I've just noticed, as it is based on Slackware not Ubuntu:

1) you need to compile, so you will need your kernel source, headers, and build-essential, all of which can be downloaded from Synaptic.

2) it mantions /etc/modules.conf.  This is just /etc/modules in Ubuntu.

There may be more, however I'm not a network guru by any means.  I beleive there is also an NdisWrapper How-To in the Ubuntu forums.

I'm sorry if this feels like I'm palming you off - I'm not.  Give it a go, and if still no joy, or you are unclear on terminology then post back - and that's not to be patronising - just not sure of your experience level.

---

### Post by ltmon on 2006-02-24
The card seems fine.  I posted my last post using it.

I finally got a connection to the AP by using wine to run the windows setup program!!!  I then set it up to use DHCP rather than a static IP address, and I can talk to it fine now.  I think the problem was the default IP for the AP was not in my subnet (192.168.0.*).

But now my pci card has gone down... *sigh*.  I'll give it another go tommorrow, I'm tired now.

L

---

### Post by ltmon on 2006-02-24
OK, so I turned on the computer this morning and everything worked just fine.

Basically I needed to make sure my AP was on the same subnet as the rest of my network devices.  I could have done this by adjusting my subnet to include the default IP address of the AP, but luckily I was able to use Wine with the supplied setup utility from Linksys to set the AP to use DHCP.  That was a real surprise, as it worked perfectly.

Once that was done everything else kinda fell into place.

Thanks for the help andrewsawyer.

L.

---

