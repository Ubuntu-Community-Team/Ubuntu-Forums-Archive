---
title: "Resynthesizer plug-in for Gimp 2.10.18 not working properly"
date: 2020-08-12
forum: Multimedia Software
---

### Post by claus on 2020-08-12
Hi all,

a few weeks ago, I found the resynthesizer plug-in for Gimp 2.10 & installed it according to [this threat]("https://www.gimp-forum.net/Thread-Gimp-2-10-Resynthesizer-Linux"), but I cannot a) create textures, or b) perform 'Heal selection'. *Filters > Map > Resynthesize* is there alright, but *Filters > Enhance > Heal* selection isn't there.

My Gimp plug-ins folder looks like this:

[https://claus-cyrny.net/wordpress/wp-content/uploads/2020/08/Screenshot-at-2020-08-12-19-46-09.png]("https://claus-cyrny.net/wordpress/wp-content/uploads/2020/08/Screenshot-at-2020-08-12-19-46-09.png")

What can I do to make this plug-in work, particularly for creating near-linear textures.

TIA,

Claus

---

### Post by ajgreeny on 2020-08-12
Are you running the repository version of Gimp or the snap?
Let's see the output of ***snap list*** in terminal.

If using the snap I'm afraid snap sandboxing means that plugins (all of them I believe) will be blocked and not work.
You can have both the snap and the repository version installed at the same time so if you currently have the snap, now install from the repos with ***sudo apt install gimp*** and se if that solves your problem.

---

### Post by claus on 2020-08-12
Hi,

I don't have the snap version installed, just the "normal" version in the repos.

Claus

---

### Post by ajgreeny on 2020-08-13
Ah well; there goes my best, and I'm afraid, my only idea for a solution.

I don't use gimp enough to have any plugins added, just the basic application, so I will have to leave this to others to hopefully help you better than I am able to.

---

### Post by shantiq on 2020-08-14
ok Claus never heard about resynthesizer so thanx really cool tool and will use it


here is a great video for the guys who want to find out [how to use it ]("https://www.youtube.com/watch?v=EvFLCRywh7g")




So first of all I replicated what you said you did:


regular 2.10.18 for 20.04


and installed the plugins [you linked]("https://www.gimp-forum.net/attachment.php?aid=2262") to ~/.config/GIMP/2.10/plug-ins


THis is what i got confirming there is a kink in python working with this version of gimp as is: [[IMG]https://i.postimg.cc/MMcwfLDp/1.png[/IMG]]("https://postimg.cc/MMcwfLDp")


=======


So [read around]("https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1881684") and there is AN EASY FIX:




```
sudo apt install python-cairo python-gobject-2
```   [I already had that it said you may need it]

In terminal:

```
[COLOR=#000000][NOPARSE]wget http://archive.ubuntu.com/ubuntu/pool/universe/p/pygtk/python-gtk2_2.24.0-6_amd64.deb
wget http://archive.ubuntu.com/ubuntu/pool/universe/g/gimp/gimp-python_2.10.8-2_amd64.deb[/NOPARSE][/COLOR]
```


THEN:

```
sudo dpkg -i python-gtk2_2.24.0-6_amd64.deb
sudo dpkg -i gimp-python_2.10.8-2_amd64.deb
```




And then: [[IMG]https://i.postimg.cc/K4ZVWwLk/Screenshot-from-2020-08-14-09-41-21.png[/IMG]]("https://postimg.cc/K4ZVWwLk")






Hope it sorts out your problem ....

---

### Post by claus on 2020-08-14
> **shantiq said:**
> ok Claus never heard about resynthesizer so thanx really cool tool and will use it ...
Hope it sorts out your problem ....

Hi,

thanks a lot. Now the plug-in is there where it's supposed to be (*Filters > Enhance > Heal selection...*).

Greetings,

Claus

P. S.: With 'Heal Selection...' one not only can remove objects, it is also possible to create so-called [near-linear textures]("https://claus-cyrny.net/wordpress/wp-content/uploads/2020/08/pattern_leopard.png"). They have much more variety than [tiling textures]("https://claus-cyrny.net/wordpress/wp-content/uploads/2020/08/pattern_leopard_tile.png"); they don't look so uniform.

---

