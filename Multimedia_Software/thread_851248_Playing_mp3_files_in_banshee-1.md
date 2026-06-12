---
title: "Playing mp3 files in banshee-1"
date: 2008-07-06
forum: Multimedia Software
---

### Post by kidko on 2008-07-06
I've downloaded the latest banshee-1 package from their repository, and as other thread suggested, I've also installed ubuntu-restricted-extras... however, when I try to play any mp3 file, it still doesn't work (and ends up with a red X next to it). Anybody find a solution?

I'm running it on Xubuntu 8.04

---

### Post by wolfen69 on 2008-07-06
open synaptic and search for fluendo mp3. if it is not installed, do it. if it is installed, try installing vlc. (you dont have to use vlc, but it will give you most codecs)

---

### Post by forger on 2008-07-06
What happens if you play it in totem or mplayer?
Is it just for some mp3 files? Some mp3 files are corrupted, they can be played in Windows, whereas the same files can't be played on Linux applications (lack of following standards?). You could try re-encoding the files with [mp3/wma/ogg converter]("http://www.freemp3wmaconverter.com/freemp3wmaconverter.html") (windows application)

---

### Post by kidko on 2008-07-06
@wolfen69: Unfortunately, neither of those seemed to fix it. Am I missing something? Are the libraries in the wrong places, perhaps, because I'm not in GNOME?

@forger: They play fine in both, and everything worked in Amarok (which I'm trying switch over from). There's only one file that Banshee will play, and it's an MP3 that wouldn't always play in Amarok...

---

### Post by forger on 2008-07-07
you're not in gnome? xfce correct?

copy paste the following commands in a terminal:

First backup:
```
mkdir ~/BACKUP; mv ~/.config/banshee ~/BACKUP/
```

I don't know how you set it in xfce, but in ubuntu there's System > Administration > Software Sources application or with the following command in terminal:
```
gksudo software-properties-gtk
```
(let's hope it works)

The point is that you must make sure you have **multiverse** and **universe** repositories checked and enabled.

Then purge/install banshee:
```

sudo aptitude purge banshee
sudo aptitude --with-recommends install banshee

```

---

### Post by kidko on 2008-07-07
I tried that, but with the specific version of Banshee I'm trying to install (1.0, in banshee-1), and it didn't fix the problem. I noticed that while the Hardy repos still contain v0.13, while the "intrepid" repository has 1.0, which is what I'm looking for. Is that the same as Banshee's own distribution server, or can I use that, since it seems to be under Ubuntu's servers?

If you want to see for yourself: [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=banshee](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=banshee)

---

### Post by forger on 2008-07-07
well.. if it's not in the official repos i can't help you :)
You can try install banshee and download the packages from packages.ubuntu.com but that could break other packages. Luckily, if something goes wrong, you can always purge the upgraded package and use the one from the repository.

you could also try this:
[http://icehot.wordpress.com/2008/06/13/banshee-10-was-released-read-how-to-install-it-in-ubuntu-gutsy-and-hardy/](http://icehot.wordpress.com/2008/06/13/banshee-10-was-released-read-how-to-install-it-in-ubuntu-gutsy-and-hardy/)

---

### Post by kidko on 2008-07-10
Still no dice. Oh well, back to Amarok.

---

