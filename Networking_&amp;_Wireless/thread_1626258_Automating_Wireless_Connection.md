---
title: "Automating Wireless Connection"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by rbscairns on 2010-11-20
I have recently done a clean install of Ubuntu 10.10 on my eee B202. I have a few little niggling problems that I am trying to sort out. One of them is connecting to my wireless network.

For a little more secturity, I have my wireless network set up such that it does not broadcast the SSID. At each start up, I have to go through the following steps to connect to my wireless network:

[LIST=1]
[*]Log in (Admin group) using my password
[*]Click on the Network item in the panel
[*]Select "Connect to Hidden Wireless Network"
[*]Select my Connection (NSD)
[*]Enter my login password again
[*]Click on connect
[/LIST]

If I go into my to Network Connections window, select the Wireless tab, highlight my NSD connection and click on Edit, I am taken to the Editing NSD window. Here I have-

[LIST]
[*]Connect automatically [Checked]
[*]SSID: = NSD
[*]Mode: = Infrastructure
[*]MTU: = automatic
[*]Available to all users [Checked]
[/LIST]

Is there a way to set Ubunto 10.10 up so that it connects automatically after step 1?

---

### Post by puppywhacker on 2010-11-20
In the field BSSID you can put the MAC address of the wireless access point. The thing is that if you hide the SSID you can not connect to it by name since it is hidden en not broadcasted. The BSSID however can not be hidden and is specific to your device, it's supposed to be unique, but it's relatively easy to clone.

Beware that hiding your SSID will not make it completely invisible, so security wise it's only a small step forward.

---

### Post by rbscairns on 2010-11-20
Puppywhacker, I owe you a beer or three. Thank you. My wireless connection now works automatically.

Hiding my SSID is only a small part of my network access security. I also have WPA & WPA2 security with a strong randomly generated network key, and access restricted to pre-approved MAC addresses only.

---

