---
title: "WiFi FAILURE To CONNECT: Linksys BCM4303"
date: 2011-04-08
forum: Networking &amp; Wireless
---

### Post by only1egg on 2011-04-08
Hello Fellow Linux Groupies,
 
Being this is my first post to the group, please pardon my ignorance of any protocols or procedures here. Having built and worked on PCs for many years, in the past I’ve always been able to solve my own problems by trolling through forums like this one, at least until now. 
 
Over the past couple years, I’ve successfully converted four household PCs one by one over to Linux OS, usually dual booting between Windows, and the latest version of Ubuntu. The last one to be switched over is my son’s AMD Athlon 1000mhz PC, with 524mb RAM, running under MS Windows 2000, an OS frankly older than he is. 
 
When beginning this process, the machine still held its antiquated ASUS 802b PCI card, which worked fine under MS Windows drivers, but which I was unable to get functioning under Ubuntu. Then went on to try Linux MINT, OpenSUSE, PCLinuxOS, and Puppy in turn, and all failed. Each one installed and dual booted under GRUB, and using NDISwrapper was able to load Windows drivers, and usually get them working… once. Then after the first reboot, in one way or another each system would either crash, lockup, or simply fail to respond. This was followed by then dropping in the GParted CD to wipe the OS, and start over again. Ultimately, I had to admit defeat, realizing this ASUS card was the source of the problem. 
 
So I swapped the ASUS to a friend for a Linksys WiFi card, with a Broadcom BCM 4303 chipset, mainly because post in various forums suggested it might be more compatible under Linux. Reinstalled Ubuntu once more, and attempted to use NDISwrapper again, seemingly with mixed results. Digging deeper, found suggestions pointing towards using b43-fwcutter, with b43legacy drivers, having some success… at least the system didn’t crash on reboot. Kept at this for many hours, searching through forum posts, tweaking settings, and seem to finally have a stable Ubuntu install. The Linksys/Broadcom WiFi card has been configured, and is currently able to recognize the two old Wireless Access Points I have in the house. HOWEVER, for some reason, it still is unable to connect to the internet. 
 
Oh, this WiFi card does repeatedly try to connect, switching back and forth between access points, until finally giving up and quitting, without making a connection. Have compared settings on this card when running under Windows 2000, as well as other WiFi enabled PCs around the house, and still find no faults within the Network Configuration. The card just scans for a very long time, then finally gives up… Which is kind of where I am now myself. After several days of trying to get this old PC networked with Ubuntu, I am about at wits end here, and thus am turning to the “Wise Ones” among you for guidance. 
 
Would welcome any assistance you UberGeeks might be willing to provide, as I am comfortable staring into the terminal, and would run any line command test suggested, then post the results back to the forum. Presently I can also download any needed updates into this box via an Ethernet connection here in my office, but it is impractical to run a cable all the way to the boy’s room. Frankly… I believe that I’m now very close to finally being able to return possession of this old PC to my son, allowing me to take back the HP Pavilion laptop for my own use. Ultimately, I am really looking forward to introducing him to the joys of Ubuntu Linux, just as soon as I am able to provide him with a functional and stable wireless internet connection on his own computer. 
 
So… Anybody want to take on this Wireless Networking challenge? Anyone…? Thanks in advance for any good ideas!
 
Sincerely
Only 1 Egg :confused:

---

