---
title: "Failure to install Flash Player"
date: 2009-08-27
forum: Multimedia Software
---

### Post by paulruscito on 2009-08-27
I am about to scrap ubuntu and install Fedora. I downloaded ubuntu three days ago. latest version, 904 I think. I go to an obscure website (Youtube) and try to play a video. Browser tells me that I have Javascript turned off (I don't) or I should get the latest flash player. Try to install the Flash player and I get some dependancy error for "Dependency not satisfiable: libnspr4-dev".

Software update says I am up to date. I want to shoot myself for wasting all this time working on this. I am once again discouraged by Ubuntu's ability to make common user functions work out of the box.

---

### Post by inobe on 2009-08-27
hi and welcome to the forums.

open synaptic package manager.

search for

**ubuntu-restricted-extras**

tick the box next to package and hit apply.

install it.

restart firefox and go to youtube

edit: or open terminal and type

```
sudo apt-get install ubuntu-restricted-extras
```

when prompted type **y**, y means yes' then press enter.

---

### Post by SoftwareExplorer on 2009-08-27
Go to System->Administration->Synaptic Package Manager and search for the package and see if you can find it.

---

### Post by SoftwareExplorer on 2009-08-27
By the way, welcome to the ubuntu forums.:)

---

### Post by paulruscito on 2009-08-28
Tried it with fedora and got it to work relatively easy. Based on their Doc, I understand why it doesn't ship with the distribution. I don't write code for linux but if I did, I would write a tool that prompted you on startup to install licensable software like popular video codecs, sound drivers etc, you know, all the Adobe, Apple and Microsoft stuff. Not a tool that installs everything under the sun tool but a tool that picks the five most popular items and walks a user through installing thempopular tool. I am sad that this is my fourth time trying Ubuntu and I failed again. Still not user friendly enough for me.

The responsiveness of the team on this list is wonderful. Something to be proud of. 

Thank you.

---

