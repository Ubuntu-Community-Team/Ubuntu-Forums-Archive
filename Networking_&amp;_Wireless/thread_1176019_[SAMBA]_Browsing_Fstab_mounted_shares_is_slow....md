---
title: "[SAMBA] Browsing Fstab mounted shares is slow..."
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by Menthu_Rae on 2009-06-01
**Edit2:** I *appear* to have solved it by changing from cifs to smbfs in fstab *ONLY* for the Server entries...

i.e.

```
//192.168.1.2/Storage2  /mnt/Server/O **cifs** credentials=/home/myusername/.smbpasswd,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

becomes...

```
//192.168.1.2/Storage2  /mnt/Server/O **smbfs** credentials=/home/myusername/.smbpasswd,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

Will post back if the problem still occurs...

-------------------------------------------------

Hi there,

I'll try to give as much information as possible, but I'm still a relative newbie to Ubuntu/Linux in general.

Here is my situation...

* Desktop PC (Jaunty 9.04, fully updated)
* Download PC (Hardy 8.04.2, fully updated)
* Server (Jaunty 9.04, fully updated)

I have enabled samba and all other required samba apps in order to share files between all 3 PC's. Everything was working flawlessly a few weeks ago, but now I'm having issues...

Here's my fstab:

```
# DownloadPC Shares

//192.168.1.4/seeding\040&\040torrents /mnt/DownloadPC/S cifs credentials=/home/myusername/.smbpasswd,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

//192.168.1.4/torrents /mnt/DownloadPC/T cifs credentials=/home/myusername/.smbpasswd,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

# Server Shares

//192.168.1.2/Misc  	/mnt/Server/M cifs credentials=/home/myusername/.smbpasswd,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

//192.168.1.2/Storage1  /mnt/Server/N cifs credentials=/home/myusername/.smbpasswd,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

//192.168.1.2/Storage2  /mnt/Server/O cifs credentials=/home/myusername/.smbpasswd,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

#//192.168.1.2/downloads  /mnt/Server/P cifs credentials=/home/myusername/.smbpasswd,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

Now, if I manually go to **Places --> Network --> Server --> |Share|** everything is super speedy and great.

However, if I go to **/mnt/Server/Share** then everything is slow. It takes about 4-5 seconds to show directory contents and sometimes even hangs nautilus.

What is weird, is if I do the same for the DownloadPC, then it's fine. Either using Network or /mnt/DownloadPC - they're both super fast and everything loads in an instant.

Note that it's not an HDD speed issue, the DownloadPC is actually using a slow 2.5" Laptop HDD, whereas the Server has top of the line Seagate 7200.11 and 7200.10 HDDs... and as I said, I had no issues before!

I have tried re-installing nautilus to no effect:

```
sudo aptitude purge nautilus && sudo aptitude install nautilus
```

So any help/suggestions are very welcome at this point! :(

**edit: Here's an output of smbtree...**

```
myusername@DESKTOPPC:~$ smbtree
Password: 
WORKGROUP
	\\SERVER         		SERVER server (Samba, Ubuntu)
		\\SERVER\print$         	Printer Drivers
		\\SERVER\Misc           	
		\\SERVER\Storage1       	
		\\SERVER\Storage2       	
		\\SERVER\IPC$           	IPC Service (SERVER server (Samba, Ubuntu))
	\\DESKTOPPC         		DESKTOPPC server (Samba, Ubuntu)
		\\DESKTOPPC\HL-2070N       	Brother HL-2070N
		\\DESKTOPPC\MX700          	Canon MX700 Series Printer
		\\DESKTOPPC\print$         	Printer Drivers
		\\DESKTOPPC\IPC$           	IPC Service (DESKTOPPC server (Samba, Ubuntu))
	\\DOWNLOADPC           		DOWNLOADPC server (Samba, Ubuntu)
		\\DOWNLOADPC\torrents       	
		\\DOWNLOADPC\seeding & torrents	
		\\DOWNLOADPC\PDF            	PDF
		\\DOWNLOADPC\print$         	Printer Drivers
		\\DOWNLOADPC\IPC$           	IPC Service (DOWNLOADPC server (Samba, Ubuntu))

```

---

### Post by dmizer on 2009-06-01
Well, that's extremely odd to me for a couple of reasons:

1) The actual SMBFS protocol hasn't been available in Ubuntu since Gutsy.
2) You're using CIFS options that don't work in SMBFS, so even if you had compiled and installed SMBFS (believe me, you'd remember if you did this) that mount command would cause an error.

So actually, even though your mount command says SMBFS, you're actually still using CIFS.

Do you have a firewall in place on either the server or the client?

---

### Post by Menthu_Rae on 2009-06-02
> **dmizer said:**
> Well, that's extremely odd to me for a couple of reasons:

1) The actual SMBFS protocol hasn't been available in Ubuntu since Gutsy.
2) You're using CIFS options that don't work in SMBFS, so even if you had compiled and installed SMBFS (believe me, you'd remember if you did this) that mount command would cause an error.

So actually, even though your mount command says SMBFS, you're actually still using CIFS.

Do you have a firewall in place on either the server or the client?

Hrmmm some interesting notes there... all I did to "fix" it was:

```
sudo gedit /etc/fstab
```

Changed 

```
//192.168.1.2/Storage2  /mnt/Server/O **cifs **credentials=/home/myusername/.smbpasswd,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

to

```
//192.168.1.2/Storage2  /mnt/Server/O **smbfs **credentials=/home/myusername/.smbpasswd,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

Saved and closed... then...

```
sudo mount -a
```

Now when clicking the mount location in the Nautilus bookmarks pane, it loads instantly... :KS

So yeah, if what you're saying is right - that's really odd! There's no firewall in place internally on my network... my modem/router deals with that.

When I get home again tonight I'll change it back to cifs and run the mount -a command again...

Thanks for your help, will keep this thread updated.

---

### Post by dmizer on 2009-06-02
Please do, because if what you say is true, then this /may be/ a bug.

Edit:
Before attempting the mount with cifs again, please run this command:
```
sudo apt-get install smbfs
```

After reading some man pages, it seems as though the smbfs type is handled by smbmount which may explain the oddness. By installing the smbfs metapackage, you'll also install the cifs protocol. Jaunty comes with CIFS by default, but it's a stripped down protocol to provide for Samba functionality in Nautilus, so unless you explicitly install smbfs, you may experience difficulty.

---

### Post by Menthu_Rae on 2009-06-02
> **dmizer said:**
> Please do, because if what you say is true, then this is a bug.

Edit:
Before attempting the mount with cifs again, please run this command:
```
sudo apt-get install smbfs
```

After reading some man pages, it seems as though the smbfs type is handled by smbmount which may explain the oddness. By installing the smbfs metapackage, you'll also install the cifs protocol. Jaunty comes with CIFS by default, but it's a stripped down protocol to provide for Samba functionality in Nautilus, so unless you explicitly install smbfs, you may experience difficulty.

I just SSH'd in back home to check that I did actually have smbfs installed (like I said in my first post I did install all the relevant samba stuff) and it is:

```
username@Server:~$ sudo apt-get install smbfs
[sudo] password for username: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
smbfs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

So yeah, that's in place... anyway will post back later tonight. Cheers for keeping an eye on this. ;)

---

### Post by Menthu_Rae on 2009-06-02
OK, the plot thickens...

I went home, edited /etc/fstab back to CIFS... then ran sudo mount -a again...

Clicked on the bookmark in nautilus sidebar, and it's... **fine!**.

So yeah... the issue seems to have been cleared up perhaps by nothing to do with smbfs/cifs, but by re-mounting the shares (mount -a)... odd.

Will keep an eye on it over the next few weeks and post back here again if any further problems occur.

Thanks for the help. ;)

---

