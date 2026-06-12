---
title: "Connecting two computers together"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by Robert Finley on 2011-01-06
I've been searching all morning.. please help.  I know the answer is simple...
 

 I have:
 Acer laptop dual booting win 7 and mint 8
 Cisco E1000 router
 Ancient desktop created out of parts laying around (incl. ethernet card) running ubuntu 10.04
 

 I connect wireless to the internet on the laptop on a public connnection not through the router it is just extra
 The desktop cannot connect to the internet it has no wireless
 

 The goal is to get the files from the laptop to the desktop.  Being able to share the internet would be nice but not todays mission
 

 What do I do here?  I tried ethernet cable from computer to computer = neither computer could connect
 

 I've tried connecting the desktop to the router via cable and the laptop via wireless = on the laptop when I go to the network folder I see "robert-laptop" and "Windows Network"
 

 "robert-laptop" shows me a folder called print$. It wants a password for WORKGROUP to get in.
 "Windows Network" shows a folder called WORKGROUP containing "robert-laptop" containing print$ and needing password again
 

 On the desktop when I go to network folder I see "robert-laptop" and "Windows Network"
 

 "robert laptop" says "could not display "smb://robert-laptop/" the file is of an unknown file type
 "Windows Network" contains a folder called WORKGROUP that is empty
 

 If I hook both computers to the router
 

 On the laptop network/windows network/ is now an empty folder
 everything else is the same..
 

 I tried connecting from win 7 to ubuntu also with similar results I read on google that connecting win and ubuntu is a pain, figured mint would have no problems.
 

 Someone please help me.  I just built the desktop.  It has a clean install of ubuntu but can't download updates

---

### Post by hansolo4949 on 2011-01-06
I believe that you need some networking packages for Ubuntu, plus, you probably don't have file sharing enabled. One way to share a file is to right click on it, then click "share this file". That should work.

Hope I helped! 

hansolo4949

---

### Post by gordintoronto on 2011-01-06
If you right-click on a folder, you can select "sharing options." Say you want to share the folder, give it a simple, lower-case name, and click the other two boxes. It's possible Ubuntu will need to install software to do the sharing, but I think Mint includes it.

You can download .deb files from packages.ubuntu.com and move them to a computer which has no Internet access, using a flash drive, CDRW, etc. Watch out for dependencies: they must be installed first.

To access a shared folder, I always go network/windows network/workgroup/computer/sharename.

---

### Post by Robert Finley on 2011-01-06
Ok, I got the allowing the folders to be shared thing.. did it

When I connect both computers to the router, neither computer sees the other.  On both computers the Windows Network folder is empty

Now what?

---

### Post by Robert Finley on 2011-01-06
I can't share the folders on the desktop.

When I try is says Sharing service installation failed.

---

### Post by gordintoronto on 2011-01-06
> **Robert Finley said:**
> Ok, I got the allowing the folders to be shared thing.. did it

When I connect both computers to the router, neither computer sees the other.  On both computers the Windows Network folder is empty

Now what?

Some routers have a setting to block communication between computers. In some routers, it is called "unicasting."

---

### Post by gordintoronto on 2011-01-06
> **Robert Finley said:**
> I can't share the folders on the desktop.

When I try is says Sharing service installation failed.

Did it say you needed to install Samba?

---

### Post by thefix0r on 2011-01-06
Oh this is an easy one!

Ok so your laptop is connected to the internet over wireless.

So enable connection sharing, right click your network adapter and enable internet connection sharing, then connect a CROSSOVER cable, unless your laptops new enough that it has an autosensing gigabit ethernet port, then you can just use a regular cable, that old ethernet port on the old computer wont know what to do when connected to another 10/100 computer. So if both are 10/100 youll need a crossover cable more than likely.

Soz, then it wouldnt work, unless you used a switch to connect between them. 

Ok, also setup a dhcp client on the ubuntu server machine, edit your conf

nano /etc/network/interfaces
google will answer how to set that up

---

### Post by PatchesTheCaveman on 2011-01-07
thefix0r:  Most Fast Ethernet (megabit) devices these days have auto-sensing ports as well.

---

### Post by kevdog on 2011-01-07
I know what you want to do -- share files -- but it depends how slick of system you want to be.

Crude -- copy to cd or thumb drive
Step up -- ftp/ssh server
Live file system - nfs, samba, cifs, or if encryption need encfs

As the solution becomes more elegant -- the cost of setting it up makes it harder.

---

### Post by dandnsmith on 2011-01-07
> **PatchesTheCaveman said:**
> thefix0r:  Most Fast Ethernet (megabit) devices these days have auto-sensing ports as well.

I'm sure you're right there - but connecting PC to PC directly can be a different thing, especially with old hardware (see original post). I need a x-over cable with netbook to fairly old hardware, otherwise the sensing just doesn't happen.

I start the testing by using tools like ping, just to verify the path (OK, pings can be blocked by firewalls ...) - simpler than working out the bugs in such an ad-hoc network.

I haven't noticed anyone mention assigning IP addresses - I doubt, with such a PC to PC connection, whether addresses will have been set to usable values for network traffic.


For ease, use a usb-stick to transfer material.

---

### Post by Robert Finley on 2011-01-07
Dude, you nailed it on that one.. 

I could just copy the files manually (though it seems not to see my thumb drive) on removable media.

But what I want is a server.  I have never attempted a network setup before, but I have a LOT of hardware. I really don't need more then 3 computers on the network at a time.

I am totally willing to format harddrives, reload systems, download packages, or whatever. Everything is backed up.

I just tryin to figure out what I need to do.

I read about crossover cables, and even how to make one, but that isn't really the solution I seek.

I don't know anything about I.P. addresses.  Can you point me to a networking primer.  Idk, I was just looking at all these computers and this router and thinkin "how hard can it be?"

---

### Post by Robert Finley on 2011-01-07
Ok yeah, live file sharing is what I'm going for here.

just downloaded the samba tarball. reading about it now

---

### Post by PatchesTheCaveman on 2011-01-07
Samba is included in the Ubuntu repositories.  You can install it by searching for "Samba" in the Ubuntu Software Center or by running this command on a terminal:
```
sudo apt-get install samba
```
No need to build it from source!

There is also a great graphical tool to configure Samba shares.  I prefer it to right-clicking on folders and using the Sharing tab like most people do.  To install it, search for "system-config-samba" in the software center or run:
```
sudo apt-get install system-config-samba
```

Then run it by going to System > Administration > Samba in your top panel.

Also if you want to share Internet from the laptop to the desktop I explained how to configure it in this thread:
[http://ubuntuforums.org/showthread.php?t=1655454](http://ubuntuforums.org/showthread.php?t=1655454)

If either your laptop or your desktop's are relatively modern (manufactured within the last 3-4 years or so), you should be able to plug them in directly to each other with any Ethernet cable.

---

### Post by dandnsmith on 2011-01-08
> I read about crossover cables, and even how to make one, but that isn't really the solution I seek.

I don't know anything about I.P. addresses. Can you point me to a networking primer. Idk, I was just looking at all these computers and this router and thinkin "how hard can it be?"

If you have a router, get it gets vastly simpler, as you have (almost certainly) the ability to assign IP addresses automatically by employing DHCP (ubuntu assumes this is used for networking, by default).

As to the networking primer, I occasionally see references to them (written for one audience or another). I don't keep the references, partly as the detail of hardware/software changes, invalidating some of the primer, but mostly because I was networking computers from the early 80s, forget things, but can muddle through most of the time.

---

