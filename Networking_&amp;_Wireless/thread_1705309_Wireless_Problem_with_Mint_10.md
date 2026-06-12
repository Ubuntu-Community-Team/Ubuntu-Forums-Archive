---
title: "Wireless Problem with Mint 10"
date: 2011-03-12
forum: Networking &amp; Wireless
---

### Post by KryptoRoxx on 2011-03-12
I recently did a fresh install of Mint 10 to test it out for the other computers in my house. I'm even thinking of going to Ubuntu with my server but that's another story. When I first did the install wireless kept dropping but it was there. Did a hard line connection via 30-40ft of lan to try and fix the solution. Tried a couple of solutions and thought I had solved it finally and then the wireless cut out completely and I cannot get mint to even recognize the adapter now. The adapter is a Rosewill rnx-n180ube and the solution that I used to fix it ended up being a simple solution in terminal.

sudo cp -R /lib/firmware/rtl8192SE /lib/firmware/rtl8192SU

Apparently the firmware was there just in the wrong spot. So is there another way to work this. I can run lsusb but I have to restart to do this and obviously I can't post once I'm in mint. I did do a secondary check with my wife's computer adapter. She has a tp-link adapter and the internet works without a hitch on mint. I am relatively new to Ubuntu....but I'm learning. This forum has been the key to that....and google lol. Thanks in advance.

---

### Post by Perfect Storm on 2011-03-12
Hi KryptoRoxx

There's a Linux Mint forum to get help with your distro.
You'll find it here: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)


regards
A.I. Dude
Ubuntu Forum Staff

---

