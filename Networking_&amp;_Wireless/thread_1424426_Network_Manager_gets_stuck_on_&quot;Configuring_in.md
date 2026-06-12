---
title: "Network Manager gets stuck on &quot;Configuring interface&quot;"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by WickedShadow on 2010-03-07
The KNetwork Manager when trying to connect to my network gets stuck on "Configure interface".

Statistics:
Type of Wireless Card: D-Link Wireless N USB Adapter DWA-130
Network Settings:
 SSID: Irrelevant
 Security: WEP
 IP Address: Automatic
Driver: Ndiswrapper/DWA-130

Any reasons why this may be happening?

Thanks in Advance,
Wicked Shadow

---

### Post by WickedShadow on 2010-03-08
*cough*

---

### Post by ORBAT on 2010-03-08
> **WickedShadow said:**
> The KNetwork Manager when trying to connect to my network gets stuck on "Configure interface".

Statistics:
Type of Wireless Card: D-Link Wireless N USB Adapter DWA-130
Network Settings:
 SSID: Irrelevant
 Security: WEP
 IP Address: Automatic
Driver: Ndiswrapper/DWA-130

Any reasons why this may be happening?

Thanks in Advance,
Wicked Shadow

Are you in control of the WLAN AP? If so, try setting it to no encryption and see if you can connect. If you can, the problem might be with the WEP password. That, or the DWA-130 and AP may just simply not work together. I've had lots of problems with some WLAN APs in the past and some just flat out refuse to work with Linux.

Can you connect to other APs?

What does /var/log/syslog say when you're trying to connect?

---

### Post by WickedShadow on 2010-03-08
I will check up on all that...

---

### Post by WickedShadow on 2010-03-08
It works without using the WEP password im haqppy and using it to post this :D

---

### Post by ORBAT on 2010-03-09
> **WickedShadow said:**
> It works without using the WEP password im haqppy and using it to post this :D

The only problem now is that you're using an insecure connection. Anybody could either eavesdrop on you or just start using your connection. You should google for your WLAN AP / card combination and see what kind of experiences other people have had. It's a mighty bad idea to have no wireless security. In fact, in some countries you'll be liable for anything stupid someone does while using your connection. You could also try WPA or WPA2 encryption and see if it'll work (however it's pretty unlikely since WEP didn't work either.)

---

### Post by B.W. on 2012-05-19
I just had the same problem and solved it. The origin was trivial: wrong WPA password. Re-entering the correct password helped.

Now for how that password got there... well, it seems my computer connection got knocked out somehow - happens . Then it prompted me for my keyring password. I entered the keyring password in good faith. And that was the end, the computer would not log me in.
Imagine my surprise now as I opened Network Manager and checked "display password" for that connection: the password was the keyring password (the one needed to access non-system connections), not the wifi password (the one to open this particular network)... Misguiding dialog box I guess...

---

### Post by howefield on 2012-05-19
Thread closed.

---

