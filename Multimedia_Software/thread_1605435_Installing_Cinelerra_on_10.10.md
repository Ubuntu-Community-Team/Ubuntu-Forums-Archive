---
title: "Installing Cinelerra on 10.10"
date: 2010-10-25
forum: Multimedia Software
---

### Post by MyHardDrive on 2010-10-25
Hello all,

I've installed Ubuntu 10.10 on my harddrive and want to install Cinelerra (CV).
I'd followed the steps on there website, but it doesn't seem to work for me.

Since they haven't upgraded there version to 10.10, you are stuck with all the old dependencies.

I needed to install: libcinelerra.
Searched it, but this libary needed libx264-85, which I cannot find in Synaptic.
Probably because it is and 10.04 libary.

I do have libx264-9x.

How can I still install this program?

Thanks!


Thomas

---

### Post by Rogueninja64 on 2010-10-26
I am also curious how to solve this dependency issue i have libx264-98 much more up to date and no longer is there a package allowing me to get libx264-85. i have spent the better part of today trying to compile cinelerra 4.2 with out any luck i keep failing there and would just like to get my open source video editor back in action.

---

### Post by beccatoria on 2010-11-03
Hi guys - I had the same problem after updating to 10.10 today.  I fixed it by installing libx264-85 from the old lucid repositories.  I added the following repository to the synaptic package manager: 

deb [http://*cz.archive.ubuntu.com/ubuntu](http://*cz.archive.ubuntu.com/ubuntu)* lucid main universe

Then reloaded, searched for libx264-85 and it let me install it.  After that Cinelerra installed without difficulty.  

I'm not sure if that means I'm now using a substandard version of libx264 or if it'll cause long term issues, but at the moment it seems to have fixed my issues.  

Apparently, Cinelerra 2.1.5 should be coming out soon which is apparently focusing on fixing these kinds of issues?

---

### Post by harishkr on 2011-02-12
> **MyHardDrive said:**
> Hello all,

I've installed Ubuntu 10.10 on my harddrive and want to install Cinelerra (CV).
I'd followed the steps on there website, but it doesn't seem to work for me.

Since they haven't upgraded there version to 10.10, you are stuck with all the old dependencies.

I needed to install: libcinelerra.
Searched it, but this libary needed libx264-85, which I cannot find in Synaptic.
Probably because it is and 10.04 libary.

I do have libx264-9x.

How can I still install this program?

Thanks!


Thomas
you can download cinelerra packages here .....
[https://launchpad.net/~cinelerra-ppa/+archive/ppa/+buildjob/2136899](https://launchpad.net/~cinelerra-ppa/+archive/ppa/+buildjob/2136899)
download the packages at the bottom of the link given above..

copy downloaded packages to a folder named 'packages' in your desktop..
then go to Application->Accessories->Terminal

type the following in terminal

$ cd Desktop/packages

$ sudo dpkg -i *


now you are done with installing cinelerra.....in ubuntu 10.10

---

### Post by Swagman on 2011-02-12
> **harishkr said:**
> you can download cinelerra packages here .....
[https://launchpad.net/~cinelerra-ppa/+archive/ppa/+buildjob/2136899](https://launchpad.net/~cinelerra-ppa/+archive/ppa/+buildjob/2136899)
download the packages at the bottom of the link given above..

copy downloaded packages to a folder named 'packages' in your desktop..
then go to Application->Accessories->Terminal

type the following in terminal

$ cd Desktop/packages

$ sudo dpkg -i *


now you are done with installing cinelerra.....in ubuntu 10.10

Well that did install it so now how do we uninstall it because it's just as b0rked as it was.

ie: click on ANY menu and it just glows. No drop down menu after clicking on it.  In other words you can't even load a video into it.

[Edit]

Ooer.. Ok.. So now it's working.. lol

Muchos Gracios !!

---

