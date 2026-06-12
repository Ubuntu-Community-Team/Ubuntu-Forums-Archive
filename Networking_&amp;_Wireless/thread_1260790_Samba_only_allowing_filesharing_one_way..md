---
title: "Samba only allowing filesharing one way."
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by ufbournutmus on 2009-09-08
Hi. 

I'm having a samba problem.

 I can access files on my Windows system from my Ubuntu system, but when I try to access a share on the Ubuntu system from the windows system, I get the error, "Windows cannot access \\<system name>\<share name>". When I click diagnose I get, "Error code 0x70080043  The network name cannot be found." And when I try to access a share in that same Ubuntu system from an Ubuntu Virtual Box within the same Windows system, I get the error, "Unable to mount location.  Failed to mount Windows share".

Ive tried accessing the share by typing in the \\<IP address>\<share name>, but that also didn't work.

I can ping the systems both ways. It takes less than 1ms.

I have permissions set to guest access both ways.

Any help would be appreciated!

---

### Post by Iowan on 2009-09-08
Have you installed the server (called **samba** in Synaptic) on the Ubuntu machine. The client comes pre-installed.

---

### Post by ufbournutmus on 2009-09-08
The package **samba** was already installed.

---

### Post by ductiletoaster on 2009-09-08
i believe Samba-common is installed but its been a while but i believe u need to install another package to allow access to ubuntu machine. Iowan said it.... the client is pre installed. so u still need to install the server side or u wont get access. 

Now if i remb right Ubuntu 9.04 has a neat feature that allows u to easily shares folders. So lets say i want to share /home/username/public then i would right click on public aand go to its properties. There should some where be an option to share this folder like a check mark. click it and hit ok if u dont have the correct packages then Ubuntu should tell you and ask you if u want to install them. restart both machine and then try agian. Post back here if any questions or if its works.

---

### Post by ufbournutmus on 2009-09-08
> **ductiletoaster said:**
> i believe Samba-common is installed but its been a while but i believe u need to install another package to allow access to ubuntu machine. Iowan said it.... the client is pre installed. so u still need to install the server side or u wont get access. 

Now if i remb right Ubuntu 9.04 has a neat feature that allows u to easily shares folders. So lets say i want to share /home/username/public then i would right click on public aand go to its properties. There should some where be an option to share this folder like a check mark. click it and hit ok if u dont have the correct packages then Ubuntu should tell you and ask you if u want to install them. restart both machine and then try agian. Post back here if any questions or if its works.

I think that's called permissions granting. I forgot to mention that my permissions on every share disappear when I log out, i.e., it no longer is a share, it's just a regular folder.

---

### Post by ductiletoaster on 2009-09-08
Yeah thats right....hmmm so ok u do that and then upon login all permissions are gone. Have you checked what packages u have installed for samba.... 
From memory i know client stuff is pre-installed 

and i know besides any dependancies u need
samba-common
samba-client (for obvious reasons)
and  
samba

so go to synaptic package manager nad see what u have.

because i believe even if the samba package in installed it still needs the samba common to work properly

---

### Post by ufbournutmus on 2009-09-08
I already had all of those installed besides samba-common but that package doesn't exist in synaptic so I installed the most similar thing I could find "smbcommon". Same error when I try to access a share.

---

### Post by ductiletoaster on 2009-09-08
it should be called samba common let me check and ill post back

ok thats strange u dont have samba-common... what version of Ubuntu are u using and also go to terminal and type 
```
sudo apt-get install samba-common
```

if that installs restart computers and then try agian

---

### Post by theozzlives on 2009-09-08
```
sudo apt-get install samba
```
```
sudo smbpasswd -a <your username>
```

---

### Post by ufbournutmus on 2009-09-08
I followed both of your instructions, but no new packages were installed or upgraded. However, I didn't enter the last command because I wasn't sure what it was for or what it did.

Thanks though.

---

### Post by ductiletoaster on 2009-09-08
well the second cmd is actually nec.... see with two windows machines they usaully dont need any authetication but if they are setup they usually use the username and password of the a particular user.  on samba this is similiar but you need to specify the authetication info. Or you will never be able to connect from the windows side.

so type:
```
sudo smbpasswd -a <your username>
```

and replace <your username> with the user you are logined in as. and then you will be prompted to type a password for the samba user and then once more to confirm

---

### Post by ufbournutmus on 2009-09-08
Type in the username of the Ubuntu system or the username of the Windows system?

---

### Post by ductiletoaster on 2009-09-08
Type in the user name of the Ubuntu machine. The user u are logged into.

once samba has made a user i would suggest restarting both computers. And then trying to access your file shares

---

### Post by ufbournutmus on 2009-09-08
Same error.

---

### Post by ductiletoaster on 2009-09-09
Can you post your network properties... what systems are u running on each PC. Can u do any other things over the lan FTP ssh....?

---

### Post by ufbournutmus on 2009-09-09
> **ductiletoaster said:**
> Can you post your network properties... what systems are u running on each PC. Can u do any other things over the lan FTP ssh....?

Sorry, I dont know what any of that means.

---

### Post by ufbournutmus on 2009-09-09
Bump.

---

### Post by Iowan on 2009-09-10
Hopefully not too far off-topic:
From a terminal, check ```
ps -ef |grep mbd
``` There should be a couple of lines containing "smbd" or "nmbd". If not, Samba (server) isn't running.

---

