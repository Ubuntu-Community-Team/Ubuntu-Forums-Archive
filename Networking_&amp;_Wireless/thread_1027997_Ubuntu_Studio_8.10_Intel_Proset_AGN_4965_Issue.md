---
title: "Ubuntu Studio 8.10 Intel Proset AGN 4965 Issue"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by bwong365 on 2009-01-01
Hi I'm brand new to Linux, I just installed Intrepid x64 over Vista last night, and I was having some trouble getting my wireless card working. After a lot of searching and a lot of trials, I discovered that I had to:

Install Network Manager (nm-applet, etc)
gedit /etc/NetworkManager/nm-system-settings.conf
       (edited) "managed=true"
sudo modprobe iwl4965, and this would finally allow me to connect to the internet.

Before I was having problems like being "connected" but not being able to ping the router, however for some reason I could still do the "sudo apt-get install ..." commands and those would work

Anyways I was wondering if there was a better way to solve the issue, since this fix seemed sort of clumsy and since adding the "sudo modprobe" command to Sessions I have to keep typing my password after logging in

thx for reading, any comments/help/suggestions would be awesome, I'd like to be able to connect w/o having to type my pw in all the time

PS also I had to install linux-backports-modules-intrepid to fix a shut down issue that the wireless was giving me after the modprobe fix

---

### Post by CJay554 on 2010-02-12
Maybe your apt-get is running from the CD, as in installing applications through the cd (if its in). Because if you ping the router and it doesn't respond you shouldnt have any connection at all O.o

Also i should mention i have the same problem with this exact card, though every time i restart the module using:
rmmod iwlagn
modprobe iwl4965

it only works for so long before disconnecting and not letting me connect either... i myself have no fix for this as i have tried alot of things, though i see that alot of people can actually get it working right, out of the box, so im wondering if there are different AGN 4965 versions

---

