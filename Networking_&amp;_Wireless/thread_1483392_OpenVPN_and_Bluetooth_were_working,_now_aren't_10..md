---
title: "OpenVPN and Bluetooth were working, now aren't 10.04"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by michaelveloz on 2010-05-14
Crazy:

Short version: bluetooth service and openvpn service were both running fine on my Ubuntu system until I swapped out the bluetooth card for a new one, and then swapped back in the old one once I discovered there was no problem with the old card (all this was done while booting to windows to try things out)

 Now, when I boot back into Ubuntu, both services have to be manually started after a boot to get them to work. 

Details:

Recently I got a new bluetooth keyboard. The bluetooth service was starting in Ubuntu (and in Windows 7; this is a dual boot laptop) but neither could discover the keyboard. As part of troubleshooting the problem, Dell sent me a new bluetooth card. Turned out to be a user error with the keyboard (how embarassing) so I put the original bluetooth card back in, booted to windows, and voila, windows discovered the bluetooth. Cool.

Rebooted back to ubuntu, hoping to now discover the keyboard there. Only now, the bluetooth service isn't running anymore (wth? I didn't touch my ubuntu settings).

After some poking around I found that if I restart the service (/etc/init.d/bluetooth restart) the service comes up and it discovers my keyboard.

So first question: why do I have to restart the service to get this to work? (If I click on bluetooth preferences in the System menu before doing the restart it just shoes a large button that says bluetooth is not enabled)

I also discovered that since I swapped out the original bluetooth card and then put the old one back in, my openvpn service is no longer working at boot-time!

Again, if I manually restart it (/etc/init.d/openvpn restart) it works.. But it used to start correctly by itself.

What the heck is doing on here and how might I troubleshoot this?? :-)

Michael

---

