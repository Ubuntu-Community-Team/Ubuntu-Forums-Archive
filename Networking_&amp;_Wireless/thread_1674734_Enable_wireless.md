---
title: "Enable wireless?"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by mollycule on 2011-01-24
I have an Asus Eee PC with Ubuntu Netbook Remix (Unity).  The other day, I turned off the wireless using the keyboard shortcut to save battery life when I was somewhere without wireless, but now it's not turning back on.  I tried restarting, I've done the keyboard shortcut several times, and it still just says "disconnected" for wireless and wired, even though there are several wireless networks around me right now.  There aren't any options in Network Connections or Network Tools to turn on the wireless.  Is there a way to manually turn it back on?

---

### Post by grahammechanical on 2011-01-24
I am not using Netbook Remix, so what I see on my desktop version of Ubuntu may not be the same as what you see on the Netbook Remix version. Please understand that.

Is there a network icon that you can right and left click on? On my version a right click produces a drop-down menu and I can see a tick mark against the lines Enable Networking and Enable wireless. Can you see anything like that? Are the tick marks there? If not put them there by clicking on them.

Do you see a line that says Edit Connections? Select it and edit the wireless connection to Automatically Connect. Or go to Network Tools as you have already done. Select the Wireless tab and set the connection to Automatically Connect using that method. Then when you reboot, with the keyboard shortcut switched on it will try to make a connection and if the pass-phrase is correct it will make the connection. If you modem/router is switched off it will tell you that there are wireless connections available. A left click of the icon will show you the available networks.

Even though the two editions are different in some ways they must be able to do the same things even if they are done in a different way.

Regards.

---

### Post by nm_geo on 2011-01-24
> **mollycule said:**
> I have an Asus Eee PC with Ubuntu Netbook Remix (Unity).  The other day, I turned off the wireless using the keyboard shortcut to save battery life when I was somewhere without wireless, but now it's not turning back on.  I tried restarting, I've done the keyboard shortcut several times, and it still just says "disconnected" for wireless and wired, even though there are several wireless networks around me right now.  There aren't any options in Network Connections or Network Tools to turn on the wireless.  Is there a way to manually turn it back on?

Also try this in terminal

```
rfkill list
```If we get a yes like these:
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

Then in terminal: ```
sudo rfkill unblock all
```

---

