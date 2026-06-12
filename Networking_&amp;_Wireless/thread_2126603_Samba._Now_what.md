---
title: "Samba. Now what?"
date: 2013-03-17
forum: Networking &amp; Wireless
---

### Post by BXRBuddha on 2013-03-17
Hello,

So installed Samba on my lubuntu comp, but I'm not sure where it on my disk. I tried installing it again, but I got. 

```
 E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```
How can I locate the related files for samba?

Thanks

---

### Post by kc1di on 2013-03-17
Hi BXRBuddha  and welcome to ubuntu,

The message you got says that something went wrong with the install you need to go to a terminal and run the dpkg command given to finish the install. the command should look like this > sudo dpkg --configure -a
then you should find samba on your machine.

---

### Post by BXRBuddha on 2013-03-17
Hi kc1di

So I ran the code, and I get

```
Processing triggers for man-db ...Setting up fonts-horai-umefont (442-1) ...
Processing triggers for fontconfig ...
Setting up libunistring0:i386 (0.9.3-5build1) ...
Setting up libgettextpo0:i386 (0.18.1.1-9ubuntu1) ...
Setting up imagemagick-common (8:6.7.7.10-2ubuntu4) ...
Setting up winbind (2:3.6.6-3ubuntu5) ...
winbind start/running, process 2443
Setting up libodbc1:i386 (2.2.14p2-5ubuntu4) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libnss-winbind:i386 (2:3.6.6-3ubuntu5) ...
Setting up cabextract (1.4-3) ...
Setting up libilmbase6 (1.0.1-4) ...
Setting up liblqr-1-0:i386 (0.4.1-2) ...
Setting up liblcms1:i386 (1.19.dfsg-1.1ubuntu2) ...
Setting up libpam-winbind:i386 (2:3.6.6-3ubuntu5) ...
Setting up libmagickcore5:i386 (8:6.7.7.10-2ubuntu4) ...
Setting up libmagickwand5:i386 (8:6.7.7.10-2ubuntu4) ...
Setting up libopenexr6 (1.6.1-6) ...
Setting up libmagickcore5-extra:i386 (8:6.7.7.10-2ubuntu4) ...
Setting up odbcinst (2.2.14p2-5ubuntu4) ...
Setting up odbcinst1debian2:i386 (2.2.14p2-5ubuntu4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

Could you explain?

Thanks for your response.

---

### Post by lykwydchykyn on 2013-03-17
dpkg is the program that actually installs packages after APT or software-center downloads them.  You apparently started an upgrade or installation, and then killed the package manager process before dpkg could finish installing everything.

When you ran the dpkg command again, it picked up where it left off and finished the installation.  That's what the terminal output was.

As for Samba, what exactly are you wanting to do?  If you install the samba service, it just runs automatically.

---

### Post by BXRBuddha on 2013-03-18
What I want to do is connect to other computers running windows xp in the same work group. However I've been having trouble getting the workgroup to acknowledge this lubuntu computer and vice versa. Do I need to install samba on the window's computers?

Thanks for the reply lykwydchykyn.

---

### Post by lykwydchykyn on 2013-03-18
Samba is an implementation of Microsoft's network protocols; these same protocols are already installed on the Windows computers, so no, you don't install samba on the windows computers.

First, see if you can see the network on the Lubuntu machine.  Open your file browser (pcmanfm) and put "smb:/" in the navigation bar.  See if any workgroups or machines come up.

If that fails, the most likely things to rule out would be: 

- A firewall on one or both systems that could be blocking Samba
- Name resolution between the computers

---

