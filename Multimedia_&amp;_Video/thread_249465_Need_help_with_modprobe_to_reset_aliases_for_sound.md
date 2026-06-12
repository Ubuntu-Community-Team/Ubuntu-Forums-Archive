---
title: "Need help with modprobe to reset aliases for sound card"
date: 2006-09-02
forum: Multimedia &amp; Video
---

### Post by HarryHalpin on 2006-09-02
I'm having issues recording sounds with anything and even playing sounds with audacity. Note that a few months ago everything worked fine - so I know it's not a fundamental hardware problem.

However, this summer I tried installing a bluetooth BT headset, and I need help removing it's drivers, since I think its the source of my problem. In essence, the BT Headset drivers are loading as the default sound card (0) and therefore all applications like audacity which try to use sound fail, until I manually change it using "System >> Sound >> Preferences" in GNOME. Even after changing it manually, any sound recording application (See [1] below) and audacity still fail (See [2] below) - and they worked beforehand. I assume they are still perhaps trying to use the BT Headset instead of my sound card, and are bypassing GNOME. I believe modprobe can change this, but I can't figure it out.

As one can tell, the BT Headset loads as default because it's numbering is 0:

$ less /proc/asound/cards
0 [Headset ]: Bluetooth SCO - BT Headset
BT Headset 1
1 [I82801DBICH4 ]: ICH4 - Intel 82801DB-ICH4
Intel 82801DB-ICH4 with AD1981B at 0xc0000c00, irq 11

Then,  I could find in /etc/modprobe.d the file "alsa-base,"  had these lines in it:

# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

which obviously don't work. 

How can I use modprobe to give by BT Headset (btsco, mostlikley snd-bt87x) index=1 and my intel sound card index=0? Or is that wrong - why are we tryin to prevent "abnormal drivers from grabbing index 0"?

I'm better there's a series of modprobe commands to sort this out...but I can't figure it out, and I can't figure out what of the many text files in /etc/modprobe.d I need to edit.

---

