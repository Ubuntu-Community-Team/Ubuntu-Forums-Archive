---
title: "Using WinXP as Gateway (?)"
date: 2006-01-02
forum: Networking &amp; Wireless
---

### Post by DarkW0lf on 2006-01-02
My modem is not supported so will have to find another way.
Internet access is dial-up and I am looking to use the WinXP's connection.
My idea was to use a X-over CAT5 between the two machines.

PC #1
Ubuntu 5.10
Dell Optiplex
3905 100 BaseTX [Boomerang]
3905B 100 BaseTX [Cyclone]

PC #2
WinXP Home SP 2
Dell Dimension 2350
Broadcom 440x 10/100 Integrated Controller
BCM V.92 56K Modem

How would I go about using the WinXP as a gateway (correct term?) for the Ubuntu system ? Mostly I am looking to make sure I can get two dissimilar machines talking to each other.

---

### Post by DarkW0lf on 2006-01-02
My initial post didn't go through right so when I rewrote I forgot to mention that  one of the two NIC's in the Ubuntu system is onboard, I didn't know this when first setting it up. I think the Cyclone is the one I put in.

---

### Post by cwaldbieser on 2006-01-02
[QUOTE=DarkW0lf]My initial post didn't go through right so when I rewrote I forgot to mention that  one of the two NIC's in the Ubuntu system is onboard, I didn't know this when first setting it up. I think the Cyclone is the one I put in.[/QUOTE]
Both systems speak the TCP/IP protocol.  On XP, there should be an "Internet Connection Sharing" option under your network settings somewhere.  Just set up you Ubuntu machine to use the XP machine as its default gateway.

---

### Post by Adrian on 2006-01-02
This should work:
Run the Network Setup Wizard (can be found in the File menu of the Network Connections window). There you can configure Windows to "share an Internet connection". I don't remember the details, but it was pretty straight-forward.

When the wizard finally asks you to create a setup disk for the other computers in the network, just chose "No". Now, Windows will act as a DHCP server (which is nice and simple).

---

### Post by DarkW0lf on 2006-01-03
Okay thanks I'll try it out.

I think once before that is the same wizard I tried but I confused with the options. One was a vpn using nic's the other was a direct connection using the modem (I don't want a vpn, and I can't use the modem in ubuntu). I'll see if that wizard is the same one that gave me fits before.

---

### Post by DarkW0lf on 2006-01-03
Ran the wizard
XP reports that the two pc's are connected.
I cannot ping the XP box from Ubuntu nor the Ubuntu from XP.
Both NIC's in the Ubuntu box are set for DHCP.

What else can be done to test connection or config ?

---

### Post by Adrian on 2006-01-03
[QUOTE=DarkW0lf]Ran the wizard XP reports that the two pc's are connected. I cannot ping the XP box from Ubuntu nor the Ubuntu from XP. Both NIC's in the Ubuntu box are set for DHCP. What else can be done to test connection or config ?[/QUOTE]

Make sure that the firewalls (if any) on both ends are configured correctly. What happens when you do an "ifconfig" on the Ubuntu machine?

---

### Post by DarkW0lf on 2006-01-06
ZAP on windows box was configured during Network Setup Wizard.
Added the connection to trusted zone.
No entry of ping attempts appears in log.

Output of ifconfig attached.

---

### Post by diggs on 2006-01-06
maybe just go buy a router. make your life easy and safe!

---

### Post by DarkW0lf on 2006-01-07
Would you know of a router that has a dial-up modem in it ?

Internet access is dial-up, I will need to get the ubuntu box to connect using XP's connection.

After rebooting (after some windows updates) I can now ping both computers.
But the ubuntu box is 192.168.0.226 when windows tells me that it is 192.168.0.0

So the two are connected now I am trying to get the Ubuntu box to access the internet. (I have told XP to share the dial-up).

---

