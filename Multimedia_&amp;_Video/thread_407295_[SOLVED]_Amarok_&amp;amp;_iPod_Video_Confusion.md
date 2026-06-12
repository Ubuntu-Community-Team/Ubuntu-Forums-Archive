---
title: "[SOLVED] Amarok &amp;amp; iPod Video Confusion"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by jeremyj on 2007-04-12
Hey all,
   I'm a little confused as to how to work Amarok and my iPod on Ubuntu 6.06.

I'm trying to copy my songs from my iPod video to my Ubuntu laptop, and have Amarok 1.3.9.  Everything seems to go well when I plug in my iPod.  It automounts, shows up on my desktop, and Rhythmbox opens automatically.  Amarok will detect my iPod when I click on "Media Device" on the left-hand side of the screen, but that's where my problems lie.

I've noticed that some of my albums aren't appearing in Amarok's list.  Some of those albums are entire bands' folders, too.  I know it's not a problem with the DRM iTunes stuff because these albums were imported from my CD collection.  The albums that are missing are on the iPod once I unmount it, and they will play like nothing went wrong.  What's the problem?

However, I *can* highlight my list of artists and right click them to "Append to Playlist."  Is this copying them to my hard drive?  Also, there's another problem that lies there.  In the list that shows up after right-clicking the list of artists and appending them to the playlist, most of the songs are only mixed up letters with a question mark for their play length, and none of them play.  Are there missing plug-ins I need to download?  Please help.  Thanks in advance.

---

### Post by koshari on 2007-04-12
for starters i would consider updating to at least 1.4.3 on dapper (and if you were on edgy the latest 1.4.5). there are packages for dapper (6.04) aroung that work well, 

1.3.* is pretty dated and there are a plethera of bugfixes since then.

---

### Post by jeremyj on 2007-04-12
> **koshari said:**
> for starters i would consider updating to at least 1.4.3 on dapper (and if you were on edgy the latest 1.4.5). there are packages for dapper (6.04) aroung that work well, 

1.3.* is pretty dated and there are a plethera of bugfixes since then.

I'm a little confused as to how to update Amarok as well.  LOL!  I have the 1.4.5 tar.gz file downloaded to my desktop, so I know the file is on my harddrive.  I uninstalled Amarok 1.3.9 and all of the files that came in it's tar.gz file as well.  Then I ran Synaptic Package Manager, searched for Amarok, and it installed 1.3.9 again for some reason.  (After installing 1.3.9 the first time, I immediately deleted both the tar.gz and extracted files from my harddrive, so why did the previous version re-install?)

I also ran Add/Remove Programs, and it didn't find any updates for Amarok 1.3.9.  Plus, Amarok doesn't have an option inside the program to update itself like I'm used to with iTunes, so that may be partly why I'm having problems.  How do I update Amarok?

And I'm still having problems with my music not copying from my iPod to my laptop.  A little more help please?

---

### Post by koshari on 2007-04-12
forget the tarball, (the tar.gz file) for now thats the source code for more experianced users to compile from source.

what you want is a dapper deb package, these are found in repositorys, and if you point synaptic to an additional repository it will auto update to the newer build.

this is the repository you need to add through synaptic

```
deb http://kubuntu.org/packages/amarok-14 dapper main
``` 

and you will need to download this key so you dont get an error when loading the repositorys, simply open a terminal and paste the lines one at a time and execute them, 


```
wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
sudo apt-key add kubuntu-packages-jriddell-key.gpg
```

then do a system update and amarok will update to the newer build of amarok, 

post back if you still have problems.

---

### Post by koshari on 2007-04-12
heres a link for more info

[http://kubuntu.org/announcements/amarok-1.4.php](http://kubuntu.org/announcements/amarok-1.4.php)

---

### Post by jeremyj on 2007-04-13
> **koshari said:**
> forget the tarball, (the tar.gz file) for now thats the source code for more experianced users to compile from source.

what you want is a dapper deb package, these are found in repositorys, and if you point synaptic to an additional repository it will auto update to the newer build.

this is the repository you need to add through synaptic

```
deb http://kubuntu.org/packages/amarok-14 dapper main
``` 

and you will need to download this key so you dont get an error when loading the repositorys, simply open a terminal and paste the lines one at a time and execute them, 


```
wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
sudo apt-key add kubuntu-packages-jriddell-key.gpg
```

then do a system update and amarok will update to the newer build of amarok, 

post back if you still have problems.

Unfortunately, I'm a complete newbie to Linux systems, and have no clue how to do anything you mentioned.  I can open Synaptic Package Manager from "System" and "Administration," but from there I don't know what to do next.

I also don't have a button on my keyboard to type the squiggly line before "jriddell" in the second line of code you gave me (the "wget http://...." line of code).  I really apologize for this.  It seems like more hassle than it's worth, but I don't want to go back to using Windoze on my laptop because it slows it down to a crawl.  Is it possible for you to give me step-by-step instructions?

**_EDIT:_**  Nevermind.  I somehow figured out how to add the first line of code (the one that starts out with "deb"), but made a stupid mistake and tried to add the "wget" line of code to the repositories in Synaptic.  Once I made that mistake, I opened the Terminal and did those last 2 lines of code correctly, but now whenever I reload Synaptic's list, it comes up with an error saying:

[I]"E: Type 'wget' is not known on line 34 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem"[/I]

What do I do now?

**_EDIT:_**  LOL!  Nevermind again!  I searched for my error message on these forums and found the sudo code to edit the sources list in gedit (is that right???).  I reloaded Synaptic's list and got another error message about not having a public key or something, searched the forums for my error message, fixed the problem with the public key in the Terminal, and Synaptic reloaded fine.  Then I used Add/Remove Programs, and it told me I had to do whatever to update my system and I used the Terminal again, and Amarok updated!  (I know because the Splash Screen said "1.4" and "Fast Forward.")

Now I have yet another problem.  When Amarok loads (this also happened with 1.3.9), I get an error message saying that "Knotify has crashed during a previous startup and I need to set another default sound output from the System Notification area" (a short and probably slightly incorrect paraphrase).  I searched yet again for the error message and found some advice to switch the output plugin from "autodetect" to "alsa."

Any ideas as to what's going wrong and what to do next?  (As of this time, I hadn't tried importing my music from my iPod to my laptop, so I'll try that next.)

---

### Post by jeremyj on 2007-04-16
**Quick update:**

Everything seems to be working fine now.  Amarok transferred my songs to my hard drive and plays them without Knotify crashing.  Thanks for your help, Koshari!  I really appreciate it!

---

### Post by koshari on 2007-04-26
iam happy it all worked out for you JJ.

and its prolly a good thing i wasnt round to help you with your last couple of errors to, because now you know how to do it and learnt all by yourself :-)

and at this rate i will be getting advice of you in the future.

---

