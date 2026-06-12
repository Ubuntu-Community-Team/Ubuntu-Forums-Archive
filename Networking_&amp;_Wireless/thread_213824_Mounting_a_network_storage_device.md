---
title: "Mounting a network storage device"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by aleska on 2006-07-11
Looked at many forum postings on this subject, and used Google to search my error messages, but having no luck.

Background: totally new to Linux (3 day newbie).  Running Ubuntu 6.06...working great so far.  I also have a home network, with a couple Windows boxes, and a network storage device (a buffalo link station) which contains all my music files, pictures, etc.

Using nautilus, I can find my linkstation very easily.  It's under a Windows Network -> Workgroup -> LINKSTATION1.  If I double click the linkstation1, I find the folder "share" listed as a x-directory/smb-share.  I can even go in to that, find my music files, click on a music file and open with Rythmbox, and it plays just fine.  

But I can't seem to mount!!!

I don't have any user name password protection on the Linkstation storage device.  
When I do the following...
```
aleska@ubuntu-desktop:~$ sudo mount -t smbfs //linkstation1/share/Music /mnt/server/music 
```
It makes me enter the password twice, then it responds with, 
> 13098: session setup failed: ERRSRV - ERRbadpw (Bad password - name/password pair in a Tree Connect or Session Setup are invalid.)
SMB connection failed
Thinking that maybe I need to designate that I'm a guest and no password is required, I've also tried, 
```
aleska@ubuntu-desktop:~$ sudo mount -t smbfs -o guest //linkstation1/share/Music /mnt/server/music 
```
The response is, 
> Anonymous login successful
13129: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed


Any thoughts on what I should try next?
Thanks in advance!
-Aleska

---

### Post by tturrisi on 2006-07-12
Seems to me that if you can browse & open files on the net drive then it is already mounted!  What are you trying to accomplish?  See thsi section:
[http://ubuntuguide.org/wiki/Dapper#Networking](http://ubuntuguide.org/wiki/Dapper#Networking)

---

### Post by aleska on 2006-07-12
From everything I'm reading, just b/c one can access a network file through smb, doesn't mean it's mounted.  The link you reference even has subsections titled, **"How to access network folders without mounting"** and **"How to mount/unmount network folders manually, and allow all users to read"**.

Problem is that if it isn't mounted, then many programs won't allow you to use them to play.  For instance, while Rhythmbox may allow you to play, others such as Banshee won't.  Same goes for some of the video players.  Rather than sticking to programs that happen to allow access through "smb://xxxx", I want to choose programs I like most by mounting so its local.   

Problem is, that all these tutorials and forum threads that discuss how to mount aren't working for me.  I'm getting the ERR messages I listed in my initial post.  When I follow the instructions in the section on mounting that you linked, again, it no worky.  

Hope that explains my sitaution better.  Thanks for the clarifying question.
Thoughts?
-Aleska

---

### Post by dasyar613 on 2006-07-12
Have you tried doing a connect to server from the places menu. I am curious to see if the log in window appears, and becomes non-functional, in other words does not accept anything that you type in.

---

### Post by aleska on 2006-07-12
Just tried it.  
The default service type selected was FTP, so I changed to Windows Share.  
I enter in my...
Server: linkstation1
Share: share
Folder: Music

and then leave User name: Domain name: and Name to use for connection: blank.

I hit Connect, and the screen goes away.  However, when I go back to Places, I now see that between Network servers and Connect to Server, Music on Linkstation1 appears with the little smb logo and pipe under the folder icon. 

So, was that a good sign?  Was that what you would have expected to happen?
-Aleska

---

### Post by dasyar613 on 2006-07-12
The new icon is basically a folder, so, in theory, you should be able to double click on that icon, and open the folder on that device. Hopefully that log in window will not open.

---

### Post by aleska on 2006-07-12
Yes, when I click it under places, it opens in nautilus without any login screen or error.  I can access the files through nautilus...again, problem remains that I can't mount it.

Incidentally, when I run ```
smbclient -L //linkstation1
```
 to see how things are set up, I get...
> 
Domain=[ATTBI] OS=[Unix] Server=[Samba 2.2.8a-ja-1.1]

        Sharename       Type      Comment
        ---------       ----      -------
        lp              Printer   Network Printer for Windows
        info            Disk      LinkStation information
        share           Disk      LinkStation Share Folder
Domain=[ATTBI] OS=[Unix] Server=[Samba 2.2.8a-ja-1.1]

        Server               Comment
        ---------            -------
        KITCHEN              Kitchen
        LINKSTATION1         LinkStation


I thought that maybe the problem was that it didn't like //linkstation1/share/Music as a share, and that maybe I needed to leave it at mounting //linkstation1/share Alas, same darn problem.
Is it possible that the linkstation is running a "bad" version of Samba that is preventing the mount???  

](*,)

---

### Post by dasyar613 on 2006-07-12
Ok, maybe I am missing something here, you said you can access the files, so doesn't that mean that the drive is mounted. Is their something else that you are not telling us.

---

### Post by aleska on 2006-07-12
That was the same question member tturissi had asked.  

I replied that from everything I'm reading, just b/c one can access a network file through smb://, doesn't mean it's mounted. Nautilus is "smart" enough to see the network folder, but other programs aren't.  They can only see it if its mounted.

Problem is that even if you can access your files through Places (nautilus), that doesn't mean the network folder you are accessing is mounted.  With music files, for instance, if the network folder that the music files are located under isn't mounted, then many programs won't allow you to use them to play. While Rhythmbox may allow you to play, others such as Banshee won't. Same goes for some of the video players. Rather than sticking to programs that happen to allow access through "smb://xxxx", I want to choose programs I like most by mounting the network folder with the media files, so its "local" and accessible to the programs I want to use (e.g. vlc).

Problem remains, that all these tutorials and forum threads that discuss how to mount a network folder aren't working for me. I'm getting the ERR messages I listed in my initial post.

Hopefully that explains the situation.  If based upon my description it is clear I'm missing something, then your advice or explanation is greatly appreciated.  Or, if I'm not missing something...that is, mounting a shared network folder is what I need to do to make those files accesible to ALL my programs, then advice on that is greatly appreciated (keeping in mind I've followed the steps listed in various threads on this forum).   

I appreciate all the help...thanks!!!
-Aleska

---

### Post by dasyar613 on 2006-07-12
Sorry, I missed the finer points of this thread. I guess what you want to do is to make your storage device appear to ununtu as a local device where it would have mount and unmount priviliges. Is their something on the storage device that would allow that, I am just making some wild guesses right now.
 
I do agree with you on the assertion that the help files are lacking. I can not add anything more.

---

### Post by aleska on 2006-07-12
***UPDATE 5-10-07 ***  Forget this advice...smbfs is depreciated and dmizer gives a great step by step how to get it working using [cifs instead of smbfs]("http://ubuntuforums.org/showthread.php?t=288534").  If you insist on using smbfs instead of cifs and you've got a linkstation, I guess what's listed below should continue to work. ***END UPDATE***

Hooraay!  For those of you interested, or who run into the same problem, this is how I was able to solve.
This post started me out in the right direction...
[https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28folder%29%7C%28mount%29%7C%28network%29#head-d14db9e44eb9655a6a09e2c8e936727115340a87]("https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28folder%29%7C%28mount%29%7C%28network%29#head-d14db9e44eb9655a6a09e2c8e936727115340a87")

So, while trying to mount my linkstation on the fly didn't work for me (no matter how I tried) I was able to mount by editing fstab and then running sudo mount -a.   

However, all was not right as I did run into a bit of a problem.  BTW - Any of you with Buffalo terastations or linkstations might find the same problem.  While my linkstation mounted...the folder and file names all came out garbledly gook (looked like japanese characters).  So, I made some tweaks to fstab...specifically, changed coding...
```
//linkstation1/share  /mnt/linkstation  smbfs  guest,uid=1000,iocharset=iso8859-1,codepage=cp850,cp850 	0	0
```
When I reran sudo mount -a, I still had the problem.  But, the windows user in me thought to restart the system and see if that helped.  It seems it did!!!  Wouldn't you know it...my linkstation is mounted and I can read the folders and file names just swell.

Thanks to all who posted in attempts to help me out.  I think I got lucky!!!  
-Aleska

---

### Post by eltech on 2006-07-12
Outstanding .. Worked great for what i wanted to do.

---

### Post by tturrisi on 2006-07-12
What's the dir structure of the net drive?  If I'm not mistaken, I believe you must mout dirs.  Or...The net server is basically "another computer on the network", therefore, the net drive name will be case sensitive & if no joy try using it's ip address instead of name.

---

### Post by tadtoll on 2006-11-03
> **aleska said:**
> Hooraay!  For those of you interested, or who run into the same problem, this is how I was able to solve.
This post started me out in the right direction...
[https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28folder%29%7C%28mount%29%7C%28network%29#head-d14db9e44eb9655a6a09e2c8e936727115340a87]("https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28folder%29%7C%28mount%29%7C%28network%29#head-d14db9e44eb9655a6a09e2c8e936727115340a87")

So, while trying to mount my linkstation on the fly didn't work for me (no matter how I tried) I was able to mount by editing fstab and then running sudo mount -a.   

However, all was not right as I did run into a bit of a problem.  BTW - Any of you with Buffalo terastations or linkstations might find the same problem.  While my linkstation mounted...the folder and file names all came out garbledly gook (looked like japanese characters).  So, I made some tweaks to fstab...specifically, changed coding...
```
//linkstation1/share  /mnt/linkstation  smbfs  guest,uid=1000,iocharset=iso8859-1,codepage=cp850,cp850 	0	0
```
When I reran sudo mount -a, I still had the problem.  But, the windows user in me thought to restart the system and see if that helped.  It seems it did!!!  Wouldn't you know it...my linkstation is mounted and I can read the folders and file names just swell.

Thanks to all who posted in attempts to help me out.  I think I got lucky!!!  
-Aleska

I did that and continued to have a problem with stalling for folders with a lot of files in them. I found mention here: 

[http://www.linuxquestions.org/questions/showthread.php?t=280936](http://www.linuxquestions.org/questions/showthread.php?t=280936)

about using "cifs" instead of "smbfs" in the fstab mount line, and now everything is working perfectly for me mounting my linkstation pro 250.

Mine now looks like this:

```
#linkstation NAS
//192.168.2.17/share  /mnt/nas  cifs  guest,uid=1000,iocharset=iso8859-1,codepage=cp850,cp850 	0	0
```

---

### Post by palladium on 2007-01-15
I was finding very slow transfer speeds to a LinkStation Pro network drive from a Toshiba Tecra M5 laptop. It would take about 7min to copy a 11Mb file when the drive was mounted using smbfs and about 1min to copy when cifs was used to mount. In contrast, I could use ftp to put the file to the NAS in about 1sec. 

I discovered that a desktop computer or a PCMCIA network card worked much better than the laptop’s internal network adapter. Eventually, I discovered that if I disabled PCI Express Link ASPM in the BIOS then the transfer speed jumped to about 5Mb per sec. I don’t know why this should be the case but I guess that this setting must interfere with the internal network adapter. 

I also found that I could mount the LinkStation Pro drive using 
```
sudo mount –t cifs –o guest //192.168.0.20/share /media/linkstation
``` 
This gave me read/write access. I did not need to use iocharset or codepage options. However, in the end I elected to mount the drive at boot by adding to /etc/fstab:
```
//192.168.0.20/share	/media/linkstation	cifs	guest,uid=1000	0	0
```

My system settings are:
320Gb LinkStation Pro connected to a ADSL router which assigns the NAS the IP 192.168.0.20
Ubuntu Linux 6.10 on a Tecra M5 laptop and Ubuntu 6.06 on a desktop. As I understand it, the network adapter of the laptop is a Intel Gigabyte that uses the e1000 driver in Ubuntu.

---

