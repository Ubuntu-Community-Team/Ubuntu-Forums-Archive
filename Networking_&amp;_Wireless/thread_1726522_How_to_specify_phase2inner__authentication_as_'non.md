---
title: "How to specify phase2/inner  authentication as 'none' in NetWork manager ?"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by lenkite on 2011-04-11
Hi,

I have already managed to connect to my corporate wireless network which uses WPA Enterprise/PEAP along with an identity and a password using my *Android* phone. 

Unfortunately, I am unable to do so via Ubuntu 10.10 on my laptop. The issue that I observe is that the 'Wireless Security' tab of network manager has 3 options MSCHAPv2, MD5 and GTC for Inner Authentication. But there is no option for 'None' - which is what my Android phone specifies. 

I tested whether this difference was responsible by explicitly specifying these 3 authentication options on my android phone and with any of the 3 selected, the wireless connection was unsuccessful. So I confirmed that this phase2 or inner authentication needs to be set to None in order to be successful. But network manager doesn't seem to allow a none or empty option. Should I open a bug on this ?

Do I need to manually setup wpa_supplicant.conf and /etc/network/interfaces ? The latter is a long winded procedure and I am uncertain about the 'side-effects' it can have with the network manager applet.

Any help/pointers appreciated!

---

### Post by misiu_mp on 2011-06-10
I am exactly in the same situation.
I would also like to know how to specify phase2/inner  authentication as 'none' in NetworkManager.

---

### Post by mbewley on 2013-04-17
> **misiu_mp said:**
> I am exactly in the same situation.
I would also like to know how to specify phase2/inner  authentication as 'none' in NetworkManager.

Me too - has anyone resolved this? Very frustrating!

---

### Post by markus_b on 2014-02-13
This is an old topic, but I just came across this problem on a corporate network with Ubuntu 12.10 and found a solution:

Edit the file /etc/NetworkManager/system-connections/<SSID> and set 'phase2-auth' to 'none'.

---

