---
title: "Creating an infrastructure hotspot with laptop"
date: 2011-11-02
forum: Networking &amp; Wireless
---

### Post by RobinBrown on 2011-11-02
Is it possible to create an infrastructure hotspot with a laptop (running ubuntu) and a wireless card? If so, how do I do it? I have tried the network preferences dialog (changing the connection type to infrastructure from ad-hoc) without success. What do?

Context - I have a Toshiba AT100, which under the current version of android, does not recognise ad-hoc hotspots (although ice cream sandwich will, apparently). I want to be able to browse the internet on this, in my room at uni which has no wireless. The only resources I have are a laptop connected via ethernet to the uni network, which is then connected to the internet. I have no money to buy a wireless router, before you suggest that.

Thank you :)

---

### Post by pastalavista on 2011-11-02
Click the nm-applet icon in the menu bar and select 'Create a new wireless network' (while still connected to the wired connection) and under the wired connection's IPv4 tab, select Method: 'Shared with other computers'.

---

### Post by RobinBrown on 2011-11-02
Using the network manager GUI doesn't work - not even making an ad-hoc hotspot. It tries to connect to the network, waits a while, asks for WEP key, and repeats indefinitely.

---

### Post by pastalavista on 2011-11-02
> **RobinBrown said:**
> Using the network manager GUI doesn't work - not even making an ad-hoc hotspot. It tries to connect to the network, waits a while, asks for WEP key, and repeats indefinitely.

This is from the Help Menu:

"To set-up an ad-hoc wireless network:
On one of the computers, click the network menu on the top panel and select Edit Connections.
Go to the Wireless tab and click Add.
In the window that appears, choose a name for the wireless network and then look at the Wireless tab.
Choose an SSID. This is the name of the network that other people will be able to see.
Change the Mode to Ad-hoc and leave the other settings at their defaults. Click Save.
On the other computer, click the network indicator on the top bar and look for a network with the SSID you chose. It might take a minute or two to appear in the list.
Click the name of your new, ad-hoc network to connect to it. You will be able to access network shares and so on, like you would if both computers were connected to a conventional wireless network."

Really, this is all I know about it. Never tried it myself. Possibly, your wireless card doesn't support it. Good-luck.

---

### Post by RobinBrown on 2011-11-02
Yep, tried that all already. I can make ad-hoc networks in xp fine, so it's not the hardware that's the problem. Either the driver is rubbish, there's some package I'm missing, or a config file that needs tweaking. I don't know where to begin in determining which is the problem though.

Thanks for your help anyway.

---

### Post by RobinBrown on 2011-11-06
Bump.

---

