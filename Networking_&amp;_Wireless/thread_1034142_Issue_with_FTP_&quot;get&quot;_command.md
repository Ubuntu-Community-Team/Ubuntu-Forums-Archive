---
title: "Issue with FTP &quot;get&quot; command"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by anilgurwara on 2009-01-08
Hey people..

I have a strange problem with FTP with one of our clients.
They want to use ftp in following manner.

First the client FTP's to its domain FTP Server

And then tries to "get" the files shared in his windows network shares.

get \\abcdserver.com\Test\test.txt

I tried this using Windows standard FTP Client but this doesnt seems to be a valid user case.
Even Linux doesn't supports this.

I would like to know if standard supports such case or is it an invalid case.
IMO, its invalid since to resolve abcdserver.com you need to do a DNS query and again authentication is required at abcdserver.com to access the shared folder Test.

Please enlighten.

Thanks in advance

---

### Post by untappedpilot2 on 2009-01-08
Doesn't your FTP server have some kind of web-interface login that you could do or Firefox or whatever broswer your using? put [ftp://yourdomainhere.com](ftp://yourdomainhere.com) in the address bar and you should get some kind of login popup. Login and it should display the files on the server. Do a "save target as" to pull down the files.

---

### Post by anilgurwara on 2009-01-08
I guess you didn't understood the issue.

See following is the requirement from customer which doesn't look a valid use case, just want to confirm the same.

Steps

1. Log to some ftp server using command line

ftp ftpserver.com

After successful login, this is what customer wants

instead of giving a valid path to "get" a file, he does this:

get \\testserver.com\test\test.txt

This testserver.com can be a windows PC or some shared server which is accessible but its against Netbios resolution.

The only way to access this test.txt from testeserver.com is to mount the shared directory on unix ftp server or if windows then use "net use" to create a network drive and then its as good a locally available resource/file. The ftp can be used to get that file.

Any other way do you suggest?
Do u feel this a valid user scenario? 
IMO, its not a valid use case, I want to take opinion from open community.

Thanks again.

---

