---
title: "FTP server"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by RedSingularity on 2010-09-06
I am looking for some good FTP server software.  Any recommendations?

---

### Post by MaindotC on 2010-09-07
It depends on how you want it managed.  In my situation I don't have multiple users nor the need to provide any web interface, so I just use sshd, which is the open ssh server, and I connect to it from a client using the command "sftp" or the "Connect to Server" option in Nautilus.  This is a secure file transfer employing the same methods of encrypting the traffic as ssh uses, so I don't have to worry about the safety of sending documents that contain my banking info or other personal information.  It is installed with the openssh-server package.

---

### Post by RedSingularity on 2010-09-07
I am looking for one that multiple users can log into.

---

### Post by MaindotC on 2010-09-07
Well, multiple users CAN log into it, but you'd have to give them local accounts on the ftp machine.  They would enjoy the same benefits as you would - authentication and a secure connection.  I'm not sure how you can limit their access to only file transfers so they wouldn't have shell access.  Is that alright?

---

### Post by RedSingularity on 2010-09-07
Thats fine as long as they cant edit system files.  Well i am going to take that option into consideration now.  :)  Thanks.  If anyone else has any other ideas please feel free to post them.

---

### Post by MaindotC on 2010-09-07
I think one way you can restrict access is to use ACL's.  There are some good youtube videos for implementing ACL's.

---

