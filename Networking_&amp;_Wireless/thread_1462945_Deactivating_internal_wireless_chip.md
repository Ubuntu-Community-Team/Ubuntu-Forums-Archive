---
title: "Deactivating internal wireless chip?"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by gwpritch on 2010-04-26
I have a Toshiba Satellite laptop with an internal atheros chip. 
I believe the internal wireless chip has been damaged as it detects my home network only at a very low signal even when I'm sitting right on top of the router.
I have an old D-link AirPlus card which I've plugged in and it works fine.
Problem is, when I log on, network-manager continues to access the network via the low signal internal card even though the wireless button on the laptop is set to off.
I have to disconnect from the internal and reconnect via the external card. PITA!
Is there a way I can totally disconnect the internal chip so it can no longer be accessed.
Alternatively, how would I configure the /etc/netork/interfaces file to connect without network-manager. I use a 128bit wpa/wpa2 passphrase for security.

Thanks

---

### Post by ProNux on 2010-04-26
I'll try if I can help you.
1.  Disconnect your D-Link Airplug
2.  Determine your atheros wireless extension
    at the terminal, type
    ```
ifconfig
```
3.  Identify what is the built-in wireless extension (like "wlan0")
4.  To disable wlan0, at the terminal, type
    ```
sudo ifdown wlan0
```

I am no networking expert. Good luck.

---

### Post by pricetech on 2010-04-26
You need to disable the internal wireless in the BIOS.  Reboot and access the BIOS using whatever hotkey your laptop calls for and look for your wireless card.  There should be an option to disable it.

Alternatively, you can disconnect or completely remove the card from the laptop.  Check the panels on the underside.  You should find one that will let you get to the wireless card.  Remove the panel, and then the card.

---

### Post by gwpritch on 2010-04-27
Thanks guys

I really appreciate your help.

---

### Post by P4man on 2010-04-27
Id like to point out that the atheros not working well is probably not a hardware defect, but the driver not working well. That might be fixable. Can you provide the output of

```
lspci

```

and tell us which version of ubuntu you are using?

---

### Post by gwpritch on 2010-04-28
Thanks for the reply P4Man. 
It is in fact physical damage, since it happened after my dog knocked the laptop off a table...lol.  It has been a consistent problem over winxp and 3 versions of ubuntu. There was no problem with drivers before this.

I tried deactivating the wireless in the bios but no joy. The only option was disable LAN and this only deactivated the wired 
NIC. I don't see any physical access to the wireless without taking the whole laptop apart. I'm thinking its not a card persay, just an integrated chip.

```
sudo ifdown wlan0 
```just returns a message that wlan0 is not configured, unless it is already active.

So far, the least objectionable solution seems to be to not set any connections to start automatically and then just pick the one I want.

Thanks to all for trying to help. Any other suggestions would be appreciated.

---

### Post by mikewhatever on 2010-04-28
You'll need to blacklist or remove the wireless module, and to find out what the module is, run *lsmod*. You might want to post the output of that.

---

### Post by gwpritch on 2010-04-28
Thanks.  I'll give that a try when I get home tonight. Can you give me details of how to blacklist the module when I find out which one it is.

---

### Post by mikewhatever on 2010-04-28
*gksudo gedit /etc/modprobe.d/blacklist.conf*

Add the module to the end of that file, save and exit.

or

*sudo modprobe -r module_name*

to remove it one time only.

---

