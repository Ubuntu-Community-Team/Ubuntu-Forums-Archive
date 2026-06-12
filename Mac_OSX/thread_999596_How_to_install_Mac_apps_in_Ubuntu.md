---
title: "How to install Mac apps in Ubuntu"
date: 2008-12-02
forum: Mac OSX
---

### Post by azwar on 2008-12-02
Is there in any way I can install mac osx software in ubuntu? Or maybe any compatibility layer like wine?

---

### Post by EnGorDiaz on 2008-12-02
seemings as osx is unix it shouldnt be too hard porting files but you will need a darwin kernel editor are oyu looking to use leopard apps? bcus it will take more work than you think but its possible my friend just mount the dmg file and try and use the files from there im saying good luck and also look at projects like gnustep they can help you with this

---

### Post by 3rdalbum on 2008-12-02
> **azwar said:**
> Is there in any way I can install mac osx software in ubuntu? Or maybe any compatibility layer like wine?

No. Mac OS X software uses a proprietary API called Cocoa, that has not been reimplemented anywhere. OS X-native programs use a different sort of executable format to Linux, so double-clicking on them in Linux will just tell you that it couldn't find a suitable application for the file.

To the other poster: Just because Darwin is sorta similar-ish to FreeBSD, it does not make it binary compatible to FreeBSD. And FreeBSD programs are not binary compatible to Linux. Mac OS X is a "certified Unix" but so is Windows Server, which gives you an idea about what use that certification really is!

---

### Post by bashveank on 2008-12-02
> **3rdalbum said:**
>  so is Windows Server

[No it's not.]("http://www.opengroup.org/openbrand/register/")

---

### Post by 3rdalbum on 2008-12-04
> **bashveank said:**
> [No it's not.]("http://www.opengroup.org/openbrand/register/")

My mistake, the sentence was originally going to say that it was POSIX-certified "and so is Windows server", but I must've had a lapse.

Go onto a Mac OS X system, start up a terminal, and do the following commands:

```
cd /
sudo ls

```

Does it look much like a Unix system? Why don't you cd into "/Libraries" and look now? Or, better yet, look at a list of Apple's recent security advisories and compare that to one from, say, Sun. Why not run CDE on Mac OS X?

Mac OS X is Unix-like, but it's less Unix-like than Linux.

---

### Post by x0as on 2008-12-06
> **3rdalbum said:**
> 

Go onto a Mac OS X system, start up a terminal, and do the following commands:

```
cd /
sudo ls

```

Does it look much like a Unix system? 

Yes it does.

> **3rdalbum said:**
> Mac OS X is Unix-like, but it's less Unix-like than Linux. 

In what way is OS X less unix like?

---

### Post by cardinals_fan on 2008-12-07
> **x0as said:**
> Yes it does.



In what way is OS X less unix like?
What was the output of ls?

---

### Post by 3rdalbum on 2008-12-08
Go to your Linux system and run the following command:

```
ls / | grep "Applications"
```

Mac OS X is less Unix than Linux.

---

### Post by bashveank on 2008-12-08
> **cardinals_fan said:**
> What was the output of ls?

.DS_Store
.Spotlight-V100
.SymAVQSFile
.Trashes	
.VolumeIcon.icns
.\debugdata\debug.txt
.com.apple.timemachine.supported
.fseventsd	
.hotfiles.btree
.vol
Applications
Desktop DB	
Desktop DF	
Developer	
Library
Network
System
User Guides And Information
Users
Volumes
bin
cores
dev
etc
home
mach_kernel
mach_kernel.ctfsys
net
private
sbin
tmp
usr
var


> **3rdalbum said:**
> Go to your Linux system and run the following command:

```
ls / | grep "Applications"
```

Mac OS X is less Unix than Linux.

So because an OS that is not Unix, but Unix-like, doesn't have a folder that an OS that IS Unix does have the Unix OS is less like Unix than the Unix-like OS?

---

### Post by Comhra on 2008-12-08
> **azwar said:**
> Is there in any way I can install mac osx software in ubuntu? Or maybe any compatibility layer like wine?

First thing is that you need to install X11 if you haven't already done so then check the Fink project out.

 [http://www.finkproject.org/](http://www.finkproject.org/)

---

### Post by bashveank on 2008-12-08
> **Comhra said:**
> First thing is that you need to install X11 if you haven't already done so then check the Fink project out.

 [http://www.finkproject.org/](http://www.finkproject.org/)


X11 is installed by default in Leopard. Besides, he doesn't want to install Linux apps in OS X, he wants to install OS X apps in Leopard.

---

### Post by Comhra on 2008-12-09
> **bashveank said:**
> X11 is installed by default in Leopard. Besides, he doesn't want to install Linux apps in OS X, he wants to install OS X apps in Leopard.

I just realised, I wanted to do the opposite, install Linux apps on Mac.  My mistake.

---

### Post by flynnguy on 2008-12-10
Check out darwinports:
[http://darwinports.com/](http://darwinports.com/)

or fink:
[http://www.finkproject.org/](http://www.finkproject.org/)

That's the easiest way to do what you want.

---

### Post by flynnguy on 2008-12-10
also you can install most linux apps from source but sometimes they require a bit of patching. (That's what fink and darwinports do)

And a binary linux app I don't think will run on OS X so you'll need the source code. (ie. all open source projects)

---

### Post by thomashome on 2008-12-12
wrong! Mac OS X is Aqua UI the only .app you can run is the NeXT Step one's the Aqua one's are a bit more integrated into Aqua. X11 and Darwin won't work either.

---

