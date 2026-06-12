---
title: "LTSP diskless frontend stalling on boot"
date: 2008-12-06
forum: Mythbuntu
---

### Post by ttabbal on 2008-12-06
I'm using the directions here: 

[https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless](https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless)

It mostly works. I can build the images and try to boot them. But the boot stalls. The only error message I see is "eth0: No link during initialization". It has a link, I just used it to load the kernel! :) 

I'm doing this on my fileserver that's running Hardy LTS. I did an aptitude update and upgrade before starting this work. The server is working, DHCP is working, and I get a kernel and initrd to load. I get a Mythbuntu splash screen, then it goes black with a cursor. The message I mentioned before is from disabling the splash screen in the PXE setup. I don't see any messages about the root FS missing, so I think the NFS mount is working. I have other NFS mounts working from that machine. Is there any way to tell if the client is connecting from the server logs? 

Any ideas would be great.

---

### Post by map7 on 2008-12-10
Does your client show it's network device as eth0?  

I had a problem with one of my PXE machines as it's ethernet device shows up as ath0 under Debian so it doesn't boot.

---

### Post by ttabbal on 2008-12-10
Thanks for the reply. I don't think we have the same problem. I managed to get it working by ignoring the wiki command line directions and using the GUI tools instead. Seems to boot now, I'm just having problems with drivers I'm trying to work out. Not sure on your ath0 issue. A quick search turned up this page, it might help you configure your system to change the interface name. 

[http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames](http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames)

---

