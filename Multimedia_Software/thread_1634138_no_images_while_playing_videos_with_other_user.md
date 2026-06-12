---
title: "no images while playing videos with other user"
date: 2010-11-30
forum: Multimedia Software
---

### Post by roy.nico on 2010-11-30
Hello Community

With user1, i have no problem. But with user2, when i start to read a video file, i have no image, just a black screen. The sound is ok, the time is running normally, but no image.
*It tested with vlc and gnome-media-player, it is the same. 
*I have no error message, when I start the program in a console.
*I suspected a permission problem, and i checked all the groups, but i don't see any difference between user1 and user2.

Any clue will be welcome.

Nico

---

### Post by runeh76 on 2010-11-30
Hmm just a wild guess..
Does user1 have root-rights? Did u use sudo?

---

### Post by roy.nico on 2010-11-30
no, no root-rights. And i did not use sudo.

---

### Post by runeh76 on 2010-11-30
Well u have to install stuff with sudo, if u want that others users can use installed applications.
Now u have done it only to user1.

---

### Post by roy.nico on 2010-11-30
No, no... Everything was installed with sudo of course. But i start the program as normal user.

---

### Post by runeh76 on 2010-11-30
u answered earlier  "no, no root-rights. And i did not use sudo."
Try to make decision  :confused:
It would help a little if u would say what kind of video it is...
hmm check users rights better

---

### Post by roy.nico on 2010-11-30
Hum, ok.

* I installed all my apps (in particular vlc, gnome media player) with 
$ sudo apt-get install ...

* I launch the apps as normal user (without sudo)
$ vlc

* The videos are avi files. It does the same by the way with my raw dv files (from my video recorder)

---

### Post by runeh76 on 2010-11-30
When u log in user2, do u have example VLC in applications/voice&video menu?
If so u could install these when u are logged in user2--->  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by roy.nico on 2010-11-30
> **runeh76 said:**
> When u log in user2, do u have example VLC in applications/voice&video menu?

Yes, i do.

> **runeh76 said:**
> 
If so u could install these when u are logged in user2--->  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Hum, you mean reinstall them, as i m logged as user2 ? I will check at home if they are installed already, which i supposed to be the case, since user1 can read videos...

---

### Post by runeh76 on 2010-11-30
> **roy.nico said:**
> Yes, i do.



Hum, you mean reinstall them, as i m logged as user2 ? I will check at home if they are installed already, which i supposed to be the case, since user1 can read videos...


Yeah try to reinstall when u are log in as user2, u dont lose nothing..and make sure u have checked ur users permissions right.

---

### Post by roy.nico on 2010-11-30
> **runeh76 said:**
> Yeah try to reinstall when u are log in as user2, u dont lose nothing..and make sure u have checked ur users permissions right.
The problem is unchanged. I re-installed ubuntu-restricted-extras from a user2 session. I checked that 
```
$ groups user1
``` 
and 
```
$ groups user2
``` give the same result.

---

### Post by runeh76 on 2010-11-30
> **roy.nico said:**
> The problem is unchanged. I re-installed ubuntu-restricted-extras from a user2 session. I checked that 
```
$ groups user1
```and 
```
$ groups user2
``` give the same result.

User2 has all crosses under advanced-tab
And u did put user2 to admin and etc. groups ?

Sry cant help any, hope u get this solved.

---

### Post by roy.nico on 2010-11-30
yes, user2 is in all the groups --- :(

---

### Post by roy.nico on 2010-11-30
I solved the problem as follows :
```
$ gstreamer-properties
```
then in the tab "video" i selected "X windows System (without xv)" instead of "automatic detection"
I dont't know exactly what it means, but it works now.

Nico

---

### Post by runeh76 on 2010-11-30
Good job !!
Glad that u get it  :popcorn:

Cheers Runeh

---

