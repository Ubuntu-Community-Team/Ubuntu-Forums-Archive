---
title: "No network connection...but I'm on the web"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by YosefKaro on 2009-11-20
Hi, I use a broadband dongle to connect to the internet.  The only way that I could get it to work was by installing kppp.  My problem is that even though I am able to connect to the internet, as far as network connections is concerned, I'm not connected to a network.  This is causing me problems with using ubuntu one and with using virtual box.  How can I solve this problem?

-Yos

---

### Post by Iowan on 2009-11-20
Ubuntu or Kubuntu? I presume the configuration is via */etc/network/interfaces*? (Which is why NM is complaining) There's an option (somewhere) to change **managed=false** to **managed=true**, but I'll need to look up which file.

/etc/NetworkManager/nm-system-settings.conf

---

### Post by YosefKaro on 2009-11-20
I'm on ubuntu.  Well, I changed managed to true but I don't see any difference yet: It still appears as not connected to a network.

-Yos

---

### Post by YosefKaro on 2009-11-21
Any ideas ?

---

### Post by Iowan on 2009-11-21
Maybe I don't understand > I'm not connected to a network. Although I was granted an Ubuntu One account, I haven't used it yet. "Virtual" is still outside my realm.

---

### Post by YosefKaro on 2009-11-21
Most users (I'm assuming) connect to the internet through Network Manager.  When they are connected to the internet, Network Manager shows that they are connected to a network.  So programs like ubuntu one and virtualbox can work with Network Manager: when Network Manager is connected to the internet, then the OS's in virtualbox can also connect to the internet.

The problem that I am facing is that I am unable to connect to the internet through Network Manager: I have to connect in a round-about manner.  However, I want for Network Manager to 'see' when I am connected to the internet so that I can use ubuntu one and my virtual machine to the fullest as well as other apps that may rely on this.

-Yos

---

### Post by steveneddy on 2009-11-21
If you connect thru kppp then go to the network manager applet and disable wireless.

If I connect to my Blackberry for internet access I turn off Wireless internet in network manager.

Disconnect with kppp first - turn off wireless connections in NM - them reconnect your kppp.

EDIT:

When you connect thru kppp, network manager won't show any network activity because you aren't connected thru NM.

Connecting thru NM shouldn't give any issues with Ubuntu One.

---

### Post by alexfish on 2009-11-21
if your in virtual box then virtual box grabs  that device so not available from your desktop  / come out of virtual box / reconnect and test

or disable the device in virtualbox by unchecking the device
 then reconnect from the desk top

if you want to use the web browser in virtual box you don't need the device
   just click on the browser / network manager takes care of that

---

