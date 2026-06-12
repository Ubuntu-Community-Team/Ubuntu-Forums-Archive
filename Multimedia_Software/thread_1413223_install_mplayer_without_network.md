---
title: "install mplayer without network"
date: 2010-02-22
forum: Multimedia Software
---

### Post by axkujur on 2010-02-22
I have installed Ubuntu 8.04.4 LTS Hardy Heron desktop OS in my machine. I do not have internet work connection. How will I install mplayer or vlc player for multimedia. All the sites which I visited for help/tutorial, shows for direct installation of players and their codecs with internet connection by directly downloading them during installtion process.

---

### Post by ldso on 2010-02-22
So you want to put mplayer or vlc on your box using a cd or usb stick, after downloading the files on another computer?  

The problem is, it will take some research to figure out what dependency files you need to install say, vlc.  You will need to install .deb's for all of the libraries that vlc uses.

There is probably a way to run dpkg or apt-cache or apt-get that will tell you what files to download.

If you can burn an ubuntu dvd somewhere it will have the files you need probably?

Hope that helps,
ldso

---

### Post by koleoptero on 2010-02-22
Enter in a terminal:

sudo apt-get install mplayer

It will show what it is going to install along with mplayer. If you get those .deb files from a computer that can go online and install them, then it should work fine.

I have no idea though how you might go ahead and get the .debs from another ubuntu install.

If I had a computer that can't go online at all for whatever reason, I'd follow [this guide]("http://ubuntuforums.org/showthread.php?t=352460") to make a local copy of the ubuntu repositories so that everything is available :) It is a bit hard if don't have a truly fast connection though.

EDIT: Actually, after you see with the "sudo aptitude install mplayer" command which packages it's trying to install, copy the list somewhere, and when you get to a pc that can go online and has the same ubuntu version as you, you can use:

sudo aptitude download *PACKAGE_NAMES*

to download those packages to a local folder and then transfer them to the pc that is offline. Then on that pc install them one by one by double clicking on them or by putting them in a folder and running:

sudo dpkg -i *.deb

which should work but I haven't really tried it. The only problem might be that some of the packages have others as dependencies so they must be installed in some order.

---

### Post by mac9416 on 2010-02-23
Take a look at [Keryx]("http://keryxproject.org"). It allows you to download the .deb files (with dependencies) to a flash drive, then install them on the offline machine.

---

### Post by koleoptero on 2010-02-23
> **mac9416 said:**
> Take a look at [Keryx]("http://keryxproject.org"). It allows you to download the .deb files (with dependencies) to a flash drive, then install them on the offline machine.

Very interesting mac. :D

---

