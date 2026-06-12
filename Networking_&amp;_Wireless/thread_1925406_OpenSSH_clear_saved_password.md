---
title: "OpenSSH: clear saved password?"
date: 2012-02-14
forum: Networking &amp; Wireless
---

### Post by VcDeveloper on 2012-02-14
When I logged in I elected to save the password permanently.  How do I clear it now?

Thanks!...

---

### Post by surfer on 2012-02-14
did you login from a shell? or did you use a graphical ssh client?

the shell does not store your password; just the fingerprint of the key of the server (which is usually a good thing).

or did i get you wrong?


(or did you use public key authentication?)

---

### Post by VcDeveloper on 2012-02-14
Just used the default settings when I installed OpenSSH on both Client and Server, and used "Places|Connect To Server" from the "Main Menu", after login, Nautilus was used to transfer files.

---

### Post by josephmills on 2012-02-14
Hello have you had a look at this [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) 
look close at the part about importing and exporting 
> you can add it to your Ubuntu system by opening the file .ssh/authorized_keys in your favourite text editor and adding the key to the bottom of the file  

Hope that this helps

---

### Post by VcDeveloper on 2012-02-14
I found it!  It was the "Password & Encryption Keys" is where there kept.

Thanks for you help!...

---

### Post by Iowan on 2012-02-14
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? ;)

---

### Post by surfer on 2012-02-15
ok, so you used nautilus (as graphical frontend). should have thought of that...

and, indeed: [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? (very nice, Iowan!)

---

