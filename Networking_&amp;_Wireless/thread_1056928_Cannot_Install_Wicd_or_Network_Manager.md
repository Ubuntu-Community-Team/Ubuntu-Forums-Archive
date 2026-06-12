---
title: "Cannot Install Wicd or Network Manager"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by mattio26 on 2009-02-01
HELP! i was getting a little bit frustrated with network manager so i tried to install wicd instead. during the install it obviously removed network manager but the install of wicd didnt work correctly. I then tried to install network-manager back and uninstall wicd. now i have neither and cannot connect to any networks at all not even wired! please someone help me

unbuntu 8.10
kernel 2.6.27-9
dell mini 9 8gb ssd 2gb ram
broadcom network card

---

### Post by kevdog on 2009-02-01
Ok, why don't you just complete your internet connection using the command line (at least temporarily)?  Just an FYI, that no package is actually needed to use internet (neither Network Manager nor WICD) -- these are just packages that make it more convenient to establish a connection.  I've got a link in my signature how to do this, however for the easiest method possible, I would use your wired connection.  After this you can then download whatever GUI you choose to restore NWM (but why would you when it didn't work in the first place??).  Im betting there is actually a problem with your driver configuration since both programs didn't work.

Please tell us more about your setup and include:
lshw -C network

---

### Post by mattio26 on 2009-02-01
ahh ive fixed it now! after spending about 3 hours here i stumbled accross the terminal command to connect via ethernet. once that was running i could donwload NM again! do u have any other suggestions for a graphical network apt other than wicd and NM ? otherwise i guess im stuck with it! thnx for ur help much appreciated!

---

### Post by kevdog on 2009-02-01
Here's my 2 cents.  If you can connect manually, then wicd should work. It basically does the same thing.  I'm not as familar with NWM -- at least the code part that is.  Its much more complex which sometimes is a good thing, and sometimes a bad thing.

---

### Post by albinootje on 2009-02-01
> **mattio26 said:**
> I then tried to install network-manager back and uninstall wicd. now i have neither and cannot connect to any networks at all not even wired!

Can you post the output of the following :
```

sudo dhclient
cat /etc/network/interfaces
ifconfig -a
route -n
cat /etc/resolv.conf

```

---

### Post by sonicislnd on 2009-07-27
I am a linux Ubuntu newbie and I cannot install the network manager on my system to connect to the internet.  My wireless usb driver is installed but I still cannot install.  I get this message -  Network manager  cannot be installed on your computer type (i386).  Please help with step by step instructions as I need them.   Thanks!

---

