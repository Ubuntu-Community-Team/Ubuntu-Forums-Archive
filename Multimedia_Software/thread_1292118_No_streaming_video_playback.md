---
title: "No streaming video playback"
date: 2009-10-15
forum: Multimedia Software
---

### Post by pgar23 on 2009-10-15
Hey all,
     As you can tell by the title of my thread that I am not receiving a video playback. I have already downloaded and installed the flash plugins, java plugins and a few others. Youtube is actually working for me, but on a number of other pages the section where the video usually will appear just stays a blank black box.  Also on any website that I can play videos, instead of a normal sized play button (you know, usually in the middle of the video box there is usually a small play button) Well mine appears super huge, the play button takes up the whole video box. I don't know what;s goin on here. Few specs: I am running 64-bit ubuntu, using 32-bit FF and also 32-bit plugins (I have also DL the 64bit of flash just to try, but no difference)

Any help or suggestions appreciated.

---

### Post by HappyFeet on 2009-10-15
Let's install the official 64bit flash plugin, shall we?

Uninstall the 32bit flash plugin. Download [this]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") file. Right click and **extract here**. Put the libflashplayer.so file on your desktop. Then:
```
sudo cp /home/your_user_name/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
```

In the above command, remember to change **your_user_name** to the name you login with, and **Desktop** is capitalized. This works for me every time.

---

### Post by HappyFeet on 2009-10-15
You might also want to install mozilla-mplayer as the firefox media plugin.

---

### Post by pgar23 on 2009-10-15
> **HappyFeet said:**
> Let's install the official 64bit flash plugin, shall we?

Uninstall the 32bit flash plugin. Download [this]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") file. Right click and **extract here**. Put the libflashplayer.so file on your desktop. Then:
```
sudo cp /home/your_user_name/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
```In the above command, remember to change **your_user_name** to the name you login with, and **Desktop** is capitalized. This works for me every time.


Thanks for the reply, but I already have both of the plugins and they are both properly installed. I am having problems with the streaming video playback, not with the plugins themselves.

---

### Post by pgar23 on 2009-10-15
> **HappyFeet said:**
> You might also want to install mozilla-mplayer as the firefox media plugin.


I have mplayer, also. I figured if one didn't work that I would have a back-up that would come in to play...still no such luck though.

---

### Post by HappyFeet on 2009-10-15
Sounds to me like your install is mucked up, or your computer is linux incompatible.

---

### Post by pgar23 on 2009-10-15
Are there any other users, with some legit advice?? No offense happyfeet but I am looking for a fix or a suggestion that would point me to a solution, NOT "Sounds to me like your install is mucked up"

---

### Post by HappyFeet on 2009-10-16
> **pgar23 said:**
> Are there any other users, with some legit advice?? No offense happyfeet but I am looking for a fix or a suggestion that would point me to a solution, NOT "Sounds to me like your install is mucked up"

Believe it or not, installs do get corrupted for whatever reason. I see this all the time as someone who fixes computers for a living. It's just an educated opinion based on what you told me, and I'm sorry I wasted your time with "non-legit" advice. Good luck with all the other people (?) trying to help.

You could also try a live cd and "install" flash. That way, you will know that it *can* install correctly and go from there. If it does not install via live cd, chances are it's not going to. This is my last time in this thread helping you, after your semi-rude response.

---

