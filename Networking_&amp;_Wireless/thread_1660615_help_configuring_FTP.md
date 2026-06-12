---
title: "help configuring FTP"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by Ceiber Boy on 2011-01-05
Hello 

I have Ubuntu server 10.10 with vsftp installed, i have no GUI but am generally comfortable using the command line.

I'm attempting to set up a ftp site where various people can log onto their own folder using a user name and password, these folders must be isolated from each other and one must be able to upload to them. Effectively creating an electronic drop box.

I've looked around by googling and found many tutorials that I've tried to follow, unfortunately each has lacked specific elements that I've needed, I have tried to combined elements of most of them to try and get to what I'm looking for but i have now become frustrated and feel at a dead end.

Could someone please walk me through in baby steps (as i'm not taking anything for granted), or point me to a known good working tutorial (with modification where necessary to achieve my specification). I appreciate this is a bit of an ask but really feel at a dead end after trying for so long.

Many Many Thanks.

---

### Post by PatchesTheCaveman on 2011-01-05
If these connections are taking place over the Internet, you probably **do not** want to use FTP.  FTP transmits everything in cleartext over the Internet so it is trivial for even the dumbest "hacker" to intercept usernames and passwords and gain access to your server.

You probably want to use SFTP, which allows for secure file transfers over an encrypted SSH tunnel.  To do that, all you have to do is install the SSH package:
```
sudo apt-get install ssh
```

Then, create a user account on the server for each user:
```
sudo useradd bob
```

Set their password:
```
sudo passwd bob
```

If you want their home directory to exist somewhere other than /home, change it using this command:
```
sudo usermod bob -d /dropboxes/bob
```

Then, create their home/dropbox directory and set the appropriate permissions on it:
```
sudo mkdir /home/bob
sudo chown bob /home/bob
sudo chmod 700 /home/bob
```

If you don't want users to be able to login and get a shell on the server (even though they won't have administrator rights), change their shell to /sbin/nologin:
```
sudo chsh -s /sbin/nologin bob
```

Then they can point any SFTP enabled client to your server and only be able to access files in their /home directory.  Most FTP clients have support for SFTP these days.  FileZilla is a good free one for Windows and Linux.  You can also use the *sftp* command from the the Linux shell.

If you must use insecure plain FTP, you can probably do something similar with vsftpd.  I believe there's a /etc/ftp_users file or some-such that gives users the ability to access their home directories via FTP.  But I haven't used FTP in several years now.

---

### Post by Ceiber Boy on 2011-01-07
> **PatchesTheCaveman said:**
> If these connections are taking place over the Internet, you probably **do not** want to use FTP.  FTP transmits everything in cleartext over the Internet so it is trivial for even the dumbest "hacker" to intercept usernames and passwords and gain access to your server.

You probably want to use SFTP, which allows for secure file transfers over an encrypted SSH tunnel.  To do that, all you have to do is install the SSH package:
```
sudo apt-get install ssh
```Then, create a user account on the server for each user:
```
sudo useradd bob
```Set their password:
```
sudo passwd bob
```If you want their home directory to exist somewhere other than /home, change it using this command:
```
sudo usermod bob -d /dropboxes/bob
```Then, create their home/dropbox directory and set the appropriate permissions on it:
```
sudo mkdir /home/bob
sudo chown bob /home/bob
sudo chmod 700 /home/bob
```If you don't want users to be able to login and get a shell on the server (even though they won't have administrator rights), change their shell to /sbin/nologin:
```
sudo chsh -s /sbin/nologin bob
```Then they can point any SFTP enabled client to your server and only be able to access files in their /home directory.  Most FTP clients have support for SFTP these days.  FileZilla is a good free one for Windows and Linux.  You can also use the *sftp* command from the the Linux shell.

If you must use insecure plain FTP, you can probably do something similar with vsftpd.  I believe there's a /etc/ftp_users file or some-such that gives users the ability to access their home directories via FTP.  But I haven't used FTP in several years now.

Thank you, i'm able to user Filezilla on the main admin account but for the 'bob' account i keep getting this message

Status:    Connecting to 192.168.1.154...
Response:    fzSftp started
Command:    open "bob@192.168.1.154" 22
Command:    Pass: ****
Error:    Authentication failed.
Error:    Critical error
Error:    Could not connect to server

i guessing it has something to do with the permissions in the Ubuntu server!?

---

### Post by PatchesTheCaveman on 2011-01-07
Did you use the *chsh* line to disable shell access?  Apparently you have to set that to something specific to make SFTP still work.  Sorry about that.  

Run this command to change the shell to the appropriate command:
```
sudo chsh -s /usr/lib/openssh/sftp-server bob
```

---

