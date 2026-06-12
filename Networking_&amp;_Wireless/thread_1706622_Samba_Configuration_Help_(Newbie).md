---
title: "Samba Configuration Help (Newbie)"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by Jynks on 2011-03-14
Hi there...

I am trying to share a USB external Hdrive from my ubuntu install to my windows systems (win 7 and 1 win xp)

Everything seams to be working.. as in I can see the computer in "network" from windows explorer.... The problem is no matter what I do I can not seam to browse onto it or even type in direct share locations....

EG: //Zbox/HDMedia

or just browse through the Zbox computer icon that appears in my "Network" window in explorer.

I have "sudo chmod 0777 /media/HDMovies"

Any ideas.. .as I can see it in the win7 Network window.. I assume it is some setting for security... any ideas... I am on a home network and not very security conscious. I just want it to work.

Thanks in advance

---

### Post by headvampyre@hotmail.co.uk on 2011-03-14
can we please have more description on the errors in Windows explorer?

Thanks

---

### Post by Morbius1 on 2011-03-14
You might want to post the output of the following commands as well since I for one am having a hard time following your description of the symptoms:
```
smbtree
net usershare info --long
testparm -s
```On more thing - how is the external USB drive formatted? Is it NTFS?

You seem to think that it's a permissions problem since you did a "chmod 777" and it likely is since the drive will mount as 700 but chmod doesn't work with NTFS. There's an easy fix by using "force user" in smb.conf but without some facts like what method of samba sharing you are using ( there are 2 ) I wouldn't even know where to tell you to put it.

---

### Post by Jynks on 2011-03-16
thanks for you replies guys.. I am sorry I didn't give you enough ionfomation.. I'll try to be much more thurow.... 

SMB.CONF
```

[global]
security = guest
workgroup = myworkgrounpname
server string = %h server (Samba, XBMC)
netbios name  = ZBox
dns proxy = no
name resolve order = hosts wins bcast
guest account = xbmc
load printers = no
show add printer wizard = no
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
enctypt passwords = no
passdb backend = tdbsam
obey pam restrictions = yes
unix password sync = yes
password program = /usr/bin/password %u
passwaord chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user

[HD Movies]
path = /media/HDMovies
comment = HD Video Drive
guest ok = yes
read only = no

```

> **Morbius1 said:**
> 
```
smbtree
net usershare info --long
testparm -s
```

smbtree dosn't do anything --- command not found
net usershare info --long --- errors, guest is not valid
testparm -s --- seams to just print to screen the smd.conf... but as it is longer than a single page and i can not seam to scroll up I can not copy it all out here... is there some kind of / command or somthign io can put after a command to make it pause when the screen if full?

---

### Post by crispy_420 on 2011-03-16
You mentioned newbie right? You setting up share in command line or using the GUI tool. I would suggest the GUI tool since it is really easy and doesn't require too much knowledge. Then from Windows box bring up run command and enter the share as \\YOUR_IP. See if that helps you at all.

---

### Post by Jynks on 2011-03-16
unfortunatly I am using XBMC LIVE witch is a custom stripped down version of ubuntu runnign a custom UI... so I can not use the gui tpo set this up. What I really wanted was to run a full ubuntu install but after much posting and no answers on how to get sound though the HDMI cable I gave up and moved to xbmc

---

### Post by Jynks on 2011-03-16
```
[global]
security = share
guest account = nobody
workgroup = WDGBWC
server string = %h server (Samba, XBMC)
netbios name = Zbox
dns proxy = no
name resolve order = hosts wins bcast
load printers = no
show add printer wizard = no
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user

[Videos]
path = /home/jynks/Videos
public = yes
only guest = yes
guest ok = yes
read only = no

[Music]
path = /home/jynks/Music
public = yes
only guest = yes
guest ok = yes
read only = no

[TV Shows]
path = /home/jynks/TV Shows
public = yes
only guest = yes
guest ok = yes
read only = no

[Downloads]
path = /home/jynks/Downloads
comment = Downloads Folder
public = yes
only guest = yes
guest ok = yes
read only = no

[Pictures]
path = /home/jynks/Pictures
comment = Pictures
public = yes
only guest = yes
guest ok = yes
read only = no

[System]
path = /home/jynks/.xbmc
comment = XBMC System Share
public = yes
only guest = yes
guest ok = yes
read only = no

[HDMovies]
path = /media/HDMovies
comment = HD Movies 01
public = yes
only guest = yes
guest ok = yes
read only = no

```

Ok I have it working now using this smb.conf.... but I STILL can not acess the external 2TB usb drive!! :( All the other shares work perfectly.

> **Morbius1 said:**
> On more thing - how is the external USB drive formatted? Is it NTFS?

<snip>

chmod doesn't work with NTFS. There's an easy fix by using "force user" in smb.conf but without some facts like what method of samba sharing you are using ( there are 2 ) I wouldn't even know where to tell you to put it.

Can you please explain this "force user" or maybe how I can tell what my drive is formatted as? I just formatted it using window7 64bit as a 2TB drive when I bought it... so I guess it is NTFS and the chamod isn't working like you said.. so how do I get aroudn this...

Thanks in advance guys... getting closer.. at least the sharing is working now... just not on this drive

---

### Post by crispy_420 on 2011-03-16
Is the drive always mounted and accessible from the host machine? Like when the remote machine can not connect can you cd to the directory from commandline and view the files?

What it be an option to mount the directory/drive to a different location? And then try that?

Just trying to keep the ideas flowing.

---

### Post by Jynks on 2011-03-16
> **crispy_420 said:**
> Is the drive always mounted and accessible from the host machine?

Yes, as soon as it is plugged in it is auto detected and mounted. On the host you can browse to the drive at will.

---

### Post by Morbius1 on 2011-03-16
Add a line to your share definition for the 2TB drive:
> [HDMovies]
path = /media/HDMovies
comment = HD Movies 01
public = yes
only guest = yes
guest ok = yes
[COLOR=Blue]** force user = jynks**[/COLOR]
read only = noSave smb.conf and in a terminal restart samba:
```
sudo service smbd restart
```The external NTFS drive will mount with owner = jynks and with permissions of 700 meaning jynks has access but no one else. Your share allows guest access so the remote user is coming across literally as owner = nobody. Nobody is not jynks so he will not gain access.

"force user" creates a mask that will convert "nobody" to "jynks" as far as that share is concerned.

---

### Post by Jynks on 2011-03-17
> **Morbius1 said:**
> Add a line to your share definition for the 2TB drive:
Save smb.conf and in a terminal restart samba:
```
sudo service smbd restart
```The external NTFS drive will mount with owner = jynks and with permissions of 700 meaning jynks has access but no one else. Your share allows guest access so the remote user is coming across literally as owner = nobody. Nobody is not jynks so he will not gain access.

"force user" creates a mask that will convert "nobody" to "jynks" as far as that share is concerned.

Thank you Morbius.. everything is working great now... youn rule!!!

---

### Post by belfbri on 2011-07-30
> **Morbius1 said:**
> On more thing - how is the external USB drive formatted? Is it NTFS?

You seem to think that it's a permissions problem since you did a "chmod 777" and it likely is since the drive will mount as 700 but chmod doesn't work with NTFS. There's an easy fix by using "force user" in smb.conf but without some facts like what method of samba sharing you are using ( there are 2 ) I wouldn't even know where to tell you to put it.

Thank you, thank you, thank you! This has been frustrating me to no end for the last few days on a new box I've built. I've had Samba working before and couldn't understand why it was not working this time. Completely forgot that the drive I'm using this time is NTFS and everything is now working after adding the force user option.

---

### Post by _sge on 2011-11-30
Thanks! Solved the problem for me.

samba's default configuration could have found a way for NTFS drives to work with minimal configurations

---

