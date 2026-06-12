---
title: "ubuntu 10.10 continue to ask WPA"
date: 2011-03-20
forum: Networking &amp; Wireless
---

### Post by peorthyr on 2011-03-20
installed ubuntu 10.10, the ethernet connection is ok, when trying the Wifi, it continue to ask the WPA key (network manager), i've searched for a while, trying some connection menagers, i'm actually using wicd, it find the SSID, try to authenticate, then give a "bad password" error, even if the router has no connection password at all...

i've tryed also the WPA PSK HOWTO, which explain how to edit the /etc/networking/interface, in this case, it seems that it can't connect to the DHCP, when i restart the network it continue to ask for DHCP at 255.255.255.255, with no response. i have a 3945abg intel card... any iedas? thanks in advance.

---

### Post by gradinaruvasile on 2011-03-20
If the router is yourss, connect to it via http and see how it is configured.

---

### Post by peorthyr on 2011-03-20
yes, it's mine, i have tryed WPA, WEP and no encryption, of course setting up them on the router first, then on the wifi manager then.
i've tryed the default connection menager, the wicd, i've also installed the wpa-supplicant and a "b43 package" driver (found on a old thread).

i've also tryed to set the WPA both in the "ascii key" mode and "passphrase" mode, passphrase created with an howot i've founded here somewhere...

the last and most odd action was to set up the router with no encryption, wicd try to connect to it (the status messages say a lot of action perfomed), then it stops on "validating authentication" (i've set no WPA or WPE as i say!) and then... "bad password" O.o

---

### Post by gradinaruvasile on 2011-03-20
Do not install wicd and network-manager side by side. After installing one of them, restar the computer.

---

### Post by peorthyr on 2011-03-20
ok, i was pretty sure that i have uninstalled the network-manager after trying wicd, i've checked and i found some more "network-manager" apps in the package manager, so i've remove them, removed the wicd and reinstalled the wicd (ofcourse rebooting after every step) now the network-manager applet is not showing at all (before this the applet shows up, but it not "managed any connection"), but the problem persist, in wicd it sees the wireless network, it show that it has a WPA encryption, start the connection and finish on bad password :/
let me thank you for the attention,  you are ver quick on answers! :)

---

### Post by gradinaruvasile on 2011-03-20
Open a terminal and type:

sudo iwlist scan

and paste the output here (between code tags)

---

### Post by peorthyr on 2011-03-20
it returns the list of the wifi around me, i've omitted the other ones, this is the part reguarding my router...

```
Cell 02 - Address: 00:25:53:07:E2:4C
                	Channel:6
                	Frequency:2.437 GHz (Channel 6)
                	Quality=32/70  Signal level=-78 dBm  
                	Encryption key:on
                	ESSID:"Alice-53495441"
                	Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                          	24 Mb/s; 36 Mb/s; 54 Mb/s
                	Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                	Mode:Master
                	Extra:tsf=000000086967e183
                	Extra: Last beacon: 2348ms ago
                	IE: Unknown: 000E416C6963652D3533343935343431
                	IE: Unknown: 010882848B962430486C
                	IE: Unknown: 030106
                	IE: Unknown: 050400010000
                	IE: Unknown: 2A0100
                	IE: Unknown: 2F0100
                	IE: Unknown: 32040C121860
                	IE: Unknown: DD0E0050F204104A0001101044000102
                	IE: Unknown: DD090010180200F0000000
                	IE: WPA Version 1
                    	Group Cipher : TKIP
                    	Pairwise Ciphers (1) : TKIP
                    	Authentication Suites (1) : PSK
```

---

### Post by gradinaruvasile on 2011-03-20
Make sure it uses another channel than the rest.

---

### Post by peorthyr on 2011-03-20
nothing, i've set manually the channel (just to be sure it has different one from others) but the problem persists.

after a while, it says "bad password" btw i'll try some more experiments -.-'

---

