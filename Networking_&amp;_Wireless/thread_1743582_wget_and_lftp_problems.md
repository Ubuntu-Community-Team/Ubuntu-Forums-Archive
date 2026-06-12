---
title: "wget and lftp problems"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by jimford on 2011-04-29
I want to retrieve files from a computer on a home network. Both machines run Ubuntu. 

I can ssh, sftp and filezilla OK to the remote computer, but wget just hangs at 'logging in user'. I'm using a command like (without the spaces either side of the colon):

wget [ftp://user](ftp://user) : password@192.168.0.1:22/remote_directory/filename

I gave up on lftp and remembered that when I tried it in the past I could never get a connection to complete!

Any ideas, please?

Jim

---

### Post by AugustinMa on 2011-06-08
I had very similar problems last month. Finally, with the help of the members of the lftp mailing list, I finally managed to make it work.

I have summarized all the important information here:
[http://linux.overshoot.tv/wiki/networking/lftp](http://linux.overshoot.tv/wiki/networking/lftp) 
See the whole page and especially see the 'Unadvertised features' section, which might apply to you.

Best of luck,

Augustin.

---

