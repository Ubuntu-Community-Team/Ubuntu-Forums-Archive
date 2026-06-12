---
title: "samba shares and their permissions"
date: 2011-11-29
forum: Networking &amp; Wireless
---

### Post by Jacobonbuntu on 2011-11-29
For those who might visit this thread and take the effort to read this : this thread is split off from: [http://ubuntuforums.org/showthread.php?t=1887617](http://ubuntuforums.org/showthread.php?t=1887617)
As such, it is not directly a request for help to solve an existing problem, as I have the situation quite like I want it (NAS, automounted etc), but a request to help clarify the logic of how samba shares are "accredited" for both client and server. It is a subject that I find pretty interesting, and although it seems complicated, I am sure it must be logical and understandable, like everything else in Linux.

this is the (test-)situation:

- I created a samba share by adding these lines to my /etc/samba/smb.config -file:
[share]
comment = Ubuntu File Server Share
path = /srv/samba/share
browsable = yes
guest ok = yes
read only = no
create mask = 0755

- I created the directory: /srv/samba/share

- I changed the owner to nobody.nogroup

all as described in this manual: [https://help.ubuntu.com/11.10/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.10/serverguide/C/samba-fileserver.html)

As suggested by morbius, as a solution for BirdZerk in a (seemingly) similar situation in the original thread, I added this line to the global section in the /etc/samba/smb.config -file:
> force user = jacob(jacob=my name ) to make all newly created files owned by "jacob", no matter if they are created from the client-side or not.

however, when I do that, on the server computer as well as on the client computer, I have no more perissions to my own share

the outcome of this command: testparm -s

> jacob@jacob-Satellite-L300:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share]"
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
force user = jacob

[printers]
comment = All Printers
path = /var/spool/samba
create mask = 0700
printable = Yes
browseable = No

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers

[share]
comment = Ubuntu File Server Share
path = /srv/samba/share
read only = No
create mask = 0755
guest ok = Yes
jacob@jacob-Satellite-L300:~$ the outcome of:
> net usershare info --longis nothing (?)

The question is: why is the "force user" option having the opposite efect of what you would expect?

---

### Post by Morbius1 on 2011-11-29
In my defense the recommendation of using force user came about specifically for use in Usershares - created from Nautilus. You have no usershares:
 > the outcome of:
     Quote:
                                                 net usershare info --long                                 
is nothing (?)It should still work here but since your dealing with classic shares I would put it within the share definition itself. However since you only have one share it really doesn't matter where you put it.

The way this is set up without the "force user" added all remote users will come across as owner = nobody which is consistent with the ownership of the target directory. You don't need or want a force user to anyone else. The way you had it originally basically set "force user = nobody"

---

### Post by Morbius1 on 2011-11-29
On a completely unrelated matter I'm surprised that anyone can browse to your share since your host name ( which gets converted to the netbios name that is visible on the network ) is 5 characters too long:
> jacob-Satellite-L300You must be accessing this share by ip address. There is an easy way to fix that in smb.conf itself if you think it needs fixing.

---

### Post by Jacobonbuntu on 2011-11-29
> **Morbius1 said:**
> On a completely unrelated matter I'm surprised that anyone can browse to your share since your host name ( which gets converted to the netbios name that is visible on the network ) is 5 characters too long:
You must be accessing this share by ip address. There is an easy way to fix that in smb.conf itself if you think it needs fixing.

AHA, Indeed I am accessing this share by ip address..
Thanks!
I did not know about the character-restriction! 

another question I have: in the Nautilus user-share option, you can, as it looks, set quite detailed permissions, but trying to do so, all settings "jump" back to the default. I tried doing it as a root (just to see what happened) with the same result. *If *it would work as it looks like it is meant to work, it would be quite a user friendly option.
actually I thought the Nautilus -way was just meant as a GUI way to edit the smb.config, but I understand it is another kind of share. 

as you see I am quite new to the subject :), I will start reading a lot :)

thanks for the effort!

---

### Post by Jacobonbuntu on 2011-11-29
> **Morbius1 said:**
> On a completely unrelated matter I'm surprised that anyone can browse to your share since your host name ( which gets converted to the netbios name that is visible on the network ) is 5 characters too long:
You must be accessing this share by ip address. There is an easy way to fix that in smb.conf itself if you think it needs fixing.


---I remembered I could also access the share via Nautilus! This is the funny thing: the name is shortened to jacob-satellite (!)

---

### Post by Morbius1 on 2011-11-29
Usershare or Nautilus share is meant to mimic a WinXP like "Simple Share" - right click a folder in the file manager and select "share this thing" - I'm paraphrasing :)

The default samba parameters and the ones in smb.conf have controll over usershares since it is still part of samba but their share definitions are some place else: /var/lib/samba/usershares. These are not meant to be edited directly but only through nautilus. 

On the client end the way nautilus can browse to and mount a remote share is also a lot easier since it sets it up automatically with the correct permissions avoiding all the uid=this and dir_mode=that that you have to go through when mounting them manually or through fstab.

There's even a way to graphically automount these shares using the same underlying mechanism but with a GUI utility: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

**EDIT**: Have to shut down for the day. There's a storm coming and power always goes off here when that happens.

---

### Post by Morbius1 on 2011-11-30
You know, the more I look at the HowTo you referenced the more I don't like it :). In a way it's very clever in the way it sets things up but ....

It had you create a directory to share and changed ownership:
```
sudo mkdir -p /srv/samba/share
sudo chown nobody.nogroup /srv/samba/share/
```If the intent was to create a share on a server that is accessed by lan clients only then so far so good. But there is a problem if you log into the server itself because the permissions look like this:
> ls -dl /srv/samba/share
drwxr-xr-x 2 nobody nogroupIf I login as jacob I have read access only to the folder since I am not "nobody". So jacob cannot add anything to the currently empty folder itself while logged into the server.

Then he had you create the following share:
> [share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755Let's make this simple and assume that I have a client running Linux that accesses this share using Nautilus. The client does not pass or is prompted to pass a user name and password to access the share since it allows guest access. If he adds a file it will save with owner = nobody with permissions for nobody to read and write but read only access to everyone else. That's fine for a server meant to be accessed by a lan client but what happens when jacob logs into the physical server itself? He can read the saved file but cannot write to it since he is not "nobody".

There are a number of ways around this problem such as an absolutely mind numbing combination of create mask, force create mask, directory mask, etc... Or you can add "force group", make jacob a member of the "nogroup" group, change permissions of the shared directory to 775 instead of 755, and change the linux default umask parameter from 022 to 002. There are many possibilities here.

I suppose you could get more convoluted and change permissions on /srv/samba/share to 777 and then have the client pass an unrequested username ( jacob ) and password when he accessed the share. This would have to be done manually or through fstab but then you are passing credentials to a guest share which sort of defeats the purpose.

That HowTo creates a share for a box that is booted but never logged into. Most users here use Samba in more a peer-to-peer mode where Bob wants to share some files with Edna.

A Samba usershare if created in a classic mode would change permissions of the target directory to 777 so that the samba "guest" and the Linux "other" are in sync. The problem still persists though for jacob on the server since the files still save with nobody as owner. This is where force user comes in. So If I were to create a share in the usershare manner correcting for the ownership problem it would look like this:
> [share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    force user = jacobAnd to replicate what usershare does automatically I would have to change permissions on the target directory to 777:
```
sudo chmod 777 /srv/samba/share
```
EDIT: That last sentence was technically in error. Usershare itself doesn't change permissions to 777 automatically, nautilus-share changes permissions automatically.

---

### Post by Jacobonbuntu on 2011-11-30
> **Morbius1 said:**
> On the client end the way nautilus can browse to and mount a remote share is also a lot easier since it sets it up automatically with the correct permissions avoiding all the uid=this and dir_mode=that that you have to go through when mounting them manually or through fstab.

There's even a way to graphically automount these shares using the same underlying mechanism but with a GUI utility: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

sharing through nautilus was indeed my first "experiment", but although I had full rights to all directories (as a client), new documents were owned by the creator (as the OP of the OT :)), which is usually not so comfortable with a share :)

I will try the Gigolo-stuff! Isn't that the default network tool of Xubuntu? 
I think eventually Ubuntu will have to provide a GUI interface for Samba-shares in the most common (home) situations.

---

### Post by Jacobonbuntu on 2011-11-30
> **Morbius1 said:**
> You know, the more I look at the HowTo you referenced the more I don't like it :). In a way it's very clever in the way it sets things up but ....

It had you create a directory to share and changed ownership:
```
sudo mkdir -p /srv/samba/share
sudo chown nobody.nogroup /srv/samba/share/
```If the intent was to create a share on a server that is accessed by lan clients only then so far so good. But there is a problem if you log into the server itself because the permissions look like this:
If I login as jacob I have read access only to the folder since I am not "nobody". So jacob cannot add anything to the currently empty folder itself while logged into the server.

Then he had you create the following share:
Let's make this simple and assume that I have a client running Linux that accesses this share using Nautilus. The client does not pass or is prompted to pass a user name and password to access the share since it allows guest access. If he adds a file it will save with owner = nobody with permissions for nobody to read and write but read only access to everyone else. That's fine for a server meant to be accessed by a lan client but what happens when jacob logs into the physical server itself? He can read the saved file but cannot write to it since he is not "nobody".

There are a number of ways around this problem such as an absolutely mind numbing combination of create mask, force create mask, directory mask, etc... Or you can add "force group", make jacob a member of the "nogroup" group, change permissions of the shared directory to 775 instead of 755, and change the linux default umask parameter from 022 to 002. There are many possibilities here.

I suppose you could get more convoluted and change permissions on /srv/samba/share to 777 and then have the client pass an unrequested username ( jacob ) and password when he accessed the share. This would have to be done manually or through fstab but then you are passing credentials to a guest share which sort of defeats the purpose.

That HowTo creates a share for a box that is booted but never logged into. Most users here use Samba in more a peer-to-peer mode where Bob wants to share some files with Edna.

A Samba usershare if created in a classic mode would change permissions of the target directory to 777 so that the samba "guest" and the Linux "other" are in sync. The problem still persists though for jacob on the server since the files still save with nobody as owner. This is where force user comes in. So If I were to create a share in the usershare manner correcting for the ownership problem it would look like this:
And to replicate what usershare does automatically I would have to change permissions on the target directory to 777:
```
sudo chmod 777 /srv/samba/share
```EDIT: That last sentence was technically in error. Usershare itself doesn't change permissions to 777 automatically, nautilus-share changes permissions automatically.

I will have to read this a few times before I fully understand this :)
what I do understand is why the force user -option was conflicting with the "nobody-nogroup" story and took away permissions.....

---

