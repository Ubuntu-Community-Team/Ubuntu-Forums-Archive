---
title: "Lost Notebook WiFi Connection"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by bayvista on 2011-01-03
Recently installed Bigpond ADSL with a Thomson wifi router. Connected desktop OK. Connected laptop OK. Ran for 3 days OK. Then I connected the laptop via Ethernet. Now I cannot get back to wifi. Desktop still OK. Keep getting Authorization screen for WPA but Router does not like this.

As the wife uses laptop, I was forced to go back to Windows which connects without any problems.

Any ideas welcome.

---

### Post by PatchesTheCaveman on 2011-01-03
Hi bayvista.  Happy New Year!

It worked before you plugged into Ethernet but not after?  That's strange.  Did you try and reboot?  At any rate, I'm going to have you run a few diagnostics so we can get an idea of what might be going on.  

Go to Applications > Accessories > Terminal, and type each of these commands in the black box, pressing Enter after each one:
```
lspci -vnn
ifconfig -a
nm-tool
sudo iwconfig
```

After that last one you will be asked to enter your password.  Just type it in and press Enter, even though it doesn't show stars or dots.

Once you have all that, highlight it, and copy and paste it into a reply to this thread.  Hopefully we can figure out what's going on.

---

### Post by bayvista on 2011-01-03
Thanks, I have attached the output from those commands

---

### Post by PatchesTheCaveman on 2011-01-03
I would try replacing NetworkManager with wicd and see if that works better.  NetworkManager and wicd are both programs that run the network icon on your desktop.  Many people find that wicd works better.  

To do so, open a terminal and run:
```
sudo apt-get update
sudo apt-get purge network-manager
sudo apt-get install wicd
```

Make sure you have a working wired connection when you do that.  You might need to restart to fully remove NetworkManager and let wicd take over.

---

### Post by bayvista on 2011-01-04
Hi Patches
Well, that worked! My notebook now connects via wifi without any problems. Thank you very much.
I would love to know why Network Manager couldn't connect.

---

