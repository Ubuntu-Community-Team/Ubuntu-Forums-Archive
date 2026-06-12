---
title: "Network Drives - NTLMv2 security"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by sarahm on 2009-12-17
I am trying to connect to a network drive which requires ntlmv2 authentication. 

At the moment when I try and connect to the network drive (smb://datastore.domain.com/~share) I am constantly prompted for login details, I have tried these in various combinations and starting to think that the ntlmv2 may be the problem. 

I am quite new to Linux / Ubuntu and wondered if anyone could advise how i can check if ntlmv2 is enabled and also how to enable it?

My system is running Ubunutu 9.10

Many thanks in advance for any input

---

### Post by drs86 on 2010-04-26
Hi sarahm,

I noticed this thread is a few months old so you might have already solved your problem. But if you haven't, here's what worked for me:

Add the following line to the [global] section of your smb.conf file.
```
client ntlmv2 auth = yes
```That will allow you to connect using smb:// in your file browser.

If you would like to permanently mount the share as a network drive as I do, you can add it to your /etc/fstab file using cifs as the filesystem type and include the option sec=ntlmv2. You'll need to create a text file with your login credentials as follows:
```
username=******
password=******
```Substitute your own username and password. Make sure there's nothing else in the file (watch for hidden bytes at the end of the file and delete them with a hex editor if necessary). It doesn't matter what you name the file, just save it somewhere secure (I suggest you hide the file, make root the owner and set the permissions to 600) and include the path to it in your fstab line with the option credentials=/path/path/filename.

You may already know this, but the file and directory permissions on a Samba share can only be set at mount time -- not while mounted. I've personally found this quite annoying, especially the first time I tried to use chmod and it pretended to work -- no errors -- but didn't change anything. As far as I can tell, that's just the way Samba is at this point.

Good luck!

David

---

### Post by sarahm on 2010-04-27
Hi drs86

Thank you so much for your reply - i had kinda given up on this until I got your message.

I have just tried it and it worked great. 

In fact - when I opened my smb.conf file, the line to change to ntlmv2 was there - I had obviously tried this previously however I had the line at the bottom of the conf file and not within the global section, Doh! Once moved it was all fine. 

Really appreciate your input on this matter

Kind regards

Sarah

---

### Post by drs86 on 2010-04-28
No problem. Glad it worked. :)

Here's hoping the Samba people figure out how to change permissions on a share while mounted...

David

---

