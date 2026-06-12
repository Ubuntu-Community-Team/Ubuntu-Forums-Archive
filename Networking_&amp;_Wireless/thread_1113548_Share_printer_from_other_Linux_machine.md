---
title: "Share printer from other Linux machine"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by Volt9000 on 2009-04-01
I've got Intrepid running on two machines, one of which has a printer connected to it. The printer is properly set up and configured on that machine, and works. I'd like to be able to use that printer, but I'm not sure what to do. I went to System > Administration > Printing and clicked New > Printer but I don't know which option to choose.

Someone please help!

---

### Post by chili555 on 2009-04-01
Select Internet Printing Protocol (IPP). It should detect your network printer automagically.

Do you have the machine with the printer set up with a static IP address? If not, IPP will either fail to find the printer the next time it boots, or you'll need to install samba, bind and a few other things and do some configuration. I don't know how to do all that, I always thought a static IP was the easy, failsafe way out.

I like easy.

Also, be sure that, on the machine with the printer, the printer properties are marked to share.

---

### Post by Volt9000 on 2009-04-01
Ah nevermind I figured it out... on the host I had to go to Server > Settings and check on "Publish shared printers connected to this system" and on the client I had to check on "Show printers shared by other systems". Problem solved. :D

---

