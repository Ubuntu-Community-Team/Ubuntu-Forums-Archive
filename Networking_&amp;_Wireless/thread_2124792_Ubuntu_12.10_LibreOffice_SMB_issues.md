---
title: "Ubuntu 12.10 LibreOffice SMB issues"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by svenole on 2013-03-12
Hello. 

I've been using Ubuntu for years in my office environment which is mainly a Windows environment and am now on 12.10. The combination Ubuntu, SMB and LibreOffice has been working like a charm for years. However, now both 12.10 default LibreOffice version and the latest 4.0 version, do not work on files stored on SMB shares. This is a very annoying situation forcing me into other desktop environments to do my work. It is very odd that both Ubuntu and the LibreOffice developers introduce versions of software with serious issues like this. So the question is if there exists a workaround for this issue? The next question is if anybody know when there is there is supposed to be issued a fix for this?

- Sven

---

### Post by Toz on 2013-03-12
> **svenole said:**
> do not work on files stored on SMB shares. 
Can you be a little more specific as to what the issue is? Libreoffice 4.x and SMB shares are working fine here with *buntus 12.04/12.10/13.04.

---

### Post by svenole on 2013-03-12
Hmm.. 

When using default Libreoffice that follows Ubuntu 12.10 (now 3.6.2.2) it is possible to open files on SMB shares, but it is not possible to save them. This creates an error message telling that file does not exist and/or general IO error. If running LibreOffice 4.0, the application just hangs when trying to open or save a document to a SMB share and the process stays in limbo until reboot. It is not possible to kill it off and it is not possible to access Libreoffice until reboot. This is 12.10 using standard Windows file server (Windows 2008 I think). Now, I would be really surprised if you can get Libreoffice 4.x to work on SMB shares since the release notes specifically says that SMB access is broken... Maybe it has been fixed in an update?

---

### Post by 88weighed on 2013-04-11
I have the same issue here, running 12.04.2 with LibreOffice 4.0.2. Seems to an issue in LO4.

---

### Post by 7horses on 2013-04-23
Same issue here. Ubuntu 12.10 with standard libreoffice 3.6.2.2
Opening a text document on same samba share with an other editor works ok. Must be a libreoffice problem.

---

### Post by Morbius1 on 2013-04-23
By my recollection this has gone on for years now. 

Is the problem with LibreOffice? Yes.
Is the problem with gvfs? Yes.
Does the problem exist when you use another editor? No.

Will these two children ever work out their differences? Without adult supervision it doesn't seem likely.

I'm guessing most of you folks are mounting the share through Nautilus. That invokes gvfs and that's where the problem begins. Mount it the way your grand pappy mounted a remote share:

Create a mount point:
```
mkdir /home/morbius/NetShare
```
Make sure you have cifs installed:
```
sudo apt-get install cifs-utils
```
Mount the remote share:
```
sudo mount -t cifs //192.168.0.100/share-name /home/morbius/Netshare -o dir_mode=0777,file_mode=0666,nounix,nobrl
```
Edit and try to save a document on the remote share.

---

### Post by Toz on 2013-04-23
There is a bug report for this [here]("https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1069757").  According to comment #44, the bug has been fixed in version 4.0.2 packaged in [this]("https://launchpad.net/~libreoffice/+archive/libreoffice-4-0") PPA.

---

### Post by josephpmh on 2013-05-06
> **Toz said:**
> There is a bug report for this [here]("https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1069757").  According to comment #44, the bug has been fixed in version 4.0.2 packaged in [this]("https://launchpad.net/~libreoffice/+archive/libreoffice-4-0") PPA.

My fstab automounts via cifs 

//192.168.1.14/Folder	/media/Folder	cifs    credentials=/home/.WinCred,file_mode=0777,dir_mode=0777   0       0

and still I can't save to a share.  

And now, it won't even save to Documents in /home/user folder.  I'm using 4.0.2.2.

---

