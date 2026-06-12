---
title: "Online vs. Manual Install?"
date: 2009-03-23
forum: Multimedia Software
---

### Post by berong on 2009-03-23
please someone explain to me why i can't install a software if i have no internet connection..
i have an old computer...
newly installed UBUNTU HARDY heron...
i have no internet connection... (if you're wondering why i can post here is that i am in cafe.)
i want to download apps that i can install on my box...but i can't find apps that can be saved in my USB and run it on my computer.. (just like in Windows.?)i read those instructions and how tos on installing, but still i had a hard time understanding it...
i admit i am a newbie in this OS...
please someone direct me, enlighten me on this problem.. 
your explanation and additional resources are very much appreciated... thank you

---

### Post by gandaran on 2009-03-23
> **berong said:**
> please someone explain to me why i can't install a software if i have no internet connection..
i have an old computer...
newly installed UBUNTU HARDY heron...
i have no internet connection... (if you're wondering why i can post here is that i am in cafe.)
i want to download apps that i can install on my box...but i can't find apps that can be saved in my USB and run it on my computer.. (just like in Windows.?)i read those instructions and how tos on installing, but still i had a hard time understanding it...
i admit i am a newbie in this OS...
please someone direct me, enlighten me on this problem.. 
your explanation and additional resources are very much appreciated... thank you
first what is it you trying to install?
you can download any application in any ubuntu/linux compatible format to a usb flash drive and install it in ubuntu, some will be harder to install due to missing dependencies which you have to get and install first
one easy format to install just like in windows (double clicking the install file) is the .deb file/package, you can get some [here]("http://www.getdeb.net/") to try or go to the ubuntu [repositories]("http://packages.ubuntu.com/hardy/allpackages")

---

### Post by 3rdalbum on 2009-03-23
An installer for a Windows program will include absolutely everything needed to install the program. This is good in some ways but bad in other ways.

Ubuntu packages only include the described contents of the package, and don't also include the things needed to make the end program work. For instance, games on Windows will also include all the support libraries to allow 3D graphics to work; on Ubuntu all that stuff will be in a seperate package.

When you're installing software on an Ubuntu that is connected to the Internet, Ubuntu will automatically download the required packages (dependencies) for the main program; that is, if you don't already have those packages.

Since you are installing offline, you need to do this "dependency resolution" by yourself. The package pages on [http://packages.ubuntu.com](http://packages.ubuntu.com) will tell you what the dependencies are for each package, so you can download those as well. Just make sure you install the dependencies before the main program, and remember that some dependencies come preinstalled on your Ubuntu system.

---

### Post by chngr on 2009-03-23
Yes Buddy, You can install softwares offline. First get a software you want in deb package and then Type these commands into console. I recommend that you must take a look at dpks'man page. 

```
dpkg -i your_software.deb
```

For more information please visit [this link]("https://help.ubuntu.com/community/InstallingSoftware#Installing%20downloaded%20packages").
[http://www.psychocats.net/ubuntu/installingsoftware#gdebi](http://www.psychocats.net/ubuntu/installingsoftware#gdebi)

Best regards.

---

### Post by berong on 2009-03-23
WOW...
fast responses...
thanks to all...
now i'm beginning to be enlightened...
now i have a reason not to go back to my old windows OS..
thanks again to your responses...
it adds another information on me...

---

