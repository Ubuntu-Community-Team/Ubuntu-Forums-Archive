---
title: "Trying to share files and printer between a windows XP and dapper computer"
date: 2006-05-18
forum: Networking &amp; Wireless
---

### Post by racermike1967 on 2006-05-18
Hello.

I am trying to share files between a windows XP desktop and a ubuntu dapper laptop.  Both computers connect to the internet via a D-Link DI 614+ wireless router.  The desktop is connected with an ethernet cable and the laptop is connected through a wireless connection.

I hear that Samba is what people use to do what I am asking but I am not sure how to set Samba on my laptop.  Even if I am able to install samba on my ubuntu laptop, what should I do on my windows XP desktop?  What are the steps I should take?  

Is there an easier way to transfer files between the two computes as well as being able to share a printer currently connected to the windows XP desktop?

Help is very much appreciated.

---

### Post by Falados on 2006-05-18
You heard correctly, Samba is the way to go.  There are a few tutorials online.
This is the one I used my first time:

[http://samba.netfirms.com/](http://samba.netfirms.com/)

You could also try setting up an FTP Server on your linux box.  Not only is the protocol universal, but it has the added bonus of being more secure than straight SMB (Seeing as how you are forced to log in and all..)

---

### Post by olsonar on 2006-05-18
for samba, just do a:

```
sudo apt-get install samba
```

pcworld has a guide for cross-platform networking here: [http://www.pcworld.com/howto/article/0,aid,122932,00.asp]("http://www.pcworld.com/howto/article/0,aid,122932,00.asp")

let me know if you need any more help.

---

### Post by Iowan on 2006-05-18
Try a **Search** for **Samba** or **share files** on the forum and the wiki.  The topic has come up a number of times, and are covered in much greater depth  than needs repeated.
Here's one:
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=samba&fullsearch=Text]("https://wiki.ubuntu.com/?action=fullsearch&context=180&value=samba&fullsearch=Text")
And another:
[http://ubuntuforums.org/search.php?searchid=5420726]("http://ubuntuforums.org/search.php?searchid=5420726")

---

### Post by jpkotta on 2006-05-18
Printers are easy.  You shouldn't even have to install Samba (because Samba client is installed by default, I think).  Enable the printer to be shared on the Windows computer in the control panel.  In Ubuntu, System -> Administration -> Printers, and add a new printer.  You should choose a Samba network printer.  The rest is pretty self explanatory.  If you don't see the exact printer you have in the list, try one that is similar, and it will probably work.

I prefer sftp (in the form of WinSCP) to transfer files from Linux to Windows.  It is more secure than even ftp, because it is encrypted, but mainly I just like WinSCP.

---

### Post by it.henrik on 2006-05-19
[QUOTE=Falados]
You could also try setting up an FTP Server on your linux box.  Not only is the protocol universal, but it has the added bonus of being more secure than straight SMB (Seeing as how you are forced to log in and all..)[/QUOTE]

[QUOTE=jpkotta]
I prefer sftp (in the form of WinSCP) to transfer files from Linux to Windows.  It is more secure than even ftp, because it is encrypted, but mainly I just like WinSCP.[/QUOTE]

one of the main reason why you should use ssh instead of ftp is that in ftp your password is sent in CLEARTEXT .. anyone listening on your traffic (wireless you say..) can read your login and pasword. 

As an opensource alternative to winscp I can recomend filezilla for windows :)
If you are going for ssh then I can really recommend that you have a look at sshfs :) this tool have saved me so much time

---

### Post by Quintin Riis on 2006-10-18
> **Falados said:**
> You could also try setting up an FTP Server on your linux box.  Not only is the protocol universal, but it has the added bonus of being more secure than straight SMB (Seeing as how you are forced to log in and all..)
Totally wrong.  FTP logins are done in clear-text, while smb logins are encrypted, by default.  That's just one point.

sftp?  sshfs?  I do not think that these are the best solutions for home users.

To install and configure samba in five minutes...

Open a terminal and type 'sudo apt-get install samba'.  Once that is finished do a 'sudo apt-get install smbclient'.

You will need to edit /etc/samba/smb.conf.  Scroll down until you find '[homes]'.  It is probably commented out by default.  Uncomment it, and be sure to also set it to be readwrite instead of read-only.  Also make it browseable.  Also recommend enabling the WINS server, and setting os level to 65.

Passwords hashes are stored differently between windows and unix, so if you want authentication to 'just work', you will need to have user accounts with the same name on each machine, and you will need to put in your windows password with 'sudo smbpasswd -a <user>'.

Home shares work 'automagically' after doing the above, i.e. all users will be able to access their home directory on the ubuntu machine without being challenged for Windows credentials..  If you need / want other shares, smb.conf includes several examples that you can look at.

---

