---
title: "Lenovo X121e;  Centrino Wireless;  Networkmanager disables with reason 2"
date: 2011-10-05
forum: Networking &amp; Wireless
---

### Post by Daniel Cutter on 2011-10-05
I've got a new lenovo X121e with the latest BIOS (1.09) and have installed Ubuntu 11.04 on it today from USB. Everything went well, included the function keys and eth0, but WLAN doesn't work.  Apparently it was disabled by Networkmanager for reason 2. Can someone help? Thanks in advance!

The output requested by the Sticky '**HOWTO post a Wireless issue' **post is attachted as a text file.

---

### Post by Daniel Cutter on 2011-10-06
Thanks for all those who didn't answer, I understand completely. It only forced me to find a solution myself. Which is good.

I can activate WLAN with rfkill. Scans then work. Can't connect, but thats a locality problem.

If I go to 'Ruhezustand' (why did I install ubuntu in German? Probably 'sleep')  it wakes up with WLAN active. If I reboot or shutdown and boot it wakes up as before and I must use rfkill to activate WLAN again.

Any ideas what's going on? Following the slightly chaotic post that tipped me off with rfkill it could have something to do with a BIOS setting. I will investigate that this evening.

If anyone has any tipps - there welcome but probably no longer needed. Thanks.

---

### Post by Dead1nside on 2011-12-03
I had a similar problem but with Bluetooth being constantly disabled. A reset of BIOS settings to default (as well as trying an upgrade to BIOS 1.09) solved it. It did reoccur, but I just did the same thing again and it has been working fine for a month.

---

