---
title: "sshfs and remote commands"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by fineghal on 2010-03-02
I am mounting a remote filesystem via sshfs. 

Is there anyway I can run a command remotely WITHOUT ssh'ing to the server?

ie) At present, if I switch to the local mountpoint ala /media/nas and for example want to unrar a file, unrar dl's file to local, unrar's, and then upload's back to server. 

So I get one heck of a network bottleneck. 

Is there something more elegant than perhaps aliasing something like remunrar = read filename && ssh nas.lan 'unrar e $filename'

---

