---
title: "Local Home Dir Disappearing above NFS mounts"
date: 2013-06-13
forum: Networking &amp; Wireless
---

### Post by TiberiusT on 2013-06-13
[FONT=arial][COLOR=#000000]Gd day all,

I  have a home server and 5 clients. All Xubuntu 12.10x64. I use NFS for  all users to centralise their data on the server but I DO NOT NFS the  actual home dir, the ~/ , (maybe I can call this the root home dir?)  which contains all the config files for that user and his programs. I  kept that local bcos we use Shotwell  and Darktable which both read and write extensively to their config  files on ~/.config/shotwell and ~/.config/darktable. Darktable (an excellent RAW photo developer) especially  bogs down horribly if its config is on NFS. In fstab I then mount all  the data dirs (Documents/Videos/Pictures etc) under the users home dir  so everything appears local and the network is transparent. 

Server fstab example line ```
/home                /export/home      none    bind  0  0
```[/COLOR]
Server exports [/FONT][FONT=arial][COLOR=#000000]example line[/COLOR][/FONT][FONT=arial] ```
/export/home  192.168.1.1/24(rw,nohide,insecure,no_subtree_check,async)
```
Client fstab example ```
192.168.1.60:/home/tiberiust/Documents /home/tiberiust/Documents  nfs4 auto  0  0
```
[COLOR=#000000]But  I have the following recurring problem: Users randomly lose access to  their local root home dir. This also means ofc that any program accessing it’s config  files stored in the home dir also has a headfit - so it’s a fairly  catastrophic error. I followed [/COLOR][COLOR=#1155CC]_[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)_[/COLOR][COLOR=#000000]  during setup and everything is as basic as possible.

 I can’t narrow  down when exactly the home dirs disappear but when they do: In terminal I can’t ls ~/ . /bin/ls works however. Tyring to access as sudo also does not work.  sudo mount -a does nothing. The only remedy seems to be to reboot,  however sometimes waiting...and waiting can bring it back.[/COLOR] BUT - NFS itself is happy, users can always access all their data dirs as normal. I can also access the file system on the local disk without a problem. 

[COLOR=#000000]I  can post all config files if anyone can help but whilst troubleshooting  this I have seen posts saying ‘don’t mount NFS shares under frequently  used dirs’ (which is exactly what I am doing) but I can’t find any  official advice to this effect. Shouldn’t my setup just work?[/COLOR] 

TIA
T

[/FONT]

---

### Post by TiberiusT on 2013-06-18
I switched to using autofs as per this [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs) and researched a bit more. I found this thread especially useful:
[http://askubuntu.com/questions/292461/placing-home-directory-on-nfs-server](http://askubuntu.com/questions/292461/placing-home-directory-on-nfs-server). 

Autofs was very easy to setup and 3 days into the change and it's all working perfectly. Everything is much smoother than it was b4 and I haven't lost the home dir at all. NFS access is instantaneous on my little network. I shall remain in the dark about what went wrong with my previous setup but I won't lose any sleep over it...solved is solved :D

T

---

