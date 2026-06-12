---
title: "Broadcom43xx magically stopped working? :("
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by skelooth on 2006-06-19
I don't know what the hell happened.

This is a brand new laptop, and it was originally running ubuntu PERFECTLY 'right out of the box'. The only configuration i had to do was install / use fwcutter and gnome network manager. It was working PERFECT and I was using it both on my wireless network and the one at school.

Then I update my kernel to .25.......

At first I couldn't understand why the wireless light wasn't going on until it dawned on me that I have to copy the firmware over to the new kernel's folder in /lib/firmware/

Okay fine, great, blue light comes on again.

iwconfig sees the card, network-admin sees the card, ifconfig sees the card...

But i get no signal.

sudo iwlist eth1 scan returns 'no networks found'

sudo iwconfig eth1 mode auto
sudo iwconfig eth1 essid myNetworkName
sudo dhclient eth1

returns failure "no working leases in persistent database"

I've gone into network admin and have tried deactivating, reactiviating, putting in the essid, and all combinations of this.

I've tried editing /etc/network/interfaces so that only eth0, eth1, and lo are there. (since it didn't work I reverted it back to normal)

I've blacklisted ndiswrapper

I've done modprobe bcm43xx

I've restarted a zillion times

I've booted into the old kernel (and it doesn't work there anymore either)

I've even gone into bios, disabled the card, booted up, then went back into bios and re enabled it.

I'm at wits end because I don't know what else to do or try. It was working PERFECTLY before :( And this is a brand new laptop that I need to use for school.....

---

### Post by cnkbrown on 2006-06-20
I solved similar problems by setting the wireless keymode to open.  in /etc/network/interfaces, a line like;

    wireless-keymode open
    wireless-key xxxxxxxxxxx

although from the iwconfig man page it looks like the command line is

    sudo iwconfig wlan0 key open
    sudo iwconfig wlan0 key xxxxxxxxx

odd they would be different.

---

### Post by jawrat on 2006-06-20
I had a similar situation with mine.  (same kernel upgrade and copy over the firmware to the new kernel folder, still no wireless) Fixed it by setting a static IP for just one time.  once that came up, i typed in dhclient eth1 and voila, working once again.  

One other thing you might try is rebooting your router (if you can).  that worked for me in the past when i've had wireless connection issues.

hope this helps.

---

