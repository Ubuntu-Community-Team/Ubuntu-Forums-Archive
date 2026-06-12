---
title: "samba mount permissions / ownership"
date: 2012-09-15
forum: Networking &amp; Wireless
---

### Post by Statia on 2012-09-15
Hi,

I mount a samba share at boot with this in fstab:

```
//fritz.box/WD-10EADSExternal-01 /mnt/samba  cifs  guest,_netdev  0 0
```It works, I can read from the disk, I can write to the disk, but every write ends with "can't change permissions on foo.bar". Turns out all the files are owned by root, and of course I am working as user.
I know I could add my UID and GID to fstab, but there are more users on this machine.
I don't know if it is possible to add multiple UID's to fstab?
I tried adding "user" to fstab, but that did not work, IIRC, that only means every user can mount and unmount the share.
Is there an other solution?
I could make a script in rc.local for every user that mounts the drive with their UID and GID, but I think there should be an easier option.

---

### Post by Statia on 2012-09-15
Tried so far:

```
# chmod 766 /mnt/samba/
```
(with drive unmounted)

Added "noperm" as an option in fstab

Added gid=121 to fstab, no UID.
 
(In /etc/group: sambashare:x:121:statia,user2)

---

### Post by Statia on 2012-09-16
Time for the I'm-in-the-wrong-timezone BUMP.

---

### Post by Statia on 2012-09-18
Try this timezone BUMP?

---

### Post by luvshines on 2012-09-19
The 'noperm' which you added might not be sufficient. The man page itself says
```
Note that this does not affect the normal ACL check on the target
machine done by the server software (of the server ACL against the
user name provided at mount time).
```
I am not sure if this will work but you may try the 'force user' option on the Samba server for that share
This should switch whatever user connects to switch to the permission of the 'force user' and might do the trickTHe

---

### Post by Statia on 2012-09-19
> **luvshines said:**
> I am not sure if this will work but you may try the 'force user' option on the Samba server for that share
This should switch whatever user connects to switch to the permission of the 'force user' and might do the trick

I can't really change things on the server side. I forgot to mention in this post (it is mentioned in my other post in this subforum, which could use some input, hint, hint, nudge nudge wink wink), the server is a Fritz!Box 7360 wireless router.
It runs something called FritzOS, which may or may not be Linux (-derived), but I don't have shell access on this box, and very limited options for configuration of its NAS functions.

---

### Post by LewisTM on 2012-09-19
What happens if you open up the share in Nautilus?
For instance enter this address (Ctrl-L)
> smb://fritz.box/WD-10EADSExternal-01
Can you read/write using some user credentials (as should be supplied with you NAS) or guest?
If so, it would be possible to automate the mounting of shares at the user level using a variation of this technique with an app called Gigolo. No need for fstab entries.

Cheers!

---

### Post by Statia on 2012-09-19
> **LewisTM said:**
> What happens if you open up the share in Nautilus?
For instance enter this address (Ctrl-L)

Can you read/write using some user credentials (as should be supplied with you NAS) or guest?
If so, it would be possible to automate the mounting of shares at the user level using a variation of this technique with an app called Gigolo. No need for fstab entries.


Nope, doesn't work:

```
Could not display "smb://fritz.box/wd-10eadsexternal-01%20/".
Error: Failed to mount Windows share
Please select another viewer and try again.
```

---

### Post by LewisTM on 2012-09-19
You have a trailing space there (%20). Make sure the address has not space at the end. You can end it with a slash to make sure.
smb://fritz.box/WD-10EADSExternal-01/

---

### Post by Statia on 2012-09-19
> **LewisTM said:**
> You have a trailing space there (%20). Make sure the address has not space at the end. You can end it with a slash to make sure.
smb://fritz.box/WD-10EADSExternal-01/

Yep, that gets me there. But if I use nautilus to copy a regular file from my ~, it still ends up on the share with ownership by root.

---

### Post by LewisTM on 2012-09-19
Okay. It's probably the way the NAS is setup. It may force root ownership on the server side but will grant full access to all.
Do you get any error? Does it keep you from working? Can you unmount it properly? 

Here's a mini [HowTo]("http://ubuntuforums.org/showpost.php?p=9941016&postcount=3") from Morbius on how to take full advantage of Gigolo for automounting SMB shares.

---

### Post by Statia on 2012-09-20
> **LewisTM said:**
> It's probably the way the NAS is setup. It may force root ownership on the server side but will grant full access to all.
Do you get any error? Does it keep you from working? Can you unmount it properly? 

Here's a mini [HowTo]("http://ubuntuforums.org/showpost.php?p=9941016&postcount=3") from Morbius on how to take full advantage of Gigolo for automounting SMB shares.

- It might indeed be something governed by the NAS, not by my box.

- I get an error for each file copied. Not much of a problem when it's one film I'm backing up, annoying when it's a directory with 900 holiday photos.
(And my notification sound is Office Space's Bill Lumberg going "Errrrr, we have a problem here". Gets old after the first 100 times :-) )
- For the rest it works, it does not keep me from working.

- It unmounts properly when I shut down the box.
I might give gigolo a try.
Thanks for your input.

---

