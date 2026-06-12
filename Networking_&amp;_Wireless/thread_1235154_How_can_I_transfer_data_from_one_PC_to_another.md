---
title: "How can I transfer data from one PC to another?"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by DaftPyramid on 2009-08-08
I have a laptop and a desktop, both using Ubuntu. I have a wireless router that is wired to the desktop. I want to transfer a large number of files from the laptop to the desktop. Is there a quick and easy way to do this?

---

### Post by quixote on 2009-08-08
Are all the files in one part of the directory tree?  If so, [clonezilla]("http://clonezilla.org") may work for you.  It runs over a network, I seem to remember that it allows you to specify what to copy right down to a given directory, and it's very fast.

There's also rsync.  Is that something you've already tried and rejected?

---

### Post by DaftPyramid on 2009-08-08
I'm not familiar with any such software, so thank you for the suggestions. All of the data I want to transfer is in one folder. 

Stupid question: Do I have to set up a "home network" of some sorts?

---

### Post by quixote on 2009-08-08
Since both computers are ubuntu machines, networking them is supposed to be automatic.  The hardest part is figuring out how to refer to them so that they can see each other.  I don't do so well on that.  Instead I use ssh to login to other machines, but that's also a can of worms.  

I'm just guessing, but I gather that if you have something called the "Windows network sharing service" installed, then if you right-click on a folder and look at "Properties" the last tab is "Sharing."  If you set it to "Shared" I believe you can see it as a folder in Nautilus on the other machine.  The location bar in nautilus will, I think, give you the syntax you'd need to use if you were trying the same thing at the command line.  I am *very* vague on all this. (I just looked, and there are wiki pages on this.  Maybe this will help: [https://help.ubuntu.com/8.04/internet/C/networking-shares.html](https://help.ubuntu.com/8.04/internet/C/networking-shares.html))  

The problem here is that a GUI method may not help you with command line things like rsync.  To run rsync it might (might!) look something like this: ```
rsync -avu /path/to/source/directory/ <user>@<other-computer-name>.local:/path/to/target/directory
``` (the front slash after source, but not after target, are important.)

Just to test whether the two computers can see each other on your local network, you can use "ping".  ```
ping *your-other-computer-name*.local
```
If they can see each other, that'll return the amount of milliseconds a roundtrip signal takes.  If they can't, then that's a separate issue, which you may want to start a new thread about.

I wish I knew the right answer to your question!

---

### Post by cdnLilwolf on 2009-08-09
> **DaftPyramid said:**
> I have a laptop and a desktop, both using Ubuntu. I have a wireless router that is wired to the desktop. I want to transfer a large number of files from the laptop to the desktop. Is there a quick and easy way to do this?

If you have the pertinent files installed for NFS, just mount the other's hard drive, drag and drop.  The important file is "etc/exports" on what could be regarded as your server.  It is here that you could specify what computer/s may connect.

I like "rsync" for backups and syncs, but for moving files about NFS may be easier once setup (which is not hard).

---

### Post by MadHatter21 on 2009-08-09
You know what is actually really nice is a little program called dropbox. essientially it is a drop box. You set up dropbox on one computer and set it up on the other then you like the two with the same username and password then drag anything into the box and it magically appears on the other computers dropbox as well. I believe the server gives you a few gigs of space. Heres the [[COLOR="Blue"]link[/COLOR]]("http://www.getdropbox.com/install?os=lnx")

MadHatter21

---

### Post by DaftPyramid on 2009-08-09
Thanks for your answers, guys. I think I conceptually understand what you're talking about, but someone is going to have to give me a step-by-step (or one that someone else has written), because I have no experience with this (and very little experience with Linux).

Also, I already use dropbox. The free account only allots 2GB of space, and I need to transfer much more than that. I could just do it in pieces, but I have a fairly slow internet connection and it would take forever to upload all of my data. If it comes down to it, I might give it a try, but I'd like to find a quicker solution.

Thanks again.

---

### Post by quixote on 2009-08-09
I'm not familiar with the /etc/exports method.  One way to find things out about stuff like that is to google "etc/exports" "file transfer" (both in the same search, and use quotes on "file transfer").  You can limit it to specific sites by adding (on the same line) site:ubuntuforums.org or say site:.ubuntu.com (which would get wiki.ubuntu.com, help.ubuntu.com, and so on).

I think the easiest thing to try first is to right-click on a directory, go to Properties, and Share it.  If you don't have the right software to do that, there's a button right there to install it.  Once it's shared, go to Places > Network on the other computer and see if it shows up.  I haven't done this, so I'm guessing, but that's what I would expect.  

Assuming it does, you could open another Nautilus window, find the directory you want to transfer, and drag it to the Nautilus window with the network share on it.  Nautilus is MUCH slower at doing this sort of thing than command line, so try it on a small directory first.  If everything's okay, set the other one up to go overnight.

If you have system files you want to transfer, start nautilus as gksudo (Start > Accessories > Terminal, and then in the terminal type "gksudo nautilus".  Don't close that terminal window until you're done with that instance of nautilus.)  "Places" in nautilus is in the Side pane.  If it's not already visible, go to Menu - View > Side Pane.

Anyway, all this is contingent on sharing working easily, so let us know if it does.

---

### Post by DaftPyramid on 2009-08-10
Thanks, this is working, but it is taking FOREVER to transfer all of the files. Does the laptop need to be on the entire time that the files are being transferred?

---

### Post by quixote on 2009-08-10
Yes.  It does take forever, and yes the laptop has to be on the whole time.  :(

That's the biggest reason to figure out how to use something like a command line "rsync".  If you want to try it, I could take a stab at walking you through the steps.

---

### Post by DaftPyramid on 2009-08-10
Nah, this will work. I will just transfer it in chunks over a period of a few days. Thanks for your help.

---

