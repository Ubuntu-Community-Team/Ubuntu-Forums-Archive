---
title: "Connecting two machines via shared internet"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by bravo sierra echo on 2009-10-09
Hello,

I have two computers which share an internet connection.  One is running Xubuntu Jaunty, and I would like to copy all the files on it to the other machine, running Kubuntu Jaunty, for the purpose of backing it up before reinstalling the OS.

Last time I did this was a couple of years ago when I had a desktop Mac and a laptop running Ubunty Hardy.  They connected quite happily using ssh and I was easily able to transfer files between them using an ftp client with ssh support.

This time around, I can't make it work - I just get "connection refused" errors.  I've been using Gigolo on the Xubuntu machine, and Putty on the Kubuntu one.  I've also tried the ssh command from the terminal - same problem.

The two machines can ping each other.

When I did this before it just worked, so I don't know what troubleshooting steps I should be taking.  Help please?

---

### Post by Iowan on 2009-10-09
Have you installed SSH-server on Xubuntu? Ubuntu usually comes with clients installed - but not the server side.

---

### Post by bravo sierra echo on 2009-10-09
Tried installing this on both machines...

I can now use Putty to log into a terminal on the Xubuntu machine (which is called Ariane) from the Kubuntu machine (which is called Apollo2) but I'm not sure then how to copy the files over using terminal commands.

Doing it the other way around, I can now connect Ariane to Apollo2 using Gigolo.  Apollo2's IP address appears as a location, but it will not open in a file window - it just doesn't, no error message, no nothing.

Many thanks so far, it's a first step, I just need to find a file manager that works now!

---

### Post by bravo sierra echo on 2009-10-09
Haha!  Done it.

The preferences in Gigolo need adjusting to add your file manager.  I'm now looking at Ariane from Apollo2 and will start backing up now!

Thanks so much for your help - that was just the step in the right direction I needed!

---

