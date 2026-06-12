---
title: "Rights for audio"
date: 2006-09-25
forum: Multimedia &amp; Video
---

### Post by bmkrein on 2006-09-25
Question abut audio (and other) rights.

Can anybody tell, how to anable audio not for one user as in /etc/group file, but for all group of users, or even to all users.

Sincerely....

-ReinL:

---

### Post by xpod on 2006-09-25
Cant you do that in "user`s and groups"??
Im sure if you click on the particular user in there it then gives an option of all the stuff their permitted access to..

I might be wrong but have a look
EDIT:double click the "user" then click the "user privalages

---

### Post by kidders on 2006-09-25
Hi there,

To do this, you would chmod (or even chown) your audio-related /dev entries as root. Of course, removing and re-inserting a USB audio device, or rebooting your computer would reset the original "sensible" permissions set. To get around this, you need to learn about udev.

Basically, by tweaking one line in a file (in the /etc directory), you can control the default access privileges for any device on your system. I wouldn't recommend trying it without doing a little reading first though.

Specific to audio devices, enabling global access is not particularly wise. Should any malicious user, script or other program gain even very low-rights access to your system, they could easily crash it, or eat up all your CPU time and cripple it. If, given that caveat, you still want to open up all-user access to audio devices, take a peek at udev. If not, simply adding the appropriate users to the "audio" group (as suggested by xpod) is the "correct" way of granting access to sound equipment.

---

### Post by bmkrein on 2006-09-26
> **xpod said:**
> 
EDIT:double click the "user" then click the "user privalages
Yes, this would be easy with 2-20 users, but I have them 200 and constantly i am adding nad deleting them. And I have 10 computers in our class with Ubuntu. 

So am using now nis authentication and would like to add in example audio rights for all three users grups like users1, users2, users3.

-ReinL:

---

### Post by bmkrein on 2006-09-26
> **kidders said:**
> Hi there,
To do this, you would chmod (or even chown) your audio-related /dev entries as root. 
Here in Ubuntu /dev/audio file is owned by group audio. But I have three groups users1, users2, users3. All of them must have audio enabled. 

I cant make ownership of file (directory) for three groups but one. 
My guestion is, can one group be member of other group? :-k 

-ReinL:

---

### Post by kidders on 2006-09-26
No, not really :-( The way you would achieve that effect is by making users a member of several groups when you create them. You can of course add users to additional groups *after* creating them ... it's quick and painless.

---

### Post by bmkrein on 2006-09-26
Yes, but still then even i use NIS, i use groups file locally as group ID in NIS server and nis client have diffrent ID-s and names. 

In example Ubuntu has groups
cdrom 24
floppy 25
audio 29
video 44
plugdev 46

In need then to add all 200  users in every 10 pc to file /etc/groups in five line... 
It makes 10 000 words to add... and when i add one more user then it makes additional 50 words.... 

](*,)  :-?

---

### Post by kidders on 2006-09-26
Oh dear... if you're using a centralised authentication mechanism, you really should sync your user & group ids. Life gets far too complicated otherwise!

In terms of modifications to your /etc/groups, you can do those pretty easily in batches, if you desire. For instance, if I happened to want to add every user in group #2001, say, to the "audio" group, I could maybe try something like **for i in `cat /etc/passwd | grep ":2001:" | sed  "s/:.*//"`; do usermod -G audio $i; done** Of course, using usermod's "-a" switch would stop any pre-existing memberships being overwritten.

I hope that's of some help to you.

---

### Post by bmkrein on 2006-10-06
> **kidders said:**
> **for i in `cat /etc/passwd | grep ":2001:" | sed  "s/:.*//"`; do usermod -G audio $i; done** Of course, using usermod's "-a" switch would stop any pre-existing memberships being overwritten.

Thank you, this script is helpful endeed.... This is the way I go now... Thank yoy. But i did not see "-a" switch  in usermod manual? 

If even someone would know how to enable systemwide rights for audio, video (usb memory, cdwrite...) not per person but per group (or lets say users from uid > 1000) then i would be very clad...

Sincerely 

Rein

---

### Post by kidders on 2006-10-06
Hey again,

Access rights to audio devices are restricted because there are ways in which such access could be abused to hang, crash, or eat the CPU time of a PC. This is why most Linux users are reluctant to **chmod o+rw /dev/audio**, for instance, which would give everyone the ability to use it. If you're happy to trust that your users won't try to do damage, you could maybe consider this option. The same principle applies equally to other devices on your system.

A preferred option is to create a special group, the members of which can access "sensitive" system devices. Although this is what Linux does by default, it almost looks as if the level of control you have over who can do what is too fine-grained. Try this suggestion:

[LIST]
[*]You have a set of users you consider "trustworthy" and you want to grant them unrestricted access to, say, audio & video devices.
[*]These user accounts are managed by a centralised authentication schema like LDAP or NIS.
[/LIST]

First off, you would create a new group with your centralised user management system, ignoring the /etc/group files on individual computers. Say you create a group called "trusted", with GID 5001. Now, you would create a quick script to alter the way permissions are allocated to /dev entries on computers you want to loosen the access control on. For example:

[LIST=1]
[*]Open /etc/udev/rules.d/40-permissions.rules.
[*]Search for the word "audio".
[*]Change **SUBSYSTEM=="sound", GROUP="audio"** to **SUBSYSTEM=="sound", GROUP="5001"**.
[/LIST]

Without actually having tried this, I'm assuming something *like* this would work for you. Applying the same principle to other devices, you'd basically end up with lots of /dev entries that can only be accessed by members of group 5001.

What I don't quite understand is your reluctance to use the pre-existing system of access control Ubuntu provides. After all, adding users to ten groups is as easy as adding them to one. The default access control is sensible, straightforward, and very easy to use, even for extremely large numbers of users. For instance, my computers all authenticate against a single source (an LDAP server) ... all I ever need to do to give a user access to audio, say, is execute a single command on my server.

I hope some of this is helpful.

About usermod's -a switch, here is a snippet from **man usermod** ...

> If the user
              is currently a member of a group which is not listed, the user
              will be removed from the group. This behaviour can be changed
              via -a option, which appends user to the current supplementary
              group list.


---

### Post by lister171254 on 2006-12-15
I have a similar problem. I have two users (Leo & Ingrid) where pretty much all of Ubuntu was set up under Leo.

I have added Ingrid, made her part of the audio user group and can use all applications (ie xmms), but get no sound for that user. No errors are reported and xmms plays the music.

/dev/audio has rw rights for the audio group and both users are member of that group.

Any help would be appreciated.

Thanks,

leo

---

