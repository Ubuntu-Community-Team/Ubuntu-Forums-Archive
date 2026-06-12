---
title: "Sharing a volume"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by mistergoomba on 2008-12-02
I just installed a new hard drive and I'm trying to share it on my network. I went to properties and clicked the checkbox and I was asked to install Samba. So far, so good. After all was said and done, it looked like the folder was ready to be shared (it had the emblem, no errors). However, I could not find the directory on my laptop (Mac). When I'm at work, a whole list of shared computers appears in my finder, but after setting this volume to be shared, I see nothing.

Any help would be greatly appreciated! Thanks

---

### Post by superprash2003 on 2008-12-03
you need to setup samba correctly , adding a samba user etc . This guide should help you get started [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by mistergoomba on 2008-12-03
set up samba correctly... that makes sense! hehe :}

thanks a lot for the guide

---

### Post by mistergoomba on 2008-12-06
sorry, i may have closed this one out prematurely. i followed the instructions and when i got the the 'graphical way' vs the 'command line way' i chose graphical way. right clicking on the folder does not bring up 'share folder', rather 'sharing options'. it didn't give me the option to choose which network to share through, so i went ahead an tried the command line way

nothing has worked so far. i tried connecting my macos to smb://{the ip of my ubuntu machine} and after a few moments, i was told it couldnt connect.

---

### Post by Kellemora on 2008-12-06
Hi MG

Also install smbclient and smbtree.
IF smbfs is installed, uncheck it so it uninstalls.

In smb.conf you want to change the name workgroup = workgroup to workgroup = nameofyourworkgroup (whatever that name is of course).

smb.conf is located in /etc/samba/smb.conf

In terminal you can type smbtree to see if your computer is listed, if so, then your network is up and running.
That don't mean you will see the share under Places/Network though, as there is a BUG in the program that displays shares now for over 2 years with no resolution to same in sight.

IF you can see your shares using smbtree, then you can mount them by going to Places/Network and clicking on the GO button and selecting LOCATION, in the bar type smb://IP of the machine you are trying to reach.  This should bring up all the shared folders on that machine in the window.  Selecting one of them will mount it.  Unless it's a sub-folder in an already mountable folder above it.  In this case, mount the folder above it and the file folder will then be mounted and usable.

As an aside, you may have to reboot your computer THREE times in succession to get the shares to show up in Places/Network, but that's no guarantee they will.

The folder Samba READS during boot up is /var/lib/samba which is a binary file, uneditable by us humanoids.  I think the smb.conf overwrites this file on the 3rd boot-up if done in quick succession.  Only because of HOW our 6 Ubuntu machines here behave!

Good Luck

TTUL
Gary

---

### Post by Mark Roberts on 2008-12-12
Does this also apply to sharing betweeen Ubuntu machines? I have 1 windows and two ubuntu machines on my network.

I don't have a problem from either ubuntu machine accessing the Windows computer, but I cannot access one ubuntu machine from the other.

---

### Post by superprash2003 on 2008-12-12
are both the machines able to ping each other?? in the ubuntu containing the samba shares post output of smbtree

---

