---
title: "ra2500 chipset locks up keyboard"
date: 2005-12-27
forum: Networking &amp; Wireless
---

### Post by ingo on 2005-12-27
Hi,

I bought myself a pcmcia wlan card with the ra2500 chipset believing it would work out of the box on my 5.10. I followed the howto to the letter and got to the point of the card blinking. 

And that was the end of it, the system had locked up completely. No mouse, no keyboard. 

I've got an old IBM TP 600E and am a little lost. Is there anything I could do, any logs to go over, etc.?

Any help much appreciated!

Cheers

Ingo

---

### Post by izm81 on 2005-12-27
You could start by documenting the steps you followed and providing **/var/log/messsages**, if possible.  I have an ra2500 pci card, and it worked out of the box.

---

### Post by ingo on 2005-12-28
Right, on insertion I get:

Dec 28 11:25:34 localhost kernel: [4297305.867000] PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
Dec 28 11:25:34 localhost kernel: [4297305.867000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
Dec 28 11:25:34 localhost kernel: [4297305.867000] rt2500 1.1.0 CVS 2005/07/10 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
Dec 28 11:25:35 localhost pci.agent[7033]:      rt2500: loaded successfully

So far so good. But when I activate it and then restart there are no further entries in the /var/log/messages file

Anywhere else I could look for further info?

---

### Post by izm81 on 2005-12-29
ok.  so it presumably created a device for your card.  You can see a list of wireless devices with:
```
$ iwconfig
```

I suppose the next easiest step would be:
```
# sudo network-admin
``` to bring up a GUI to change settings, deactivate, and activate your wireless network.

Which ***howto*** are you following?

---

### Post by ingo on 2005-12-29
with iwconfig I get ra0 listed.

sudo network-admin does not exist on my system, i.e. network-admin: command not found

I don't actually mind using the shell. Thing is, I don't know all the files that have a part to play when it comes to interacting modules. Obviously...

A miracle has just happened: first I typed 

sudo ifconfig ra0 down (without the card being activated!) 

and then 

sudo ifconfig ra0 up

and the system didn't crash!!! Don't want to reproduce now, but first check whether I can get onto my network...

Oh, I've been following this howto: [https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

Cheers and I'll report on the outcome of all...

---

### Post by ingo on 2005-12-30
bugger, it didn't connect nor is it reproducable, same old keyboard conk-out!

At my wit's end:confused:

---

### Post by izm81 on 2005-12-31
Oh, WPA?  I haven't tried that.  Are  you using WPA?  I would try simple and work your way up, if possible.  No encryption, WEP, then WPA.  I'm using WEP.  If I wanted to bring up my ra0 interface from the command line, I would do the following (if I recall correctly):

```

sudo ifconfig ra0 down
sudo iwconfig ra0 essid "mynetworkname"
sudo iwconfig ra0 key "s:myasciipassword"
sudo ifconfig ra0 up

```

Oh, and because I'm currently using Dapper (NOT recommended), I have to toggle encryption on and off, for some reason (bug).
```

sudo iwconfig eth1 encryption off

```

If that doesn't work, but I've set the correct essid and key, then I might try:
```

sudo /etc/init.d/networking restart

```

Also, depending on how your access point is setup, you'll probably want to make sure ra0 is using dhcp.
```
/etc/network/interfaces
```

Other than that, I'm not really sure what to suggest.  Maybe it's a hardware issue (despite being the rt2500)?  Are other people using the same exact hardware successfully?  You could try recompiling the kernel.

Good luck!

---

