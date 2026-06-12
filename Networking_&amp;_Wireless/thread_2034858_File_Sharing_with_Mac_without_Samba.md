---
title: "File Sharing with Mac without Samba"
date: 2012-07-29
forum: Networking &amp; Wireless
---

### Post by sjb300 on 2012-07-29
I would like to be able to access my Public folder from my mac without using Samba. I have checked 'Share this folder' and clicked 'Modify share' in the Share tab of Public's properties. I have checked 'Share public files on network' and selected 'never' ask for password in the Personal File Sharing preferences window.

But what do I type into the 'connect to server' window on the mac to connect to my ubuntu private folder? I figure its ???://myIP but what is the ??? meant to be? I have tried ftp and that seems to connect but then requests I log in with a password or as a guest. I have tried my ubuntu username and password but this does not work, and nor does logging in as a guest. The 'Guest access' check box in the share tab for Private is greyed out so I don't know if that has anything to do with it.

I am in need of help. Thanks.

---

### Post by bakegoodz on 2012-07-30
Without Samba eh? I use sftp (ssh file transfer) to move files all the time. In Ubuntu you can make a connection just by going to Alt-F2 and putting something like sftp://10.2.2.251 and will ask for a user and password on the remote box, you can even use root. I found some decent instructions for Mac too: [http://docs.cs.cf.ac.uk/html/811/node3.html#SECTION00035000000000000000](http://docs.cs.cf.ac.uk/html/811/node3.html#SECTION00035000000000000000)

I think the "Connect to server" (Command-K) dialog your looking for to connect to a Samba share is smb://myIP The same syntax works in Ubuntu in the "Run Application" (alt F2) dialog too.

---

