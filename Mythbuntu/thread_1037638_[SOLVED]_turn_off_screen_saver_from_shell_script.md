---
title: "[SOLVED] turn off screen saver from shell script"
date: 2009-01-12
forum: Mythbuntu
---

### Post by lmclaren on 2009-01-12
Hi,

I run a shell script that turns on my television from the remote control via an IR blaster and would like to turn off the screen saver from the same batch file.

I have tried options with xset like turning of dpms and the screen save but they dont work, I have tried sending keys to Mythtv via the network control and that wont turn off the screen saver.

Can anyone shed some light on how it works and how I might turn it off via a batch file.

thanks

Lee

---

### Post by kaibob on 2009-01-12
I'm not familiar with mythbuntu, but if it's similar to Ubuntu you may want to look at the gnome-screensaver-command. It has deactivate and inhibit options.

[http://linux.die.net/man/1/gnome-screensaver-command](http://linux.die.net/man/1/gnome-screensaver-command)

---

### Post by lmclaren on 2009-01-13
Thanks Kaibob,

That got me onto the right track, looks like you need to do the following as the user that runs the Mythtv front end:

xset dpms force on
export DISPLAY=:0 && gnome-screensaver-command -p

All working fine now.

:)

---

