---
title: "A newb trying to set up a network."
date: 2012-09-02
forum: Networking &amp; Wireless
---

### Post by feldon0606 on 2012-09-02
So hello and welcome!
I have this little project in mind, one that will allow me to learn basics of networking, and to be honest I don't think I can do it on my own.

I want to set up a wired (I will explain later on why) network between 2 laptops and an external hard drive.

One of my laptops (I've named it the FAP_BOOK) has a broken wireless card built in. I do have several external Wi-fi thingies (Belkin ones) but I would much rather set everything up using cable because my Belkin antennas do tend to fail. FAP_BOOK is currently running on Ubuntu 12.04.

Second laptop (I've named it OLDER_BOOK) is a bit older and it struggled to run the newest Unity, I believe it was too graphically demending. However windows XP runs fine on it. Windows XP is currently running on Windows XP

Also, I have a single external USB HD (320GB).

Here's what I hope to archive:
1. To set up SSH protocol (remote desktop) between the two of my laptops.
2. To allow data sharing between my laptops.
3. Try some data recovery (I am really eager to try that)
4. Set up a schedule for back-ups.
5. Maybe set up RAID if i manage to get my hands on another HD

Of course, I would love to do all that using the terminal like a boss! 

Here's what I need help with:
-Picking the right software.
-Where to begin and how!
-Using the correct commands.
-Perhaps giving me more fun ideas?
-Setting everything up.
-Point me towards the right direction should my knowledge and understanding of certain issues prove to not be enough.

I have never attempted to at anything quite like this. I do have the basic understanding of how a network works or how to operate the terminal. Actually, I am doing this to LEARN! My priority isn't to make a mega functional network, but  one that would have worked if i had the proper equipment and to LEARN as much as possible. 

I do hope that I've made clear what I hope to achieve. If by any chance I've omitted something crucial please do tell me and I'll do what has to be done. 

P.S. If you feel that you need to email me here is my adress: 
[email]feldon0606@gmail.com[/email]

---

### Post by 2F4U on 2012-09-02
SSH access requires a SSH server. This is easy in Ubuntu, but I don't know a SSH server for Windows. A good SSH client for Windows would be PuTTY, in Ubuntu this would already be included.

[http://www.unixtutorial.org/2009/05/ubuntu-ssh-how-to-enable-secure-shell-in-ubuntu/](http://www.unixtutorial.org/2009/05/ubuntu-ssh-how-to-enable-secure-shell-in-ubuntu/)

File sharing between Windows and Ubuntu would probably be easiest by using Samba. Again, a Samba server needs to be running and I only know how to do this in Ubuntu:

[http://www.unixmen.com/howto-install-and-configure-samba-share-in-ubuntu/](http://www.unixmen.com/howto-install-and-configure-samba-share-in-ubuntu/)
[http://www.abclinux.com.pl/linux-samba-en/](http://www.abclinux.com.pl/linux-samba-en/)

---

### Post by feldon0606 on 2012-09-03
Thanks for your reply 2F4U!

You see, I am thinking of installing ubuntu 10.04 on the older laptop.
Would SSH work with no problems between two different versions of ubuntu? I did find a guide how to set up SSH in "Linux Format" and it does look quite easy. 

Okay, I will have a go at setting up that Samba server thing after I install Ubuntu 10.04 on my older laptop.

By the way, could you suggest any good data recovery software please?
Thank you for your help!
(Your third link appears to be broken.)

---

### Post by 2F4U on 2012-09-03
SSH works between different versions, as long as they support the same protocol. It also works between different distributions, or between Windows, Linux, Mac OSX, etc.
Setting up SSH is indeed quite easy, even if you intend to use public/private key instead of password.

Yeah, the third link is now indeed broken. Found a replacement, a kind of meta documenation from the Ubuntu Wiki that links to several more detailed articles.

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

I usually do backups to my server through Samba. On my clients, the Samba shares are mounted and look like they are folders in the local filesystem. I found an application named Unison, which is able to sync two folders (including subfolders). So I have my data stored locally and replicated to the server and make sure that it is always in sync. This, by the way, can be done with more than two computers.

---

