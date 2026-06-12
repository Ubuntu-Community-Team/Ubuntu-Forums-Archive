---
title: "How can I reinstall my wireless driver ?"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by hoboy on 2009-05-08
I am using ubuntu 9.04 on stationary computer, after installation my wireless worked very fine until few days ago.
now when iwconfig the outpu.
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.462 GHz  Access Point: 00:90:4C:7E:00:6E   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-29 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

virbr0    no wireless extensions.

pan0      no wireless extensions.

---

### Post by chili555 on 2009-05-08
> my wireless worked very fine until few days ago.I am afraid you have not given us enough information to work with. Your *iwconfig* looks fine, except you are not associated with any access point.

When you click the Network Manager icon to connect, does your wireless interface show up? Do you see your network? Does it try and fail to connect? Does it connect and then drop? Or does it connect and the surfing is very slow?

---

### Post by hoboy on 2009-05-08
> **chili555 said:**
> I am afraid you have not given us enough information to work with. Your *iwconfig* looks fine, except you are not associated with any access point.

When you click the Network Manager icon to connect, does your wireless interface show up? Do you see your network? Does it try and fail to connect? Does it connect and then drop? Or does it connect and the surfing is very slow?

A:You say that "except you are not associated with any access point." How do I do that ?
B: does your wireless interface show up?- Yes  and it has my NetGear name on it.
C:Do you see your network? nop before it was on the panel it has desapeared from their.
D: Does it connect and then drop? no ,it used to but not anymore.

---

### Post by chili555 on 2009-05-08
> does your wireless interface show up?- Yes and it has my NetGear name on it.Isn't NetGear the name of you router? When you see it in the Network Manager icon, can't you click on it and connect? Where are you seeing 'NetGear?' Isn't it in the Network Manager icon, after you click it?

---

### Post by hoboy on 2009-05-08
> **chili555 said:**
> Isn't NetGear the name of you router? When you see it in the Network Manager icon, can't you click on it and connect? Where are you seeing 'NetGear?' Isn't it in the Network Manager icon, after you click it?
This is where I se NetGear, before it was visible on my menu panel,there was a menu like I could click on to se if Netgear was connect, then I could select NetGear to connect as they are other wireless round me.
but this menu/buton has been deleted, it is not there anymore

A:System/Network connections/wireless--here I can se auto NetGear 13 days ago

---

### Post by hoboy on 2009-05-08
> **chili555 said:**
> Isn't NetGear the name of you router? When you see it in the Network Manager icon, can't you click on it and connect? Where are you seeing 'NetGear?' Isn't it in the Network Manager icon, after you click it?

When I install ubuntu on the top-right corenr of my screen there was an icon that showed Network connection, that icon has desapeare, not there anymore, on that icon i could click to se if NeteGear was connected or I had a wired connection.

---

### Post by chili555 on 2009-05-08
Please right click on the panel, hit add to panel, and then select network monitor. Or, if that doesn't work, press Alt-F2 and type:```
nm-applet --sm-disable
```Are we back in business?

---

### Post by hoboy on 2009-05-08
> **chili555 said:**
> Please right click on the panel, hit add to panel, and then select network monitor. Or, if that doesn't work, press Alt-F2 and type:```
nm-applet --sm-disable
```Are we back in business?

Tks a lots my wireless is working now, in fact i am answering this mail using it,I have also got the network monitor icon on the menu panel.
but this is not what I had when I install  ubuntu from scratch.
It was an icon when I click on I could se a wired and  other wireless round me then I could select mine to connect.
But I am very please that my wireless is working very fine that is the most importent to me.

---

