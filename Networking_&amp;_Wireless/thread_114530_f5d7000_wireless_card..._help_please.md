---
title: "f5d7000 wireless card... help please"
date: 2006-01-08
forum: Networking &amp; Wireless
---

### Post by marc.orr on 2006-01-08
Hello, I have been trying for several days now to get my belking f5d7000 desktop network card to work on ubuntu 5.10.  I am trying to use ndiswrapper and i have followed several tutorials including the wiki tutorial, the howto tutorial on here, and a few more that don't stand out in my memory.

I have tried several different drivers.  After doing a ndiswrapper -i name.inf I get one of two responses depending on the inf file:

1) invalid driver!
2) name driver present


What worries me is that after typing ndiswrapper -l with many different .inf file isntalled I have never once seen it say hardware present like it says it should in many of the tutorials.

I have tried ndiswrapper version 1.1 (the package included with ubuntu) and I have also tried ndiswrapper version 1.7.  They both seem to behave the same way.

I also reformatted my computer to see if it would help but everything seems to act the same.

It is a big hassel to download stuff onto my comp because I don't have access to a land line I have to use wireless because me and my neighbor share internet and the router is not in my apt.  I have been going to the repositories online and downloading packages and tranferring them to my linux box and using dpkg which is a big hassel.

What worries me is that when I type lspci -v my wireless card seems to be recognized but is disabled.  Is this why ndiswrapper never says hardware present or is ndiswrapper supposed to enable it?

I am fairly new to linux.  So if you need me to give you more info I would be happy to but simple instructions on how to do it might save us some time and unneccesary posts of me saying "I don't understand".  I really appreciate anyone who can read this.  Thanks for everyone's time!

-Marc Orr

---

### Post by marc.orr on 2006-01-08
I forgot to say that I also download Ndiswrapper .11 because I couple of people on the wiki least said they were able to get it to work but I got compile time errors so I was unable to try using it.

-Marc

---

### Post by nijinsky on 2006-01-09
[QUOTE=marc.orr]I forgot to say that I also download Ndiswrapper .11 because I couple of people on the wiki least said they were able to get it to work but I got compile time errors so I was unable to try using it.

-Marc[/QUOTE]

Hi there

I'm a newbie but you could use this method I used for the f5D5070 usb stick.

Just try substituting your drivers etc.

URL is
[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

Cheers
Bob

---

### Post by marc.orr on 2006-01-09
I guess I was just using the wrong driver.  I went on to the belkin website and downloaded their drivers and tried all of them (for the f5d7000) until i found one that works.  One thing that may help people who come accross this post that I discovered is that in windows you can sometimes change the extension of a exe file to zip and then open it as a zip file to extract files without running the exe and installing god knows what onto your computer.  I imagine you can do something similar in linux but I haven't tried.

-Marc

---

