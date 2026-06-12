---
title: "Sharing my audio card with other users."
date: 2006-06-23
forum: Multimedia &amp; Video
---

### Post by Mick Dalen on 2006-06-23
Hey.

We are some friends who have an ubuntu network with 10 stations attached. all is working well, except one thing. When we log on our admin user everything is working well, but when we log on the personal users, the audio card can`t be detected. I guess this has something to do with granting rights to the users, and as a beginner in ubuntu, i`ve searched for hours, and found nothing on this topic. I guess in not the technical marvel when it comes to computers myself, but some of my friends are more proud, not wanting to ask this question. Anyway, I hope one of you out there can tell me how to enable the soundcard for read only users.

Yours faithfully
Mick
Norway

---

### Post by masterjonny on 2006-06-23
If its similar to Gentoo you'll need to add the users to the "audio" group to be able to hear sound, otherwise only root will have it. Could be miles off the mark, i'm new to Ubuntu but i think it's something like that ;)

---

### Post by Mick Dalen on 2006-06-23
I`ve tried all that. I can`t find a soundgroup anywhere. Perhaps you are right about root. im struggeling to find out what commands to use in order to administer rights to users. im a blank rookie on that field im afraid. (we use pseudo for root of course).

---

### Post by Mick Dalen on 2006-06-23
I allow myself to bump this thread to say that i found out what to do so i need no further help. 

i found the answer deeper into the forum threads under the heading:
no sound in ubuntu 6.06.

the answer is apparently: 

First, become root (su -). Then use your favorite text editor to edit the file /etc/group.
Find the line that looks like this:

audio:x:29:

Add your username to it:

audio:x:29:mick

(i couldnt use root though, i used admin (not root) and had to pico. 
My username is not mick though. 

Thanks to forum for help:)

---

