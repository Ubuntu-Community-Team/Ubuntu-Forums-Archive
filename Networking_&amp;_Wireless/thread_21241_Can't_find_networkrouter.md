---
title: "Can't find network/router"
date: 2005-03-21
forum: Networking &amp; Wireless
---

### Post by edwina on 2005-03-21
I'm starting to run out of hope on sorting this out, so this is my last shot. Any help would be gratefully received! Unfortunately I'm a total newbie, so am reliant on fairly simple instructions. Once I've got Ubuntu internet up and running I'll have a better chance of getting to grips with it.

I've installed Ubuntu onto a 20Gb drive that I added to my Windows PC. Windows is still installed, on a separate drive, and allows me to access the internet quite happily through my ethernet router/modem using DHCP. Similarly, Knoppix 3.7 gets me straight onto the internet, although I haven't tried the Ubuntu LiveCD.

When I install Ubuntu, all goes very happily with the only hiccup being the ethernet part. The installer tells me that it can't find a network, or something, and advises me to assign a static IP or use etherconf once the installation is complete. I really don't know how to use etherconf, or even where it is, so that leaves me a bit stuck.

When I do an ifconfig there is nothing very helpful to see - the only IP I can see is 127.0.0.0 or something. No sign of a familiar 192.168.1.2 or anything. Using Network Settings (or the terminal) I am unable to ping 192.168.1.2 (or similar) or 10.0.0.0.

If I set up a DHCP connection in the Network tools (or whatever it is), then it won't go active. The "active" box just unticks itself after a few seconds.

The device manager recognises my ethernet card but there's no sign of my router.

Finally, my installation appears to have some other (related?) problem. It gives me a long list of failed items along the lines of "lib/modules/2.6.10-3dmdk". Could this be relevant? Is there any way of finding out what failed to install at boot without copying it (very fast) from the screen as it scrolls past?

Presumably I am missing something here. As Knoppix picks up the router, I would assume that the relevant drivers are in a standard Debian-based package, although this may be wrong. I am not sure that I know how to find and install a relevant driver, so perhaps I could grab it from my Knoppix CD?

Sorry to be so very long-winded, but I'm trying hard to put down as much relevant information as I can. I've spent a ridiculous amount of time trying to work this out via forums by booting to Ubuntu/Windows and trying things out. Any ideas?

Many thanks.

---

### Post by node on 2005-03-21
What NIC do you have ?

---

### Post by kleeman on 2005-03-21
It sounds like you are using hoary since you appear to be using the 2.6.10 kernel. Hoary still has bugs including quite possibly networking (I have had probs). Try using warty and if that works upgrade later (using apt-get dist-upgrade and the instructions on this site) when bugs are sorted out.

---

### Post by edwina on 2005-03-21
Thanks for responding.

I am definitely running the Warty release (4.10). I seem to remember it coming up on the install, plus the file I downloaded from Ubuntu is called *warty-release-install-i386*, which seems pretty clear.

My ethernet runs straight off my Asus P4S800 motherboard. Is that what you mean by NIC? The motherboard manual defines the LAN as:* integrated MAC with VIA 6103L 10/100 LAN PHY*, if that helps.

---

### Post by kleeman on 2005-03-21
OK so I misunderstood. If you have lib/modules/2.6.10-3dmdk this suggests a 2.6.10 kernel (but also a Mandrake kernel as this is what mdk usually means). But maybe you didn't properly catch the flying text.  So  does ifconfig show eth0 or just lo? If it only shows lo your network interface card may not have a module loaded. Newbie execise  8)  Use google to find the module for your nic (use the info you gave in the last post). Check to see whether it is loaded by using lsmod (it should show up as a seperate line). If it isn't try loading it manually using modprobe (as root type "modprobe MODULENAME"). If it is try bring up the interface eth0 using the ifup command (again as root). Report any probs here  8)

---

### Post by alastair on 2005-03-21
"lib/modules/2.6.10-3dmdk" ?

Are you sure? That's a Mandrake extension (mdk)? Mandrake? Something's screwy about your install/setup if this is printed.

As for Hoary vs Warty - I would advise you downloading and installing a Hoary snapshot. It is close to release now. Will it work for you - hopefully it will, but no guarantees. 

17th March :
[http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/5.04/array-7/](http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/5.04/array-7/)

---

### Post by edwina on 2005-03-21
Thanks for all of that. I shall try it when I get home and let you know.

The Mandrake thing makes sense, in a way. I had Mandrake 10.2beta installed previously but installed Ubuntu over the top (erase entire hard-drive option). I installed Lilo onto the same drive (not the Master Boot Record) in both cases, but it still boots up with the Mandrake background until the Gnome GUI kicks in. Perhaps there are some pieces of Mandrake still floating around. I'll reformat the drive through Windows and reinstall.

For the record, Mandrake gave me several headaches with sorting out screen resolutions and the like. As I couldn't get the internet working with that either, I thought I'd try Ubuntu. It's a much cleaner installation method, I found, using Ubuntu - fewer CDs, fewer questions and fewer errors.

Thanks again. I'll keep you posted.

---

### Post by kleeman on 2005-03-21
If you are getting a Mandrake background before gnome and seeing mdk stuff fly by I would strongly suspect you are actually booting Mandrake. It is very hard to mix distros in the way you are suggesting. A clean install sounds like a good first step  :D  :D  :D

---

### Post by stoneguy on 2005-03-21
Possibly you installed Mandrake using a separate /boot partition? If your LILO entry is pointing there, that would account for the flyby Mandrake background. Since you (cautiously) are using a separate drive for Linux experiments, I'll second kleeman's clean install recommendation (including taking down any partitions on that drive).

---

### Post by edwina on 2005-03-23
Hurrah! Ubuntu Hoary installed happily and set up my internet by itself. Thank-you very much for all your help. The solution is often so simple, isn't it?

For the record (in case it helps anybody else) ...

Having installed Mandrake previously on my second hard drive, I had to erase the partitions on the drive via Windows (control panel/admin tools/disk management as it isn't visible via My Computer). I then installed Ubuntu 5.04 to that second drive with the Grub boot loader. I had to edit Grub by pressing 'e' at the menu because I hadn't realised that Grub treats the first drive (hd0) as whichever drive boots first. I had chosen to install Grub on my second drive, not the master boot record (MBR) of my primary, Windows drive. To boot Ubuntu, therefore, I simply change the primary boot drive via the system BIOS. This keeps my two OSs completely separate, which helps to avoid newbie problems.  ;-) 

I tried all of this with Ubuntu 4.10, but it didn't sort out my internet for me. As 5.04 sorted it out straight away, I didn't bother trying to understand what had gone wrong previously.

Thanks again everybody. I'm loving my Ubuntu set-up!

---

