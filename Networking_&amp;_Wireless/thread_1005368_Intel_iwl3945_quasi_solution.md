---
title: "Intel iwl3945 quasi solution"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by Grzybu123 on 2008-12-08
At first of all, sorry for my English (i using PL and i didn't know english names of some programs - please feel free to ask). Since I'a using Ubuntu 8.10 i got problem (like many others) with Intel 3945 (didn't connect at all). So here the way i forced the card to work with the wpa2 hotspot.

At first i tryed to connect, entering right pass and then put down wlan0 interface. I opened gnome pass manager and find entry for that code, retype it there (since it changed into a lot of numbers) and then pilagges for networkManager and connection-editor to read only.

I entered connection modifier in gnome network configuration and change that connection to auto connect.

When i wake wlan0 interface it try to connect, but didn't get ip / dns and all other things...

And here is a funy story. When i plugged ethernet cable from wifi router at system startup wifi also connects (!!). When unplugged its keep working fine. When i down interface and up without ethernet cable its can't get IP and didn't connect... Its look like it is a problem with gaining TCPIP configuration from wrong interface.

I got most updated Ubuntu, no backports installed.

I hope this will help solve iwl3945 problem.

---

