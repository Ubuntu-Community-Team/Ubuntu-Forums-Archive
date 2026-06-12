---
title: "Get Mac OSX and Ubuntu 9.04 to share folders."
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by anonymousturtle3 on 2009-10-13
Hello,
I have two computers that I get on regularly, an iMac with Mac OS X and an HP pavilion desktop with Ubuntu 9.04 on it. Both are connected to the same hub (The Pavilion is upstairs and the Mac is downstairs but I ran a wire from upstairs to the hub that is next to the Mac) and the HP is connected to a Linksys wireless router that we use as a hub upstairs to connect two computers to the Internet (it was the only thing we had, but it works quite well, and we get wifi in the house :P). I was just wondering if someone could give me step-by-step instructions on how to set up a network that both Ubuntu and Mac OSX can access easily in order to share files. It would make it a whole lot easier since I am often running my flash drive from one computer to the other. Let know before you start giving me the instructions whether the network will be through the wireless connection (which also reaches the mac) or the wired connection. I am not a beginner in Ubuntu or OS X but I don't know a lot about networks and I don't want to screw anything up.

Thanks in advance.

---

### Post by rifak on 2009-10-13
this might not be what you are looking for, because it's not a home network, but you could dry Dropbox on each computer. its an online storage system that syncs all computers connected to that account. i use it for home/work/school and it works great. you can also create links to share files with others who don't have dropbox...you can do a lot.

basically, how it works is this: in your home folder on each computer, you will have a folder named "Dropbox". you can put files in this folder, and it is uploaded to Dropbox's online storage (which you can access). then, if you look on another computer that has Dropbox installed and linked to the same account, the file is uploaded there automatically. also, if you are not on the computers with Dropbox installed, you can download files from the online service, edit it, and upload back into there and it will automatically change the files on your home computers.

---

### Post by anonymousturtle3 on 2009-10-17
After a few hours of trying, I finally got what I wanted. I had to follow a tutorial ([http://maketecheasier.com/ubuntu-intrepid-how-to-share-file-with-mac-os-x-via-netatalk/2008/11/05](http://maketecheasier.com/ubuntu-intrepid-how-to-share-file-with-mac-os-x-via-netatalk/2008/11/05)) which got me set up, but I still couldn't connect until iTunes on my Mac let me know that my firewall would not allow file sharing between computers. So I just set up my firewall to allow local filesharing.

It is pretty much exactly what I wanted.

---

