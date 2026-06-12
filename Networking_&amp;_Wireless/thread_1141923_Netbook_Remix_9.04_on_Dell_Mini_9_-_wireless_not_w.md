---
title: "Netbook Remix 9.04 on Dell Mini 9 - wireless not working"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by fsigti on 2009-04-28
I successfully installed Ubuntu Netbook Remix 9.04 from Live USB onto my new Dell Mini 9 last night. Everything works as it should, except wireless.

Upon initial startup, the system detected the wireless card and installed the restricted Broadcom STA driver. The Network Manager applet allows me to disable/enable wireless.  However, I do not see a list of hotspots in the area (I know there are 15+).  I also cannot join my home WPA2 AES network. The connection attempt times out, then I get asked for my WPA2 key over and over again.

ifconfig shows the wireless adapter (eth1) and its MAC address.
iwconfig shows the presence of the card.

I plugged the Mini 9 into my router with ethernet cable and ran all system updates. No luck.

I Googled and searched the forums but only found sparse discussions about this issue.  Ubuntu claims full tier 1 support for the Mini 9, but so far, wireless not working is pretty much a deal breaker.

Any suggestions before I dust off my USB CD-ROM and reinstall Windows XP SP3 (ack) with _full_ driver support?

---

### Post by fsigti on 2009-04-29
I reinstalled UNR tonight but wireless still does not work.

No other Mini 9 users experience the same issues with wireless on 9.04 UNR?

---

### Post by fsigti on 2009-04-29
EUREKA!

I followed the ideas in the first post of this thread:

[http://ubuntuforums.org/showthread.php?t=1134631](http://ubuntuforums.org/showthread.php?t=1134631)

Primarily, I entered the BIOS and reset it to factory settings (despite not having actually made any changes in the past...).  I also hit Fn + 2 (to toggle the wireless) before the Linux kernel booted.

I'm not sure which of these tweaks did the trick, but I verified that the Network Manager in both the locally installed OS, and a new Live USB, was working.

---

### Post by rico suave on 2009-10-28
IT WORKED!

I had the same problem.  Following the previous post this is what I did:

- Restart
- I hit 2 quickly right after the Dell logo appears
- Once in BIOS I moved to the advanced tab (don't know if it makes a difference) and reset to the default values
- Save and rebooted
- It worked

---

### Post by maggiemonic on 2010-02-10
i just had the same problem on my eeepc 1000. 

pressing Fn and F2 together, to turn on wireless, was all that was needed.

---

