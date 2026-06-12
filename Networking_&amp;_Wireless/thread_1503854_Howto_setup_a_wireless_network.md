---
title: "Howto setup a wireless network"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by IronArjen on 2010-06-07
I want to setup a wireless network in my lab. Main reason is that I want to be able to print from every computer, but it would also be nice if we can share files. I have three 64 bit machines, a netbook and 32 bit notebook and my internet goes via an Wifi router to which other Windoooze machines connect. I want to change to Lucy now and hope it is easier to setup the network in  clean manner.

---

### Post by Detonate on 2010-06-07
If all of the machines are connected to the wireless router, setting up the network is no different than setting up a wired network.  For printing support I would suggest a wireless network printer.  I use a Brother HL-2170W which was easy to setup with a fixed IP which is what I recommend.

---

### Post by IronArjen on 2010-06-07
Please excuse my ignorance,

Then ,how does one setup a wired network?
Unfortunately I have to work with the printers I have, meaning not wireless.

---

### Post by Detonate on 2010-06-07
Need more information.  Will these computers all be running linux?  Or will there be a mixture of Linux and Windows machines?  Do you want all of the computers to be able to access files on all of the other computers, or will you have one computer designated as a server, where all of the shared files will be stored?  Are the printers installed all on the same computer, or are they on different computers?  Are they on windows or Linux computers?  Do you have a computer you can designate as the "print server"?  If you use a computer as the "network server" it can be the same computer.  How many computers and printers do you have?

---

### Post by IronArjen on 2010-06-07
All PCs will run Ubuntu.
I think I like the server idea. The main things we share are PDFs and sometimes we exchange files to work on. Now we use mail or a ISB stick for that. This is easier no? How heavy is this on the "server". Can one still work normally (I have double core PCs).
I have two printers.

---

### Post by Detonate on 2010-06-07
As you are not using any Windows machines in the network, I would recommend NFS as the fastest and most reliable network.  A little trikey to set up, but once you've learned it, it's a piece of cake.  Do yourself a favor and estgablish a static IP address for every computer to be on the network.  This will make things a lot easier.

See this "howto" for setting up NFS.

[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)

---

### Post by IronArjen on 2010-06-08
Unforatunately, the system manager of the faculty says the Wifi net does not support static IPs. The IPs remain ID for one week. Should I use another system or just deal with changing the IPs once a week? I am also thinking just to keep the server running.

---

### Post by Detonate on 2010-06-08
The first thing you need to do is get a new system manager.  He doesn't want to be bothered with taking the ten minutes it would take to change a couple of settings in the router.  NFS will work anyway, but every time a new IP gets assigned to a computer, it will break your network, if you set it up with IP addresses.  You will have to set it up using the computer name instead of the IP address, and each computer will have to have a unique name.  He's making things a lot harder than they need to be.

---

### Post by IronArjen on 2010-06-08
Imagine that that is the guy who is helpful! I will set out to set it up with names and if I run into problems put a new thread. Thanks for all the help!

---

