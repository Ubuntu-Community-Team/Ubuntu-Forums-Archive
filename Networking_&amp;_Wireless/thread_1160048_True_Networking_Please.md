---
title: "True Networking Please"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by AgentZ86 on 2009-05-15
Hi,

I've noticed over the years with Ubuntu and Gnome that I've not really been able to truely network exactly. Well not without using Smb4K

I sort of understand this has something to do with fuse or something, but anyhow here is the topic:
[LIST]
Typically you should be able to open a document from a networked location.. Ubuntu does not always do this with the default installed network feature. Some files don't open with their default program.[/LIST]
[LIST]
Also you should be able to save files to the network or network share.Default Ubuntu networking options do not do this very well either.Basically you can't save-as to the network, and sometimes even if you open a file with the default program such as OpenOffice you cannot save the changes to the network it always asks you to browse to that location to save the file on the network someplace.Sort of works but only after making browse and jump through a few hoops. It won't just save your changes when clicking the save button.[/LIST]
[LIST]
You should be able to create symlinks on desktop to the network shares and this is not easy either[/LIST]

Anyhow basically I've been using Smb4K to work around this and it does all the things I want, but just wish Ubuntu would have something like this by default.

Is there still no Gnome / Ubuntu version of networking package that will allow you to (open files on the network with default programs, save changes once you open and edit your file, and create symlinks on desktop to the network shares ?

I'm not sure if I'm articulating this sybject well enough, but to clarify the standard network sharing does not let you do some of the simplest tasks as far as I know.
It does let me browse the network etc. but not really complete as Smb4K

Any ideas on this topic ?
I'm not complaining I love using my Ubuntu for the last 4-5 years as my only OS for all my computers.

Thanks

P.S Smb4K allows all documents whether Gnome based or K based to be viewed, saved, edited and also from the smb4K folder you can create symlinks to the desktop for the network share which is really handy.
But I want Gnomified version to match my Ubuntu. Doesn't that exist ?

---

### Post by superprash2003 on 2009-05-15
your right , GNOME needs improvement , especially as of now , it has a LOT of bugs , simple things like browsing network shares dont work well on 8.10  , even trying to directly open a mounted share from the desktop gives an error..

---

### Post by AgentZ86 on 2009-05-19
> **superprash2003 said:**
> your right , GNOME needs improvement , especially as of now , it has a LOT of bugs , simple things like browsing network shares dont work well on 8.10  , even trying to directly open a mounted share from the desktop gives an error..

I wish I knew why ?

I don't think it's a bug though.
I think it's just not full featured as with K Smb4K. 
I installed Smb4K and used it for years and it's fully functional as any network application but I want Gnomified version.
pyNeighborhood for Gnome use to work quite well which was a gnomified LinNeighborhood, but it's old and I don't think it's maintained anymore.

All files open in their designed program, sometimes I have to right click and open with, if I've been opening the file with one app. then edit with another etc etc.

But it is available and works great, however I want Gnomified since I've been using Ubuntu with Gnome. Although I still prefer K over Gnome I've been using Gnome for 4 years now.

---

### Post by netztier on 2009-05-19
> **AgentZ86 said:**
> [LIST]
Typically you should be able to open a document from a networked location.. Ubuntu does not always do this with the default installed network feature. Some files don't open with their default program.[/LIST]


Not Ubuntu's problem in all cases. Gnome-VFS aware applications will show you the network places you conneced to with "Connect to server..." beforehand. The networked drive will show up in their open/save/save as dialog boxes. But of course, the apps need to be aware of Gnome-VFS (or is it fuse? ..not quite sure).

> 
[LIST]
You should be able to create symlinks on desktop to the network shares and this is not easy either[/LIST]

Whenever I access a samba share via "Connect to Server ...", I instantly get a symbol on the desktop for it - no need for a symlink. Same goes for any NFS mounts that have their mountpoints in /media (instead of the more traditional /mnt). That's on a clean 8.10 install.

> 
Is there still no Gnome / Ubuntu version of networking package that will allow you to (open files on the network with default programs, save changes once you open and edit your file, and create symlinks on desktop to the network shares ?


OpenOffice, Gnome's editor, Gimp, totem, Rhythmbox and a lot more are all Gnome-VFS aware - that should include all apps shipped with the default Ubuntu installation. Do a "connect to server..." and mount the samba share. You'll see it appear almost everwhere you open a file or save it. 

Sorry, but I don't quite see the issue? The mechanism/framework for what you ask for does exist in Gnome and it is being actively used. If developpers of third party apps don't make their gtk-based programs aware of Gnome-VFS, it's not Ubuntu's nor Gnome's fault.


regards

Marc



BTW: if you really want something changed, file a bug report or feature request at lauchpad.net. Ubuntuforums.org is not the place where Ubuntu devs hang out.

---

### Post by AgentZ86 on 2009-06-21
> **netztier said:**
> Not Ubuntu's problem in all cases. Gnome-VFS aware applications will show you the network places you conneced to with "Connect to server..." beforehand. The networked drive will show up in their open/save/save as dialog boxes. But of course, the apps need to be aware of Gnome-VFS (or is it fuse? ..not quite sure).



Whenever I access a samba share via "Connect to Server ...", I instantly get a symbol on the desktop for it - no need for a symlink. Same goes for any NFS mounts that have their mountpoints in /media (instead of the more traditional /mnt). That's on a clean 8.10 install.



OpenOffice, Gnome's editor, Gimp, totem, Rhythmbox and a lot more are all Gnome-VFS aware - that should include all apps shipped with the default Ubuntu installation. Do a "connect to server..." and mount the samba share. You'll see it appear almost everwhere you open a file or save it. 

Sorry, but I don't quite see the issue? The mechanism/framework for what you ask for does exist in Gnome and it is being actively used. If developpers of third party apps don't make their gtk-based programs aware of Gnome-VFS, it's not Ubuntu's nor Gnome's fault.


regards

Marc



BTW: if you really want something changed, file a bug report or feature request at lauchpad.net. Ubuntuforums.org is not the place where Ubuntu devs hang out.

Thanks, I'll do that

The mechanism is not there as I've said. 
Although I've noticed with each new version of Ubuntu there appears to be work done on this.

I was never able to use the (save-page-as) feature with Firefox and save to a network share using the standard Gnomified networking versions included with Ubuntu. It would appear this is available now and was a known problem with networking compatibility.

However, when opening OPEN office for example if you try to save-as document and the windows comes up to browse to your folder locations. There still does not appear to be a mechanism which I can browse to save to the network location. 

Try it and see, open up your open office without opening a document from a share just the open office program itself. And then select to save a blank document to your network. You can't because the network folders do not show up. 

Also when you click on a network file many times Open Office tries to startup and then the file never opens. This happens on fresh installation on all the computers I've tried and I've sold many computers. So the solution has been to install Smb4K which I hate doing but do not know of anything else I can do that Ubuntu has by default.

I would love to have all this working if you could point me in the right direction to have the networking capabilities that Smb4K is using which works perfectly whether it's Gnome or KDE programs either one it does not care.

Thanks for the input.

---

