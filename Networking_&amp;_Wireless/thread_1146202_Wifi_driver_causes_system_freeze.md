---
title: "Wifi driver causes system freeze"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by mathemagician on 2009-05-02
I've just upgraded my system - hardware and software - and now my wifi is causing the system to freeze.

I'm running a Asus P5Q motherboard, intel Q8400 chip, and a fresh install of Jaunty - 64bit version.

Under Ibex (and my old mobo/chip), my wifi card (d-link G-520) worked out of the box. 

With the new hardware, I couldn't get Jaunty to boot with the card installed until I blacklisted ath5k. If I try to activate the alternate atheros madwifi driver, the system freezes immediately.

I'm stumped. Any suggestions?

---

### Post by mathemagician on 2009-05-02
Here's my lspci output:

```
05:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
```

Again, the wireless card worked under Ibex/32bit and my old hardware. So I'm not sure if this is a conflict with my new mobo, Jaunty, or the fact that I'm now running the 64bit kernel.

---

### Post by mathemagician on 2009-05-03
Update: I attached my old 32bit Ibex drive - it worked on my old hardware - and it freezes on boot as well. However, it will boot after removing the wireless card.

So this isn't a Jaunty issue, but a mobo/nic/ath5k issue.

Any suggestions?

---

### Post by Chuwbacca on 2009-05-04
Same problem with same card, but freeze was from time-to-time... Fixed with installation  linux-backports-modules-jaunty and reboot...

---

### Post by mathemagician on 2009-05-05
Yeah, I tried that. I didn't help. :( Anything else I can try?

---

### Post by musther on 2009-08-04
Same problem with same wifi driver and an ASUS motherboard (GA-EG31MF-S2).  My problem was the intermittent freeze, not fail on boot.  I've just installed the backport modules, will see if it makes any difference and report back.

---

### Post by tamagotchi on 2009-08-07
I'm experiencing random freezes as well since I added a wireless card to my machine. 
lspci says:
Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

It sometimes runs for a day or two, sometimes it locks up after 20 minutes.
Resume after suspend also stopped working.

Any ideas?

---

### Post by musther on 2009-08-07
My machine has been on for over four days now, with no crash, so at least for my setup, I seem to have sorted it.  

[LIST]Right click on the network icon in the notification area and select 'Connection Information'.[/LIST]
[LIST]Find your wireless connection and see what driver it's using, I think before the fix mine was ath_5kpci (or maybe ath5k_pci).[/LIST]
[LIST]Now, go to System --> Administration --> Software Sources[/LIST]
[LIST]Go to the updates tab, and tick 'Unsupported updates (jaunty-backports)' - note that I also enabled 'jaunty-proposed'.[/LIST]
[LIST]Then close and let it reload the package list.'[/LIST]
[LIST]Go System --> Administration --> Update Manager, click the 'check' button, and then do any available updates.[/LIST]
[LIST]Then run: ```
sudo apt-get install linux-backports-modules-jaunty
```[/LIST]
[LIST]Reboot[/LIST]
[LIST]You should now find that the driver name is slightly different, for me it's now 'ath5k' - and this new driver seems to do the trick for me.[/LIST]

---

### Post by tamagotchi on 2009-08-08
Interestingly the default wireless driver was already ath5k after I installed the wireless card. There was no ath_5kpci or alike. 

After installing some update ath5k became suddenly blacklisted in /etc/modprobe.d/madwifi.conf. So I had to manually modprobe it.

I'm trying the backport option you described above, thanks for the information. Let's see how that works out. 

-t

---

