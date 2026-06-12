---
title: "Wireless is touch and go now in 9.10"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by gerowen on 2009-11-01
Now I've been away for a bit, but I used 9.04 and never had a problem.  Now in 9.10 my wireless seems to be, touch and go.  Like it'll hang every now and then.  Only shortly before installing 9.10 I had vista on this same machine and never had a problem, and the other PCs in the house don't have this issue, so it's not my networking equipment.

I'm using a 64 bit WPA2-Personal key on Wireless-G, a WRT54G Linksys router, been using the same one for a while now.  I'm using a Toshiba Satellite L355D-S7829 with an Atheros(can't remember specific model) wireless card.  It worked fine in 9.04, here is a video so you can kind of see specifically what I'm talking about, watch my download of the Ubuntu Server Edition on the left.

[http://www.youtube.com/watch?v=eYYKu4zdJi4](http://www.youtube.com/watch?v=eYYKu4zdJi4)

Edit: I'm aware the displayed speed doesn't move much in the video even though I said "see how it fluctuates".  If you watch at the very beginning you'll see for a second what I meant, it was bouncing between like 10 kB/s to 600 kB/s and up to the normal 1 MB/s-ish

---

### Post by gerowen on 2009-11-01
New Information

Output of lspci
```
05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

When I run dmesg it kind of loops this:
```
[17542.286805] wlan0: associated
[17551.040087] wlan0: no probe response from AP 00:1c:10:c0:81:cc - disassociating
[17552.254866] wlan0: authenticate with AP 00:1c:10:c0:81:cc
[17552.451332] wlan0: authenticate with AP 00:1c:10:c0:81:cc
[17552.463710] wlan0: authenticated
[17552.463724] wlan0: associate with AP 00:1c:10:c0:81:cc
[17552.468079] wlan0: RX ReassocResp from 00:1c:10:c0:81:cc (capab=0x411 status=0 aid=2)

```

Kernel version returns 2.6.31-14-generic x86_64

---

### Post by Rallg on 2009-11-01
My EEEPC had no problem with wireless during the 9.10 late alpha and early beta stage. But within the past few days, apparently as the release was made final, something odd occurred. This is a 32 bit system, and I am in range of reasonably strong WiFi without password encryption.

It does not happen everywhere, as I migrate from place to place, leading me to think that it may have something to do with the WiFi transmitter in use at each place, or some other factor.

Sitting in the same location, switching back and forth between Windows XP and ubuntu 9.10, I sometimes find that there is a DNS problem on 9.10. That is, sites that should be immediate and easy to find must be "looked up" in 9.10, and there is a delay until the site is "found." Once it is "found" it loads quickly. Meanwhile, XP finds those sites immediately, as it did before.

Could it be that 9.10 has a problem with DNS, possibly due to a recent Firefox update that isn't yet on XP, or isn't a problem there?

Edit: Indeed, when I first submitted this post via FF on 9.10, it had to "look up" Ubuntu Forums, even though I was already on the site.

---

### Post by gerowen on 2009-11-01
I think it is a DNS issue, because I have a domain name set up with dyndns.org that works just fine every other time, but since 9.10 I get messages saying it can't resolve that hostname.

---

### Post by gerowen on 2009-11-02
I think I may have fixed it, I use MAC filtering on my wireless network to ensure that only devices I personally look at and configure will connect to my router.  My connection was repeatedly dropping off.  So I figured WTF and plugged the wireless card's MAC into the settings for my wireless network manually, and since then things have been responding a LOT faster and I haven't had a single drop in the past 30 minutes, and it usually happens once every 2 or 3 minutes for 10 seconds or so.  I wonder why this would fix the issue.

Edit: One reason this was really annoying is I also just upgraded my server and I'm using SSH/VNC to set it all up and having it freeze in the middle of me doing something was counter-productive.

---

