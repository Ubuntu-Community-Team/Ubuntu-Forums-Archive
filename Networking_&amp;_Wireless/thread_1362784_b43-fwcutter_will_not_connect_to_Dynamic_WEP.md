---
title: "b43-fwcutter will not connect to Dynamic WEP"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by mcdjork on 2009-12-23
I am running Karmic 64 bit on a Dell Latitude D630 with a Broadcom 4312 wireless card. For months I was using the Broadcom STA driver which would frequently send the computer into kernel panic, and also lost its connection while any torrent software was running. Sometimes the computer would freeze and lock up so badly, that my file system would be rendered unusable. I also had a 32 bit version of Karmic installed, which didn't create a kernel panic, but did drop my connections when torrents were running. I even compiled the updated STA driver form the broadcom website and ran into the same problems.

One day I decided to switch to the b43-fwcutter driver. Not once since then has my computer frozen up and gone into kernel panic. I do not lose my connection when running torrents. Everything is great except for one problem. I cannot connect to my PEAP network at work. This connection worked fine with the STA driver, but impossible with the b43-fwcutter. I have read bits and pieces on the net about other people running into this problem, but never a solution that helped me. Does anyone have any ideas? I have attached the syslog for what happens when I try to connect.

---

### Post by puppywhacker on 2009-12-23
b43-fwcutter is only a tool to strip the firmware for the b43 driver to use, that you have working. What goes wrong is the wpa_supplicant which negotiates the security keys. This works in phase 2 of 5, something about scanning.

In your syslog configuration it says 'scan_ssid' value '1'. This scanning seems not to work (maybe a hidden BSSID?) This all comes from NetworkManager, which does a lot of stuff on it's own which is very hard for me to control or configure, so I don't like it yet.

I keep hearing that people have better luck using WICD as network manager.

---

### Post by mcdjork on 2009-12-23
I forgot to mention that I also tried WICD. I didn't play with it too much, but with that I couldn't even get Ethernet connections to work.

If it's a problem with Network Manager, why does it work with the STA driver and not the other?

---

