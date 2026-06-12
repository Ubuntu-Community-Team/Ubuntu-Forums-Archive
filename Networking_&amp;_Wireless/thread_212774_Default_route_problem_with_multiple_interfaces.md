---
title: "Default route problem with multiple interfaces"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by Aramis on 2006-07-10
Hi y'all,

I have several Ubuntu machines (both Dapper and Brezzy) with multiple interfaces. I use these to perform some network tests. Hence the interfaces are used as follow:

1 - interface eth0 connected to 192.168.0.0/24 used for management (ssh) purposes
2 - interface eth1 connected to 10.0.10.0/24 used for testing, the interfaces typically received their IP, default gateway via DHCP.

Now I have some machines on the 10.0.20.0/24 network. What I would like to achieve is that the tests use the Interface ETH1 do reach the 10.0.20.0 . I know about the ROUTE command. **However**, it would appear that EVERY time the interface ETH1 looses connectivity the ROUTES are flushed and hence all my tests subsequently fail.

My query is quite simple, I would like to be able to configure the "ROUTE" everytime the machines boot, or everytime the interface ETH1 comes (back) up. I have done a bit of research, and found the following topic : [ [link]("http://ubuntuforums.org/showthread.php?t=82369&highlight=multiple+interfaces+route") ] . Unfortunately the last post's author does not give an example of the type of script, or syntax, that could be used.

all help will be apprieciated,

Cheers...

---

### Post by mpvano on 2006-07-10
Since you are trying to do something failry advanced, I assume you will NOT be using a GUI to configure things.

Read man pages and /usr/share/doc for at least the following: interfaces, ifup, ifdown, ifconfig, iwconfig

Configure your interfaces exclusively using the interfaces file as described in that documentation. You can put custom route (or any other arbitrary commands) in interface paragraphs in /etc/network/interfaces and they will always be executed when the official mechanisms are used to start and stop networking.

However, be aware that the Gnome network administration applet and some wireless card "managers" do NOT properly use this file. Don't use them if you are manually configuring interfaces.

Mario

---

### Post by Aramis on 2006-07-10
Hello Mario and thank you for this speedy reply.

my machines are not installed as server, but 99% of the time I use the command line to configure them, or do my tests. As for the various man pages that you have mentioned I had a read over them, and I must say I did not "see" an example of 'interfaces' with a custom route in it. But I guess after reading you I ll go back to them.

I ll try to remember your advice on the Gnome Networking manager and the like ;) 

Cheers,

Ar@mi$

---

### Post by mpvano on 2006-07-10
You can put ANY arbitrary linux command in an interface paragraph, and have it executed either BEFORE or AFTER the interface is enabled. Sometimes the use of things like this are so obvious they're easy to miss!

You can use this to put any actual "route" command either in an interface paragraph or in a script in the various directories that autoexecute scripts. The script method is more flexible if you want to run more code to make a more complicated routing decision before adding the route.

You can also just put scripts into ifup.d and ifdown.d (and all their friends) to automatically be executed. The benefit/nuisance of doing it this way is that the script needs to figure out which interface is being enabled or disabled.

Also make sure you read carefully the parts about what happens when "ifup -a" and "ifdown -a" are executed. They're widely used by the system in unexpected places like suspend/resume, startup/shutdown and when changing run levels. They're also called from higher level scripts like the master service script that starts and stops networking.

The problem with GUI managers is not that they're GUI's. The problem is that they sometimes directly issue networking commands instead of going through the proper "channels" (like ifup and ifdown) to make sure that all the pieces of the system get the message.... It's not good to have too many bosses...

hope this helps...

Mario

---

### Post by Aramis on 2006-07-14
Hi Mario,

just a quick update! I have decided to use the solution with **UP** in the appropriate "*interfaces*" paragraph. I am afraid I am too new to the Linux/ubuntu to fully comprehend the bit about ifup ifdown and the like. I have done some test with my *new* Interfaces file and except for a corrupted ARP-cache for a minute or so after change of network speed, it works fine. Since I repeat the various tests many times, I can cater for one or two errors/failures.

That is that for the moment!

Thank you very much for your help...

I ll keep you posted :D

Ar@mi$

---

