---
title: "Ubuntu 11.0.4 beta &amp; 2 Dvd movie playback"
date: 2011-04-21
forum: Multimedia Software
---

### Post by Tommykry on 2011-04-21
Hi all, i'm new to Ubuntu 11.0.4 beta 2, just installed it and so far really like it! Everything seems to be working great, My question is i can't get movie dvd's to play, when i try it says:Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed.
I Tried installing a ton of things and codecs and vlc player but still not working.
Can some one show me a easy step by step way of getting this working?
I've used Pclos 2011 and Mint Linux and its always just worked out of the box with these distros. Any help would be greatly appreciated.:D
Tommy

---

### Post by aromo on 2011-04-21
Due to licensing issues, DVD's won't play in *ubuntu out of the box.  Open a terminal and run ```
sudo apt-get install ubuntu-restricted-extras
``` and that should do the trick.

---

### Post by rg4w on 2011-04-21
Right now, when we try to play a commercial DVD without the restricted extras it just fails without letting the user know how easily fixable that problem is.

Would it violate the licenses involved if a dialog was presented offering to download the restricted extras for the user?

Requiring millions of people to hunt down this answer in forums seems a suboptimal solution.

---

### Post by Tommykry on 2011-04-21
Aromo, thank you, i tried exactly what you said and it said i already had the newest versions: tommy@tommy-Shadow-K8:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for tommy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tommy@tommy-Shadow-K8:~$
Anymore ideas?:(
rg4w +1
Thanks guys for your help.
Anyone else have any suggestions?
Thanks, 
Tommy

---

