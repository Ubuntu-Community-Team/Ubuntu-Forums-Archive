---
title: "Networking 2 ubuntu 9.10 machines"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by linuxNoob81 on 2010-02-10
Ok, I have a question for all of you more experienced with Ubuntu 9.10. I am trying to network and send files between 2 ubuntu 9.10 machines  and cannot figure out how to do so. I have gone on many websites on the net and they have led me to samba. I installed samba and used it to share folders between my ubuntu and windows vista and windows 7 machine with no problems but my 2 ubuntu 9.10 machines still cannot see eachother. Am I just a total noob and not understand samba and i'm just using it incorrectly? I saw one website was stating that you dont need samba at all for windows and ubuntu to communicate with eachother, that there was a default program added in 9.10 called nautilis that you can use. Are my machines actually just communicating with my windows through nautilis and not samba at all? I went through all the sudo steps of setting up samba correctly but still no luck networking 2 ubuntu machines.

Any help would be appreciated and thank you.
Linuxnoob81

---

### Post by Morbius1 on 2010-02-10
> I installed samba and used it to share folders between my ubuntu and windows vista and windows 7 machine with no problems but my 2 ubuntu 9.10 machines still cannot see eachother. Am I just a total noob and not understand samba and i'm just using it incorrectly?If you got sharing to work between linux and Win7 you are hardly a noob. In fact you may want to write down how you did it and submit a howto since you're doing better than most folks.

I'm shutting down for the day but if you post the output of the following commands so we can see the status of your setup somebody here can help you. I'll check on it first thing tomorrow.

Let's start with one of the Ubuntu machines that has shared folders:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

From the other ubuntu machine that wants to access the share above:

Open **Terminal**
Type **smbtree**
Type **findsmb**

---

### Post by Iowan on 2010-02-10
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a How-To for Windows sharing problems. You could also use NFS, SSH, or FTP to share files between the two Ubuntu machines - but since Windows is in the mix - and Samba is at least partly working...

---

