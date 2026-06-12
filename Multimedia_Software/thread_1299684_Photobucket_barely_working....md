---
title: "Photobucket barely working..."
date: 2009-10-24
forum: Multimedia Software
---

### Post by Pott on 2009-10-24
It doesn't work at all with FF 3.0.14 (I don't know how to upgrade to 3.5, none of the instructions I got worked). It works with Shiretoko but it greys out the FF window while the picture uploads, which is rather annoying...

Anybody also encounter that?

---

### Post by eaglemob on 2009-10-24
Updates from server in terminal
Example:

To install the latest Firefox 3.5 (final) 
or Firefox 3.6 in Ubuntu, open a terminal and type:

sudo sh -c "echo 'deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list"
sudo sh -c "echo 'deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list"

Then add the Launchpad PPA GPG key:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE

And finally, install Firefox 3.5 or 3.6
sudo apt-get update && sudo apt-get install firefox-3.5

or
sudo apt-get update && sudo apt-get install firefox-3.6

If you already have a version of Firefox 3.5 installed from a repo then
upgrade it:

sudo apt-get update && sudo apt-get upgrade

I hoop it works for ya.

Good luck :)

---

