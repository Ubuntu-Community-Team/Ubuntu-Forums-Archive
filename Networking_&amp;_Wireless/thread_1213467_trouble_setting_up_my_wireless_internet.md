---
title: "trouble setting up my wireless internet"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by Thorstien78 on 2009-07-14
i kinda feel like a broken record, as iv'e spent the last five hours reading similair threads.  here's the issue; i have ubuntu 9.04 and did a system update yesterday, it froze during the process and i had to reboot.  after reboot the update completed, but I noticed i had no internet whatsoever. (i always use the wireless)  after a little reading i figured out how to get lan back online, but i have had no success with the wireless. after trying several scripts in the terminal, ikeep getting error messages.  i have found several other threads with similar problems to mine, but none seem to be the solution. my biggest problem is trying to install ndiswrapper-1.55. i have been using this guide-[B]How To: Install Ndiswrapper (source, svn) - with Included Problem Solving Suggestions.  
I get to the part where i have to [/B]Compile and Install ndiswrapper, and that is where it all falls apart.  In order to do this step i need to build a deb package for fakeroot debian/rules binary module and it does not exist and i don't know how to build it or where I can download it. I am very new at linux, but I'm a fast learner.  is there anybody out there who would care to help me?  

my system specs
aspire 5220-1515 notebook
mobile AMD sempron processer 3600+ 
2.0 GHz, 256 kb 

here is a copy of lshw -C networkdustin@dustin-laptop:~$ lshw -C networkWARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:61:f9:75
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.101 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ae:ae:7f:db:51:e7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Thorstien78 on 2009-07-14
Here is the dpkg-buildpackage -rfakeroot command sequence as well.

dustin@dustin-laptop:~/ndiswrapper-1.55$ dpkg-buildpackage -rfakeroot
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
tail: cannot open `debian/changelog' for reading: No such file or directory
dpkg-buildpackage: failure: tail of debian/changelog gave error exit status 1

---

### Post by Thorstien78 on 2009-07-14
**GOT IT!!!!**  I guess i was to hasty in posting this thread.  I went over the ndiswrapper guide for the seventh time and i caught a few of my own mistakes in the command script.  sorry for wasting space with this useless thread.   kevdog is the MAN!  a very useful guide I must say.  linux really is easy, even for a newb  like me.  

When all else fails, try, try again.

---

### Post by Thorstien78 on 2009-07-14
for those of you that are scanning for your own solution, all i did is make sure that I moved the .sys and .inf files from my atheros folder into their own driver folder so ndiswrapper could find them.  

problem solved.  

oh yeah, read the guide VERY CAREFULLY!

Thanx ubuntu forums, your wealth of knowledge is a gold mine for ubuntu users.

---

