---
title: "Sudden Problems with Intel Wireless on Thinkpad Edge"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by nmaster on 2010-08-26
Until a couple of hours ago, everything was working perfectly on my Thinkpad Edge.  I was testing out the HDMI when that gave me an irreversible blank screen. This didn't worry me since it had happened before; I just held down the power button and forced a shutdown.

Upon restarting, I've had some issues with the wireless.  I'm able to connect to the network, but not to the internet.  I've tried booting to a LiveCD/LiveUSB and I have the same problem there (even though it used to work perfectly).

I checked with one of my roommates, everything works fine for him, so I'm very sure its not a problem with the router.

It seems like a hardware problem with my laptop. I was going to use the recovery discs to see what happens on Windows 7, but decided to ask for help first.

The wired ethernet works as expected.

Here is some info on the wireless card:
```

 sudo lshw -C network
  *-network               
       description: Wireless interface
       product: WiFi Link 1000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:26:c7:3e:7a:92
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.2 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:37 memory:f0500000-f0501fff


```

Let me know if there is anything else you need to know.

---

### Post by nmaster on 2010-08-27
UPDATE:

So I used the recovery discs and went back to Windows 7.  Still no luck with my home network.

I took my laptop to a different location and the wireless seems fine on a network without WPA.  When I'm back at home, I'll try disabling the encryption on that network and see if everything works.

Is it possible that this could be a hardware level problem?  I don't really know how the 802.11 encryption works.  Since it happens with both Windows and Ubuntu, I feel like it must be.  Has this happened to anyone before?

---

### Post by nmaster on 2010-08-27
a little bit of reading makes me feel that an issue with the encryption could be at the hardware level.  i guess this weekend i'll have to call tech support and see if they can send me a new wifi card. :(

---

### Post by nmaster on 2010-08-29
in case anyone cares, its not a problem with the encryption.  the card just doesn't work sometimes.  i should have a new card this week, if the lenovo people get they're act together.

---

### Post by nomnex on 2010-09-14
How's the new card doing?

---

### Post by nmaster on 2010-09-14
> **nomnex said:**
> How's the new card doing?

the new card is good.  i had to sent the entire laptop into the depot so i didn't have it for a week.

the downside is that at the depot someone broke my keyboard :(  some of the keys don't work (they did before).  i'm a little disappointed, but i guess i've just had some bad luck. they're going to fix it, but i don't want to have to send it in again, since i need it for work. i'm kind of in limbo right now with the tech support people.  hopefully everything will work out for the best.

---

### Post by nomnex on 2010-09-17
> **nmaster said:**
> the new card is good.  i had to sent the entire laptop into the depot so i didn't have it for a week.

the downside is that at the depot someone broke my keyboard :(  some of the keys don't work (they did before).  i'm a little disappointed, but i guess i've just had some bad luck. they're going to fix it, but i don't want to have to send it in again, since i need it for work. i'm kind of in limbo right now with the tech support people.  hopefully everything will work out for the best.

support centers often suck. Qualified technicians but careless. 99% of the private customers won't complain and get over it. They don't even care to open the notebook to check inside, once they get it back.

I fix my notebook alone. If it is a major failure and the computer is still under warranty (and new). I send a warning notice about the PC condition to sign and to return to me, before they work on it. I also contact the manager to detail the PC condition upon arrival. It is dumb, pain-in-the-ssa-style, but it usually works. It takes longer (~1 more week) for the repair, but no a single scratch ever since I do that.

---

