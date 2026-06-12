---
title: "Linksys WUSB54GC"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by completetech on 2011-04-06
Sorry to make this my first post :(  but after reading over the forums and searching for hours and hours and also Googling for about the same amount of time I need some assistance.

I have a MacBook Pro with Parallels installed.  I am running Ubuntu 10.10 in a Parallels virtual window.  Nice as it only took less then 10 minutes to install.  Anyhow thats a little about the setup.  now onto what I am trying to do and the issues.

I have a older Linksys WUSB54GC that I want to use within Ubuntu (sometimes) to use aircrack-ng and a few other utilities with it as seeing this card is supported by a lot of these types of apps.

However when I tried to follow a bunch (of the same guides it appears), I see the device using the lsusb command and it shows on 
BUS 001 Device 002 ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink rt73]


show it is showing up.  It lets me connect, however when I try to disable the airport device within the MacBook I am not able to get out to the internet, I can only ping my router.  nothing else outside of my local network.

What could be the cause of this as I can not seem to get this figured out and all of the guides here seem to be for the newer V3 of this model.


I guess at this point I am not really sure where to go from here as I am still fairly new to the whole Ubuntu / Linux command line (even though I should know better by now, to have switched that is to this a long time ago).

Any suggestions and / or help you can give me in getting this going or directions would be great.


Thanks!

---

### Post by completetech on 2011-04-15
Is this one of those things that is something that no one else is wanting to do or not???

Just looking for a little guidence

---

### Post by uncaspi on 2011-04-15
First have a look in /etc/resolv.conf to see if the nameservers are listed.

---

