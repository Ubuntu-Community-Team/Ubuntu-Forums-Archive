---
title: "problem installing flashplugin-nonfree"
date: 2009-01-25
forum: Multimedia Software
---

### Post by _zax_ on 2009-01-25
The problem is that i have no sound on firefox's viddeos. 
when i give the folowing command: <sudo apt-get install flashplugin-nonfree>
i'm getting this error:

[B]
Download done.
md5sum mismatch install_flash_player_10_linux.tar.gz
The Flash plugin is NOT installed.[/B]

can you help me?
i'm on Ubuntu 8.10 32bit.

---

### Post by x33a on 2009-01-25
where are you downloading it from?

try installing it through synaptic.

---

### Post by wolfen69 on 2009-01-25
do ```
sudo apt-get update
``` first. 

or go [here]("http://get.adobe.com/flashplayer/") and download the .deb flash file for ubuntu. click to install.

---

### Post by _zax_ on 2009-01-25
thnx for that but i have several problem's

first of all my system is updated so this is'not the problem
i've look for the 'md5sum mismatch' over the internet and i've realised that there is a bug
and someone suggest to download and install manually the install_flash_player_10_linux.tar.gz

in a terminal, unpacking the tar.gz and runing the instaler (./flashplayer-installer). at some point the installer ask for the path of the installation: 

[B]Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):
[/B]
 so i give 

[B]/usr/lib/firefox 
[/B]
and the installer returns

**Warning:insert a valid instalation path.**

after this i close the installer and i give:

**whereis firefox**

so the terminal returns this:
**firefox: /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/share/firefox**

so finally i do this:

[B]root@ubuntu:/# cd /usr/lib/firefox
root@ubuntu:/usr/lib/firefox# ls
extensions  plugins
[/B]

and i go mad because /usr/lib/firefox exists and everything should work fine but nothing works at all

---

### Post by wolfen69 on 2009-01-25
you should use /usr/lib/mozilla

mozilla is the company that makes firefox. you would think that /usr/lib/firefox would work, but that's the way it is.

---

### Post by _zax_ on 2009-01-25
[I]you should use /usr/lib/mozilla

mozilla is the company that makes firefox. you would think that /usr/lib/firefox would work, but that's the way it is. 

[/I]


i have allready done this and the problem is exactly the same


[B]WARNING: Please enter a valid installation path.

[/B]

---

### Post by wolfen69 on 2009-01-25
did you try [this]("http://get.adobe.com/flashplayer/")? download the .deb for ubuntu 8.04+. click to install. then restart firefox if open.

---

### Post by _zax_ on 2009-01-25
> **wolfen69 said:**
> did you try [this]("http://get.adobe.com/flashplayer/")? download the .deb for ubuntu 8.04+. click to install. then restart firefox if open.

but i'm on ubuntu 8.10,  not 8.04.
is this right for me? should it work??

---

### Post by wolfen69 on 2009-01-25
> **_zax_ said:**
> but i'm on ubuntu 8.10,  not 8.04.
is this right for me? should it work??

that's what the + means. 8.04 and beyond. so yes, it will work.

---

### Post by gandaran on 2009-01-25
> first of all my system is updated so this is'not the problem
i've look for the 'md5sum mismatch' over the internet and i've realised that there is a bug
it's not a bug, the flashplugin-nonfree has been updated to the new adobe flash release and you have to update synaptic to get it before installing it
run sudo apt-get update like wolfen69 first posted or click the reload option in synaptic then you can install the new package, remove completely the old one first or you'll land up installing the same one again.

---

### Post by _zax_ on 2009-01-25
i did what you said to : 
sudo aptitude purge flashplugin-nonfree
sudo apt-get update
and then via synaptic install flashplugin-nonfree

and i got again this at the end of the installation:

Download done.
md5sum mismatch install_flash_player_10_linux.tar.gz
The Flash plugin is NOT installed.


thanx anyway for your time both wolfen69 and gandaran

---

### Post by _zax_ on 2009-01-25
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890/comments/296](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890/comments/296)

---

### Post by gandaran on 2009-01-26
> sudo aptitude purge flashplugin-nonfree

no,no, this command is not right it didn't remove the empty/broken flashplugin-nonfree installed, use synaptic and choose complete removal then update and only then install the flashplugin-nonfree, it'll work!

edit:
do you have the security and recommended update channels enabled?

---

### Post by gandaran on 2009-01-26
_zax_  
look if you are running ubuntu 64-bits it's better you install the 64-bits adobe flash 10 beta (the flashplugin-nonfree is 32-bits), get it here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html), download the tar.gz package, extract and just drag the libflashplayer.so file to /home/'user'/.mozilla/plugins or /usr/lib/mozilla/plugins.

---

