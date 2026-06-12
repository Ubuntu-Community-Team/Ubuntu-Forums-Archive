---
title: "bcm4306 problem with kubuntu 5.10"
date: 2006-02-23
forum: Networking &amp; Wireless
---

### Post by cylent on 2006-02-23
Hello.

I just installed Kubuntu 5.10 today and I am having trouble getting my Broadcom bcm4306 internal wifi to work.

I have a HP/Compaq NX6110 laptop.

I have followed the steps here with no success. ([https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx))

I have the same adapter listed in the guide,
*0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)*
*0000:02:02.0 0280: 14e4:4320 (rev 03)*

i followed the steps in the guide to the letter.

I did have one issue but i went around it and that was when i did this command:

for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done

it said "Permission denied" for the files it listed so I did "sudo su" and i was root then i repeated the command again and it worked.

after that i rebooted, loaded the K wifi control panel but my card wasnt listed nor recognized.

i then inserted "ndiswrapper" into /etc/modules and tried rebooting again.

i even tried "sudo modprobe ndiswrapper"

i am stuck. its just not working and i dont know what else to do.

any help is appreciated!

---

### Post by psYchotic on 2006-02-23
I suspect the bcmwl5 module is still loading. To make sure it doesn't do the following in a terminal:
```
sudo nano /etc/hotplug/blacklist
```
Add a line with only "bcmwl5" (without the quotes) and press Control+X, followed by a Y, and then ENTER (to save the changes).
After that, reboot and see if it's working.

---

### Post by cylent on 2006-02-23
:mad: :sad: :sad: :sad: That did not work.

---

### Post by Lambert on 2006-02-23
Breezy 5.10 comes with kernel 2.6.12

The bcm43xx driver will not work with this kernel. YOu need 2.6.15 or higher.

So unless you've compiled a newer kernel, it won't work with 5.10

---

### Post by cylent on 2006-02-23
thats just lovely :(

can you tell me if theres an apt-get package with the new kernel that will auto setup grub or lilo (whichever ubuntu uses). ?

---

### Post by Lambert on 2006-02-23
Ubuntu doesn't update anything with each release unless it's security related so no, you won't find a packaged kernel you can just apg-get install. You need to recompile. There are guides in the howto section.

When dapper is released in April, it will have a newer kernel and the bcm43xx driver preinstalled. You will just need to follow the instructions to get the firmware.

It still is a beta driver that's being reverse engineered so still very buggy.

I would suggest using ndiswrapper and giving the native driver a try when dapper is released.

---

### Post by psYchotic on 2006-02-25
What happens when you do ```
ndiswrapper -l
```? (l is the lowercase L)
Something like this should be shown
```
psychotic@Otaconix:~$ ndiswrapper -l
Installed ndis drivers:
2802w   driver present, hardware present
```

---

