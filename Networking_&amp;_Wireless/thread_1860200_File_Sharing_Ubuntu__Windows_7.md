---
title: "File Sharing Ubuntu / Windows 7"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by leehamer on 2011-10-14
Evening,

I am having a nightmare, all I want to do is share some files on my Ubuntu laptop with my windows 7 laptop (about 15GB of music). I thought this would be simple, but no its certainly isn't!

I have followed numerous guides on Samba but I just cant get it to work... Can some one walk me through it??

---

### Post by collisionystm on 2011-10-14
> **leehamer said:**
> Evening,

I am having a nightmare, all I want to do is share some files on my Ubuntu laptop with my windows 7 laptop (about 15GB of music). I thought this would be simple, but no its certainly isn't!

I have followed numerous guides on Samba but I just cant get it to work... Can some one walk me through it??


Yeah.

Right click on the folder you want to share on ubuntu.

Go to sharing options

share folder.

from windows  go to start, in the search box type run
hit enter
in the run box type

\\ip-address-of-ubuntu

to map your share, just right click on the folder and hit map network drive.

---

### Post by leehamer on 2011-10-14
Thank you so much!!!! 

I have tried all sorts of things, spent ages. Just followed your instructions and it was all done in a second.

I am glad the solution was so simple :)

---

### Post by collisionystm on 2011-10-14
> **leehamer said:**
> Thank you so much!!!! 

I have tried all sorts of things, spent ages. Just followed your instructions and it was all done in a second.

I am glad the solution was so simple :)

It usually is... lol. A lot of things get over complicated really quick on this forum.

---

### Post by leehamer on 2011-10-14
> **collisionystm said:**
> It usually is... lol. A lot of things get over complicated really quick on this forum.

yup, samba installed, numerous ftp clients, some very unusual tricks and tips, lots of shouting, wine consumed and a missus who thinks I am loosing the plot!! :D

---

### Post by collisionystm on 2011-10-14
> **leehamer said:**
> yup, samba installed, numerous ftp clients, some very unusual tricks and tips, lots of shouting, wine consumed and a missus who thinks I am loosing the plot!! :D

haha. Well now you can proudly tell your wife it is finished! .....And then go consume more wine :D

---

### Post by madjr on 2011-10-14
> **collisionystm said:**
> Yeah.

Right click on the folder you want to share on ubuntu.

Go to sharing options

share folder.

from windows  go to start, in the search box type run
hit enter
in the run box type

\\ip-address-of-ubuntu

to map your share, just right click on the folder and hit map network drive.

if you notice ubuntu is usually not the problem, just click on share.

windows is where you need to do the rest.

people usually blame ubuntu / linux...

---

### Post by collisionystm on 2011-10-14
> **madjr said:**
> if you notice ubuntu is usually not the problem, just click on share.

windows is where you need to do the rest.

people usually blame ubuntu / linux...

Actually Windows is pretty easy to! You do the same on there lol.

It's when people start fiddling with samba config files that it gets crazy.

Using the terminal has become sort of a 'right of passage' on here and its the way people like to do things. Thank god there are people like me... :)

---

### Post by madjr on 2011-10-14
> **collisionystm said:**
> Actually Windows is pretty easy to! You do the same on there lol.

It's when people start fiddling with samba config files that it gets crazy.

Using the terminal has become sort of a 'right of passage' on here and its **the way people like to do things**. Thank god there are people like me... :)

correction: it's the way **technocrats** like to do it...

I've seen new users wanting to install 1 common app for ubuntu and these technocrats give them a **compiling guide**... instead of referring them to the software center... (Jesus..)

yes, and thank God for people that understand new users like yourself

---

### Post by collisionystm on 2011-10-14
> **madjr said:**
> correction: it's the way **technocrats** like to do it...

I've seen new users wanting to install 1 common app for ubuntu and these technocrats give them a **compiling guide**... instead of referring them to the software center... (Jesus..)

yes, and thank God for people that understand new users like yourself

technocrats lol. Ill remember that one

---

### Post by leehamer on 2011-10-14
I completely agree, I think that the love of using terminal by a lot of ubuntu users scares people from using it. I try and tell people how good it is but terminal is what puts them off.

Would be nice if people could explain things as easy as it was for me in this thread, more people may turn to ubuntu or other distros! :popcorn:

---

### Post by sdswingr on 2011-10-26
I am having the same problem..so how do I find the ip address of ubuntu?

---

### Post by Steve54 on 2011-10-26
The easiest way is to log into your router and then look in its menu for 'attached devices' (Netgear speak) or something similar.

---

