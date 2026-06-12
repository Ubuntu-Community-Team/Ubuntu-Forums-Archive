---
title: "sites wont load after first visit using edimax wireless nic w/ time warner cable"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by mowgliee on 2009-08-18
symptoms: go to any site, loads fine.  sometimes even loads 2nd or 3rd page on same domain (ie gmail login comes up fine, sometimes inbox comes up, but thereafter nothing loads, even the original inbox or login pages).  this applies to all sites, http or https, survives a reboot sometimes, survives network restart or ifup/ifdown.  all works fine using patch cable and rj45 port.  changing dns servers does nothing.  reloading site, clearing cache, restarting firefox all change nothing.  just spins and spins.  also wap disappears often and takes forever to reconnect, but this problem occurs even while connected (can ping domains just fine even when same domains dont load on browser).  laptop does get dhcp and onto wireless LAN just fine upon every boot/reboot.  interfaces file doesnt have wlan0 in there; only has lo.

specs: jaunty on dell inspiron 8000 w/ edimax 7108PCg wireless nic, jaunty is fully updated via aptitude repos, using time warner cable w/ wireless router/cable modem they provided.  using wpa v1 w/ aes encryption.

other info: macbook on same network works fine w/ no issues.  so does mac mini. laptop w/ issue works fine on any other wireless network; only fails to load pages at home.

so its only my laptop on my home network thats causing the probs.  cant tell if its nic, laptop, time warner, modem/router, or what!!! cant isolate the problem and log files have 0 posts.

please suggest any ideas, sites, feedback (other than throwing everything in a bloody tree shredder ... that option is already on the table).

---

### Post by superprash2003 on 2009-08-19
you could try changing MTU [http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html](http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html) and also try disabling ipv6 [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by mowgliee on 2009-09-25
hey those suggestions didnt solve it.  now i've tested the wireless nic in another dell laptop and worked fine at first, then same exact issues!  and this laptop was on hardy.

is it something to do with the nic driver or how its configured?  i just let ubuntu auto load driver.  i'm at a complete loss how it just stops working after hitting every domain once!

---

### Post by mowgliee on 2009-10-14
an update:
the macbook still works 100% fine on same LAN.
the ubuntu dell laptop w/ edimax pci nic fails consistently.  and its not the dns or domains any more.  the card doesnt even stay connected long enough to test those things.  in < 1 min ubuntu loses connection (while macbook right beside it doesnt).  sometimes it reconnects, sometimes not, but always loses connection permenantly in about 5 min.

100% same exact behviour every time.

same card in another dell laptop works fine w/ other wpa waps.  same card in another dell laptop fails on this (home) wpa wap.  so its the combo of this wap and this nic that fails.

but i cant tell how/why/etc?  where do i even begin to troubleshoot this?

---

