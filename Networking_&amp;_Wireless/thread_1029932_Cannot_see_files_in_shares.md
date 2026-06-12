---
title: "Cannot see files in shares"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by K3JAE on 2009-01-03
Dist: ubuntu 8.10

I am about as clueless on Linux as a new baby so please be gentle and thorough with answers. Been only using Linux less than a week. I have made progress but am still trying to learn. 

When opening the file browser I see my Windows based shares (computers). when I click on any of the computers, nothing shared shows.

There is 2 Vista machines and a XP machine. There are a total of 4 computers showing on the Network page, of which one is the Linux box. The Linux box shows the shares.

I can see on the XP machine the (Samba, Ubuntu) but nothing else.
On the Vista machines I see the Linux share box and can access the shared  folders (which at this time is only the Document folder and the printer). 

Question basically is why cannot I access the shared items on the XP box even though all shares are enabled and folders are enabled.  Vista/XP shares work fine.
I am clueless how to get into the shares on the windows based system.

---

### Post by jonandrews on 2009-01-04
I think you may have two problems running here.  

To set up Ubuntu so that it is fully accessible to your windows pc's, have a look at my step-by-step guide:
[www.europe.eclipse.co.uk/Ubuntu](www.europe.eclipse.co.uk/Ubuntu)

Now, straight 'out of the box' a Ubuntu pc should be able to access shares on a pre-existing Windows network. So, assuming your basic Ubuntu installation was error-free, and the Ubuntu pc connects to the internet ok, then first suspect has to be firewall settings on the windows pc's. Just turn them off to see.....

---

### Post by K3JAE on 2009-01-04
I followed your instructions on your site you refer to and as suspected, did not need to DL Samba as already have that installed. I have no problem seeing and accessing the Linux box from the PC, and was not required to login via username and password. ~shrugs~

The installation was an upgrade from 8.04 to 8.10 and was error free to my knowledge... ie nothing apparently went wrong.

Yet, I am still unable to access shares from the Linux box to the PC. Internet connection etc. is fine and Firewall has been disabled on the router for almost a week now so this was never an issue.  Windows Firewall also disabled.

I am able to apparently get onto the PC computer but see no shares once on it. Additionally I attempted to move a file from the PC to the Linux box and was initially denied but then files moved fine and transfer was complete.

---

### Post by bsh on 2009-01-04
depending on how you configured samba, shares can be acceseb by everyone or only given users. you might need to make samba users in some cases. be default, some windows pc's try to acces shares as guest, and maybe you try to acces windows shares from ubuntu as guest too, but the guest account is disabled on most windows installs.
not seeing computers on the network is most likely a dns issue. some windows pcs may attemt to become the network browser but not sahring the browse list with ubuntu, since it may not be set up to use a dns proxy, or to be a network browser itself...
all in all, it is not taht easy to set it up properly.
please post your /etc/samba/smb.conf
and read the samba manual too :)

---

### Post by Iowan on 2009-01-04
See if this helps:
> **superprash2003 said:**
> try typing smb://x.x.x.x where x.x.x.x is the ip of the windows machine.. it hopefully should open the shared folders.. [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

