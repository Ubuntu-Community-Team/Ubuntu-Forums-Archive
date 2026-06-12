---
title: "Devede help"
date: 2006-12-13
forum: Multimedia &amp; Video
---

### Post by crimsontide on 2006-12-13
I'm trying to convert avi video and then burn it to a dvd to watch on my dvd player using devede but i keep geting this message " Aborted. There can be temporary files at the directory destination."  Not sure what to do here.  Can anyone help?

---

### Post by crimsontide on 2006-12-18
Anyone?

---

### Post by artships on 2006-12-19
As I recall devede is a python script.  So, load it into an editor, search for that error message, and read what it's doing when it throws that message.

---

### Post by nalmeth on 2006-12-19
" Aborted. There can be temporary files at the directory destination."
Do you mean to say there CAN'T be temporary files at the directory destination? That error message doesn't make much sense..

---

### Post by DonPachi on 2006-12-20
ROLL TIDE ROLL!!! Mobile, Alabama here!  I'm just getting into installing Devede this afternoon so I'm definitely not an expert.  Did you check all the relevant permissions?

---

### Post by crimsontide on 2006-12-21
[COLOR="Red"]**[SIZE="5"]ROLL TIDE ROLL !!  [/SIZE]**[/COLOR]    I've just reinstalled Devede and it seems to be working just fine now.    :confused:     Thnx everyone for there help anyway.  :)

---

### Post by DonPachi on 2006-12-21
Well I'm having trouble with it still so if you don't mind I'm gonna hijack your thread rather than start a new one.  I had Devede2.6 running smoothly on dapper, but after doing a fresh install of Edgy and installing devede2.8 through synaptic, I'm getting an error:

donpachi@xexex:~$ devede
DeVeDe 2.8
Failed to load modules 2. Exiting
donpachi@xexex:~$ 

Anyone know what modules it might be looking for?

---

### Post by teet on 2006-12-22
> **DonPachi said:**
> Well I'm having trouble with it still so if you don't mind I'm gonna hijack your thread rather than start a new one.  I had Devede2.6 running smoothly on dapper, but after doing a fresh install of Edgy and installing devede2.8 through synaptic, I'm getting an error:

donpachi@xexex:~$ devede
DeVeDe 2.8
Failed to load modules 2. Exiting
donpachi@xexex:~$ 

Anyone know what modules it might be looking for?

I get the same error.

-teet

---

### Post by DonPachi on 2006-12-24
Quick fix? Launch devede by first invoking python with the terminal. Open a terminal and go to the directory where the devede script is and type:

python devede

Launches this way with no error.  Not sure why this works but there ya go.

---

### Post by teet on 2006-12-25
Just to update:

I uninstalled devede (sudo aptitude remove devede)...after it was done, I was curious so I typed 'devede' into the terminal and BOOM it popped open and worked.  Don't ask me.

I had first tried installing devede from the source I downloaded from their website so I guess that is why it works.  The latest version of devede is 2.8, but in synaptic it says the devede version in the repos is only 2.1...whatever.

-teet

---

### Post by Didge on 2007-08-19
Amazing how that worked for me too. I installed 3.01after downloading it from [http://www.rastersoft.com/descargas/devede-3.01.tar.bz2](http://www.rastersoft.com/descargas/devede-3.01.tar.bz2). Nothing worked so I installed the version from the repositories which is earlier. sudo aptitude remove devede, and then devede version 3.01 fired up fine when I typed sudo devede in a terminal. 

I may be a complete fool but does it render faster than Tmpgenc?

---

