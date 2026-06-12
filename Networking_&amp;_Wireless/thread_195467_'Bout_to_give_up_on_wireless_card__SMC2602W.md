---
title: "'Bout to give up on wireless card:  SMC2602W"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by Culito on 2006-06-12
After some searching and fiddling around, I I couldn't find my card on the ndiswrapper list, but I found another card with the same AMD chipset, and they were the same drivers on my cd:
Card: Sitecom WL-011 v2

    * Chipset: AMD AM1771
    * Driver: [http://www.smc.com/files/AQ%5CDR_SMC2602Wv3_2_5.zip](http://www.smc.com/files/AQ%5CDR_SMC2602Wv3_2_5.zip)
    * Other: This driver works only with 2.6 kernels with preemption enabled (tested with vanilla 2.6.15 and 2.6.16 kernels with preemption enabled). Works with ndiswrpper 1.12 with WPA-PSK + TKIP. 

More fiddling, and I get this from ndiswrapper -l:
Installed ndis drivers:
netam772                driver present, hardware present

Well, that's a good start.  But that's it.  The card doesn't show up in networking.  I installed Network Manager, but....where is it?  How do I run it?  It isn't in Apps>Internet like I thought it would be.

ifconfig shows:
 eth0      Link encap:Ethernet  HWaddr 00:50:BA:C4:45:65
          inet addr:12.206.102.122  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fec4:4565/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:299945 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3857 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:22771301 (21.7 MiB)  TX bytes:547057 (534.2 KiB)
          Interrupt:3 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:178486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:178486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13970412 (13.3 MiB)  TX bytes:13970412 (13.3 MiB)

So that's my wired eithernet, but no wlan stuff.
iwconfig shows:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

And that's that, I guess.  Any ideas?
-C

---

### Post by Culito on 2006-06-13
Anyone?

---

### Post by Culito on 2006-06-14
Welp, After scouring the 'net for a few hours, and seeing a million zero-reply messageboard posts on other linux forums about this very card, I guess I can tell I'm out of luck.

---

### Post by Culito on 2006-06-14
Strange...I can't even get the power light to come on.  It worked before....

---

### Post by noname101 on 2006-06-15
Did you run sudo modprobe ndiswrapper?

---

### Post by Culito on 2006-06-15
Yessir.  Tried everything in the book, It seems.  I even found a tip somewhere that told me to add in "RadioEnable|1" in the .conf files for the drivers...nothing works.

Ah, cards are cheap, I guess I'll get a supported one, but I still want to trick this one into working, for a challenge.

---

### Post by noname101 on 2006-06-15
Oops. Ok nevermind about ndiswrapper -l. But you could try ndiswrapper version 1.12.

---

### Post by topomorto on 2006-08-03
Hi!

I have the same prblem with the same card... Have you given up, or did you find a workaraound?

I think the answer is here:

 This driver works only with 2.6 kernels with preemption enabled (tested with vanilla 2.6.15 and 2.6.16 kernels with preemption enabled). Works with ndiswrpper 1.12 with WPA-PSK + TKIP.

So I will try (at least) to upgrade Ndiswrapper; it won't be easy as I am a total newbie with Linux/Ubuntu.

---

