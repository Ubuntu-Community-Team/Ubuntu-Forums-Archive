---
title: "No sound after"
date: 2009-10-25
forum: Multimedia Software
---

### Post by CamiloSmurf on 2009-10-25
I'm running 9.04 on my Acer Aspire One. Sometimes when I turn my computer on the sound is static which is fixed by adjusting the PCM on the volume control.

However, when I suspend my session and then come back to it, I lose all sound. Video, testing, music, whatever, doesn't make a peep, and if I want to listen to something I have to reboot.

Any suggestions as to how I can get this working? I'm extremely new to Ubuntu, btw.

---

### Post by ScarySquirrel on 2010-04-23
Oh yeah it's easy. Just get a backported kernel, upgrade alsa-kernel-module-452665, and you're set! Make sure to make a backup of the previous kernel in a separate partition in case you have broken packages. 
Also make sure to install and update your kernel headers. And run dpkg. And be a genius. 



...


Just kidding. Try a 3rd party suspend tool. I have read good things about the [tux that is on ice]("http://www.tuxonice.net/"). On their web site.

This may help explain what I'm talking about: 
[IMG]http://icanhascheezburger.files.wordpress.com/2010/04/funny-pictures-cat-does-not-care.jpg[/IMG]

---

