---
title: "Install gnomebaker in precise"
date: 2012-05-14
forum: Multimedia Software
---

### Post by slumbergod on 2012-05-14
Credit where credit is due. I followed the instructions listed here:
[http://www.liberiangeek.net/2012/04/how-i-installed-gnomebaker-in-ubuntu-12-04-precise-pangolin/]("http://www.liberiangeek.net/2012/04/how-i-installed-gnomebaker-in-ubuntu-12-04-precise-pangolin/")

For the last two releases of ubuntu I have had a lot of trouble writing DVDs. Brasero has always been crap for me. Xfburn is also unreliable. Usually, Nero works but, of course, it isn't free.

The problem isn't my laptop's DVD writer; it is something to do with the kernel and how it interacts with the writer. I always get "Power Calibration" errors.

So a solution is to go back to the good ol' reliable gnomebaker which is not in the repos any more. Solves my problems and maybe it'll solve yours too.
1. sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 8472BD8C
2. gksudo leafpad /etc/apt/sources.list.d/gnomebaker.list
3. Add
deb [http://ppa.launchpad.net/gnomebaker/stable/ubuntu](http://ppa.launchpad.net/gnomebaker/stable/ubuntu) oneiric main 
4. sudo apt-get update && sudo apt-get install gnomebaker

---

