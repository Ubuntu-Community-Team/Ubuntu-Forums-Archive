---
title: "Not connecting to server but can ping it"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by mnduck on 2009-11-05
I&#8217;ve very little real experience of Linux and I should also admit to command line phobia but I&#8217;ve managed set up a small network with ClarkConnect 5 as a file server wired to the router and the clients connecting wirelessly.
The clients were all windows pc&#8217;s so obviously the server is running samba and all worked well until I swapped my mini9 to UNR.  I have the mini9 up and running and browsing the internet but it can&#8217;t see the server or connect to it although it can ping it.

The windows PCs still connect and work with the server as expected it&#8217;s just the UNR  mini9 that&#8217;s giving a problem. I have installed no extra packages other than the driver for the wireless card it&#8217;s a default install.

I should add that the user name and password are the same as they were when the mini9 was running XP and able to connect to the server.


Any suggestions as to where I should go from here?

One other smaler issue; on bootup I get a bootloader screen and I would prefer it to boot straight into UNR how do I fix it?


Many Thanks          mnduck.

---

### Post by Lars Noodén on 2009-11-05
If you think of it as shell scripting, rather than 'command line', it is easier to get into the philosophy of that interface.  And it maybe avoids the years of negative marketing from a company that can't do shell...

When you did the netbook, did you add Samba clients?  If so, did you bring over your configuration files?  If not, then that would be the first step.

You can look in Synaptic (the package manager) to see if "Samba clients" is installed.

---

### Post by Lars Noodén on 2009-11-05
> **mnduck said:**
> 
One other smaler issue; on bootup I get a bootloader screen and I would prefer it to boot straight into UNR how do I fix it?


If the bootloader is grub, then you need to set the timeout to 0 and make sure that UNR is the default operating system if you have others.  I usually have another linux distro (or version) plus OS X and/or BSD, so I need a longer timeout.  

if the bootloader is grub, then the package 'startupmanager' might be what you are looking for.

---

### Post by mnduck on 2009-11-05
Thanks, I was wondering if I needed some part of samba to get it going.


Best Regards       mnduck

---

### Post by mnduck on 2009-11-07
I've installed samba, samba clients and samba 4 and so on but I still cant connect to my server.

It's getting to be a problem now I'll have to go back to XP if I cant find a way to fix this.


Please help    mnduck

---

### Post by mnduck on 2009-11-07
file manager has found the server and mounted it BUT I still cannot see any files :confused::confused::confused:


mnduck

---

### Post by Iowan on 2009-11-07
If the files are there and properly shared, [this]("http://ubuntuforums.org/showthread.php?t=1169149") one *might* help.

---

