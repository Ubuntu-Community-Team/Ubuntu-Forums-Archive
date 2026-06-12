---
title: "Connect to Server"
date: 2011-12-04
forum: Networking &amp; Wireless
---

### Post by temporizer on 2011-12-04
Hey Everyone,

I am curious how to connect to a remote server via command line as opposed to clicking Places > Connect to Server in Ubuntu 11.04 (classic) using Gnome instead of Unity. 

Anyways, i've tried using sshfs to connect [sshfs user@server:/path/to/shared /mount/point] : connect is successful, however when double clicking on a file within said shared drive, it doesn't recognize the filetype [see screen2] and asks me to select an application to open it in.. when I connect via GUI (clicking places > connect to server) it recognizes the file type [see screen1]. 

you can see in my screenshots that screen1.png shows the filetype on the icon, as screen2.png does not.

any help would be helpful.

Thanks

---

### Post by papibe on 2011-12-04
I can think of 2 options: you can use sftp (similar interface as ftp), or you could mount the share (read this [tutorial]("https://help.ubuntu.com/community/SSHFS")).

Hope it helps,
Regards.

---

### Post by temporizer on 2011-12-04
> **papibe said:**
> I can think of 2 options: you can use sftp (similar interface as ftp), or you could mount the share (read this [tutorial]("https://help.ubuntu.com/community/SSHFS")).

Hope it helps,
Regards.

Thank you for your reply, but, if you read my post and look at the screenshots, i have tried sshfs, it's not the same as Places > Connect to server.

also, doing sftp is also NOT the same thing as Places > Connect to server.

---

### Post by bluexrider on 2011-12-04
I picked this up from an old thread I think it will help

 				 				**Re: "Connect to server..." from command line?** 			
 			 			 		   		 		 		the command is 
 	Code:
 	ssh ipaddress 
for more info try:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

to execute it at start up go to System > Preferences > Sessions
then click the Add button and enter the command there

---

### Post by temporizer on 2011-12-04
> **bluexrider said:**
> I picked this up from an old thread I think it will help

 				 				**Re: "Connect to server..." from command line?** 			
 			 			 		   		 		 		the command is 
 	Code:
 	ssh ipaddress 
for more info try:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

to execute it at start up go to System > Preferences > Sessions
then click the Add button and enter the command there

ok, this is not like using Place > connect to server in the sense that it does not mount the drive as usable.


Maybe i am not wording the question right. maybe i am trying to do something that can be done differently.

what i am trying to do:
-i have a server connected to my home network.
-i have a laptop that connects to the same home network.
-i am trying to "automount" a shared directory from the server to the laptop upon startup that allows the user to edit/create/modify files in that directory on the server.
-i know i can do this from samba, but i don't want to connect as the local[laptop] user, i want to connect as a user on the server machine.

can this be done, or is the only way to do so is via Places > connect to server?

---

### Post by temporizer on 2011-12-04
Hi Everyone.
I am sorry if I seemed rude or inconsiderate. I used to post in forums and stopped because people were replying without reading the entire OP. This seemed the case here because all posts referred back to sshfs, which I clearly stated in my OP that sshfs didn't do what I wanted it to do.

Anyhow, I figured out what I wanted to do and how to do it. I wanted to have a script to automount, upon startup, a network drive and still have said mount recognize file types (adding network mount to fstab didn't do that either, I tried). I finally stumbled upon this post: [http://ubuntuforums.org/showpost.php?p=11512083&postcount=2]("http://ubuntuforums.org/showpost.php?p=11512083&postcount=2"), which solved my problem. Even though it works through samba, it works like a charm, exactly what I wanted to do through the command line.

The mapped drive is then accessible through nautilus, as well as through the terminal via ~/.gvfs.

Thank you for the posts, though.

---

