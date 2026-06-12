---
title: "Sky Broadband Wireless (Black Netgear Router) with Hardy (8.04)"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by Grez on 2010-03-30
After having some difficulty getting this going, I thought I'd share a few tips to get you started.

The problem I had was that having installed the driver for the dongle, it was picking up the router, but Hardy wouldn't allow me to use the correct protocol (WPA Personal) to access the thing using automatic detection. So this is what you do:

1 Click the network icon and choose "Manual configuration..."

2 Click "Unlock" in the "Network Settings" dialog box and enter your sudo password when prompted.

3 Click on the "Connections" tab, select "Wireless Connection" and click the "Properties" button.

4 Uncheck the "Enable Roaming Mode" check box, top left.

5 Select your Network name (ESSID) from the drop down box.

6 Select your Password type as "WPA Personal" from the drop-down box.

7 Type your Network key (printed on the base of the router) into the Network password box.

8 Select Configuration as "Automatic Configuration (DHCP)" from the drop-down box.

9 Click OK, and hey presto, the computer should now be up and running on the internet.

If your wireless network fails to connect next time you log on, follow instructions 1-3 and re-enter your Network key. It would appear that Hardy encrypts it and that there are some problems with it "forgetting" the encryption.

Have fun! :D

---

