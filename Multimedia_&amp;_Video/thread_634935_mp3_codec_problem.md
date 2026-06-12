---
title: "mp3 codec problem"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by rpirvu on 2007-12-08
Hello,

I'm very new to Ubuntu and I ran into a problem with the mp3 codec when I installed it. Due to help from a community member I got so far (see below). 

[INDENT]Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
gstreamer0.10-plugins-ugly: Depends: libid3tag0 (>= 0.15.1b) but it is not installable
Depends: libmad0 (>= 0.15.1b) but it is not installable
E: Broken packages[/INDENT]

I then tried this:

[INDENT]sudo apt-get update
sudo apt-get -f install
sudo apt-get install -s gstreamer0.10-plugins-ugly[/INDENT]

and got the same result. Any help will be appreciated:

---

### Post by rpirvu on 2007-12-08
Resolved by installing restricted applications

---

