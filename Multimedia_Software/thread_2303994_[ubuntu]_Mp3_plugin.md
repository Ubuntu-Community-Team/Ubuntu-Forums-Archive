---
title: "[ubuntu] Mp3 plugin"
date: 2015-11-23
forum: Multimedia Software
---

### Post by ricardo43 on 2015-11-23
hi.
i was trying to listen some music on ubuntu. but it appear me a window to install plugins, i don't know which to choose. 
What is the difference between ugly, bad and fluendo?

[ATTACH=CONFIG]265738[/ATTACH]

---

### Post by Bucky Ball on 2015-11-23
Close that window and try installing 'ubuntu-restricted-extras' from the Software Centre. That should take care of it. Do you have VLC installed? That drags in just about everything you'll need also.

---

### Post by ricardo43 on 2015-11-23
no, i don't have VLC installed. you it's better than the plugins?

---

### Post by Bucky Ball on 2015-11-24
As I say, installing ubuntu-restricted-extras or VLC should fix things for you and save you trawling through the bads and uglys. It will grab what you need (should).

---

### Post by Yellow Pasque on 2015-11-24
> **ricardo43 said:**
> hi. i was trying to listen some music on ubuntu. but it appear me a window to install plugins, i don't know which to choose. What is the difference between ugly, bad and fluendo?

All of them will work, It is simply a question of legality. Unless you are trying to use the mp3 format for business/profit, you probably don't need to worry about it. (Fluendo is the safest legal choice if you do need to worry about it.)

```
installing ubuntu-restricted-extras or VLC should fix things
```
I don't think installing VLC will install the needed gstreamer plugins.

---

### Post by Rob Sayer on 2015-11-26
Installing VLC is a good idea because it comes with its own codec libraries, as does SMPlayer, which is what I use usually.

But since VLC uses its own codecs, it won't help with rhythmbox or other players.

As mentioned, install the restricted codecs.  Open the terminal and copy and paste:

```
sudo apt-get update
```

and then

```
sudo apt-get install ubuntu-restricted-extras
```

I included apt-get update because you should always refresh the sources list before installing anything from the repos or a ppa.

Or use Synaptic Package Manager (which is how I generally do it).  Hit the Refresh button before installing.

---

### Post by ricardo43 on 2015-11-30
thanks. it's solved

---

### Post by Bucky Ball on 2015-11-30
> **ricardo43 said:**
> thanks. it's solved

Please share with the community how. Thanks. :)

---

