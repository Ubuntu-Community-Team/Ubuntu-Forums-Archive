---
title: "Help! Installing upgrades killed wireless in ubuntu 8.10 thinkpad t400"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by lionstone on 2009-02-20
Hi, I'm wondering if anyone could help here-

I'm running Ubuntu 8.10 64 on a lenovo thinkpad t400, have had no problems with the wireless until today, when I installed 100+ upgrades at once. 

network manager reveals a big x where the wireless networks have always appeared. 

ifconfig revels that eth0 and lo look operational

but 'if up wlan' (which should've happened automatically, ya?) only returns "ifup: failed to opten statefile /var/run/network/ifstate: Permission Denied"

iwconfig doesn't recognize any wireless extensions at all.

lspci recognizes a "communication controller": Intel Corporation Mobile 4 Series Chipset MEI Controller.

I don't even know enough to debug without help at this point, as I can't even copy and paste errors since I have to get online on a seperate machine :(

This is a major issue for me as I need wireless to get online. I am having to use a $100 laptop to write this message while my thinkpad lies useless. I'm particularly bummed cause I was preaching the virtues of ubuntu all week and now it's friday afternoon and i'm having to mess with it , c'est le vie :)

what can i do? how can i troubleshoot at this point? what package was busted?

---

### Post by lionstone on 2009-02-21
Well I actually figured out the fix myself here...

To get the wifi working in the first place, I had installed and compiled madwifi drivers from source.

Turns out that I needed to rebuild the madwifi drivers for the new kernel, which was one of the upgrades. 

So I went to my madwifi directory and did the following:

sudo make clean
make
sudo make install
sudo shutdown -r now

...and after a reboot, all is well again. Guess I'll have to do this everytime I upgrade kernals ( GRUMBLE )

But issue resolved.

---

