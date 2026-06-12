---
title: "Is it ok to remove Rythmbox from Trusty 14.04 ?"
date: 2014-09-25
forum: Multimedia Software
---

### Post by Cbhihe on 2014-09-25
Hi, I just decided to replace _*Rythmbox*_ by _*Clementine*_ hoping it would offer better integration with my iPod Classic 6th gen., by that I mean "better sync functionality" of whatever comes close to it. (Any opinion on the subject are welcome although this is not what my question is really about).

I want to rid my machine of *_Rythmbox_*, for which I have no use, even though I like its simple interface. 
[B]
Q)[/B] Can I just go ahead and do ?
```
sudo apt-get remove rythmbox
```
or is it preferable to do ?
```
sudo apt-get purge rythmbox
```

Not knowing exactly what all the dependencies for the *_Rythmbox_* package are, I am concerned that a 'purge' could actually purge pieces and bits that are useful for *_Clementine_* or other applications I have (*_Skype_*, etc.). I guess I don't know how purge really works...

Thanks.

---

### Post by ajgreeny on 2014-09-25
Purge will never remove a package that is a dependency of something else, so in that respect you can rest easy.

Of course you can remove rhythmbox if you really want to. If it looks as if it takes ubuntu-desktop with it when removed don't panic; that is a meta-package and contains nothing but a list of the dependencies of ubuntu-desktop, it does not mean that your ubuntu-desktop system has also been removed.

Your choice whether you remove or purge; all the remove command leaves behind are the config files and folders for RB that are in the system folders; it does not remove anything from your /home folder or partition.

---

### Post by Cbhihe on 2014-09-25
Thanks. I understand the difference now. 
But do those "config files" left by remove and effectively removed by purge include any previously constructed RB database for instance ? If so I would certainly favor "purging" rather than "removing".
Also, is there a way to actually see all dependencies for a given package (from the command line or from the gui) ? -ced

---

### Post by ajgreeny on 2014-09-25
Synaptic is the best GUI package manager around in my opinion, and if set to show package properties in the bottom panel will show you all the dependencies of any highlighted package.

I am not sure about the databases in RB config folders etc etc, and I don't use RB in Xubuntu so can't help with that.

I don't know any way to simply list the dependencies of a package in command line, but I will be surprised if it can't be done.
Yes a quick search for my own information shows that ```
apt-cache depends *packagename*
``` will list this for you

---

### Post by Cbhihe on 2014-09-25
It does list all in command mode. I checked the man page to understand the various tags 'apt-cache depends [dpkg]' shows in its output.
Thank you @ajgreeny

---

### Post by ian-weisser on 2014-09-25
> **Cbhihe said:**
> do those "config files" left by remove and effectively removed by purge include any previously constructed RB database for instance ?

Not really.

--remove removes all the package files EXCEPT those in /etc and /home
--purge removes all the package files EXCEPT those in /home
No package management command removes the files in /home . Only you can do that, manually.

Rhythmbox's system-level configs, if any, will be in /etc
All user-level configs, including the music database, will be in /home



> **Cbhihe said:**
> is there a way to actually see all dependencies for a given package?

There sure is.

The dependencies for each package is stored in a database maintained by dpkg. You can easily query that database:
```
$ apt-cache depends rhythmbox
$ apt-cache rdepends rhythmbox
```

'depends' tells you which packages rhythmbox depends upon.
'rdepends' tells you which packages depend upon rhythmbox.

---

### Post by Cbhihe on 2014-09-26
That definitely puts me on the right track. Thanks @ian-weisser. 

Although version numbers would be needed for direct and reverse dependencies in order to make unequivocal sense of breaks and conflicts. 

... I just found out on a [Stackexchange]("http://serverfault.com/questions/477089/apt-cache-under-debian-6-0-displays-a-packet-both-as-a-dependency-and-conflict-a") that the 'apt-cache show [pkg]' actually provides all version info for dependencies and that chapter 7 of the [_*Debian Policy Manual*_]("http://www.debian.org/doc/debian-policy/ch-relationships.html") is the ultimate reference for all of it, as noted on Ayman Farhat's [blog's page]("http://thecodeship.com/gnu-linux/understanding-apt-cache-depends-output/").

[TOPIC CLOSED]

---

