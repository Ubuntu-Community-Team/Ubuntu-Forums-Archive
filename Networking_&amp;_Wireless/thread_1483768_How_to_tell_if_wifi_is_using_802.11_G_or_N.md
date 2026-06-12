---
title: "How to tell if wifi is using 802.11 G or N?"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by nilbus on 2010-05-15
I can't figure out how to tell which wireless protocol is using to connect to my router with. Both my laptop and router support Wireless 802.11N, but I'd like to verify that it's actually using that since my router is in mixed mode.

I can't find that information in nm-applet's Connection Information screen, nor is it in iwconfig's output. I'm not sure where else I might look. I didn't find it in /var/log/syslog where all the connection logging happens. Ideas?

---

### Post by bkratz on 2010-05-15
> **nilbus said:**
> I can't figure out how to tell which wireless protocol is using to connect to my router with. Both my laptop and router support Wireless 802.11N, but I'd like to verify that it's actually using that since my router is in mixed mode.

I can't find that information in nm-applet's Connection Information screen, nor is it in iwconfig's output. I'm not sure where else I might look. I didn't find it in /var/log/syslog where all the connection logging happens. Ideas?

It actually is in iwconfig, there is probably a real way of discovering it, but this will show you.  I copied someone else's iwconfig from this forum below.

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off

You will see that it shows a bit rate of 11Mb/s (mega bits per second). If yours shows around 54Mb/s it is version G. Higher than that is version N. I think 11 is B, but not sure. Please correct if inaccurate so we all can learn.

---

### Post by bovcan on 2010-05-15
Yes, 
B standard is 11Mb/s
G standard is 54Mb/s
N standard is 300Mb/s

---

### Post by nilbus on 2010-05-15
Thanks, knowing the bitrates answers my question. I guess I would have seen it in iwconfig if it worked with my wl Broadcom wireless driver.

Now that I know it's only connecting with G (54mbit), I can start to troubleshoot why it's not using N. Perhaps it's because of my authentication method (WPA2 Personal)?

---

