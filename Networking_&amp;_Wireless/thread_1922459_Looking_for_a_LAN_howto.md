---
title: "Looking for a LAN howto"
date: 2012-02-08
forum: Networking &amp; Wireless
---

### Post by Baasha on 2012-02-08
Hi,
I am running running Ubuntu 11.10.

I have been looking in vain for a LAN howto.  I have two computers (both Ubuntu) connected to a router and I want to share files between them.  Can anyone point me to a simple, complete howto?  There are lots of documentation and forum posts on this subject but they are all either out-dated or incomplete.  There is also lots of conflicting advice, so after hours and hours trying to figure this out I am hopelessly confused..

Here is what I am trying to accomplish:
1. Connect 2 Ubuntu machines so each is visible to the other.
2. Share files back and forth between them.

---

### Post by SteveDee on 2012-02-10
> **Baasha said:**
> ...Here is what I am trying to accomplish:
1. Connect 2 Ubuntu machines so each is visible to the other.
2. Share files back and forth between them.

The simplest/cheapest way to connect 2 computers together is with a network cross-over cable.
You can also connect them via a network switch or router using standard network cables.

The procedure that follows assumes the 2 computers are not part of a wider network, there is no server and no DHCP service.

On computer #1 edit your wired network connection IPv4 Settings:-
Method: Manual
Address: 200.0.0.1
Netmask: 255.255.255.0

Do the same on computer #2 but set Address: 200.0.0.2

Open file manager on computer #1 and enter: smb://200.0.0.2/

If you have any shared folders set up on computer #2 you should see them listed.

If you don't have any folder shares, you need to find out how to do this on Ubuntu, which I seem to remember involves right-clicking a folder and selecting Share. I think this initiates downloading the Samba service.

For Lubuntu you can follow this: [http://ubuntuforums.org/showthread.php?t=1623346&highlight=samba](http://ubuntuforums.org/showthread.php?t=1623346&highlight=samba)

If your file manager has a Network button, you can probably use this instead of typing: smb://200.0.0.2/
This will also list the workgroups that the computers belong to. Contrary to popular belief, your computers don't have to be in the same workgroup.

I hope this helps.

---

### Post by ianp5a on 2012-02-12
A How To is missing in the [Official Ubuntu documentation.]("https://help.ubuntu.com/11.10/ubuntu-help/net.html") Networking is a tricky for beginners so networking basics is really needed.

What I did was to first share a folder. Right click on it and click on Sharing Options. Then enable the sharing. After that that folder should be visible from the other computer in Nautilus.

Edit: I found this when searching. [Share files and Folder with another computer]("https://help.ubuntu.com/8.04/internet/C/networking-shares.html") But by navigating it was well hidden.

---

### Post by Baasha on 2012-02-12
Thx Ian,
You are right about the documentation.  Everyone seems to have a different way of setting this up and the advice is often conflicting.  Even in the official docs (like the link you posted) one can never be sure if it is trustworthy when it says it is for a particular version of Ubuntu that is now obsolete.

In the end I ended up installing Samba which probably has way more overhead for what I need.

Now I have to figure out how to set up WOL so I don't have to go to the other end of the house to turn on the computer :-(

---

### Post by ianp5a on 2012-02-13
> **Baasha said:**
> Thx Ian,
 one can never be sure if it is trustworthy 
It's important that users are confident in the methods. So a clear and updated LAN basics is needed.

---

