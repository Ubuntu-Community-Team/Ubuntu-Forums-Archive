---
title: "Java Help."
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by Linux Loser on 2008-01-07
Ok, Well I'm a noob at this and I just installed Linux a few days ago. So, I don't know all the codes and stuff. 

Well. I tried installing Java so I can play a game. I sort of followed the instructions the best I could, but I didn't have much luck.

I have no idea what I'm doing. So, please help me. :lolflag:

---

### Post by TKill on 2008-01-07
System menu -> Administration -> Synaptic Package Manager
Find and install the package "sun-java6-bin"

---

### Post by Linux Loser on 2008-01-07
Didn't work.

Wouldn't let me install it for some reason.

---

### Post by Linux Loser on 2008-01-08
Ok well i've installed every java program that you can install.

And nothing, the game I want will still not load. Its not the game either because other java apps wont work. And I don't know how to get Frostwire to work either.

---

### Post by djbsteart1 on 2008-01-08
frostwire or limewire both need java so wont work until it is installed, you can install java in the terminal with this, it worked for me in both fiesty and dapper. 
sudo apt-get install sun-java6-jdk sun-java6-plugin
hope this works ok

---

### Post by jespdj on 2008-01-08
> **Linux Loser said:**
> Didn't work.

Wouldn't let me install it for some reason.
Did you get an error message? If so, then what is the error message? It's a bit hard to help you if you're being so vague.

What happens if you try this?
```
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin
```
If this works without any errors, then make sure that Sun Java 6 is the default Java used on your system by executing:
```
sudo update-alternatives --config java
```
Select Sun Java 6 in the menu that appears.

---

### Post by djbsteart1 on 2008-01-08
ah my bad i missed the apt update, if that doesnt work check that the back ports are configured to allow updates in system - admin and then try again from synaptic. search for java otherwise it will take ages.

---

