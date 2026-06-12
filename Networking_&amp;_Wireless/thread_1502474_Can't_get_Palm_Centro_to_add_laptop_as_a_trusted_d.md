---
title: "Can't get Palm Centro to add laptop as a trusted device."
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by f1r3br4nd on 2010-06-05
I have a clean install of 64-bit Kubuntu Lucid Lynx 10.04, with the bluez 4.60 package installed and working. "hcitool dev" finds my own card and "hcitool inq" finds my Palm Centro. Now I am trying to make the Palm recognize the laptop as a trusted device.

I tried following these instructions and many others:
[http://howto.pilot-link.org/bluesync/](http://howto.pilot-link.org/bluesync/)
[http://www.harbaum.org/till/palm/bluetooth/](http://www.harbaum.org/till/palm/bluetooth/)
[http://ubuntuforums.org/archive/index.php/t-911447.html](http://ubuntuforums.org/archive/index.php/t-911447.html)

The problem I'm running into is that when I add my laptop as a trusted device on the Palm end, I get prompted for a passkey. All of the above instructions are out of date in its instructions for setting the key. 

Some of them say to put the passkey into /etc/bluetooth/pin, but that doesn't exist on my system. I created it, restarted the bluetooth daemon and put in the same string from my Palm when prompted, but the Palm says "unable to add xxx to your trusted device list".

Others say to change the passkey or pin_helper setting in /etc/bluetooth/hcid.conf, but that file no longer exists either and apparently the passkey setting is obsolete. The pin_helper apparently used to point to /usr/bin/bluez-pin and later /usr/bin/bluepin, but in Lucid neither of these files exist. One page suggested creating a batch file by that name and having it echo back "PIN:" followed by the contents of /etc/bluetooth/pin. I tried that, but it doesn't work either, I still can't add the laptop to the trusted device list.

I really think the problem is that I just don't know how to set the pin correctly, and it isn't documented anywhere. Does anybody know how to do this?

Supposedly there's some kind of Gnome GUI utility for doing this, but I'd rather not have to download a bunch of GUI libraries for something that can be done from the command line. But hey, if that's what I have to do I'll do it, so if you know about it, I'd like to hear all about it.

Thank you.

---

