---
title: "mget not working?"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by wizard10000 on 2011-06-07
...I can duplicate this in either Natty or Squeeze and it's causing me a fair bit of extra work every day - mget doesn't work in either distribution. 

I've got a cron job that runs on my leased VPS that makes a sql dump then creates a .tgz archive of the entire site in my home directory on the VPS. The script creates a file using the current date as part of the filename like this - 

[FONT="Courier New"]backup-`date -I`.tgz [/FONT]

Since ftp isn't a shell I can't use a variable in the ftp script so I have to use mget and mdelete - both of which worked fine until Natty. 

Here's what happens if I try to use mget against the server - 

[FONT="Courier New"]wizard@wizard-netbook:~$ ftp vps.com 
Connected to vps.com. 
220---------- Welcome to Pure-FTPd [privsep] [TLS] ---------- 
220-You are user number 1 of 50 allowed. 
220-Local time is now 10:57. Server port: 21. 
220-This is a private system - No anonymous login 
220 You will be disconnected after 15 minutes of inactivity. 
Name (vps.com:wizard): wizard 
331 User wizard OK. Password required 
Password: 
230 OK. Current restricted directory is / 
Remote system type is UNIX. 
Using binary mode to transfer files. 
ftp> mget *.tgz 
ftp> 
ftp> quit 
221-Goodbye. You uploaded 0 and downloaded 0 kbytes. 
221 Logout. 
wizard@wizard-netbook:~$[/FONT]

See the empty ftp prompt? That's all I get. I can duplicate this on Natty and Squeeze but my webhost's technical support can do it using my account with no trouble, so I don't think it's server side. 

Interestingly, if I issue manual commands with gftp mget works but mdelete doesn't. 

Anybody got any ideas? 

thanks -

---

