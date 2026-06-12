---
title: "Beginner installing drivers for Nvidia 460GTX through terminal needing little help..."
date: 2011-03-12
forum: Multimedia Software
---

### Post by Hektik Keef on 2011-03-12
Basically, I think this will be an easy one, but I have downloaded the drivers from NVidia,  and have entered the command given on the page with the download, but it just says error- NVidia installer must be run as root.   How do I do this? 

Details of system  Ubuntu 10.10 64, no dual boot. Pentium quad core. card is 4600 GTX.  one 250Gb system drive, one 1.5 Tb storage drive, both  SATA 2. 4gig DDr3 memory

---

### Post by 289Shelby on 2011-03-12
sudo sh <Nvidia driver.run>

sudo gives you root privileges. 

It will ask you for *your* password which won't be displayed.

Hope this is what you need.

---

### Post by Hektik Keef on 2011-03-12
That failed.  Terminal just displayed-
                                syntax error unexpected token `newline'
Nvidia site says this command line         sh ./NVIDIA-Linux-x86_64-260.19.44.run       is the answer, it says it cant open /nvidia -linux-x86 when i feed it that prefixed with sudo.  
                            Cheers for the trying tho...

---

### Post by gmargo on 2011-03-12
You don't need to do it manually.  You can use the drivers in this PPA:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by Hektik Keef on 2011-03-12
Right.  you could say that all worked,, as in drivers where installed- except the colours are out.   There should be screenshot attached to this if  it worked.  I notice that there is a colour balance corrector widget/ thingumybob as part of the driver preferences, but what to do with it i dont know,  Cheers tho. is one step closer to making it work...

---

### Post by Hektik Keef on 2011-03-12
aaaah>  No its worse than mis balanced colours.  When I disable the card to just use the standard monitor out,  Computer refuses to boot, asks for my login on a blank black Terminal screen, then tells me is a problem with CPU security, but when i change the setting it tells me to in the BIOS,  I dont even get asked to login on a blank black screen that leeds to nothing.  To get rid off these not working X drivers, do I use the purge command listed on the site that they came from?  And how do I install the official Nvidia drivers i can download,  Via terminal?  I dont mind using it,  just don't know it at all well yet..·

Final note after I worked it out-
The reason why the issue with the BIOS  and CPU security is still a mystery,  but a quick re-install and following the same steps got the card working normally,  although I had made the muppet mistake of connecting a modern card to an old monitor,  and the colour balance looking out while being correct in the above screen shot is a result of that muppet mistake.  Sorry folks...

---

