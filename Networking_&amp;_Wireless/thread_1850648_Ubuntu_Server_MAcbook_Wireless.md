---
title: "Ubuntu Server MAcbook Wireless"
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by Hodge_1974 on 2011-09-26
Hey folks. I have a macbook running 10.4 lts server and if I had hair I'd have pulled it out getting wpa2 enabled. 
If I unencrypt my router I can connect just fine. (so my card is working and I can see my network)

I have read several tutorials and have had to take bits an pieces from them to get to where I am at. I have wpa_supplicant with the following in wpa_supplicant.conf. 

```

ctrl_interface=/var/run/wpa_supplicant.conf
ap_scan=1

network={
ssid ="mine"
scan_ssid=1
proto=RSN
key_mgmt=WPA-PSK
pairwise=CCMP
group=CCMP
#psk="mypassowrd"
psk=bigLongHexNumber
}

```Running wpa_supplicant with:
sudo wpa_supplicant -Dwext -i wlan0 -c/etc/wpa_supplicant.conf

The result is a series of disconnects and timeouts like
Associate with <macadress>
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet

At this point I am fine with starting from scratch, or editing this stuff as it is. I am at loss and have looked and looked with no luck.

---

### Post by Hodge_1974 on 2011-09-26
Would you believe.....
that all I had to do was request a an ip.

dhclient worked instantly and Im rolling. I think I am going to pick up the Soebell book for stuff like this. Piecing together a solution by way of google was painful.

---

### Post by Hodge_1974 on 2011-09-26
Not sure how to mark this as solved...:confused:

---

### Post by Hodge_1974 on 2011-09-30
I had to reboot and I lost it again.  I verified my wpa_supplicant.conf entries were still there. Using the wpa_supplicant command results in what look like successful attempts at adding the interface and authenticating to my router. But after about 10 sec of what looks like looping through the same routine, it hangs at EAPOL Tick --->
1

Dhclient just trys DHPdiscovery several times and then gives up.
I would copy and paste but with server I have command line only. 
Any suggestions would be appreciated. This is particularly maddening seeing as how it was working before I rebooted. Thanks for the help.

---

### Post by Hodge_1974 on 2011-09-30
Of note, when the wpasupplicant goes through the scan, it shows my essid and it says "GTK Cipher Mismatch".

---

### Post by Hodge_1974 on 2011-09-30
My chipset is atheros 5k. I am going to try this link, but I'd be happy to hear from anyone here that might be able to help. Also I am going to try and load the atheros driver in this link.
[http://wiki.debian.org/ath5k](http://wiki.debian.org/ath5k)

---

