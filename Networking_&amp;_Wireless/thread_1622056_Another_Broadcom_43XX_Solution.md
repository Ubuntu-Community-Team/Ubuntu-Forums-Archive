---
title: "Another Broadcom 43XX Solution"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by originalseven on 2010-11-15
Like many, I've tried every known tutorial on how to activate the Broadcom wireless card in Ubuntu. The wrapper, the cutter, firmware updates, driver updates, on and on and on. This solution was achieved with a fresh install but I suspect the underlying problem mentioned below will solve any issues with your card regardless of how much you've screwed with the wireless on your OS.

I was just about to migrate back to Suse when I found something buried within the internets. The problem is with the radio button and bios wireless blocking and the solution is here:

sudo rfkill list

0: hp-wifi: Wireless LAN
Soft blocked: yes
Hard blocked: yes
1: phy0: Wireless LAN
Soft blocked: yes
Hard blocked: yes

Push the wifi button on the keyboard once and re sudo rfkill list

0: hp-wifi: Wireless LAN
Soft blocked: yes
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: yes
Hard blocked: no

Now do this....

sudo rfkill unblock all

0: hp-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

If you haven't already, run...

sudo apt-get install b43-fwcutter

and make sure your B43XX driver is active in System > Administration > Additional Drivers


This light came on and a list of available networks immediately popped up. Working fine now @ 54Mps.

---

### Post by JIMY JAMES on 2010-11-16
NICE! I tried everything and finally this worked!  Makes me wonder if this could be whats causes so many people so much trouble.  Glad someone figured it!  Thanks Alot

---

### Post by thesupergame on 2011-01-11
doesnt work for me, my 'hard blocked: yes' does not go away. I have a dell, and the wireless switch is fn-f2 keys, which only toggles soft block on and off. The unblock feature of rfkill also only toggles the soft block

---

