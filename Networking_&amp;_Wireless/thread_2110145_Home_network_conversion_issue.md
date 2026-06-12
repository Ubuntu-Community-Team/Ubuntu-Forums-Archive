---
title: "Home network conversion issue"
date: 2013-01-29
forum: Networking &amp; Wireless
---

### Post by cscj01 on 2013-01-29
I have had a home network set up with an Ubuntu PC (which I'll call PC1) and an XP PC (which I'll call PC2) using a router and wired connection and Samba.  I am currently running Ubuntu 12.04 on PC1, and I have just added Ubuntu 12.04 to PC2 in a dual boot configuration.  My problem is I can't figure out how to share the same files/drives I was sharing before when PC2 is running Ubuntu (i.e., both PCs are running Ubuntu).

I was able to share the printer easily by adding a printer to PC2 under Ubuntu.  Ubuntu found the printer on PC1 when I selected Add under System Tools->System Settings->Printers.  However, when I specify share options for the folders/drives on PC2, I cannot access them on PC1.

The folders/drives on PC2 I want to share are in an NTFS file system, and PC1 thinks they are part of a Windows share even though I assigned the share options while in Ubuntu.  In fact when I go to Places->Network->CP2 (which is the name of PC2) on PC1, I can see all the folders/drives in Nautilus that I shared, but they show as "Windows shares on CP2."  If I try to open or mount them, I get a message saying "**Unable to mount location** Failed to mount Windows shares"

I still have the Samba setup I had before in case PC2 is booted to XP.

I have Ubuntu 12.04 x64 on PC1 and Ubuntu 12.04 x32 on PC2.

[LIST=1]
[*]Is the problem with the fact I am trying to share NTFS folders/drives?  [*]Or because the Samba configuration is still active on PC1?  [*]How can I share these folders/drives when both PCs are running Ubuntu?  [*]If the Samba configuration is confusing the issue, what do I do with it so that it is there if PC2 is running XP?[/LIST]

---

### Post by craigcrawford114 on 2013-01-29
I had this problem a while back and couldn't find any good answers so I decided to work it out for myself. Here's a little thing I wrote on how I setup machines on my network for 12.10 (maybe it will help you?):

**BE SURE TO ADAPT THIS PROPERLY FOR YOUR NETWORK AND/OR FILES**

Install required software:
```
sudo apt-get update
sudo apt-get install cifs-utils libpam-mount
```

Edit /etc/security/pam_mount.conf.xml:
```
gksudo gedit /etc/security/pam_mount.conf.xml
```
Add:
```
<volume
	fstype="cifs" mountpoint="~/.network/%(USER)"
	server="storage" path="%(USER)"
	options="uid=%(USER),dir_mode=0700,file_mode=0600,nodfs,noperm"
/>
<volume
	fstype="cifs" mountpoint="~/.network/Media"
	server="storage" path="Media"
	options="uid=%(USER),dir_mode=0700,file_mode=0600,nodfs,noperm"
/> 
<volume
	fstype="cifs" mountpoint="~/.network/Admin"
	server="storage" path="Admin"
	options="uid=%(USER),dir_mode=0700,file_mode=0600,nodfs,noperm"
>
	<sgrp>sudo</sgrp>
</volume>
```

Edit /etc/profile:
```
gksudo gedit /etc/profile
```

Add:
```
if [ "$USER" != 'root' ]; then
# User profile setup
# Variables
XDG_UDU=/usr/bin/xdg-user-dirs-update
GVFS_SA=/usr/bin/gvfs-set-attribute

# Remove redundant stuff
rmdir ~/Documents ~/Music ~/Pictures ~/Videos ~/Public
rm ~/examples.desktop
rm -R ~/"Ubuntu One"

# Change user folder permissions
chmod 0700 /home/$USER

# Create softlinks
ln -sf ~/.network/$USER/Documents ~/Documents
ln -sf ~/.network/$USER/Music ~/Music
ln -sf ~/.network/$USER/Pictures ~/Pictures
ln -sf ~/.network/$USER/Videos ~/Videos
ln -sf ~/.network/Media ~/Media
if grep -qs /home/$USER/.network/Admin /proc/mounts; then
ln -sf ~/.network/Admin ~/Admin
fi

# Set up folder icons
$GVFS_SA -t string ~/Documents metadata::custom-icon 	file:///usr/share/icons/Humanity/places/64/folder-documents.svg
$GVFS_SA -t string ~/Music metadata::custom-icon 	file:///usr/share/icons/Humanity/places/64/folder-music.svg
$GVFS_SA -t string ~/Pictures metadata::custom-icon 	file:///usr/share/icons/Humanity/places/64/folder-pictures.svg
$GVFS_SA -t string ~/Videos metadata::custom-icon 	file:///usr/share/icons/Humanity/places/64/folder-videos.svg

# Set up XDG
$XDG_UDU --force --set DOCUMENTS $HOME/Documents
$XDG_UDU --force --set MUSIC $HOME/Music
$XDG_UDU --force --set PICTURES $HOME/Pictures
$XDG_UDU --force --set VIDEOS $HOME/Videos
fi
```

Just a little note: If you're sharing files between two Linux clients it might be better to use NFS rather than Samba.

---

### Post by cscj01 on 2013-01-30
Craig,

Thanks for your reply.  I took a look at NFS and think that is a better way to go.  I have one question though.  If I have folders/drives I want to share on more than one PC, do I need to install both server and client pieces on all the PCs?  From the explanations found here [https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo"), I believe this is the case.

---

### Post by craigcrawford114 on 2013-01-30
Yes, you need to install the server for each PC hosting files and the client on any PC that requires access to files.

It might be best to consider setting up a cheap server to centrally host all your content, I do and it's the best thing I've ever done :).

---

### Post by cscj01 on 2013-01-31
Okay, I followed the instructions given here: [https://help.ubuntu.com/community/NFSv4Howto]("https://help.ubuntu.com/community/NFSv4Howto").

When I issue the command ```
sudo mount -t nfs4 -o proto=tcp,port=2049 nfs-server:/ /mnt
```I get the message ```
mount.nfs4: Failed to resolve server nfs-server: No address associated with hostname
```I searched for the message with Google, but there is only one where the distro is Ubuntu.  That one doesn't give an answer to why the share will not mount.

Any thoughts?

---

### Post by cscj01 on 2013-01-31
Well, I just substituted the IP address for the server in the mount command as follows```
sudo mount -t nfs4 -o proto=tcp,port=2049 192.168.1.143:/ /mnt
```
and it mounts.  Is there a name I can use rather that an IP address?

---

### Post by steeldriver on 2013-01-31
if you have the avahi service running, then you should be able to use the *hostname*.local form, e.g. for me this works

```
$ ping -c4 nas-01.local
PING nas-01.local (192.168.1.127) 56(84) bytes of data.
64 bytes from nas-01.local (192.168.1.127): icmp_req=1 ttl=64 time=0.983 ms
64 bytes from nas-01.local (192.168.1.127): icmp_req=2 ttl=64 time=0.971 ms
64 bytes from nas-01.local (192.168.1.127): icmp_req=3 ttl=64 time=0.959 ms
64 bytes from nas-01.local (192.168.1.127): icmp_req=4 ttl=64 time=5.98 ms

--- nas-01.local ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 0.959/2.225/5.989/2.173 ms

```

---

### Post by Morbius1 on 2013-01-31
I realize you've moved on to nfs but this is generally not a samba error:
 > If I try to open or mount them, I get a message saying "**Unable to mount location** Failed to mount Windows shares"It's a Linux permissions error. It's not that it can't find it it's that it literally cannot mount it. Either the path to the NTFS directory does not allow the smb / samba client to traverse the directory or it doesn't exist. Take a look at the permissions on all the folders to the shared folder to find out.

---

### Post by cscj01 on 2013-01-31
Thanks to everyone.  I now have it working using using host names.  I also cleared up the samba share issue somewhere, but I can't say where, because I don't know what I did to fix that.  Thanks again.  I'll close this now.

---

