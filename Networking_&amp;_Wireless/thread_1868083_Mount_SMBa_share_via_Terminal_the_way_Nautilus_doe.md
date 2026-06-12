---
title: "Mount SMBa share via Terminal the way Nautilus does it"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by Don Giovanni on 2011-10-23
I have a shortcut in Places (Ubuntu 11.04) to access my Samba share
smb://nas/qdownload/

I have a symlink to this smb share in my home folder such that this share can be accessed locally as
~/qdownload/

Once I have mounted this share from the GUI I can then access it from Terminal as if it were a local folder. I know how to connect to smb shares over terminal but this does not give me the same kind of access to the share as with the way I am mounting through Nautilus.
I tend to access the machine from the internet and it's rather slow VNC into the box just to mount an smb share via the GUI.

So my question is what is the appropriate command in terminal to achieve the same effect that I have with nautilus?

---

### Post by capscrew on 2011-10-23
> **Don Giovanni said:**
> I have a shortcut in Places (Ubuntu 11.04) to access my Samba share
smb://nas/qdownload/

I have a symlink to this smb share in my home folder such that this share can be accessed locally as
~/qdownload/

Once I have mounted this share from the GUI I can then access it from Terminal as if it were a local folder. I know how to connect to smb shares over terminal but this does not give me the same kind of access to the share as with the way I am mounting through Nautilus.
I tend to access the machine from the internet and it's rather slow VNC into the box just to mount an smb share via the GUI.

So my question is what is the appropriate command in terminal to achieve the same effect that I have with nautilus?
I assume you are running a VPN to this host.  The terminal command will not traverse the Internet.  It must be used on a local segment (e.g on a LAN).  The terminal command would be```
smbclient //samba_server/share_name
```
This works very much like an FTP client (get/put).

---

### Post by Don Giovanni on 2011-10-23
Thanks for the suggestion but the smbclient log in from terminal is what I was referring to as the method that doesn't work for me.

Perhaps I didn't explain properly.

Currently I access the share from Nautilus GUI.  Once accessed from Nautilus it is available through the symlink ~/qdownload/
and functions as a local directory on that machine

What I currently do over the internet is VNC into the box, use nautilus to mount the SMB (very slow), then from Terminal SSH into the box such that I have access to the Terminal of that box.
Through terminal I can then
```

cd ~/qdownload/

```
and access the SMB as if it were a local directory on that machine. (I hope this makes sense)

So what I want to be able to do is:
-SSH into the box
-Use an appropriate command such that smb://nas/qdownload/ mounts and is accessible by the symlink ~/qdownload/ and appears as a local directory on the box I have SSH'd into
-Avoid the use VNC into the box

---

### Post by capscrew on 2011-10-24
> **Don Giovanni said:**
> Thanks for the suggestion but the smbclient log in from terminal is what I was referring to as the method that doesn't work for me.

Perhaps I didn't explain properly.

Currently I access the share from Nautilus GUI.  Once accessed from Nautilus it is available through the symlink ~/qdownload/
and functions as a local directory on that machine

What I currently do over the internet is VNC into the box, use nautilus to mount the SMB (very slow), then from Terminal SSH into the box such that I have access to the Terminal of that box.
Through terminal I can then
```

cd ~/qdownload/

```
and access the SMB as if it were a local directory on that machine. (I hope this makes sense)

So what I want to be able to do is:
-SSH into the box
-Use an appropriate command such that smb://nas/qdownload/ mounts and is accessible by the symlink ~/qdownload/ and appears as a local directory on the box I have SSH'd into
-Avoid the use VNC into the box
I don't understand the reason for the sym-link.  Can you explain why you need to do what you are doing here?

When you ssh to the remote host do you want to move the files from the remote host to your local host?  If so use sFTP (SSH based).  If not then the defined share is available in that remote host's file system.  For instance: all of my shares actually are at */smb/<somedir>*.  If I ssh to that host in can just *cd /smb/<something>*.

---

### Post by Don Giovanni on 2011-10-24
> **capscrew said:**
> I don't understand the reason for the sym-link.  Can you explain why you need to do what you are doing here?

When you ssh to the remote host do you want to move the files from the remote host to your local host?  If so use sFTP (SSH based).  If not then the defined share is available in that remote host's file system.  

All files remain on my remote lan but get copied from my NAS (the SMB share location) to my MythTV box (the box I SSH into over the internet).

The reason for the sym-link is so the SMB share is accessible as a local directory on the MythTV box and accessible from the Terminal of that box.
ex
I use the script tvnamer to rename tvshow episodes.

if I do use smbclient
```

user@mythtv:~$ smbclient //nas/qdownload/
Enter user's password: 
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.5.2]
smb: \> tvnamer .
tvnamer: command not found
smb: \> 
```
It doesn't work.

But if i first mount the share via nautilus so that it is accessible via my symlink I can
```

user@mythtv:~$ cd qdownload
user@mythtv:~/qdownload$ tvnamer .

```
and the script runs and renames the files appropriately.

> For instance: all of my shares actually are at */smb/<somedir>*.  If I ssh to that host in can just *cd /smb/<something>*]
My smb shares do not show up under /smb/ ... Did you do something special to set this up?

---

### Post by capscrew on 2011-10-24
> **Don Giovanni said:**
> All files remain on my remote lan but get copied from my NAS (the SMB share location) to my MythTV box (the box I SSH into over the internet).

The reason for the sym-link is so the SMB share is accessible as a local directory on the MythTV box and accessible from the Terminal of that box.
ex
I use the script tvnamer to rename tvshow episodes.

if I do use smbclient
```

user@mythtv:~$ smbclient //nas/qdownload/
Enter user's password: 
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.5.2]
smb: \> tvnamer .
tvnamer: command not found
smb: \> 
```
It doesn't work.

But if i first mount the share via nautilus so that it is accessible via my symlink I can
```

user@mythtv:~$ cd qdownload
user@mythtv:~/qdownload$ tvnamer .

```
and the script runs and renames the files appropriately.

]
My smb shares do not show up under /smb/ ... Did you do something special to set this up?

The real question is: *"how do I mount the share at //nas/qdownload to the host mythtv via the terminal"*.  This is done by the mount command.  But first you need to create a mount point.  I would get rid of the symlink and create a directory to be used as the mount point using the same name (mkdir ~/qdownloads).  Then in the terminal you mount the share like this ```
sudo mount -t cifs //nas/qdownload/ qdownloads -o guest,uid=1000
```

Now you can cd to ~/qdownloads and run your script.  In the future you can run the mount command from the terminal or you can automatically mount upon booting up by adding a mount to the fstab file. 

I will be gone most of today, but if you need help I will be available again this evening.

---

### Post by Don Giovanni on 2011-10-24
thanks so much capscrew for your help and patience in sorting out my convoluted question!

I tend to do things in a roundabout way in linux until I absolutely need a proper way...which I do now (seeing as I am mostly out of the country that the box lives in) .


```

sudo mount -t cifs //nas/qdownload qdownloads -o user=abc,password=1234,uid=abc

mount error: could not resolve address for nas: No address associated with hostname

```
I'm not sure why it can't resolve the IP for the nas when when nautilus is able to, but for the meantime I have specified the IP (it is static anyways)

I made a credentials file and stuck it in my home folder for now (is there a "safer"/better place to put it?)

I am using the following command and getting full read and write privileges
```

sudo mount -t cifs //1.1.1.1/qdownload qdownloads -o cred=~/cred,uid=abc

```
Exactly what I wanted. Thank you!

One last question for you though.  If I add this line to my fstab and for whatever reason the nas is down or inaccessible will it cause the system (mythtv) to hang at boot or spit out an error message?
I think I need to add the noauto option to prevent that yes?

So I would add this to my fstab?
```

//1.1.1.1/qdownload ~/qdownloads cifs cred=~/cred,uid=abc,noauto 0 0

```

---

### Post by capscrew on 2011-10-24
> **Don Giovanni said:**
> thanks so much capscrew for your help and patience in sorting out my convoluted question!

I tend to do things in a roundabout way in linux until I absolutely need a proper way...which I do now (seeing as I am mostly out of the country that the box lives in) .


```

sudo mount -t cifs //nas/qdownload qdownloads -o user=abc,password=1234,uid=abc

mount error: could not resolve address for nas: No address associated with hostname

```
I'm not sure why it can't resolve the IP for the nas when when nautilus is able to, but for the meantime I have specified the IP (it is static anyways)
This is a name service problem.  Maybe a NETBIOS problem with the nas.  But since it resolves to an IP address I would use that anyway.  i would prefer that anyway.> 

I made a credentials file and stuck it in my home folder for now (is there a "safer"/better place to put it?)

I am using the following command and getting full read and write privileges
```

sudo mount -t cifs //1.1.1.1/qdownload qdownloads -o cred=~/cred,uid=abc

```
Exactly what I wanted. Thank you!

I assume you are behind a firewall and this is a home network, so no big security needs.  I would however use an absolute path instead of the alias for your home (~).  Consider what happens if a different user were to invoke the script or worse yet, have the mount executed from fstab.  Use /home/<the_dir>/cred.  Make the file read only (440).> 

One last question for you though.  If I add this line to my fstab and for whatever reason the nas is down or inaccessible will it cause the system (mythtv) to hang at boot or spit out an error message?
I think I need to add the noauto option to prevent that yes?

So I would add this to my fstab?
```

//1.1.1.1/qdownload ~/qdownloads cifs cred=~/cred,uid=abc,noauto 0 0

```

The noauto option means the mount will not be run from fstab.  You could create a script to execute the mount after checking for the nas availability that will mount the share without needing root abilities.

---

### Post by deckoff on 2011-10-25
Sorry for interrupting here. I have a similar question and thought about posting a theme - I want to find the best way to mount my NAS drive to my laptop. It is mounted most of the time, but sometimes the laptop is on the go. my only problem is that when I am on the go, Krusader and nautilus hang when trying to access the drive. Up till now, I used wicd(in Kubuntu 11.04) to run a post-connect and pre-disconnect scripts for the specific connections. It worked well, but wicd is too buggy now in 11.10 and I thing it breaks hibernation...

this is the script I used to run

```

sudo mount -t cifs //192.168.1.106/Public /media/MyBookLive -o username=******,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777,soft,user,noperm

```

Any ideas how to make this mount when reachable , and not hang when not  are welcome :)
If this post not for here, please delete it.
Strangely, this problem has been around for years, with no good solution.
thank you

---

### Post by capscrew on 2011-10-25
> **deckoff said:**
> Sorry for interrupting here. I have a similar question and thought about posting a theme - I want to find the best way to mount my NAS drive to my laptop. It is mounted most of the time, but sometimes the laptop is on the go. my only problem is that when I am on the go, Krusader and nautilus hang when trying to access the drive. Up till now, I used wicd(in Kubuntu 11.04) to run a post-connect and pre-disconnect scripts for the specific connections. It worked well, but wicd is too buggy now in 11.10 and I thing it breaks hibernation...

this is the script I used to run

```

sudo mount -t cifs //192.168.1.106/Public /media/MyBookLive -o username=******,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777,soft,user,noperm

```

Any ideas how to make this mount when reachable , and not hang when not  are welcome :)
If this post not for here, please delete it.
Strangely, this problem has been around for years, with no good solution.
thank you

You are right, you should should start you own thread.

---

### Post by Don Giovanni on 2011-10-25
> **capscrew said:**
> You could create a script to execute the mount after checking for the nas availability that will mount the share without needing root abilities.

With your help I have achieved exactly what I needed (I'm 100% from Terminal now :D), so unless I stumble across a link detailing how to create such a script I think I'll leave well enough alone.

Thanks again!

---

