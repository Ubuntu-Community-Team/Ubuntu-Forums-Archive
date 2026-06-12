---
title: "connecting to a hidden ap"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by inso_741 on 2010-10-16
I've entered the essid, wpa2 key and the bssid but kubuntu still won't connect to the router....m I missing something here?

---

### Post by kio_http on 2010-10-16
Yes, some people get confused with the password prompts:

Kdewallet > Stores all password that are unlocked when you type a master password. The first time you store a password, you are prompted to create a password for kdewallet.

Network Manager promt> WPA2 password goes here.

If you state what version of Kubuntu you have, I can give you step by step instructions on how to set up the connection.

---

### Post by inso_741 on 2010-10-16
I found [this]("https://bugs.kde.org/show_bug.cgi?id=209464")....
I'm using the live version of kubuntu 10.10 x64...I've no such problem with ubuntu...I would have tried wicd but I need to be connected to download it in the 1st place....maybe I should stick to ubuntu until the above bug is fixed

---

### Post by kio_http on 2010-10-16
> **inso_741 said:**
> I found [this]("https://bugs.kde.org/show_bug.cgi?id=209464")....
I'm using the live version of kubuntu 10.10 x64...I've no such problem with ubuntu...I would have tried wicd but I need to be connected to download it in the 1st place....maybe I should stick to ubuntu until the above bug is fixed

"This" is for the years old using KDE 4.3.1. Kubuntu 10.10 runs KDE 4.5.1!!
Are you sure you are not typing the password of wireless in KDE wallet?

You can still avoid using the network plamoid by installing knetworkmanager or even install gnome's network applet and use it.

---

### Post by inso_741 on 2010-10-16
I've added a new wireless connection in the manager and entered the passkey in the security tab after selecting wpa/wpa2 personal protocol....there was no wallet prompt...I'm using live usb of kubuntu...how do i install knetworkman w/o a working internet connection....and the whole point is to test kde so if I have to install and use gnome applet I'll rather stick to ubuntu

---

### Post by kio_http on 2010-10-16
>>>[URL="http://packages.ubuntu.com/lucid/network-manager-kde"]http://packages.ubuntu.com/lucid/network-manager-kde[/URL

Now knetworkmanager may probably be already installed in Kubuntu. Try running it. ALT + F2 
```
knetworkmanager
```

---

