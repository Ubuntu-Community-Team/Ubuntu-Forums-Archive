---
title: "Linksys HP200 Wont Connect/Authenticate"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by opticyclic on 2009-06-05
I am running Linux Mint 7 which is based on Ubuntu 9.04
I have a Linksys HP200 Wireless PCMCIA card that I am running with the ndiswrapper.
I can dual boot to Windows XP and use the card without problem.
I copied the installation directory from XP to my home dir and pointed the wrapper to LSMVNDS.inf

The driver seems to be installed, as it picks up the fact there are networks available.
However, when I put in the SSID and password it never authenticates and keeps asking me to put the password in again.
I have another laptop with Mint on it that uses an internal wireless card and this can connect fine with the same credentials.

---

### Post by PatrickVogeli on 2009-06-05
I'd suggest to try wicd. Maybe network-manager doesn't like your card too much.

Are you using some fancy credentials? If you are using wep or WPA for the encryption, I'd try wicd.

---

### Post by opticyclic on 2009-06-05
I am using WPA for the encryption.
I panicked a bit after installing wicd as Synaptic removed network manager and wicd didn't pick up any wireless networks at all.
After a bit of digging around I realised I had to set the wireless interface to wlan0 in the preferences and it found my SSID.

However, I am still unable to connect.

I have noticed that if I put in the wrong password that I get an error returned telling me this so there is some authentication going on.

---

### Post by opticyclic on 2009-06-05
When I change the WPA Supplicant Driver in the preferences from ndiswrapper back to wext I get more info in the status bar:
Putting interface down
Putting interface up
Generating the WPA configuration file
Validating Authentication
then after a while it stops and says Not connected

---

