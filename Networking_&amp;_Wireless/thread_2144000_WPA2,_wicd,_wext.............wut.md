---
title: "WPA2, wicd, wext.............wut?"
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by tjefferson on 2013-05-10
A family friend gave me an old computer (c. 2006) to play around with. I installed lubuntu 13.04, and it works pretty well. Unfortunately, the wireless is kinda wacky. On the first install, it would connect through network-manager without a hitch. I learned how to use wget and downloaded a few other applications. Suddenly, the wireless no longer worked, and in my many attempts to reconnect, I ended up bricking the system.

I connected the computer with ethernet and did a fresh install last night, but the wireless still doesn't work. I install WICD, as per another thread's suggestion. It seems to work better than nm, which i uninstalled, but it hangs up when trying to validate the connection.

I've tried using iwconfig, iwlist, wpa_supplicant, etc. None of these seem to work. I'm kind of a newb, but I can follow directions pretty well.

I have to type all this by hand on another computer, so please don't ask me for hundreds of lines of output. :) I'll post any necessary information, but here's what I think to be germane: 

wireless hardware: DLink USB, model# DWL-G122 B1 (no internal wifi card)
card name: wlan0
network encryption: WPA2 PSK

**sudo ifconfig wlan0 up**
[INDENT]yep, i made sure the device is on.[/INDENT]

[B]iwlist wlan0 s
[/B][INDENT]this correctly identifies my network. [/INDENT]

[B]iwconfig wlan0
[/B][INDENT]identifies card wlan0 just fine.[/INDENT]
[INDENT](output): IEEE 802.11bg ESSID: off/any Mode: Managed Frequency: 2.447 GHz Access Point: Not-associated TX-Power=20 dBm Retry long limit:7 FTR thr: off Fragment thr:off Power Management:on[/INDENT]

i can assign an essid to wlan0 with
**sudo iwconfig wlan0 essid my_network** 

no problem here, and it shows up correctly on **iwconfig wlan0**, as well.

i made a _wpa_supplicant.conf_ document at /etc. It's reproduced below:
[B]ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2
network={
[INDENT]ssid="my_network"
scan_ssid=1
key_mgmt=WPA-PSK
#psk="my_password"
psk=hex_my_password[/INDENT]
}[/B]

when i run **sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext**, the output is nonsensical. sometimes it says **ioctl[SIOCSIWENCODEEXT]: Invalid argument**. i often get ** association request to the driver failed**

I installed WICD, and have tried all this with the GUI frontend. No dice. Any ideas?

---

