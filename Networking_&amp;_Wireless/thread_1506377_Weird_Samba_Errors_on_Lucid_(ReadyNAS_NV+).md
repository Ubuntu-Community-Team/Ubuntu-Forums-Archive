---
title: "Weird Samba Errors on Lucid (ReadyNAS NV+)"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by mkoby on 2010-06-10
Hi,

I'm having some weird issues when trying to mount shares on my network attached storage device (ReadyNAS NV+) to a folder on my Lucid box.  

When I try to mount the folder (either manually or through fstab) I get the following error

```
error(11) Resource Temporarily Unavailable
```

I have the security on the ReadyNAS device set to "Share", I have the CIFS service turned on, and the Workgroup on both the ReadyNAS and in my smb.conf on my computer are set to "WORKGROUP".

I believe this is a Samba configuration issue for a couple of reasons:

[LIST=1]
[*]I can mount the device using NFS
[*]I can navigate to the same folder via the "Network" icon under the "Places" menu
[/LIST]

I don't want to use NFS due to the fact that the UIDs have to sync up in order for me to get full write access to the shares, and i have multiple shares I will be connecting to on the NAS at various times.

I like having the folders mounted for a couple of reasons as well, mainly because I use symbolic links in my home folder to point it to my documents folder on the NAS.  Also moving files onto the NAS using the "mv" command when they are large files is better than using Nautilus.

This worked fine in 9.10, but for some reason hasn't been working correctly in Lucid.  I've researched the problem thoroughly and can't seem to find an answer.  So any help is greatly appreciated.

UPDATE:

When I run findsmb I get teh following output:
```

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.135   DESKTOP +[WORKGROUP] [Unix] [Samba 3.4.7]
192.168.1.145   NAS02     +[WORKGROUP] [Unix] [Samba 3.0.36]

```

and if I do a smbclient -L nas02 I get:
```

Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.36]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (nas02)
	webroot         Disk      
	video           Disk      video files
	media           Disk      Media Server Share
	games           Disk      video games
	backup          Disk      Backup Share
	audio           Disk      audio files

	Server               Comment
	---------            -------
	WIFESCOMP                
	NAS02            kobynas02
	DESKTOP        mkoby-desktop server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            NAS02
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.36]

```

So smbclient and findsmb can SEE my ReadyNAS and the shares on it, but for some reason I can't mount the shares to a local folder.

---

### Post by mkoby on 2010-06-11
I'm bumping this, hopefully someone out there has answers because I'm completely stumped.

---

### Post by mkoby on 2010-06-16
This turned out to be an issue with the ReadyNAS NV+ rather than my linux install.  After trying to set up the same shares on 9.04 on my daughter's computer and running into the same issue, I decided to take a closer look at the ReadyNAS.

I wasn't able to make it work by configuring options (CIFS, permissions, etc) in the RAIDiator admin website so I took to what one might consider drastic measures (at least Netgear support would call them drastic).

I installed the SSH addons (ToggleSSH and EnableRootSSH), found [here]("http://www.readynas.com/?page_id=94") and then I SSHed into the NAS device and restarted the samba dameons (/etc/init.d/samba restart), and it seems to be working again.

Not sure what caused the samba issues on the NAS but it seems to be fixed now.

---

### Post by simonmullis on 2010-07-01
Just to say... I had exactly the same issue:

Mounting from command line as my normal "cifs user"
With a Readynas NV+
After installing root SSH.

I could mount as guest (RO) without problems.

Restarting samba on the NV+ fixed it for me too.

Thankyou!

SM

---

### Post by hojac on 2010-09-02
Hi

I'm also have readynas nv+. Not able to get to files, please list exact steps u used to access
nas box from ubuntu 10.04 (mint 9). Win 7 no problem...... but linux I'm a newbie.

thank you

---

