---
title: "Sharing Network Printer"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by fleamour on 2011-02-23
I have shared my printer between laptop & host PC successfully by entering the IP address under Find Network Printer.  Problem being the router uses DHCP, so when the host PC is assigned another IP address the link is broken.

I do not know where to start looking, or even the correct terms to Google.  But think I need to find the host PC's address that under Windows starts with \\ or //.  Merely typing the host name draws a blank.  Am I along the right lines?

Help!

---

### Post by howefield on 2011-02-23
Assign a static IP to the host.

---

### Post by headvampyre@hotmail.co.uk on 2011-02-23
As the last post didnt post much info... Go to terminal and type:
ifconfig

Find the interface your using, for ethernet its probably eth0 and for wireless - wlan0.

Then right click on the network icon (top right of the screen, next to volume) and select "Edit connections", then go to the tab for the type of connection your using, then ipv4 settings and on the dropdown box select "manual".

Now, go back to terminal and find "
inet addr:" < this is probably something like 192.168.2.5
then go back to the connection editor and click add.

Set the address to the IP we just found.
Now go back to terminal and get the "mask:"

This number is what goes in the netmask box.
Now go back to terminal and type route -n
The gateway is on the bottom line under the "Gateway" section.

Copy this into the Gateway in network manager.

Now for dns, i just use googles servers, so in the dns box type:
8.8.8.8,8.8.4.4

Thats it :)

---

### Post by fleamour on 2011-02-24
Thanks!!!

:):biggrin::)

---

### Post by fleamour on 2011-03-04
Only problem with all that is I have DHCP set up on my router.  The PC drops the internet connection when rebooting with fixed IP.

---

