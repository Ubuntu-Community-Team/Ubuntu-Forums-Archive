---
title: "What format should my music be in?"
date: 2009-01-07
forum: Multimedia Software
---

### Post by killbydemons on 2009-01-07
This a more general question, but I'm wondering what digital music format (mp3/wmv/etc) is the "best".  I ask because I've been ripping all my music in windows in .wmv 320 kbps, which was fine until I tried playing the .wmv files with amarok, and it said I didn't have the necessary codecs.  Would amarok read .mp3 files just fine...should all my music be .mp3? Thanks.

---

### Post by Therion on 2009-01-07
Keep your .wmv files if you like.  Just use Synaptic and search on **w32codec**.  It should pull up the package, or packages, you need to play that particular format.  You might also search for and install **ubuntu-restricted-extras** while you've got Synaptic open.



Edit:  You know what, just install **ubuntu-restricted-extras**.  That's the only package you'll need.  Do it the easy way:```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by killbydemons on 2009-01-07
i've already installed ubuntu-restricted-extras...it was one of the first things i did after installing Ubuntu.

---

### Post by wolfen69 on 2009-01-07
i'm assuming your using ubuntu 8.10

if so, do
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```
then
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
then search synaptic for w32codecs. you will then be able to play wma files.

---

### Post by killbydemons on 2009-01-08
okay, i installed the medibuntu-keyring, and tried installing w32codec.  but a synaptic search for w32codecs gave me the non-free-codecs package..which i already had installed.  also, the description for the non-free-codecs package said that i would need w32codecs for i386 ubuntu, 32 bit, and w64codecs for amd64.  I should have said earlier that i have 64 bit ubuntu installed, not 32 bit. so when i searched synaptic for w64codecs, i found that it was already installed.

amarok though, still won't play my .wma files. is it because i have 64 bit ubuntu? does amarok not work with 64 bit?

---

