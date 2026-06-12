---
title: "Samba config not working for me. =("
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by ripeart on 2010-01-12
[FONT=Arial]Hi, I feel like kind of an idiot because I know this is a relatively easy thing to do. I am simply trying to setup a share from my Ubuntu 9.10 box to my LAN to a Windows box.

The share exists on an external USB drive. I have samba & smbfs installed. I have tried sharing using the GUI but on the Windows side I was receiving an access denied error. I've done this once before manually so I figured it would be quick to setup using nano. However I've followed the 9.10 tutorials and others on a few other sites but am still receiving access denied. Here's an output of the samba error log: /var/log/samba/log.vaioonone

[/FONT][INDENT][FONT=Fixedsys][2010/01/12 01:08:59,  0] param/loadparm.c:8546(process_usershare_file)
[/FONT][FONT=Fixedsys]  process_usershare_file: stat of /var/lib/samba/usershares/music failed. Permission denied
[/FONT][FONT=Fixedsys][2010/01/12 01:08:59,  1] smbd/service.c:676(make_connection_snum)
[/FONT][FONT=Fixedsys]  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED
[/FONT][FONT=Fixedsys][2010/01/12 01:08:59,  1] smbd/service.c:676(make_connection_snum)
[/FONT][FONT=Fixedsys]  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED[/FONT]
[/INDENT][FONT=Arial]
I attached my /etc/samba/smb.conf file to this post.

So, I'm sure it's something simple and I would appreciate any push in the right direction.

Thanks!
[/FONT]

---

### Post by changingstate on 2010-01-12
Does the username you're using on the windows machine have a user account on the ubuntu server? 

Your smb.conf has  "security = user" set, so samba will be checking the ubuntu machines list of logins for authorisation. There's two ways around this. 

1) Use the adduser command to add a user account to the ubuntu machine for the windows user. Restart samba. This will keep things secure.

2) Switch to "security = share" to make samba behave like windows shared folders where anyone can connect. Restart samba. This will let everyone look at your files.

---

### Post by Morbius1 on 2010-01-12
You've got two problems:

(1) If your share is an external usb drive that you auto mount by just plugging it in you will never get access across the network because it mounts with you as owner and permissions for you and only you to read and write. You're allowing guess access so it's never going to work. It looks to me like a linux file permissions problem not a samba problem.

To fix that:

Open **Terminal**
Type [B]gksu gedit /etc/samba/smb.conf
[/B] 
Modify your share definition from this:
> [Music]
comment = "Jukebox music library."
path = /media/1gb/Music
browseable = yes
writeable = yes
guest ok = yes
read only = no
create mask = 777
directory mask = 777To this:
> [Music]
comment = "Jukebox music library."
path = /media/1gb/Music
browseable = yes
writeable = yes
guest ok = yes
read only = no
force user = morbius1[COLOR=Blue][I]Change morbius1 to your own local login user name.
[/I][/COLOR] 
When you're done with the change, save the file, exit gedit, and back in the terminal type:

[B]sudo service samba restart

[/B](2) The error references [FONT=Fixedsys]/var/lib/samba/usershares/music.

That's not classic samba where the shares are defined in smb.conf. It's nautilus-share where you share a folder directly from nautilus.  Please post the output of the following command:

**net usershare info**

There could be interference from sharing the same folder using two completely different methods of sharing.
[/FONT]

---

### Post by ripeart on 2010-01-12
Ok, here's what I did. I scrapped the install on the tablet PC I was working with and installed 9.10 on a G5 I had here. Starting with a fresh install, I changed the smb.conf:

security = share

At this time, I'm just getting it setup and accessible, etc... Later I will make the access per Ubuntu user. Additionally, I am not using the external drive anymore.

Thanks for the help, the ```
security = share
``` did it!

:P:P:P:P:P:P:P:P

---

