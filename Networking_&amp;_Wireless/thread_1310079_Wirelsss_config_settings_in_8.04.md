---
title: "Wirelsss config settings in 8.04"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by modmidget on 2009-11-01
I've been using Ubuntu 8.04 for a few years and had a good wireless connection until my hard drive died last week.  Now I can't figure out how to re-configure my wireless card.  When I go into the config manager it asks for my ssid, type of encryption (WEP), and a password.  It does not ask for the WEP encryption key.

I went into a terminal window and typed "lshw -C network.  The results properly identified my wireless card with the Prism ISL3890 chipset.

Then I tried typing $ sudo iwconfig wmaster0 key s:my-ascii-key but got an error message that says "unknown command s:my-ascii-key" (I did use my correct 10 digit ascii wep key).

I specifically bought this wireless card because it is Linux compatible and does not require NDISWRAPPER and it has been working very well with Ubuntu.

By the way, in config manager I tried entering my ascii WEP key in the password box and rebooted but that didn't work.

Any help would be appriciated.

Ken

---

### Post by chili555 on 2009-11-01
I think iwconfig wants the actual interface, *wlan0*, I believe, and not the dummy *wmaster0*. Also, if you have ten characters, it's HEX, and not ASCII. Please see here: [http://www.smallbusinesscomputing.com/webmaster/article.php/3556296](http://www.smallbusinesscomputing.com/webmaster/article.php/3556296)

---

### Post by modmidget on 2009-11-01
I replaced wmaster0 with wlan0 and ran the command.  Didn't get any error message but still no connection.  Also changed the WEP key to "0x-my-hex-key", but still no connection.  Once again, no error message but in both cases I didn't get any kind of confirmation message either.  I'm sure I'm overlooking something really stupid but the last time I did this was 2 or 3 years ago and I can't remember what I did back then.

By the way,  in the config manager, what does it want as a password?  Is it my actual router password or my WEP encryption code with 0x in the front of it?

---

### Post by chili555 on 2009-11-02
In Network Manager, it wants the WEP key in '40/128-bit HEX key' *without* 0x in front. I am not sure that manual configuration will work correctly with Network Manager fighting for control of your networking interfaces; however, the correct commands would be:```
sudo iwconfig wlan0 essid mylilrouter
sudo iwconfig wlan0 key my-10-character-key
sudo dhclient wlan0
```In *iwconfig*, no 0x is required or recognized.

---

### Post by modmidget on 2009-11-02
Thank you chili555.  I went into the Network Manager, entered the hex WEP key without the 0x in front of it, and rebooted.  That fixed it!!!!!

Thanks again.

Ken

---

