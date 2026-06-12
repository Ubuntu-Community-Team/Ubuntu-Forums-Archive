---
title: "Volume control icon disappeared"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by clean97gti on 2007-02-05
System is as follows:
Gigabyte K8nsc-939 system board - nforce3
AMD Athlon 64 3200+ cpu
1gb ram
onboard sound (AC97 I believe)
ATI Radeon X1300 Pro vid card (FGLRX 8.33installed without issue)
onboard gigabit NIC

Just reinstalled Edgy (32 bit) on a hard drive in my dual boot system. Install went without issue and everything worked after install. Now, I really dislike running Totem for anything. I find XMMS and VLC cover all my media playing needs. So, I removed everything Totem from the system, and installed VLC and XMMS along with gstreamer plugins listed in Ubuntuguide.org. Again, everything works fine. movies play, musics plays.
Problem is that I no longer have a volume control in the notification area where it once was. I don't know what command to use to start it, nor can I figure out what package in Synaptic contains it.
I'm assuming it got wiped out when I removed all the Totem stuff.
Any ideas on how to get it back?
Anyone know the command to start it?

---

### Post by ESPOiG on 2007-02-05
right click on the panel and select the volume manager applet

---

### Post by clean97gti on 2007-02-05
> **ESPOiG said:**
> right click on the panel and select the volume manager applet

Tried and got an error message.

The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".
Do you want to delete this applet from your configuration?

:(

also noticed that my GAIM notification icon no longer appears after trying the above step.

---

### Post by clean97gti on 2007-02-05
OK, figured out the problem. Easily fixed with

sudo apt-get install gnome-applets
sudo apt-get install gnome applets-data

got the volume control back. :)

---

### Post by clean97gti on 2007-02-05
Still missing the GAIM notification though. Just tried removing GAIM and restarting the entire system.
No luck.

---

### Post by ESPOiG on 2007-02-08
did u try the preferences in gaim??, i think it has it there "display in tray or something" do u have the "tray" applet loaded??

---

