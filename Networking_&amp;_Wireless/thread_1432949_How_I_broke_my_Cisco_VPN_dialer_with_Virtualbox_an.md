---
title: "How I broke my Cisco VPN dialer with Virtualbox and how I fixed it"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by sween1911 on 2010-03-18
I use Cisco VPN to dial into my work network from home when I support On-Call. I recently upgraded from 7.10 to 8.04 Hardy, and had to get the newer client, patch it, and got it to work.

ACT I:
Just last night, I was playing with VirtualBox. I had to help test our webapps that use IE, so I was hoping I could create a Windows box for said testing. I tried loading up an old Windows install disk I had just to get the hang of creating the virtualbox. I got a few kernel-related errors, so I went into Synaptic, searched on "Virtualbox" and downloaded virtual-box files relating to my Kernel until it eventually worked. During this process, I removed and installed Virtualbox a few times until it would work. I got an old Windows 98 installation to actually work! Yay.

ACT II: Ever since I upgraded to Hardy, I've been checking my VPN whenever I change anything, just to make sure it works. While I was playing with the virtual 98 machine, I tried my VPN dialer. No gots. I got the... I forget the exact verbiage.. "Cannot Connect... is kernel installed?" something like that. I tried installing VPN again. No gots. WTH? I was trying to think (and panic set in as I'm currently on-call) what could the virtualbox thing do with regard to my kernel? Wasn't the whole point of the virtualbox a way to play with a system isolated from the host system? One thing I noticed was when I install Cisco VPN, it asks me for the kernel source directory. When I installed it a few weeks ago after upgrading to Hardy 8.04, it shows you the defaults. There was no default for my kernel source this time.

ACT III: In desperation, I called in a solid from my system admin at work. This was 10pm last night. Fortunately, 1) she's a Linux user 2) apparently I got on her good side 3) She must have a soft spot for fellow Linux users fighting the good fight. She talked me through checking my kernel level and installed packages...

Weird, I run "uname -a" and it displayed my kernel, but the matching directory was not in the /usr/src directory. Hmmm... she suggested that my repeated install/removal of Virtualbox may have cleaned it up, moved it, or done something bad to it. Yeah I dunno, but it was working fine right before I began messing with this. Maybe I removed the headers accidentally and didn't realize it. I checked the VPN the first time I installed Virtualbox and it worked fine. Anyway, I went in as root, did a find from /, and couldn't find the headers that matched my kernel. Which made sense that the VPN installer couldn't find it to display it as one of the defaults. She talked me through running apt-get to go get my needed headers, but I got 404 not found. I tried it in Synaptic and got same deal. Had to open up my sources, re-run package manager, search on "linux-headers", scroll through to find the one that matched my kernel, and installed it. Re-install VPN, re-patch (the original code was fine, but just to get a clean run, I re-did the tar file, so I needed to repatch it), drop my VPN profile file in the place, and it worked!

Putting this out there in case anyone runs into anything similar. Thanks.

---

### Post by sween1911 on 2010-03-18
Follow up problem... Oddly enough, I came home from work today to my wife telling me that the sound doesn't work. I figure it was installing new headers last night or playing with the Virtualbox. I know there have been many problems with sound in 8.04, but I can assure you it worked fine when I upgraded from Gutsy. I had purchased some MP3's from Amazon, listened to them and put them on my iPOD with no problems since I installed, but before the problems yesterday.

So, I am booting into the Linux Kernel second down on the grub list.

My kernel that was giving me sound problems: 

 2.6.24-27-386

I am booting into 

 2.6.24-27-generic 

and sound works fine.

---

