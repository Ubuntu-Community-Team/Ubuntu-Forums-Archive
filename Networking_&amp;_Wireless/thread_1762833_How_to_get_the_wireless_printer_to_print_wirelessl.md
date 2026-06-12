---
title: "How to get the wireless printer to print wirelessly"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by duce_85 on 2011-05-19
I have an HP deskjet f4580 and i downloaded hplip and the printer  prints when its plugged into the usb but not wirelessly.. and i noticed an hp setup adhoc on my network connections but i couldnt get on it..i'm nearly certain its something i am missing just dont know what..? and i have ubuntu 11.04

---

### Post by Dennis N on 2011-05-19
Did you go through the dialog under

```
System > Administration > Printing
```

When the printer is connected by wireless connection to your network, click the ADD button in that dialog box, and the printer should be automatically detected as a network printer. The drivers will be installed for you during the setup process. Usually no need for you to download anything yourself.

---

### Post by duce_85 on 2011-05-20
I tried that a million time and i tried to ping it and still nothing.

---

### Post by rickyjones on 2011-05-20
Did you connect the printer to your wireless network? It sounds like the printer is broadcasting its' own wireless network... you'll need to join it to your normal network.

Thanks,
Richard

---

### Post by duce_85 on 2011-06-01
it did have its own wireless network in the beginning then it vanished

---

### Post by rickyjones on 2011-06-01
> **duce_85 said:**
> it did have its own wireless network in the beginning then it vanished

Yes, I believe that printer can broadcast its' own ad-hoc wireless network. However for you to access it the printer must be connected to your regular wired/wireless network. If you do not have a wireless network then you'll most likely need to purchase a wireless router/access point to make it work. Another option is to physically connect the printer to the network.

Thanks,
Richard

---

### Post by duce_85 on 2011-06-01
I have connected it to my regular wireless network through hplip and it says it online the wireless light on the printer stop blinking and lights up to indicate its on. its almost like something is blocking the connection but i dont have a firewall and antivirus or anything like that

---

### Post by duce_85 on 2011-06-01
and for me to physically connect it to the wireless network i would need the ip address and dns to the printer but i dont know how to print that out

---

### Post by rickyjones on 2011-06-01
I'm confused... is the printer connected to the wireless network that you have in your home? If it is, then it should (most likely) be configured for DHCP, so it should already have an IP address. Find the manual and it'll give you instructions on how to find the currently assigned IP address. Then see if you can PING it from your desktop.

Thanks,
Richard

---

### Post by duce_85 on 2011-06-01
could not find how to get the printer IP address but i did  print out the network configuration page and its says its connected to the network i put it on but still not printing wirelessly

---

### Post by duce_85 on 2011-06-01
i pinged it and i got a response and as it was catching a signal the wireless light blinked and lit up when i got the response

---

### Post by rickyjones on 2011-06-01
> **duce_85 said:**
> could not find how to get the printer IP address but i did  print out the network configuration page and its says its connected to the network i put it on but still not printing wirelessly

So the network configuration page says it is connected to your network, but it doesn't list the IP address? Can you check your router to see if it lists the printer in the DHCP table? Once you find that you should be able to set up the printer like normal.

Thanks,
Richard

---

### Post by duce_85 on 2011-06-01
Now it recognizes it wirelessly but its saying its printing when it isnt

---

