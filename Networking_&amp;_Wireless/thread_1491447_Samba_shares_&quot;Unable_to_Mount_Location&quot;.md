---
title: "Samba shares &quot;Unable to Mount Location&quot;"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by MasterMIKE on 2010-05-23
ok so on 10.04 I clicked to share my music folder with the network (other computer also having 10.04) and it installed samba for me. I restarted expecting to find sharing working as it had on the other computer by doing the exact same thing. But for some strange reason I can't access the shares on either computer through the network workgroup. It just says "Unable to Mount Location" Is there something I'm missing here?

---

### Post by rg_stephens on 2010-05-24
If both computers are using Linux, you don't necessarily have to use Samba.

10.4 seems to have some missing packages that have to be installed to get things working right.

see: 
[http://ubuntuforums.org/showthread.php?t=1473760](http://ubuntuforums.org/showthread.php?t=1473760)

---

### Post by MasterMIKE on 2010-05-26
First off I'd prefer to use Samba just in case my dad decides to stick windows on his comp. I'd like to still be able to share with him. And also as it happens I already have those packages installed. Too my knowledge nothing is missing and the shares permissions are set correctly.

---

### Post by kwalters on 2010-05-26
This problem has had me tearing my hair out for over a week.  I have 3 pcs, each dual booting Ubuntu and Windows XP.  I have been going through threads ad nauseam; but the thread below (written in 2006 for version 6 of Ubuntu and only slightly amended by me) has cracked the problem. I can now share files between Ubuntu machines and between Ubuntu and Windows

I am very grateful that I found this thread by Stormbringer; for, if I had not, I was going to revert to an earlier version of Ubuntu.  I followed it slavishly apart from using Samba4 instead of Samba. Remember to change the words when you start Samba4 instead of Samba if you do the same. Obviously I installed Samba4 using the Synaptic GUI

Here is the thread [http://ubuntuforums.org/showthread.php?t=202605&](http://ubuntuforums.org/showthread.php?t=202605&).  JUst in case I have not transmitted it properly, it was first shown on 23 Jun 2006.

Incidentally, I hate using anything other than a GUI, but this magnum opus in typing terms was well worth the effort.  The only problem (as always when I have to call for help from this forum) is that I HAVE NOT A CLUE about the process I have gone through; but it worked.

KW

---

### Post by MasterMIKE on 2010-05-30
Ah thanks alot.I haven't had the chance to test it out yet. Been kinda busy. I will test it out later today. I'll let you know if it does or doesn't work, but I am going away for a while tomorrow.

---

### Post by Morbius1 on 2010-05-30
I just thought i would mention that in this thread three different methods of sharing files were mentioned and two of them may ( note - may ) conflict with the other.

**1st: Personal File Sharing**: [http://ubuntuforums.org/showthread.php?t=1473760](http://ubuntuforums.org/showthread.php?t=1473760)
This is not samba and from my experience with it there is a reason Ubuntu ships this thing disabled :wink:
[B]
2nd: Samba Classic-shares[/B]: [http://ubuntuforums.org/showthread.php?t=202605&](http://ubuntuforums.org/showthread.php?t=202605&)
Nothing wrong with this method. It's the way it has always been done and is still the most flexible and configurable of the two samba methods available. There's a lot of docmentation about this method on the web and some of it is actually accurate.

**3rd: Samba Nautilus-shares**. 
If I'm reading your posts accurately then this is the method you are currently using. A lot of people think this is new but I think it's been around since Gutsy. I read one post here that stated it's not samba but it is in fact part of samba and has been for years.

From my own experiences I've found that Classic-shares and Nautilus-shares don't play well together. IT can be done and I use both myself but it's best to use one method or the other to avoid conflicts.

If you post the output of the following commands perhaps we can get some insight into the reasons for your dilemma:
```
net usershare info
sudo net usershare info
testparm -s

```

---

### Post by MasterMIKE on 2010-06-18
[FONT=monospace]Sorry for my late reply been real busy with college work.

net usershare info[/FONT]
> [breaking bad]
path=/home/michael/Public/Videos/Breaking Bad
comment=
usershare_acl=Everyone:R,
guest_ok=y

[sample videos]
path=/home/michael/Public/Videos/Sample Videos
comment=
usershare_acl=Everyone:R,
guest_ok=y

[half pint brawlers]
path=/home/michael/Public/Videos/Half Pint Brawlers
comment=
usershare_acl=Everyone:R,
guest_ok=y

[videos]
path=/home/michael/Public/Videos
comment=
usershare_acl=Everyone:R,
guest_ok=y

[documents]
path=/home/michael/Public/Documents
comment=
usershare_acl=Everyone:R,
guest_ok=y

[pioneer.one.s01e01.720p.x264-vodo]
path=/home/michael/Public/Videos/Pioneer.One.S01E01.720p.x264-VODO
comment=
usershare_acl=Everyone:R,
guest_ok=y

[music]
path=/home/michael/Public/Music
comment=
usershare_acl=Everyone:R,
guest_ok=y

[public]
path=/home/michael/Public
comment=
usershare_acl=Everyone:R,
guest_ok=y

[other]
path=/home/michael/Public/Videos/Other
comment=
usershare_acl=Everyone:R,
guest_ok=y

[game-play]
path=/home/michael/Public/Videos/Game-Play
comment=
usershare_acl=Everyone:R,
guest_ok=y

[pictures]
path=/home/michael/Public/Pictures
comment=
usershare_acl=Everyone:R,
guest_ok=y

[FONT=monospace]sudo net usershare info[/FONT]
no output at all

testparm -s
> Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


---

### Post by Morbius1 on 2010-06-18
Wow!

You have shared a parent folder:
> [public]
path=/home/michael/Public
comment=
usershare_acl=Everyone:R,
guest_ok=yAnd then you shared 10 child folders under Public.

That might actually work only because they all are configured to allow guests and are read only. You could see that Samba might get confused if one of the children where set to write access and did not allow guests.

From one of the other linux machines post the output of the following command:
```
smbtree
```

---

