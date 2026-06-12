---
title: "How to playback videos through a network?"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by nessus on 2006-07-02
I have ubuntu installed on one PC, and have some video files on the other pc which is a window os across the network.

i can use "file browser" browse throuhg the network and access all the shared files on this windows machines just fine. but i can't get my ubuntu to play video directly from that windows PC.

i use mplayer for example, and i guess it doesnt recognize the smb:/ protocol? do i need to some how mount the network shared folders so that linux can treat them "locally", i dont know if the idea is correct here, plz help.

and also anothe quick question, since mplayer is not a default media player in ubuntu, can i associate the video/audio file extensions to mplayer in ubuntu? so next time i just need to dould-click the video/audio file and mplayer will pop in and play?

thank you in advance!!

---

### Post by MacLeod_1980 on 2006-07-03
This is exactly the question I want to ask. I am having a problem playing movies from my samba share on my Windows desktop, using VLC. I have mounted the drive in which the video files exist, I have even copied some of the files over to see if VLC can infact play them... and it can - so I am doing something wrong, or even less likely - VLC isn't set-up right??? Any help with this problem would be great.

---

### Post by MacLeod_1980 on 2006-07-05
Ok I found a couple of solutions from searching and from help from a friend.

 If you open file with vlc and actually write the location of the file it will play... but this is a bit of a hassel.

So I found another solution to mount the share locally I guess
[http://ubuntuforums.org/showthread.php?t=208863&highlight=vlc+samba](http://ubuntuforums.org/showthread.php?t=208863&highlight=vlc+samba)

---

### Post by chris1112 on 2006-07-06
I am trying to do this also but I haven't had any luck with the examples given. Has any one got videos to stream?

---

### Post by MacLeod_1980 on 2006-07-06
I have got the videos to stream. Tell me what you have tried and what you have achieved... error messages would be helpful - as you can see I am not an expert but I'll try to help.

---

### Post by chris1112 on 2006-07-06
First I must say that I am new to Linux. With that said, after going to the link above and trying to make a directory I ran into the problem creating a folder call videos.

chris@chris-laptop:~$ mkdir -p /mnt/server/videos
mkdir: cannot create directory `/mnt/server': Permission denied
chris@chris-laptop:~$

I have a feeling that I need to be in a different user account but not sure how to get there.

---

### Post by chris1112 on 2006-07-06
Ok I think I am on the right track I changed to root and did not get a error when making the folder. However I am lost at how you mount the drive.




 chris@chris-laptop:~$ sudo -s -h
sudo: Only one of the -e, -h, -k, -K, -l, -s, -v or -V options may be used
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
chris@chris-laptop:~$ sudo -s
Password:
root@chris-laptop:~# mkdir -p /mnt/server/videos
root@chris-laptop:~# mount -t smbfs -o //Windows Network/home /mnt/server/videos
mount: wrong fs type, bad option, bad superblock on Network/home,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@chris-laptop:~# mount -t smbfs -o username=MyWindowsUser,password=MyWinPasswd //ServerName/ShareName /mnt/server/videos
mount: wrong fs type, bad option, bad superblock on //ServerName/ShareName,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@chris-laptop:~#

---

### Post by MacLeod_1980 on 2006-07-07
I think part of your problem is that you need to install smbfs. It doesn't understand the type argument (-t) smbfs so that is probably part of your problem. Also you initially specified an option argument (-o) but had no options. If you check synaptic (system - preferences - synaptic) - search for smb or samba, you will find the package/packages you need. It may just be...

**sudo apt-get install smbfs**

I think you also have problems with your share name... you don't need to explicitly list Window Network, and I also FYI linux doesn't handles spaces well.

For example my computer is called marvin so the correct way for me to enter the command is

**mount -t smbfs //marvin/movies /mnt/share/movies**

NOT mount -t smbfs //Windows Network/HOME/marvin/movies /mnt/share/movies

You have correctly created the directories in the /mnt/ folder though.

Now I don't need username and password option so there is no -o argument. I don't require username and password to access my shares on my network.

Once you get this working you will want to put the info in /etc/fstab (file system table) file so it mounts automatically at boot.

I will tell you how to do that once we get this problem sorted, it is entered slightly different.

Just to show my reasoning on your comman.. remember I'm no expert either, but as I understand.
> root@chris-laptop:~# mount -t smbfs -o //Windows Network/home /mnt/server/videos  > mount: wrong fs type, bad option, bad superblock on Network/home, missing codepage or other error It doesn't understand smbfs cause the protocol is not installed - I think. Bad option because you didn't specify an option, you wrote your network location instead, you don't need the Microsoft Network . What your telling it is that //Windows is the option and that the remote location is Network/home which it can't find - bad superblock I guess???

P.S
To change user you don't need to do **sudo -s** you can just type **su**. Also I wouldn't enter as root when your trying stuff out just incase so if you need to be root for a command, just type **sudo** infront of it. So to make a folder you could just type **sudo mkdir -p /mnt/server/videos**

---

### Post by chris1112 on 2006-07-08
When I went to get smbfs from the synaptic package manager and I got this error message.

smbfs:
  Depends: samba-common (=3.0.14a-6ubuntu1) but 3.0.22-1ubuntu3 is to be installed

So I tried to run it from the command line and i get the same thing 


chris@chris-laptop:~$ sudo apt-get install smbfs


Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  smbfs: Depends: samba-common (= 3.0.14a-6ubuntu1) but 3.0.22-1ubuntu3 is to be installed
E: Broken packages
chris@chris-laptop:~$

Any ideas

---

### Post by MacLeod_1980 on 2006-07-08
I guess you are missing some other packages. The ones I think you need are...

[B]libgnomevsf2-extra
libsmbclient
samba
samba-common
smbclient
smbfs[/B]

I have all these samba packages, and others, installed and mine works like a dream.

Read the description for each in synaptic, **samba** is probably the only one you will need to install - since the others, or most of the others are dependencies. So I would try and install samba first, as it should achieve what you need.
[B]
sudo apt-get install samba[/B]

or through synaptic.

---

### Post by koshari on 2006-07-08
i have found mounting a samba share with cifs to give better results.

---

### Post by chris1112 on 2006-07-09
Here is what i got when i tried to install from the command line


chris@chris-laptop:~$ sudo apt-get install samba
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.14a-6ubuntu1) but 3.0.22-1ubuntu3 is to be installed
         Depends: libcupsys2-gnutls10 (>= 1.1.23-1)
E: Broken packages
chris@chris-laptop:~$ sudo apt-get install samba
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
chris@chris-laptop:~$ sudo apt-get install samba
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
chris@chris-laptop:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.14a-6ubuntu1) but 3.0.22-1ubuntu3 is to be installed
E: Broken packages
chris@chris-laptop:~$  sudo apt-get install 6ubuntu1
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package 6ubuntu1
chris@chris-laptop:~$ sudo apt-get install 1ubuntu3
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package 1ubuntu3
chris@chris-laptop:~$

I get the same thing from the GUI installers 

= 3.0.14a-6ubuntu1) but 3.0.22-1ubuntu3 is to be installed

---

### Post by MacLeod_1980 on 2006-07-09
I am afraid I am at a loss, you should see what more experienced users are saying. If you do find the answer I would appreciate you posting it here also. Also make sure when you are doing any installation work, you are only using one way terminal/synaptic. Trying to do things in both will create a conflict and you won't be able to proceed.

What is the result if you type **uname -a**

And have you updated your system recently?

I would check to see if you have any broken packages...
[B]
System - Administration - Synaptic[/B]
Choose **Custom** and check to see if there are any **Broken** - I imagine you can fix them by just reinstalling them.

---

### Post by chris1112 on 2006-07-11
Here is what I get when I tried uname -a

chris@chris-laptop:~$ uname -a
Linux chris-laptop 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686 GNU/Linux
chris@chris-laptop:~$

I do not have any broken packages


koshari

I installed cifs but it did not do much that I could tell. However I am no longer able to access the networked drive I now get a error message 

"smb:///" is not a valid location


I think I need to remount the drive but not sure how i did it the first time.

---

### Post by chris1112 on 2006-07-16
Ok, I finally got it to work. Here is what got me up and running.

The site 

[http://ubuntuguide.org/wiki/Dapper#How_to_remount_.2Fetc.2Ffstab_without_rebooting](http://ubuntuguide.org/wiki/Dapper#How_to_remount_.2Fetc.2Ffstab_without_rebooting)

The Code

sudo mkdir /media/sharename
sudo mount //192.168.1.101/E /media/sharename/ 

Than I Put this in to fstab and saved it 

 //192.168.1.101/E /media/sharename/ ntfs      0    0

I now can stream media over my home network. Thanks to everyone for helping me out now if i could just get my videos files to work.

---

### Post by MacLeod_1980 on 2006-07-16
Glad to here you got your problem fixed.

Your best bet is to install VLC. It come with a heap of codec and has never failed me. 

[VLC for Ubuntu]("http://www.videolan.org/vlc/download-ubuntu.html")

I had to all an additional repository to my list, which was...

**deb [http://nightlies.videolan.org/build/dapper-i386/](http://nightlies.videolan.org/build/dapper-i386/)**

The install guide is located [here]("http://nightlies.videolan.org/")!

---

