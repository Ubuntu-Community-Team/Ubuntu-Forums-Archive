---
title: "Stream Video No MRL"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by mp4215 on 2006-11-11
I have a file server that I have ripped my DVD's to. I have Samba set up on the server and connect to it with a client. I right click on the file that I want to play and the following comes up:

No plugin found to handle this resource (smb://mikeyp@drsatan/mikeyp/Movies/LOST%20-%20%20The%20entire%201st%20season/lost%20ep01.avi)

The details section lists:
xine: cannot find input plugin for MRL [smb://mikeyp@drsatan/mikeyp/Movies/LOST%20-%20%20The%20entire%201st%20season/lost%20ep01.avi]
xine: input plugin cannot open MRL [smb://mikeyp@drsatan/mikeyp/Movies/LOST%20-%20%20The%20entire%201st%20season/lost%20ep01.avi]
xine: found input plugin : CIFS/SMB input plugin based on libsmbclient




I do not understand why it wouldnt work. I have libsmbclient installed. When trying to play these files directly on the client machine it works. So why wont it work through the server?

---

### Post by mp4215 on 2006-11-13
Any ideas?

---

### Post by pete on 2006-11-13
Assuming you're connecting to the server via Places -> Connect to Server...

The problem is that xine (and many other apps) doesn't understand how to get to the files on the server via Nautilus.  You need to mount the remote directory in your local file system via either smbmount or by adding it to /etc/fstab.

---

### Post by mp4215 on 2006-11-13
Alright I will give that a try when I get home.


Whats really weird about all this is that it used to work without using smbmount. I ended up hosing my machine, I reinstalled ubuntu and now it doesnt work.

---

### Post by mp4215 on 2006-11-14
Alright pete, that solved the problem. Thanks a bunch!

---

### Post by lych on 2007-05-11
But how?!
I am also having problems with playing the video from the remote samba shares.

I am using Kubuntu and wondering, Konqueror could open samba shares, it asks for authorization and finally could list these shares content, but why doesn't it allow to play e.g. video files directly from itself? 
Yes I know that we could mount samba shares to some mount point on our local filesystem, and I do this every time. But why? Is it possible to make Konqueror mount things automatically by on its own straight away it opens some samba share?

What is is the purpose of this Konqueror facility then if it lists the share content but require downloading the media file for viewing? Is the share listing the only facility the Konqueror provides? It is really confusing me all the time.

If anybody could give me an insight about this I would really appreciate this.

Well.. at least I would be glad to know some third utility that allows me to mount samba shares without any command line intervention..

---

### Post by JuanSinMiedo on 2007-05-15
I've found what the problem is (or think so). Konqueror can browse the files but when you click on the file to play it xine doesn't get/understand the user-password so it can't access the file. I've solved this by changing the configuration to that samba share:
public = yes
Then I can play those files without a hassel.
Hope it helps.

---

