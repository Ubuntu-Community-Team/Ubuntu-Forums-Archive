---
title: "FTP Server Impossible?"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by Return Privacy on 2010-10-15
Hi All,
Why is there no FTP server setup for Ubuntu? All I can find is the command line type. I was able to set up Filezilla FTP server on windows xp with no problem. It had the screens where you just created the allowed users, and the directories and passwords. I tried to install proftpd and vsftpd on Ubuntu 10.04, and it is a nightmare to say the least. (Neither would work) I can't believe no one has made a FTP server for Ubuntu that you can "see" the program, and make the setup changes you need. Trying to do this from a command line is impossible, (for me at least).
 My network security camera uses FTP to send motion activated video clips on the home network. Right now, I have Filezilla FTP server setup on a windows xp computer, and the security camera sends the clips to that. I just want to put a FTP server on the Ubuntu 10.04 computer and have it receive the security video clips on there. That way I can get rid of the windows computer all together!
Does anybody know of an FTP server for Ubuntu, that is a real program that you use, and not a command line thing?
-thanks

---

### Post by bvanaerde on 2010-10-15
I'm using Gadmin-PROFTPD.
It's not perfect, but it does the job well.

This manual might help you installing and configuring it:
[http://n00bsonubuntu.com/content/install-gadmin-proftpd-ubuntu-1010-maverick-meerkat](http://n00bsonubuntu.com/content/install-gadmin-proftpd-ubuntu-1010-maverick-meerkat)

---

### Post by WG- on 2010-10-15
When you are on your desktop go to

locations->set up connection with server

You can connect to a ftp server.

---

### Post by dck_82 on 2010-10-15
ftp is possible

---

### Post by Return Privacy on 2010-10-17
Thanks bvanaerde,
I'll give that a try. I did already try PureFTPd server with puradmin the other night. 
For some reason, it won't authenticate the username of incoming connection attempts. 
I did everything in the how to, but still no go. I still can't believe that this is proving to be so difficult. I'm surprised someone hasn't made a simple FTP server install program that installs it with the GUI, and then just have you put in the details. I just need the FTP server to run on the Ubuntu 10.04, I don't need FTP client on it at all.

---

### Post by sgosnell on 2010-10-17
Filezilla for Linux is available.  I have it installed.  It's in the repos, and you can get it with either Synaptic Package Manager, apt-get, or aptitude.

---

### Post by Return Privacy on 2010-10-17
Bevanearde,
I just installed GADMIN_PROFTPD, and tried to follow the how to from the link you provided.
It installed fine, but when I tried to configure it, I got to the part where it asks for a directory,
and I picked one, but it wouldn't allow it. No matter what folder I picked, it refuses to let me 
set a directory. It keeps saying "null" in the box? I tried /home, /home/ftpusers, /media/Backups/ftp, nothing. I even tried to create a new folder in /home, and it still won't allow it. So, then I opened /etc/proftpd/proftpd.conf and tried to manually put in the directory name on line 81 (which is what the Gadmin was saying was the error) and it won't allow me. 
So, when I try to click on "activate" it gives the error that there is no directory, and can't activate. The status remains "deactivated". This is really weird? Why won't it allow me to select a directory to be used? Like I said, I tried everything and any directory, but no go?
-RP

---

### Post by Return Privacy on 2010-10-17
Sgosnell,
Are you sure about FIlezilla for Linux? All I could find was the client, not the server for linux.
I need the server, not the client. All I need to do is have Ubuntu 10.04 receive files through FTP.
?????

---

### Post by bvanaerde on 2010-10-18
> **Return Privacy said:**
> and I picked one, but it wouldn't allow it. No matter what folder I picked, it refuses to let me 
set a directory.
-RP

That's strange. I had the same problem with giving a description to users: it wouldn't let me fill something in. After a restart this worked though.
How come you can't edit the config file? What error did you get?

*Oh, and to the others responding: the OP is looking for an FTP server with gui, not an FTP client. FileZilla server is only available for Windows.*

---

### Post by Return Privacy on 2010-10-19
Hi bvanaerde,
I have attached a few pics of the error messages. No matter what directory I try to set, it won't accept it. When I try to press "activate" I get this message. It stays on "deactivated". 
Any help in getting this to work would be greatly appreciated! -Thanks

---

### Post by Return Privacy on 2010-10-19
Forgot to add this pic also, to my above post.

---

### Post by bvanaerde on 2010-10-19
Can you show the lines around line 109 of the file
/etc/proftpd/proftpd.conf

Have you edited this file manually?

---

### Post by Return Privacy on 2010-10-19
Here is a copy of the entire Proftpd.conf file. I copied and pasted it into an OpenOffice document. That way you can look at the whole file, and hopefully figure this out? -Thanks

---

### Post by Return Privacy on 2010-10-20
Hi again bvanaerde,

I have been googling info about getting an ftp server with GUI on Ubuntu, while trying to figure this GADMIN-PROFTPD server out. I came across an article on Ubuntu Forums (here) from back in 2006, and the guy was having the same problems. He ended up installing Wine, and installing bulletproof ftp server (windoze version) and he said it worked. So, I installed Wine, and then installed Filezilla FTP server (windoze version) and it actually is working. I can't believe it, but it's true. Now, I don't want to leave it this way, and have to use a "cough", "choke" "windoze" FTP program on my Ubuntu computer! 
I'm sure it is taking up a lot of resources to keep the "Wine" emulation and "windoze" FTP program running all the time. I would MUCH rather figure out how to get a Linux FTP server (with GUI) running correctly on my Ubuntu computer. I'm still stumped why GADMIN-ProFTPD server won't start / work? (and PureFTP server, CrossFTP server, Crush FTP server, and vsftpd server) (I've tried them all, and couldn't get any of them to work at all. I've spent a week on this with no results)

I'm hoping you can figure something out from the ProFTPD.conf file (document copy) that I posted here. I won't give up if you won't...lol
-Thanks

---

### Post by bvanaerde on 2010-10-20
I'll try to look at the log when I get home...
About using Wine: I don't think it'll use that much resources. Unless you noticed a big difference?

FileZilla server is quite good and easy to use, so I'm hoping that they'll release a linux version someday.

---

### Post by bvanaerde on 2011-01-02
Hmm, I seem to have forgotten about this thread.
Not sure when it happened, but my FTP server stopped working... so I looked for a newer version of Gadmin ProFTPd, which I found: gadmin-proftpd_0.4.0-2_amd64

Maybe this version is already available in the repositories for Maverick or Natty, but Lucid is stuck with v3.8 or something. Downloading the package for Ubuntu manually didn't work due to dependencies, but the Debian version seems to work great:

[http://ftp.debian.org/debian/pool/main/g/gadmin-proftpd/](http://ftp.debian.org/debian/pool/main/g/gadmin-proftpd/)

What I did was completely remove the previous version, deleted the config files, and started over. Before I knew it, it was working better than ever.

---

