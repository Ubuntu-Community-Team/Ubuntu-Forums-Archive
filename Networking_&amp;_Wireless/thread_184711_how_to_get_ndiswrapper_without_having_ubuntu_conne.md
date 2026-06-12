---
title: "how to get ndiswrapper without having ubuntu connected to internet"
date: 2006-05-30
forum: Networking &amp; Wireless
---

### Post by shutupimpoor on 2006-05-30
i need to be able to 
```
 sudo apt-get install ndiswrapper-utils 
```
but, I don't have the internet connected (kinda funny how you need the internet in order to get your wireless internet to work?) anyway, is there a way I can download the things I need while i'm in windows then burn them to a disk and put them where they belong in ubuntu?

---

### Post by kostkon on 2006-05-30
Of course you can!

Go to [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and there find the deb you want and download it. Click the *all* link of the *Architecture* column at the Download section of the package page.

---

### Post by az on 2006-05-30
[QUOTE=shutupimpoor]i need to be able to 
```
 sudo apt-get install ndiswrapper-utils 
```
but, I don't have the internet connected (kinda funny how you need the internet in order to get your wireless internet to work?) anyway, is there a way I can download the things I need while i'm in windows then burn them to a disk and put them where they belong in ubuntu?[/QUOTE]
ndiswrapper-utils is on the install cd.  Install it with synaptic.

For Dapper, it is in a repository on the Desktop (live) cd as well on the alternate cd.

If you installed using the Desktop graphical installer, reboot into your new ubuntu system and insert the live cd again.  You will be asked if you want to add the packages on the repository to your list.  From there, you search for and install ndiswrapper-utils.

---

### Post by shutupimpoor on 2006-05-30
I haven't tried the second solution, but in response to the third, I don't have a live CD or any means of installing ubuntu - my friend lent me his. i meant to copy it before we left college, but as you can see... i didn't

---

### Post by az on 2006-05-30
[QUOTE=shutupimpoor]I haven't tried the second solution, but in response to the third, I don't have a live CD or any means of installing ubuntu - my friend lent me his. i meant to copy it before we left college, but as you can see... i didn't[/QUOTE]
By default, breezy caches the extra packages on your hard drive.  If you haven't cleared out your cache, ndiswrapper-utils is still there.

---

### Post by aldegaz on 2006-06-08
I have tried to follow your instructions.

ndiswrapper-utils is there but when I click to install it, it tries to download some extra 40kb or so, but I dont have an internet connection... how could this be solved?

I also downloaded the latest ndiswrapper but I dont know how to install it from a folder.

you see.. I am new to linux, sorry...

can you help me?

---

### Post by az on 2006-06-08
If you have never been on the net, it will "download" the packages from the cd.  If you have been on the net and added repos at one time, just edit thouse sources out of your list (remove the repositories using synaptic) update and try to install again.

You do not need to go on the net to install ndiswrapper utils

---

### Post by aldegaz on 2006-06-08
Everything worked just as you said. Thanks for the prompt response. Now this might not be a question directly related to the problem, but it is, second handed.
The reason I am trying to get ndiswrapper to work is to get my wifi network to work.
I have done everything stated on this [thread]("http://www.ubuntuforums.org/showthread.php?t=25683&highlight=siocgifflags") 
but I am missing the last part when I try to put this on the terminal window:
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile

here it gives me an error message...would you know something about this piece of code?

thanks

---

### Post by aldegaz on 2006-06-09
Does ndiswrapper have a visual interface?

I managed to install ndiswrapper but I cant seem to have the visual interface under system/administration

---

### Post by Dr. Nick on 2006-06-09
no gui unless you have internet and install the ndisgtk package .

---

### Post by aldegaz on 2006-06-11
why after installing everythin and doing 
ndiswrapper -|

I get a:
>

---

### Post by Dr. Nick on 2006-06-11
what character is that? a lowercase L? it looks like a | to me, not a lower L. Just a idea

---

### Post by aldegaz on 2006-06-12
yep you are right....problem fixed, although I still have problems to connect to the internet...you might want to help me here: [http://ubuntuforums.org/showthread.php?p=1129622#post1129622](http://ubuntuforums.org/showthread.php?p=1129622#post1129622)

---

### Post by Dr. Nick on 2006-06-12
[quote=aldegaz]yep you are right....problem fixed, although I still have problems to connect to the internet[/quote]

Just a few tips, If you get the driver/hardware present on ndiswrapper -l then do 

sudo modprobe ndiswrapper

Also disable any on board ethernet or modem, even if you are not using them. This can be done from system - administration -network. While thier make sure your wireless shows up and is activated. I would reccomend disabling any wep in the router until you get it working.

Also make sure no modules are loaded for you wireles other than ndiswrapper, try "lsmod" and see if you see anything on your wireless card, look for ndiswrapper and see if anything is next to it. You may habe to remove another module.

To get ndiswrapper on boot add "ndiswrapper" to /etc/modules.

hopefully one of them will get you further

---

