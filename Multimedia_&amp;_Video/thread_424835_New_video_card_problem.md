---
title: "New video card problem"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by MadMac on 2007-04-27
Howdy!

Okay, I am upgrading my video card from legacy to non-legacy.  The new card is a e-GeForce FX 5500, has a DVI connection for the monitor to plug into, plugs into a PCI slot, and is replacing an older Nvidia card.  The monitor is a Hanns-G JC199D 19 inch LCD.

My problem is that after I have set the BIOS to work with PCI versus AGP and I get the first splash screen it decides that it will give me the "cannot start X" error screen and can/will not go any further.

I am considering doing a complete re-install of Fiesty with the new card in place and see what it will do.  Anyone have any ideas on what I can do to A) install the card without re-installing Fiesty or B) steps to take where the xorg.conf file/Nvidia update from Synaptic will accept the card?

Thanks!

---

### Post by hardyn on 2007-04-27
sudo dpkg-reconfigure xserver-xorg

you may reconfigure your X server by running this.

---

### Post by MadMac on 2007-05-01
> **hardyn said:**
> sudo dpkg-reconfigure xserver-xorg

you may reconfigure your X server by running this.

Okay, is this something I should run before or after I have re-installed the video card?  I know that I will wind up with the "cannot start X server" error when I reboot with the card in the machine.  Oh, should I download and install the "updated" Nvidia drivers from Synaptic before I re-install the card?

(Sorry for the delay in responding - "Real Life" got me by the short and curlies for a coupla days.)

Thanks!

---

### Post by WinterWeaver on 2007-05-01
you run that command as soon as you get that "cannot start X" - error

It's basically to reconfigure your x settings.

---

### Post by MadMac on 2007-05-01
> **WinterWeaver said:**
> you run that command as soon as you get that "cannot start X" - error

It's basically to reconfigure your x settings.

Alrighty, I'll give that a shot. 

Thanks!

---

### Post by MadMac on 2007-05-02
Managed to get it up and running!  :popcorn: 

The only problem is that I cannot change the refresh rate on my monitor (Hanns-G JC199D) and the text seems to be sort of "rough" - hard to explain, but maybe this post will show it.

Thanks again!

---

### Post by MadMac on 2007-05-05
Anyone?  Please?

---

