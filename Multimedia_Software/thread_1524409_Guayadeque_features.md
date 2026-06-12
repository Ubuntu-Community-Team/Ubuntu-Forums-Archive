---
title: "Guayadeque features"
date: 2010-07-05
forum: Multimedia Software
---

### Post by gavdari on 2010-07-05
I am using guayadeque and I need it to notify me about the title and the artist when a new song begins. Also it would be great if it could be controlled without restoring the window. I mean, every time I want to pause the song or skip to the next track, I should restore the minimized window and do whatever I want. Is there a way to control from the task bar or upper panel?

I'm an absolute newbie to ubuntu and eager to learn, so if you can please explain in the simplest terms.

---

### Post by Linye on 2010-07-05
In Guayadeque, Go to Library > Preferences

under **General** check the box that says "activate task bar icon". The icon is a bit ugly but there you can control the music.

Then go to **Playback** check the box "Show Notifications". Then Guayadeque will use the native notification system for the songs.

---

### Post by gavdari on 2010-07-05
Thanks. But I can't find the notification option you mentioned in Playback tab. What may be the problem?

---

### Post by Linye on 2010-07-05
Maybe an older version?  It should be there.


[IMG]http://ubuntuone.com/p/8od/[/IMG]

If not, then check this thread for support. 

[http://ubuntuforums.org/showthread.php?t=1380811](http://ubuntuforums.org/showthread.php?t=1380811)

---

### Post by gavdari on 2010-07-05
mine is 0.2.5, which is the latest I found.

---

### Post by anonbeat on 2010-07-05
> **gavdari said:**
> mine is 0.2.5, which is the latest I found.

Install guayadeque-svn from the ppa. See my signature for the ppa link

---

### Post by gavdari on 2010-07-06
I did what it is shown here:
[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)
and then I tried to install svn packages from .deb and also from synaptic. both of them stopped with an error:
"E: /var/cache/apt/archives/guayadeque-svn_1123~lucid-1_i386.deb: trying to overwrite '/usr/share/pixmaps/guayadeque.png', which is also in package guayadeque 0"
Am I missing something?

---

### Post by anonbeat on 2010-07-06
> **gavdari said:**
> I did what it is shown here:
[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)
and then I tried to install svn packages from .deb and also from synaptic. both of them stopped with an error:
"E: /var/cache/apt/archives/guayadeque-svn_1123~lucid-1_i386.deb: trying to overwrite '/usr/share/pixmaps/guayadeque.png', which is also in package guayadeque 0"
Am I missing something?

Yes you are missing 

```

sudo add-apt-reporitory ppa:anonbeat/guayadeque
sudo apt-get update
sudo apt-get remove guayadeque
sudo apt-get install guayadeque-svn

```

---

### Post by gavdari on 2010-07-06
Thanks, I had no idea what is a svn.
by the way, great music player. thanks.

---

### Post by chamadi on 2010-07-06
This post has helped me a lot in getting many useful informations.

---

