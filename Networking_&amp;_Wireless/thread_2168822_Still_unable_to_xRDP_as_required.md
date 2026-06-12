---
title: "Still unable to xRDP as required"
date: 2013-08-19
forum: Networking &amp; Wireless
---

### Post by MACE1 on 2013-08-19
Having the luxuary of a spare 1U retired rack server to play with I decided to wipe and install KUbuntu 12.04 with a view of introducing people to Kubuntu in this otherwise Windows 7 64 network.
As it is not at all critical and considering everyone would access it by RDP I edited all the polkit-1 policies to give remote equal rights to local.
I edited sesman.ini to point to a new RDPuser group for the default console user and the chosen network user, which currently have identical group access.
I used scarygliders utilities 3 to build x11rdp and the session config desktop tool for KDE.

After all this, ONLY the default console user validates and can log in, the new network user will not validate so can't log in !
If I log in over xRDP as the console user, none of the expected relaxed policies have worked as still cant edit network, install updates etc. 
(The confirm permission with a password dialogues are not displayed so can't elevate any privelidges!)

Thus fare I am at a loss regarding what else I should do to make xRDP useable.

There is not going to be a VNC client distribution so it wil have to be RDP and needs to be simple to get any interest from our windows users.

1. Could anyone suggest what is preventing one user from validating when the other can, particularly when both appear to have identical group membership ?
2. What else is missing in the main policies that would prevent all users from managing the system as they would at the console.

I confess to having wasted an inordinate amount of time on this so without further input it is not going to go any further.

M

---

### Post by lukeiamyourfather on 2013-08-19
It sounds like you're trying to give every user root privileges on a server and open it up to other users through RDP. That's just a bad idea in every possible way. Typically servers are managed from a local terminal or through ssh and users who need root privileges can be added to sudoers (for everything or just specific commands).

---

### Post by steeldriver on 2013-08-19
Yes I couldn't understand why you needed to edit the polkit-1 policies either

I have Kubuntu 12.04 in a VM with the standard (non-scarygliders) xrdp server running, and as my regular primary user I am able to login from the Win7 host and run sudo commands just like in a regular session. I was then able to add a new standard user (with *sudo adduser newuser* - again from within the xrdp session) and subsequently start a second xrdp session as that user. No modification of privileges or groups required. Or am I completely misunderstanding your requirements?

---

### Post by MACE1 on 2013-08-20
The need to setup remote access with useable full RDP control lead from minimal intervention to full scale polkit edit to try to bypass the two issues listed.
I simply want the level of control via xRDP I would have if sat in front of a standard PC as working at the console is not practical or desireable.

Not many regular users of a gui like KDE want to drop to the command line to sudo anything.

If I cant even get the chosen user to log in to the xRDP session then what hope a novice user !!
The post clearly explained, this is a redundant server being re-tasked as a rack workstation !

I have created a user intended for xRDP access and currently it has the same group access as the user used on the console.
sesman.ini is pointing at the RDPuser group created for this purpose. Both of these users are currently set as RDPuser members.

Without the ability to log in on xRDP no one is going to get access...
Without the ability to see elevated privelages prompts, the machine is not going to be useable regardless of any other settings.

There is very little of anything needs locking down on this network whether windows or Linux so largely no issues how ultimately we get this working. It is a PC which is to be remotely run !

I NEED ideas as to what mechanisms are stopping access as described.

---

### Post by MACE1 on 2013-08-23
No further on so I 'bit the bullet' flattened the machine and re-installed to defaults.
I've created just one user which I can successfully use via simple xRDP, probably as it will be in admin group.

This said, an xRDP session immediatley causes App crashes: e.g.

/usr/share/kde4/apps/printer-applet/...  using python2.7

I think I will re-apply scarygliders tools and avoid using vino directly and see if it gains any more stability.

With the polkit-1 adjustments not appearing to help, even if I add per user overrides it looks like many apps and services are still not suited to this VNC method.

Quite sadening that as much as I try to champion ubuntu in this windows centric world, such as this which are taken for granted by windows users and which are so fundamental to daily life only serve to make windows uses  dismiss linux out of hand. #-o

---

### Post by steeldriver on 2013-08-23
IMHO you'd get a far better end-user experience by using a VNC-based solution - Xvnc is a well established remote desktop protocol from the *nix side and there are plenty of good Windows client viewers for it (TightVNC, UltraVNC, RealVNC). Fundamentally RDP is a Microsoft protocol.

---

### Post by lukeiamyourfather on 2013-08-26
> **MACE1 said:**
> 
Quite sadening that as much as I try to champion ubuntu in this windows centric world, such as this which are taken for granted by windows users and which are so fundamental to daily life only serve to make windows uses  dismiss linux out of hand.

Linux is not Windows nor does it try to be. If you want Remote Desktop Sessions (Terminal Services) then get Windows Server. A long-time Linux user could just as easily rag on Windows for all the stupid crap it does (or doesn't do) but that's not the point. Use whatever is best for the situation.

---

