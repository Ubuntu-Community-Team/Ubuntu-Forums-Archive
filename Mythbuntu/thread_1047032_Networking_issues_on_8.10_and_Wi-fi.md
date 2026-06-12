---
title: "Networking issues on 8.10 and Wi-fi"
date: 2009-01-22
forum: Mythbuntu
---

### Post by tehbeermang on 2009-01-22
I don't have a wired connection available to the MythTV box.

I grabbed NDISWrapper 1.38 from a Feisty CD through synaptic.

ndiswrapper -i /path/to/driver.inf was successful and there was much rejoicing.

The network manager 0.70 applet sucks. It doesn't keep my wep passphrase, it seems to think my sudo and keyring passwords are different than what I specified. (I tried both, it barked at me both times.)

I'm at the point where I just want to remove the offending software and configure it the old-fashioned way.

How do I configure wlan0 manually?

Searching this forum tells me the location is /etc/network/interfaces

I don't know the commands. Can anyone help out?

Thanks in advance for anyone's help in keeping me away from a WinXP/SageTV build.

---

### Post by Slate8 on 2009-01-22
I'm not sure how sensible this is, but I had a similar problem and ended up deleting my default keyring. Not only did this solve the issue but I also meant I don't have to unlock the keyring on every boot (a pain on a keyboardless mythbox).

I used the instructions at [http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/](http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/)

hope this helps

---

### Post by tehbeermang on 2009-01-22
I shut it off and bring it back up, and it remembers my passphrase.

My network icon still has a red square with a white x.

Any commandline magic to make it connect?

---

### Post by tehbeermang on 2009-01-22
Got it to work, I added ndiswrapper to the end of /etc/modules and clicked a couple other things I should have written down in case I need to further troubleshoot.

---

