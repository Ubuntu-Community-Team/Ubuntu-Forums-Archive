---
title: "[QUE] lftp PASSIVE mode error"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by pi3ch on 2010-10-23
Hi

I m trying to use lftp script to connect to my ftp server and sync my data however I always get this error (debug mode):

```
  
<--- 230 OK. Current restricted directory is /
---> PBSZ 0
<--- 200 PBSZ=0                                                
---> CWD /home
<--- 250 OK. Current directory is /home                        
---> PROT P
<--- 200 Data protection level set to "private"           
---> PASV
<--- 227 Entering Passive Mode      
---- Address returned by PASV is ignored according to ftp:ignore-pasv-address setting
**** Socket error (Connection timed out) - reconnecting     
---> LIST
---> ABOR
---- Closing aborted data socket
---- Closing control socket

```Apparently it gets the connection and makes directories on server (I can see directories has been created through cpanel) but for some reason it cannot list files and start mirroring.

here is my script
```
debug 10
open <ftp host>
user <user> <pass>
mirror -e -R -v --only-newer /mnt/local/sync /remote/home
exit
```Could everyone help me to figure out what is the problem? it is all about this line I think "Address returned by PASV is ignored according to **ftp:ignore-pasv-address setting**"

Thanks :)

---

### Post by gmargo on 2010-10-23
What is your **ftp:ignore-pasv-address** setting?  Did you try changing it to the other value?

---

### Post by pi3ch on 2010-10-24
I tried to set "**ftp:ignore-pasv-address**" to on and off in /etc/lftp.conf file but noting different. any other alternative to lftp for ftp sync?

---

### Post by gmargo on 2010-10-24
Is there a firewall that's blocking the ftp data connection?

---

### Post by pi3ch on 2010-10-24
On my own box there is no firewall running (iptables -L) on server I dont think there should be any because I can connect to it using FileZilla or WinSCP (on my XP box)?

---

### Post by pi3ch on 2010-10-26
*it is just ridiculous*! on win box I can easily use powerful **winscp** and its built-in scripting to sync all of my files over FTP but in _ubuntu_ after almost a week I even cannot use simple **lftp** command to connect to **Passive FTP server**!!!!!!!!!

_Filezilla_ works find but I need to run in command line and put commands is a script file to sync my files and I have **NO IDEA** why lftp cannot get connected! it just stuck in make connection.:mad:

```
pi3ch@pici:/mnt/home2/pi3ch/sync$ lftp
lftp :~> open ftp.MYSITE.com
lftp ftp.MYSITE.com:~> user USERNAME
Password: 
lftp USERNAME@ftp.MYSITE.com:~> ls
`ls' at 0 [Making data connection...]

```Open host fine, login fine, make data conection ===> takes for ever!!! :confused: :confused: :confused: (my ftp server is on Bluehost)

---

### Post by gmargo on 2010-10-26
> **pi3ch said:**
> _Filezilla_ works 

Is that Filezilla running on the linux box?

Also do other ftp tools like "ftp -p" and ncftp work?  If some program works from the linux box, other than lftp, then that tells us that a lot of things are working (networks and firewalls and such) and it's just an lftp issue.

Also, you might ask Bluehost what ftp server software they use.  Assuming it's an open source one then we can do some testing.

---

### Post by pi3ch on 2010-10-27
FireZilla is running on Linux box and works fine.

NcFTP installed and run using "ncftp -u USERNAME -p PASSWORD FTPNAME" and works without any problem. I could easily get directories list and CD to them.

PureFTP I reckon is running on server because when I connect using NcFTP I get this welcome message "Welcome to Pure-FTPd [privsep] [TLS]" it also accept IPv6.

---

### Post by gmargo on 2010-10-27
In the process of setting up a test, I came across this ftp client in the repository: **weex**, "A non-interactive FTP client for updating web pages".  Have you tried it?

[http://packages.ubuntu.com/maverick/weex](http://packages.ubuntu.com/maverick/weex)

---

### Post by pi3ch on 2010-10-29
**weex** sounds interesting! I ll give it try.

Cheers *gmargo *:)

---

### Post by pi3ch on 2010-10-31
I give up with lftp, finally get permission for SSH and now using rsync. [gmargo]("http://ubuntuforums.org/member.php?u=1009937"), I m happy to continue working of lftp to find out the problem.

---

### Post by gmargo on 2010-11-01
I did do some testing with a PureFTP server, but could not make lftp fail in any way.  If there's a way for you to give me a restricted permission login on your system I can give lftp a try from here.

---

### Post by pi3ch on 2010-11-01
I sent credential through email to you.

---

### Post by gmargo on 2010-11-02
It seems to be a problem with encrypted data streams.

I was able to get lftp to work but only by disabling ssl entirely.  There are options for only disabling ssl on the data side but they didn't help.

So add the following option to your lftp script
```

set ftp:ssl-allow no

```So the password and data get passed in the clear, but that's what all the other tools are doing.

---

### Post by pi3ch on 2010-11-02
That is interesting since even with enabled SSL lftp could successfully login but it stucks in directory listing part when in passive mode lftp is going to get list of files.
Thanks [gmargo]("http://ubuntuforums.org/member.php?u=1009937") you finally solved the issue.

---

### Post by gmargo on 2010-11-02
The encryption on the command channel worked fine; it was just the data channel that wouldn't work.  The data connection would attempt to connect, but it was as though the server was not actually listening on the specified data port.

So I just finished a test to a local pure-ftpd 1.0.28 server (maverick's version), adding the TLS encryption.  And lftp works just fine to it, even encrypting the data stream.

I'd be curious to know exactly what version of the server your host is using.

---

