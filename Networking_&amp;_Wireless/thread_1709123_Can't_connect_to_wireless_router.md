---
title: "Can't connect to wireless router"
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by mr.grimlock on 2011-03-17
Hi, I have installed ubuntu 10.10 and am really happy. I want to sort the wireless conection out now.
I have been through this forum for hours today and can't get it working. Would love someone to help.

I have a Broadcom wireless card, which seems to be working fine, but I am not 100% convinced.
I have attached the output of some of the commands that I have seen referred to on here.

I am using the wired connection on the same router, so the router connects fine.
I click on the network icon and I see the skyNNNN router in the list. I have tried connecting to 
it and it asks me for my password, which I provide then nothing happens until it asks me again.
I have removed the security from the router and I then see the same skyNNNN router without a
lock icon. I try to connect and it still fails.

I am not using an access list on the router, so there is no issue with the mac address.

Can anyone shed some light on this for me please?

Thanks

---

### Post by Yutsud on 2011-03-17
I am trying out the Netbook edition of Ubuntu and everything but Wifi is working perfectly fine. I have always been able to connect to wifi on this netbook while using windows, but for some reason I just can not connect to the same wifi routers while using Ubuntu, well, at least not automatically. Does Ubuntu automatically connect to new routers, there is nothing under the wifi options as far as possible connections.

---

### Post by mr.grimlock on 2011-03-17
If you connect to the router, then an entry appears in the network connections panel. You can then set it to automatically connect, but I think it has to connect first.

---

### Post by Ryan20 on 2011-03-17
When you're typing in the password, have you tried different options in the drop down box?   Are you using a network key for the pass?  Sorry I can't offer your anything more technical, I'm new to this myself but I managed to get connected after some fiddling.

---

### Post by mr.grimlock on 2011-03-18
thanks for the reply. I was only presented with one option in the password dialog, so it wasn't that, but I still can't connect even when I take the security off the wireless router.  This can't be hard to resolve surely?

---

### Post by Ryan20 on 2011-03-18
How did you go?   Are you running Ubuntu 10.10? 

Like I said I'm not a techie, but have you got router / modem connection?  

Maybe it's something to do with the MAC address not being the same with the router and modem?  Has it worked in the past with another OS?

I have to go to work.  I hope someone else steps in and give you a hand before I get back!   I think there's a big difference in our time zones and I doubt I could be any real help!

---

### Post by varunendra on 2011-03-20
For secured networks, you have to put the passkey / passphrase under NetworkManager's Wireless settings, and at the same place, you have to choose the correct encryption type that your wifi router is using.

For unsecured connection, the encryption type has to be set to "None".

The NetworkManager icon appears at top right side of the screen as concentric arcs (when using wireless) or two opposite arrow marks (when using wired LAN).


The basic troubleshooting steps would be:

[LIST=1]
[*]Click on NetworkManager icon and see if your wireless network is there in the drop-down list. If it is not, then maybe it is not detected or the wifi interface is disabled for some reason.
[*]Right-click on the NM (NetworkManager) icon and make sure "Enable Networking" has a tick mark by its side. If it is not there, just click it to put the tick-mark.
[*]Right-click NM > click "Edit Connections" > goto "Wireless" tab > select your network > click "Edit" button > goto "Wireless Security" tab > choose correct encryption type (WEP, WPA,.... whatever your router uses).
[*]Enter the passkey (mind the case of letters)
[*]Click "Apply" and close the dialogue-boxes.
[/LIST]
Wait a minute to let the settings take effect. If the security type is "WPA/WPA2" type, then give "personal" type the first preference, if it doesn't work then try "enterprise" type.

These are normal steps to connect to a secured wifi network. If these don't work, only then extended troubleshooting is required (which I'm not expert of).

---

### Post by gordintoronto on 2011-03-20
Is the SSID really skyNNNN? Try changing it to skynnnn.

---

