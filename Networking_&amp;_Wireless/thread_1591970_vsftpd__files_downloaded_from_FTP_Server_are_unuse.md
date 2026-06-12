---
title: "vsftpd : files downloaded from FTP Server are unuseable"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by dwvm3 on 2010-10-10
Sorry, I discovered that this post should be in Servers Forum. Unfortunately I can not move it, so I posted it again.

Hello,

I have a very strange problem with vsftpd. I have set up vsftpd on Ubuntu 10.04 32 Bit. Local users have access to their home directory using their username and password to log in.

Users can upload files to the server and the files are OK. If I download the same file, it is unuseable. The file size is the same than the original file on the server, but the content is different. I tried many FTP clients on Windows  and Ubuntu and set transfer mode to Auto and Binary, but no success.

I examined the two different files in a Hex editor and it is clear that the content is not the same.

Here is a screenshot of the working file on the FTP server:

[IMG]http://www.control-nodes.com/Bilder/HexServer.png[/IMG]

This is the same File downloaded via FTP on the client:

[IMG]http://www.control-nodes.com/Bilder/HexClient.png[/IMG]

I can not see any scheme or any hint that tells me why the two files are different. Has anybody an idea?

Thanks in advance

Dierk

---

