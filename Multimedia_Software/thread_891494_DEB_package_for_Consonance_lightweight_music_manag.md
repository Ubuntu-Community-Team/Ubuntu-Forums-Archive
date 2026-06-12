---
title: "DEB package for Consonance lightweight music manager"
date: 2008-08-16
forum: Multimedia Software
---

### Post by loell on 2008-08-16
**Download:**[ATTACH]81710[/ATTACH]

a lightweight and promising music manager/player. :KS
just providing a deb, since there was none.. enjoy.. ;)

[IMG]http://sourceforge.net/dbimage.php?id=165824[/IMG]

---

### Post by librano on 2008-10-26
Hi, I am getting an error...

Dependency is not satisfiable: libasound2

I am using the Hardy repos.

[EDIT] I added these repos and installed from there. It works great.

> deb [http://ppa.launchpad.net/andrewsomething/ubuntu](http://ppa.launchpad.net/andrewsomething/ubuntu) hardy main


---

### Post by zmjjmz on 2008-11-18
Would it be too much for you to create an lpia (Intel Atom) package for this?

EDIT: Nevermind, I found the package on your PPA.

---

### Post by kholis on 2008-11-18
@loell
is there consonance package for amd64 mechine?

thanks.

---

### Post by loell on 2008-11-18
[64 bit deb]("http://tinyurl.com/5shpwx")

---

### Post by kholis on 2008-11-18
@loell

i got error.

~$ consonance 

** (consonance:7699): CRITICAL **: (alsa_init_mixer): Unable to find alsa mixer element : PCM

** (consonance:7699): CRITICAL **: (main): Unable to init audio

---

### Post by kholis on 2008-11-26
i've made my own packages for intrepid. please try it...

[https://launchpad.net/~kholis/+archive](https://launchpad.net/~kholis/+archive)

---

### Post by Jose Catre-Vandis on 2009-01-17
> **kholis said:**
> i've made my own packages for intrepid. please try it...

[https://launchpad.net/~kholis/+archive](https://launchpad.net/~kholis/+archive)

Thanks. Tried to compile from source but it complained about alsa not being there or wrong version (.15 and intrepid is .17)

Your deb worked fine

---

### Post by etnlIcarus on 2009-03-16
*bump*

Version 0.5 has just been released. If you're running Jaunty alpha you've probably got up-to-date-enough libs & headers to install easily. If you're on Intrepid, you've got to change several dozen library version numbers but once you do, it compiles correctly (hasn't crashed yet so it seems like it's maintainer just set the library min versions at whatever he's running on Arch and hasn't tested it on anything else).

> Tried to compile from source but it complained about alsa not being there or wrong version (.15 and intrepid is .17) If it's complaining about alsa-<version>, you need to do an apt-get install libasound2 libasound2-dev. That confused the hell out of me as well.

---

### Post by galv on 2009-05-10
> **etnlIcarus said:**
> *bump*

Version 0.5 has just been released.

Is there a .deb for this version? (I'm using Jaunty)

Thanks.

---

### Post by galv on 2009-05-10
> **etnlIcarus said:**
> 
 If it's complaining about alsa-<version>, you need to do an apt-get install libasound2 libasound2-dev. That confused the hell out of me as well.
Thank you for this tip. I was searching for alsa-dev and going no where.

---

