---
title: "sxiv install issues"
date: 2019-09-15
forum: Multimedia Software
---

### Post by plutobuntu on 2019-09-15
Hi! I'm fairly new to Ubuntu, I've installed many apps through terminal or store, but I always struggle with the packages. I'm using Xubuntu now, just saying in case it makes a difference.

Was trying to install sxiv which I downloaded from here: [https://github.com/muennich/sxiv](https://github.com/muennich/sxiv)

But as much as I try to follow the instructions, I can't install it with the commands provided in the instructions.

---

### Post by howefield on 2019-09-15
Help others to help you by providing the terminal input/output up to the point of you getting stuck.

---

### Post by coffeecat on 2019-09-15
> **plutobuntu said:**
> 
But as much as I try to follow the instructions, I can't install it with the commands provided in the instructions.

Simple answer: don't.

You are making a common newbie error, that of trying to compile an app from source, when all you have to do is to use the package manager that came with Xubuntu. The app sxiv is in the repositories, so it is just a couple of clicks away. It couldn't be easier.

That being said, I don't use Xubuntu, so I'm not sure which package manager comes in Xubuntu, or where you find it in the menu system. No doubt an Xubuntu user will be along shortly to guide you.

Please post the release version of Xubuntu you are using (16.04, 18.04, 19.04). We need to make sure you aren't making another newcomer mistake, that of trying to use an obsolete release.

---

### Post by Holger_Gehrke on 2019-09-16
@coffecat: yes, sxiv is in the repos, but XUbuntu comes with gnome-software by default which won't show it since it doesn't have appstream metadata ...

@plutobuntu: coffecat is right, unless you've got very good reasons you shouldn't install from source. Installing from the repositories is easier, can make updates in case of bugfixes automatic (although only certain very bad kinds of bugs are fixed for programs in the repos) and uninstalling programs you don't want / need any more is just as easy as installing them. For most major programs you can use a program that should be in the menu as "Software", but a lot of minor or technical programs aren't shown in that (on the other hand "Software" makes the difference between .deb-packages, snap-packages and --if you've got that installed -- flatpaks transparent, so it does have it's uses). You can either install synaptic - which is another installation tool, which will "see" the .deb-packages "Software" doesn't - or install from the command line. Since Synaptic should be shown in "Software", I'll only tell you how to install from the CLI. Open a terminal, and enter```
sudo apt update
```You will be asked for your password. For security reasons the password will not be shown on screen at all. After hitting enter this will update the local lists of available programs. Next enter ```
sudo apt install sxiv
```This will download the program and any libraries it needs and install. That's it, you're done. 

In case you want to install something else: 'apt search' followed by a search term will list packages that have the term either in their name or description and 'apt info' followed by a package name will output most everything you might want to know about a package.

Holger

---

### Post by plutobuntu on 2019-09-16
> **Holger_Gehrke said:**
> @coffecat: yes, sxiv is in the repos, but XUbuntu comes with gnome-software by default which won't show it since it doesn't have appstream metadata ...

@plutobuntu: coffecat is right, unless you've got very good reasons you shouldn't install from source. Installing from the repositories is easier, can make updates in case of bugfixes automatic (although only certain very bad kinds of bugs are fixed for programs in the repos) and uninstalling programs you don't want / need any more is just as easy as installing them. For most major programs you can use a program that should be in the menu as "Software", but a lot of minor or technical programs aren't shown in that (on the other hand "Software" makes the difference between .deb-packages, snap-packages and --if you've got that installed -- flatpaks transparent, so it does have it's uses). You can either install synaptic - which is another installation tool, which will "see" the .deb-packages "Software" doesn't - or install from the command line. Since Synaptic should be shown in "Software", I'll only tell you how to install from the CLI. Open a terminal, and enter```
sudo apt update
```You will be asked for your password. For security reasons the password will not be shown on screen at all. After hitting enter this will update the local lists of available programs. Next enter ```
sudo apt install sxiv
```This will download the program and any libraries it needs and install. That's it, you're done. 

In case you want to install something else: 'apt search' followed by a search term will list packages that have the term either in their name or description and 'apt info' followed by a package name will output most everything you might want to know about a package.

Holger

Thank you! It worked.

---

