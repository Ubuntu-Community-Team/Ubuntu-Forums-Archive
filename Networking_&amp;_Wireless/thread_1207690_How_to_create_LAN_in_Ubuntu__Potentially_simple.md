---
title: "How to create LAN in Ubuntu?  Potentially simple?"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by the_pod on 2009-07-08
Hi. I've tried to search for an answer for a good while but can't seem to find anything that seems as simple as I believe it should be so I figured I'd ask on the forums.

***Goal***:  Be able to have two Ubuntu machines see each other on a LAN.

***Setup***:  One computer, wired, running Ubuntu 64 9.4 (NetworkManager).  Second computer, wireless, Mythbuntu 32 9.4 (Wicd).  

***Connectivity already:***  Both computers can access the internet (using same router).  Both computers can access a 3rd computer's XP Network and associated shared files.

***Problem / What I'm Trying to do: * **I want the 2 Ubuntu machines to be able to see each other.  The eventual goal is to have my personal machine be able to do a "share desktop" on the Mythtv machine which is tucked away behind the tv and difficult to configure / troubleshoot.  

With a background in MSFT, I found it easy to setup a local network in XP using Network Neighborhood. However, I don't have any idea how to do this in Ubuntu (or if its even a similar process).  I imagine it can't be horribly difficult since I can access a MSFT lan right now.

Am currently reading through [https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking) thinking there may be something that helps.  

If someone has a simple solution or walk-through, or can even point me in the right direction I'd appreciate it.  I'm trying to avoid 4-8 hours of incorrect tinkering which is what usually happens when I try to anything remotely out of the box with Ubuntu.

Thanks for any help.

---

### Post by x22 on 2009-07-08
> to see each other

if you mean, login to the one A ip a.b.c.d from the
other B ip a.b.c.e then "ssh" is the thing:

from A: "ssh a.b.c.e"
from B: "ssh a.b.c.d"

or you can put nicknames in /etc/hosts like this

a.b.c.d   A
a.b.c.e   B

then "ssh A" does it (from B)

---

### Post by SteveDee on 2009-07-08
> **the_pod said:**
> Hi. I've tried to search for an answer for a good while but can't seem to find anything that seems as simple as I believe it should be so I figured I'd ask on the forums.

***Goal***:  Be able to have two Ubuntu machines see each other on a LAN.

***Setup***:  One computer, wired, running Ubuntu 64 9.4 (NetworkManager).  Second computer, wireless, Mythbuntu 32 9.4 (Wicd).  

***Connectivity already:***  Both computers can access the internet (using same router).  Both computers can access a 3rd computer's XP Network and associated shared files.

***Problem / What I'm Trying to do: * **I want the 2 Ubuntu machines to be able to see each other.  The eventual goal is to have my personal machine be able to do a "share desktop" on the Mythtv machine which is tucked away behind the tv and difficult to configure / troubleshoot.  

With a background in MSFT, I found it easy to setup a local network in XP using Network Neighborhood. However, I don't have any idea how to do this in Ubuntu (or if its even a similar process).  I imagine it can't be horribly difficult since I can access a MSFT lan right now.

Am currently reading through [https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking) thinking there may be something that helps.  

If someone has a simple solution or walk-through, or can even point me in the right direction I'd appreciate it.  I'm trying to avoid 4-8 hours of incorrect tinkering which is what usually happens when I try to anything remotely out of the box with Ubuntu.

Thanks for any help.

It should be simple. When you create a shared folder on each of your 2 computers for the first time (e.g. in Nautilus right click a folder and select "Sharing Options...") you are prompted to download some doo-hickey to allow network sharing. You then reboot and repeat the sharing operation, so now you have a shared folder.

Go Places > Network > Windows Network and you should now see 1 or more workgroups, although this can sometimes take several minutes (on my WiFi) and/or several attempts straight after the computers have been booted (a bit like Windows with a simple network config). Obviously clicking on a workgroup should now show a computer.

To change workgroup name, go Applications > System Tools > Configuration Editor > System > smb > workgroup.

I hope this helps.

---

### Post by the_pod on 2009-07-08
Thanks. I'll give it a try when I get home.  I knew that the crazy maze of command line instructions that I'd been perusing had to be overkill.

---

### Post by SteveDee on 2009-07-08
> **the_pod said:**
> Thanks. I'll give it a try when I get home.  I knew that the crazy maze of command line instructions that I'd been perusing had to be overkill.

I was just trying to get the Configuration Editor to change my workgroup. I'm sure I've used it successfully in the past (maybe on Hardy or Intrepid) but its sure not working for me on Jaunty.

So please edit smb.conf if you need to change the workgroup name, example:-
sudo gedit /etc/samba/smb.conf
enter your password, press enter.
find the line "workgroup" (e.g. workgroup=workgroup)
and change (e.g. workgroup=ubuntu).

---

### Post by swerdna on 2009-07-08
If you have any further trouble, this might be worth a read, but the CLI is in it fairly heavily: 
[Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

### Post by SteveDee on 2009-07-09
> **swerdna said:**
> If you have any further trouble, this might be worth a read, but the CLI is in it fairly heavily: 
[Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

I just want to thank you for the clear documentation that you have carefully prepared and presented at: [http://ubuntu.swerdna.org/index.html](http://ubuntu.swerdna.org/index.html)

You have a very "easy to read" style, and this has allowed me to print across my network for the first time! I look forward to more.

---

### Post by swerdna on 2009-07-09
> **SteveDee said:**
> I just want to thank you for the clear documentation that you have carefully prepared and presented at: [http://ubuntu.swerdna.org/index.html](http://ubuntu.swerdna.org/index.html)

You have a very "easy to read" style, and this has allowed me to print across my network for the first time! I look forward to more.

Thanks for the compliment. I do plan more articles as I wend my way through Ubuntu -- a very appealing distro.

---

