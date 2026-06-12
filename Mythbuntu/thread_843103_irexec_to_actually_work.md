---
title: "irexec to actually work"
date: 2008-06-27
forum: Mythbuntu
---

### Post by IndieRockSteve on 2008-06-27
well, I've tired putting it in the rc.local file, then tried to do it as 
sudo -u myuser
but it seems as though the only way to get
irexec -d ~/.lirc/lircrc
to work is to run a terminal and run it manually.

so, how do i get irexec to run on the local machine when my main user automatically logs in?

---

### Post by tgm4883 on 2008-06-28
IIRC, if you map a irexec command to a remote key it will automatically start at boot.  I don't remember having to do anything extra on my install.

---

### Post by freymann on 2008-06-29
> **tgm4883 said:**
> IIRC, if you map a irexec command to a remote key it will automatically start at boot.  I don't remember having to do anything extra on my install.

This was true in 7.10 but not under 8.04.

I had to load irexec via /etc/rc.local in order for my mapped keys, using irexec commands, to work.

For the OP, this was the command line I used:

/usr/bin/irexec -d /home/freymann/.mythtv/lircrc

Maybe that will help you.

---

### Post by gfowler on 2008-06-29
> **IndieRockSteve said:**
> well, I've tired putting it in the rc.local file, then tried to do it as 
sudo -u myuser
but it seems as though the only way to get
irexec -d ~/.lirc/lircrc
to work is to run a terminal and run it manually.

so, how do i get irexec to run on the local machine when my main user automatically logs in?

Try:

su -c '/usr/bin/irexec -d /home/username/.lircrc' -l username

in /etc/rc.local

Jerry

---

### Post by tgm4883 on 2008-06-29
> **freymann said:**
> This was true in 7.10 but not under 8.04.

I had to load irexec via /etc/rc.local in order for my mapped keys, using irexec commands, to work.

For the OP, this was the command line I used:

/usr/bin/irexec -d /home/freymann/.mythtv/lircrc

Maybe that will help you.

Again, I would venture that is not the case.  I didn't use irexec until 8.04 and it is working on both systems that were upgraded from 7.10 and clean installs of 8.04

---

### Post by freymann on 2008-06-30
> **tgm4883 said:**
> Again, I would venture that is not the case.  I didn't use irexec until 8.04 and it is working on both systems that were upgraded from 7.10 and clean installs of 8.04

 I guess this is a case of your mileage may vary! :-)

 Everything worked fine for me in 7.10.

 I upgraded 3 machines to 8.04 and lost my programmed keys.

 Adding irexec to rc.local was the solution that worked for me.

 Perhaps this is a bug of some kind?

---

### Post by IndieRockSteve on 2008-09-14
rc.local didn't work for me, I ended up having to make a ".desktop" link for it and putting that file in ~/.config/autostart which got it to run properly.

---

