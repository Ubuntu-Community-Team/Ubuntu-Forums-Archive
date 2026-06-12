---
title: "ubuntu 11.04 beta - problem with decrypt the home folder (without passphrase)"
date: 2011-01-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by stuppaz on 2011-01-08
I install the new version, during the installation steps I checked "yes" to encrypt the home folder.
When I logged in for the first time I didn't set the passphrase when it was asked. After that I moved inside the home folder some important files.

For same problems I had to install again the os (always 11.04) but I changed the user account.
Now, if I try to get the data from the first home folder I can see only two folder  encrypted.
In the following the contents inside the first home folder (about the first account):

-Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
- .ecryptfs -> /home/.ecryptfs/francy-anto/.ecryptfs/
- .Private -> /home/.ecryptfs/francy-anto/.Private/
- README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt

how can I recovery the data from the first home folder without the passphrase (I don't know it).

I hope I was clearly.:(
can you help me ?

---

### Post by stuppaz on 2011-01-14
nobody can help me ?

---

### Post by mbugno on 2011-03-25
This also happened to me. Can some one please answer. I have googled this and don't understand. I choose not to encrypt yet it did it anyway. I have the pass phrase, ran it and it states success but there is no folder from 10.10. See below.... Is this the correct method?


[sudo] password for matthew: 
root@Steathraptor:/home/matthew# '/usr/bin/ecryptfs-recover-private' 
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/home/.ecryptfs/raptor/.Private].
Try to recover this directory? [Y/n]: Y
INFO: Enter your LOGIN passphrase...
Passphrase: 
Inserted auth tok with sig [534779d60b4d6540] into the user session keyring
INFO: Success!  Private data mounted read-only at [/tmp/ecryptfs.zYaIRb3e].
INFO: Found [/home/.ecryptfs/matthew/.Private].
Try to recover this directory? [Y/n]: y
INFO: Enter your LOGIN passphrase...
Passphrase: 
Inserted auth tok with sig [3dcc921df37e8943] into the user session keyring
INFO: Success!  Private data mounted read-only at [/tmp/ecryptfs.HUBkBCLo].
root@Steathraptor:/home/matthew# 
:confused:

---

### Post by madmax75 on 2011-03-26
Why rush?

The stable version of 11.04 is still a month away. I would stick to 10.04 or 10.10 at least for a couple weeks *after* they release the stable version.

To my understanding, even the beta version is still a couple days off. Wasn't the beta scheduled for March 31st?

---

### Post by Hakunka-Matata on 2011-03-28
> **stuppaz said:**
> I install the new version, during the installation steps I checked "yes" to encrypt the home folder.
When I logged in for the first time I didn't set the passphrase when it was asked. After that I moved inside the home folder some important files.

For same problems I had to install again the os (always 11.04) but I changed the user account.
Now, if I try to get the data from the first home folder I can see only two folder  encrypted.
In the following the contents inside the first home folder (about the first account):

-Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
- .ecryptfs -> /home/.ecryptfs/francy-anto/.ecryptfs/
- .Private -> /home/.ecryptfs/francy-anto/.Private/
- README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt

how can I recovery the data from the first home folder without the passphrase (I don't know it).

I hope I was clearly.:(
can you help me ?

The problem exists when the user selects "Login Automatically" and then uses the encrypted file system.
The encrypted file system requires the use of password authentication, so if you have set the system to "Login Automatically",,,,------  Upon first using encryption, the "Login Automatically" option is changed back to default, "Use Password" to logon.
Solution:  Change your logon method to "Use Password"

---

### Post by Dutch70 on 2011-03-28
> **stuppaz said:**
> nobody can help me ?

When you install a development release you are the one helping, by reporting bugs and such. Not asking for help with a system that's still in development stages. Most of us that install development releases, either use a virtual machine, usb stick, or have a separate partition on our hdd & still use a stable version of Ubuntu that we know we can depend on.

---

### Post by Sean Moran on 2011-03-28
Just out of interest, has the beta been uploaded already? I was expecting to wait until the EoM for the first beta.  Has it come early?

---

### Post by howefield on 2011-03-28
Thread moved to "*Natty Narwhal Testing and Discussion*"

---

### Post by cariboo on 2011-03-28
Just as a point of interest, if you choose to encrypt the home partition, then use auto-login, you are defeating the purpose of having an encrypted home partition. The encrypted partition is to prevent others from access files in the home partition when you are logged out of your computer. With auto-login, any one can access the home partition, by just starting up the computer.

---

