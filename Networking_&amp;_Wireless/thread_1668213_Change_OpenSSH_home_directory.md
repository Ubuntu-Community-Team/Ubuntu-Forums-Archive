---
title: "Change OpenSSH home directory"
date: 2011-01-16
forum: Networking &amp; Wireless
---

### Post by theamazingbeat on 2011-01-16
Hello Everyone,
So I now have my ssh server all setup on my ubuntu 10.10 machine and properly working with a private rsa key. Anyway when I connect to it via my client it opens to:

/home/myusername

I am able to run around the whole drive and have full access to everything, which is great. But I don't have anything on this hard drive. All my data and files that I really want to access are on the second drive of this computer. It doesn't have an OS on it, just files. Anyway I need to know how to change the directory to point to that drive and have full access of everything.


Thanks in advance

---

### Post by sj1410 on 2011-01-16
ssh lands you to the home directory of the user.

---

### Post by theamazingbeat on 2011-01-16
Okay how do I change that?

---

### Post by spiky001 on 2011-01-16
I have found this have a look [http://www.linuxquestions.org/questions/linux-software-2/ssh-to-different-directory-other-than-home-502051/#post2505853](http://www.linuxquestions.org/questions/linux-software-2/ssh-to-different-directory-other-than-home-502051/#post2505853)

---

### Post by theamazingbeat on 2011-01-16
I don't believe that is what I am looking for. I have 2 drives in my ubuntu machine. When I SFTP into the machine it just shows the OS drive. I need to be able to have full access and see the other drive in the machine

---

### Post by spiky001 on 2011-01-16
So your using Nautilus to access the other machine?

---

### Post by spiky001 on 2011-01-16
So your using Nautilus to access the other machine?

---

### Post by spiky001 on 2011-01-16
So your using Nautilus to access the other machine?

---

### Post by theamazingbeat on 2011-01-16
No,

Windows machine SFTP using WinSCP as client --->Connects to Ubuntu machine and shows main Hard Drive

I have a second drive in that ubuntu machine that I wish to access via SFTP. I can only browse around the main hard drive at this moment. How do I browse the second hard drive

---

### Post by spiky001 on 2011-01-16
Ok I dont use windows but when I use Nautilus I put sftp://user@ipaddress /media/hard drive  If the drive is mounted it,s in /media folder

---

### Post by theamazingbeat on 2011-01-16
lmao,
Wow I am kinda stupid.
Ya I just realized I had to enter the path. See it opens to my home folder so I believed I was locked in there. Yet I just entered /media/Local Disk in the path and presto!


Lol this is a waste of thread because of a newbie..


Thanks though

---

### Post by theamazingbeat on 2011-01-16
lmao,
Wow I am kinda stupid.
Ya I just realized I had to enter the path. See it opens to my home  folder so I believed I was locked in there. Yet I just entered  /media/Local Disk in the path and presto!


Lol this is a waste of thread because of a newbie..


Thanks though

---

### Post by theamazingbeat on 2011-01-16
lmao,
Wow I am kinda stupid.
Ya I just realized I had to enter the path. See it opens to my home   folder so I believed I was locked in there. Yet I just entered   /media/Local Disk in the path and presto!


Lol this is a waste of thread because of a newbie..


Thanks though

---

### Post by spiky001 on 2011-01-16
Not really maybe it will help someone else

---

