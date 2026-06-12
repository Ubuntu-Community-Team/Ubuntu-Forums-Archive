---
title: "Can't find libmp3lame.so to use with Audacity in Xubuntu"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by bobdc on 2007-08-24
I'm using Xubuntu, and ran all system updates before installing Audacity, and I want to convert a file recorded with Audacity to MP3, and Audacity wants to know where to find libmp3lame.so. I've done the equivalent addition of lame to Audacity on Windows machines many times. 

I tried installing lame with both the Synaptic Package manager and with "sudo apt-get install lame", and both seemed to install successfully, using the "Search for Files" utility to search the whole hard disk for a file with "lame" in it doesn't find the so file. 

Any suggestions? 

thanks,

Bob

---

### Post by Amazona aestiva on 2007-08-24
You need this:

i386:[http://ftp.kfki.hu/linux/ubuntu/pool/multiverse/l/lame/liblame-dev_3.96.1-2ubuntu1_i386.deb]("http://ftp.kfki.hu/linux/ubuntu/pool/multiverse/l/lame/liblame-dev_3.96.1-2ubuntu1_i386.deb")
or
amd64:[http://ftp.kfki.hu/linux/ubuntu/pool/multiverse/l/lame/liblame-dev_3.96.1-2ubuntu1_amd64.deb]("http://ftp.kfki.hu/linux/ubuntu/pool/multiverse/l/lame/liblame-dev_3.96.1-2ubuntu1_amd64.deb")

The file should be in /usr/lib/ after install!

---

### Post by bobdc on 2007-08-24
That worked, thanks!

Bob

---

### Post by Amazona aestiva on 2007-08-24
Hooray!
=D>=D>=D>
I advise a link in my signature!

---

### Post by devi on 2007-09-05
Worked for me too! Thanks!

---

### Post by kvarley on 2007-09-15
This worked for me too, you're a god, I used it for Ubuntu Feisty.

---

### Post by marn on 2007-09-25
After "sudo apt-get install lame" which worked OK, Audacity still couldn't find what it was looking for. 

Chose "Extended files" in the Audacity Mp3 setup (Preferences > File Formats > Mp3 Export Setup > Find Library) and selected "libmp3lame.so.0" Everything works fine. Don't know why the file has a "0" at the end though.

---

### Post by mdren68 on 2007-11-22
Uh-oh.  My package installer gives me an this:
[COLOR=Red][SIZE=3]Error: Dependency is not satisfiable: liblame0
[COLOR=Black][SIZE=2]
I have just installed 'Gutsy Gibbon' 7.10.  What else do I need to do to get Audacity up to speed with MP3s?
[/SIZE][/COLOR][/SIZE][/COLOR]

---

