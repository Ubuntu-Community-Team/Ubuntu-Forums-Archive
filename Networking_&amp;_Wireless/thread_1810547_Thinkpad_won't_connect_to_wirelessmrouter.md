---
title: "Thinkpad won't connect to wirelessmrouter"
date: 2011-07-23
forum: Networking &amp; Wireless
---

### Post by Funkuncut on 2011-07-23
I am using a Thinkpad T41 with Intel PRO/Wireless LAN 2100 mini pci wireless adapter using Ubuntu 10.04 
I had no problems with connection to a Livebox router using WEP security, but I've just changed ISP to Virgin with a Netgear router - this won't work, as I'm told that it doesn't support Ubuntu, but I've connected a spare Linksys router to it, which works fine with my ipod touch and is detected by my Thinkpad, but I can't connect. It's using WPA security, and I'm asked for authentification but it never connects. Ethernet connection is fine, but as I'm currently stuck in bed after an operation I'd like a wireless connection!
Can anyone help?

---

### Post by bkratz on 2011-07-23
> **Funkuncut said:**
> I am using a Thinkpad T41 with Intel PRO/Wireless LAN 2100 mini pci wireless adapter using Ubuntu 10.04 
I had no problems with connection to a Livebox router using WEP security, but I've just changed ISP to Virgin with a Netgear router - this won't work, as I'm told that it doesn't support Ubuntu, but I've connected a spare Linksys router to it, which works fine with my ipod touch and is detected by my Thinkpad, but I can't connect. It's using WPA security, and I'm asked for authentification but it never connects. Ethernet connection is fine, but as I'm currently stuck in bed after an operation I'd like a wireless connection!
Can anyone help?

You might check the wireless AP to see if it is actually set up for wpa.  If it is actually set to mixed mode, Ubuntu sometimes seems to have problems connecting. You will probably have more luck with either wpa or wpa2, but not both (mixed mode).

---

### Post by Funkuncut on 2011-07-24
> **bkratz said:**
> You might check the wireless AP to see if it is actually set up for wpa.  If it is actually set to mixed mode, Ubuntu sometimes seems to have problems connecting. You will probably have more luck with either wpa or wpa2, but not both (mixed mode).

Thanks for that - I'll give it a go as soon as I can get upstairs and plug in an ethernet connection.

---

### Post by Funkuncut on 2011-07-24
> **bkratz said:**
> You might check the wireless AP to see if it is actually set up for wpa.  If it is actually set to mixed mode, Ubuntu sometimes seems to have problems connecting. You will probably have more luck with either wpa or wpa2, but not both (mixed mode).

The router (Linksys WKPC54G) is set up for WPA, but the Wireless Network Authentication Required window has WPA & WPA2 Personal in the Wireless secrity box, with no apparent means of changing to WPA only. Is there a way of changing this?

---

### Post by Funkuncut on 2011-07-24
I've disabled wireless security and can connect with no problem (except that, given my location, and despite the fact that I don't mind sharing my connection up to a point, it's probably aleady being used to distribute tempting financial investment offers from a number of kindly nigerian Generals...)
Do I deduce that this is just some problem Ubuntu has with security? (the reality, not the concept)

---

### Post by bkratz on 2011-07-24
> **Funkuncut said:**
> I've disabled wireless security and can connect with no problem (except that, given my location, and despite the fact that I don't mind sharing my connection up to a point, it's probably aleady being used to distribute tempting financial investment offers from a number of kindly nigerian Generals...)
Do I deduce that this is just some problem Ubuntu has with security? (the reality, not the concept)


Most of us use some type of security, I use wpa2/aes (never did get wpa/tkip or even wep working!). Perhaps if you try --and fail connection again then look at

```
sudo tail -n25 /var/log/syslog
```

a clue might be there to why you are having problems.

---

### Post by Funkuncut on 2011-07-25
Thank you very much for your help - it is really appreciated.
I only have the option of wpa/tkip on this router. The command you suggested gave me this:

paul@Mothership:~$ sudo tail -n25 /var/log/syslog
[sudo] password for paul: 
Jul 25 12:53:01 Mothership wpa_supplicant[846]: Trying to associate with 00:12:17:dd:12:8d (SSID='linksys' freq=2462 MHz)
Jul 25 12:53:01 Mothership NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Jul 25 12:53:01 Mothership wpa_supplicant[846]: Association request to the driver failed
Jul 25 12:53:01 Mothership wpa_supplicant[846]: Associated with 00:12:17:dd:12:8d
Jul 25 12:53:01 Mothership NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated
Jul 25 12:53:03 Mothership NetworkManager: <info>  (eth1): supplicant connection state:  associated -> 4-way handshake
Jul 25 12:53:03 Mothership NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> group handshake
Jul 25 12:53:03 Mothership wpa_supplicant[846]: WPA: Key negotiation completed with 00:12:17:dd:12:8d [PTK=TKIP GTK=TKIP]
Jul 25 12:53:03 Mothership NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Jul 25 12:53:03 Mothership wpa_supplicant[846]: CTRL-EVENT-CONNECTED - Connection to 00:12:17:dd:12:8d completed (reauth) [id=0 id_str=]
Jul 25 12:53:07 Mothership wpa_supplicant[846]: WPA: Group rekeying completed with 00:12:17:dd:12:8d [GTK=TKIP]
Jul 25 12:53:07 Mothership NetworkManager: <info>  (eth1): supplicant connection state:  completed -> group handshake
Jul 25 12:53:07 Mothership NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Jul 25 12:53:09 Mothership NetworkManager: <info>  (eth1): DHCP transaction took too long, stopping it.
Jul 25 12:53:09 Mothership NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 1421
Jul 25 12:53:09 Mothership NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jul 25 12:53:09 Mothership NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) started...
Jul 25 12:53:09 Mothership NetworkManager: <info>  (eth1): device state change: 7 -> 9 (reason 5)
Jul 25 12:53:09 Mothership NetworkManager: <info>  Activation (eth1) failed for access point (linksys)
Jul 25 12:53:09 Mothership NetworkManager: <info>  Marking connection 'Auto linksys' invalid.
Jul 25 12:53:09 Mothership NetworkManager: <info>  Activation (eth1) failed.
Jul 25 12:53:09 Mothership NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jul 25 12:53:09 Mothership NetworkManager: <info>  (eth1): device state change: 9 -> 3 (reason 0)
Jul 25 12:53:09 Mothership NetworkManager: <info>  (eth1): deactivating device (reason: 0).
Jul 25 12:53:09 Mothership wpa_supplicant[846]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
paul@Mothership:~$ 


Maybe I should try the old Inventel Livebox instead - there was never a problem connecting to that (well, nothing that rebooting wouldn't solve...)

---

### Post by Funkuncut on 2011-07-31
Quick update - couldn't get a connection by changing to wpa/aes, but succeeded with wep on the Virgin Netgear router. Thanks!

---

### Post by bkratz on 2011-07-31
> **Funkuncut said:**
> Quick update - couldn't get a connection by changing to wpa/aes, but succeeded with wep on the Virgin Netgear router. Thanks!



Glad to see you got it sorted.. Sorry wasn't more help. Congratulations!!!

---

