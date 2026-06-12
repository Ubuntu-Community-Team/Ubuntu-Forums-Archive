---
title: "Installing cinelerra on Ubuntu 10.10 maverick"
date: 2010-09-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by agent_509 on 2010-09-10
I have been trying to get cinerella installed for awhile, and i recently upgraded to maverick, how do I install it? Will I have to compile it from source code?

---

### Post by Sef on 2010-09-10
Moved to MMTnD.

---

### Post by agent_509 on 2010-09-11
help, anyone? I would also like to point out that it wouldn't install on 10.04 either.

---

### Post by SevenMachines on 2010-09-11
Cinelerra seems to work fine using its repositories. See,
[http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu)

I'm sure they'll get a maverick repository once its released. for the moment lucid works fine here

deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-lucid main

---

### Post by agent_509 on 2010-09-11
I mentioned that i also had the same problem with lucid. When I try to reload the sources after putting the repositories in, it says that it could not fetch it with the error 404, not found

---

### Post by SevenMachines on 2010-09-11
Seems strange, i've tried it out here on i386 the lucid repository on maverick and as i said, theres no problem here. I can only think its maybe a typo in your repositories entry or some amd64 problem with the cinelaerra repos. maybe an amd64 user can chip in on that

---

### Post by agent_509 on 2010-09-11
yeah, i use amd64 so maybe it's that...

---

### Post by Gilberg on 2010-10-10
I use i386 and get trouble. 
```
sudo apt-get install cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cinelerra : Depends: libcinelerra (= 2.1.1+git20100325) but it is not going to be installed
E: Broken packages

```
This lib depend libx264-85, but in maverick installed libx264-98.
```
sudo apt-get install libx264-85
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libx264-85 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libx264-85' has no installation candidate

```

---

