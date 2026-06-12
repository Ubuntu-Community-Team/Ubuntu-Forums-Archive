---
title: "Interaction between Ubuntu computer and Smoothwall 3.0"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by Dngrsone on 2009-02-24
I have a home network set up consisting of several desktops and laptops connected to the internet via a Smoothwall Express 3.0 firewall appliance.  I have Win XP Pro, Vista, and Ubuntu 8.10 on these machines (some dedicated, some dual-boot)

My problem is this-- the machine in my garage (the 'lab' machine) is a brand new Ubuntu 8.10 LTS installation.  I can access the internet from it, but when I try to do an update, I get errors like this: [COLOR="Green"] W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
[/COLOR]
If I turn the proxy off on the firewall, I can update normally.

Additionally, I cannot see the 'Lab' machine form any of the other computers on the network.  It can see the other computers on the network, I can ssh into it (once I got the ssh server installed on it) from the network, but I can't access it from Windows Explorer (haven't tried to get it from Ubuntu lately).

I have set up samba on the 'Lab' machine to provide access to one of the partitions on its drive, but it won't work if I can't even see it from the network...

So, this seems to be a firewall problem, but I have an Ubuntu laptop that interacts with the network and firewall just fine.

Any ideas where I might look for a solution to these issues?

---

### Post by Dngrsone on 2009-02-27
Lot of people jumping in on this, thanks!  :rolleyes:  

I gave up trying to get this machine to cooperate, so I am putting it back to XP Pro... unless someone can give me a hint as to why my firewall might not like this Ubuntu machine.

---

### Post by Iowan on 2009-02-27
I downloaded the SmoothWall software, but don't have it installed on a machine yet.  Not that it matters, but 8.10 is not an LTS version.   Dapper Drake (6.06) and Hardy Heron (8.04) are the only two LTS versions I'm aware of.  
[Here ]("http://www.europe.eclipse.co.uk/Ubuntu/810%20on%20Win%20Network.htm") is a How-To that *might* be helpful for integrating Ubuntu into a Windows network... although you mentioned you already have a laptop working fine. Is it 8.10?

---

### Post by Dngrsone on 2009-03-02
I thought it was... now I am not so sure.

The one I have problems with was originally set up with 8.04, but I couldn't update it so I downloaded 8.10 and installed.

The one I am using regularly had 8.04 installed on it fresh, and I have no idea if it's upgraded to 8.10 or not.  Wouldn't you know, I am answering this from Windows right now 'cause Dngrswife is using the computer to watch movies.

---

