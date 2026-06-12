---
title: "How can I set up a remote access connection between two linux boxes?"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by jesermay on 2008-12-19
Hey,

I've recently made a computer for my Auntie. She's not very computer literate and needs a lot of help and I was wondering how I would go about setting up a connection between the computer I made for her, which will be at her house, and my laptop, which will be at my house obviously. 

Thanks,

Jeremy

---

### Post by jonobr on 2008-12-19
On her machine you need to enable remote connections
you do that by going to system-> prefs->remote desktop
In there allow sharing with approprate passwords and you should notify the user when doing it.

On your machine connect using application-> internet- remote desktop viewer

Enter contact details and connect.

You must ensure you can ping the remote machine, and that if its a private network you will need to port forward to the remote machine.

You can also use a service like logmein to connect yourself to the other machine

---

### Post by jesermay on 2009-02-11
Thanks,

I'll try that soon!

---

### Post by FJ62Driver on 2009-02-12
Hey, any idea on how to do this on Xubuntu via command line? I only have ssh control (no GUI) on my Xubuntu box, and using Remote Desktop Viewer on Ubuntu 8.10 to connect to it is not working for some reason...

---

