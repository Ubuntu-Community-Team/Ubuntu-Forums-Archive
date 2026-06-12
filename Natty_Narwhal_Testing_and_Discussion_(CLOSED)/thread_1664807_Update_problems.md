---
title: "Update problems"
date: 2011-01-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by popeblack on 2011-01-11
Hi,

I am new to Ubuntu and this forum and I would be very grateful for a bit of advice. 

[I] just tried to upgrade to 10.04 and somehow managed to upgrade to  11.4. It seems to be working ok except for the fact I can't upgrade,  open the Ubuntu Software Center, and when I try and do upgrades through  the terminal, I can't type my password in. It just won't let me. 


I'm not really a computer geek but instead of going through the hassle of reinstalling 10.04, I've decided to stick it out.

Anyone had the above problems or have any advice?

SLÄCK/LÜCK,
PopeBlack[/I]

---

### Post by Kirboosy on 2011-01-11
When you say that it won't let you upgrade in terminal what is the error its giving you?

---

### Post by popeblack on 2011-01-11
I get no error. In the termnal, it will let me type in code but when I'm prompted for my password, it won't let me type it in.  When I go to the software center, to try and download programs, it won't open.

---

### Post by Kirboosy on 2011-01-11
Try updating it Via Update Manager

I'm assuming you are using gnome
System --> Administration --> Update Manger


Just a quick FYI. In terminal when you type in any password it looks like you aren't typing anything but you really are. Its a security thing to not show the character amount. I bet if you type your password without looking at the screen and push enter it will take off. :)

---

### Post by popeblack on 2011-01-11
> **Caboose885 said:**
> Try updating it Via Update Manager

I'm assuming you are using gnome
System --> Administration --> Update Manger


This is the first thing I tried. It won't open. 


Just a quick FYI. In terminal when you type in any password it looks like you aren't typing anything but you really are. Its a security thing to not show the character amount. I bet if you type your password without looking at the screen and push enter it will take off.


 :)

I tried this too. Nothing. It's not letting me type my password at all.  It's as if the entire functue of updates is inoperable. I would like to  mention here that I have done this on 2 different computers and have the  same problem.

---

### Post by Kirboosy on 2011-01-11
Interesting. Maybe you should file a bug with the Ubuntu developers. 
[U]
[https://bugs.launchpad.net/](https://bugs.launchpad.net/)[/U][]("http://%22https://bugs.launchpad.net/")

---

### Post by cariboo on 2011-01-11
> **popeblack said:**
> I tried this too. Nothing. It's not letting me type my password at all.  It's as if the entire functue of updates is inoperable. I would like to  mention here that I have done this on 2 different computers and have the  same problem.

What happens when you type your password? What commands are you using to try and update.

Personally I install aptitude, as it isn't installed by default any more, then type:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

when updating from a terminal, otherwise I use System->Administration->Synaptic Package Manager to do my 3 times daily updates.

---

### Post by popeblack on 2011-01-12
This helped the most. Thanks

> **cariboo907 said:**
> What happens when you type your password? What commands are you using to try and update.

Personally I install aptitude, as it isn't installed by default any more, then type:

```
sudo aptitude update && sudo aptitude safe-upgrade
```when updating from a terminal, otherwise I use System->Administration->Synaptic Package Manager to do my 3 times daily updates.

---

