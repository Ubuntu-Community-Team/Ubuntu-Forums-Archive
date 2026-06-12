---
title: "ipod install question"
date: 2007-05-16
forum: Multimedia &amp; Video
---

### Post by Evegan on 2007-05-16
Hi, first off let me say that I am a total noob with Linux. I got an ipod 30g for my birthday and I'm having trouble setting it up to work. I installed gtkpod, followed all the instructions but it still doesn't work. When I try to sync my music library to the ipod gtkpod asks if it's ok to create several directories, I click OK and then it says: "ipod directory structure must be present before syncing to the ipod can be performed." How do I do this?

Also, when I plug in the ipod via the usb port an icon appears on the desktop but the ipod screen just blinks with a red circle with a line through it and it says "Do Not Disconnect." So I'm assuming I need to format my ipod but I have no idea how to do this.

Again, I'm a total beginner at this so as specific instructions as possible would be helpful.

Thanks

Evan

edit - I have a PC at work with iTunes already on it. Would plugging it in there help? Or should I not do this at all?

---

### Post by reclusivemonkey on 2007-05-16
I'm not 100% sure, but I don't believe you can format a new iPod under Linux. I would do this on your Windows PC with iTunes, but after that it should work fine under Linux.

---

### Post by Evegan on 2007-05-16
So i'm at work and plugged in the ipod but I'm still getting the "do not disconnect" screen and the blinking red circle with the line through it. What else do I need to do?

edit again - nevermind, i think it may be working now.

---

### Post by reclusivemonkey on 2007-05-16
> **Evegan said:**
> So i'm at work and plugged in the ipod but I'm still getting the "do not disconnect" screen and the blinking red circle with the line through it. 

That will always appear on the iPod when it is connected. You should be able to control everything through iTunes.

---

### Post by Evegan on 2007-05-16
OK, so I set up the iPod at work with iTunes and everything seemed to work fine. Now, at home, I keep getting the same dialoge box ***"iPod directory structure must be present before synching to the iPod can be performed."***

What do I do? I'm lost.

Evan

---

### Post by reclusivemonkey on 2007-05-17
My gf's iPod "just worked" for me.

What application are you using to sync with the iPod?

---

### Post by fjf on 2007-05-17
Go to [http://www.rockbox.org/](http://www.rockbox.org/), change the firmware of your ipod and just drag-and-drop folders to it as with any usb harddrive.

---

### Post by Evegan on 2007-05-17
Will installing rockbox change the interface with the ipod? Will it still work with iTunes? WHY doesn't it work with gtkpod?

Evan

---

### Post by reclusivemonkey on 2007-05-17
> **Evegan said:**
> Will installing rockbox change the interface with the ipod? Will it still work with iTunes? WHY doesn't it work with gtkpod?

Evan

Installing Rockbox will change the interface.

Installing Rockbox will make your iPod incompatible with iTunes.

Your iPod should work with GTKPod. Have you selected the model within GTKPod? Does you iPod work with iTunes in Windows? If so, then I would suggest deleting ~/.gtkpod. You may be experiencing problems from the old data in the gtkpod preferences.

Which model of iPod are you using?

---

### Post by Evegan on 2007-05-18
My ipod is a brand new 30g, yes it works fine with itunes.

I'm not going to install anything on my ipod that changes the interface. Seems like that would end up creating more problems than it would solve.

I think I may end up with an ibook anyways so this may all be for nothing. Who knows.

Evan

---

### Post by reclusivemonkey on 2007-05-18
> **Evegan said:**
> My ipod is a brand new 30g, yes it works fine with itunes.

In that case I would think that deleting the GTKPod preferences file should work.

I set uop my gf's nano once on iTunes and that was it though, so I can't say that using iTunes and GTKPod or Lkinux applications will play nicely together, although I imagine they should.

> **Evegan said:**
> I'm not going to install anything on my ipod that changes the interface. Seems like that would end up creating more problems than it would solve.

I completely agree, installing Rockbox on your iPod is not the solution to your issues here. I personally never understood people wanting to do this on an iPod, unless for some reason their iPod didn't work with its own firmware or they wanted to experiment.

> **Evegan said:**
> I think I may end up with an ibook anyways so this may all be for nothing. Who knows.

I'm saving for one myself, but with two kids its a slow process.

Did you try removing the GKTPod dir? I've got everything working on my gf's nano; music with album art, pictures, contacts, calendars, etc. It works very well now in Feisty.

---

### Post by Evegan on 2007-05-18
Hmm, how do I remove the directories? Does doing this still leave the gtkpod operational? 

Linux seems to recognize that I have an ipod, an icon pops up on the desktop, but gtkpod doesn't see it. Again, I'm a noob, as detailed info as possible is what I need.

Thanks for all the help guys, I appreciate it.

Evan

---

### Post by Gavin77 on 2007-05-19
I use my ipod with Amarok, works flawlessly.  Maybe you could try that.

---

### Post by reclusivemonkey on 2007-05-19
> **Evegan said:**
> Hmm, how do I remove the directories? Does doing this still leave the gtkpod operational? 

Yes, all you are doing is removing the preferences for GTKPod, you are leaving the application alone. The easiest way would be from a terminal, just

```

rm -Rf ~/.gtkpod

```

Once you start GTKPod again, it will recreate the directory with "clean" settings.

---

### Post by Evegan on 2007-05-19
> **reclusivemonkey said:**
> Yes, all you are doing is removing the preferences for GTKPod, you are leaving the application alone. The easiest way would be from a terminal, just

```

rm -Rf ~/.gtkpod

```

Once you start GTKPod again, it will recreate the directory with "clean" settings.

So, I just open up the terminal and put that in? I did it and nothing happened. Do I need to be in a different directory other than the default to do this?

When I open the terminal it says:

root@computer:/home/user #

Evan

---

### Post by LLRNR on 2007-05-19
> **Evegan said:**
> So, I just open up the terminal and put that in? I did it and nothing happened. Do I need to be in a different directory other than the default to do this?

When I open the terminal it says:

root@computer:/home/user #

Evan

You don't need to be in a "special" directory. From that line above, see the ~ - this means /home/user 

I'm not following the GTKPod discussion, I have no clue what that's supposed to be... yessss, I'm an ignorant. Hey, you can be one too, you know ? ;-) I just bought an iPod nano (4 GB) this morning, as I connected it to the computer to charge it a window popped up asking me whether to open its contents in a new window... and then... wow. Amarok did the whole thing. To save yourself from a lot of pain you can try installing amarok (my version is 1.4.5 - it's the default in the Feisty repos) - then it will simply ask you when you plug the iPod into the PC what to "do" with it. It will appear on a generic tab called "devices". From there on, you can simply drag files from your playlist into it.

As a side note: I only have USB 1.1 and it seems to "just work" (TM). Aaaand... Feisty ;-)

Good luck.

---

### Post by catdriver on 2007-05-19
> **Evegan said:**
> My ipod is a brand new 30g, yes it works fine with itunes.

I'm not going to install anything on my ipod that changes the interface. Seems like that would end up creating more problems than it would solve.

I think I may end up with an ibook anyways so this may all be for nothing. Who knows.

Evan

when you installed gtkpod did you also install the requisite  ipod compatability lib's?  iPod's suck with linux IME.  Search iPod with package manager, and read the gtkpod pages.  I don't remember them being very detailed though.  It is in fact possible to format an iod to vfat with linux and then gtkpod will create the required directory structure (that's what the message you keep getting is requesting, but since you set it up on a windows machine the directory structure should be there...right?). It's major pain and barely worth the effort IMHO.  Also you should be aware that once your 'pod is formated to windows it will have to be reformatted to interface with an Mac.   You get to use it with one or the other both.....  This is what I remember from my battles with 'pods, I killed two of them in 18 months, they're a lot more afected by vibration and jarring and bad format runs than anyone would care to admit.

---

### Post by catdriver on 2007-05-19
> **Evegan said:**
> So, I just open up the terminal and put that in? I did it and nothing happened. Do I need to be in a different directory other than the default to do this?

When I open the terminal it says:

root@computer:/home/user #

Evan
you need to be in the dir where the target file exists.  Also isn't it kinda out of favor to run as root user?

---

### Post by catdriver on 2007-05-19
> **LLRNR said:**
> You don't need to be in a "special" directory. From that line above, see the ~ - this means /home/user 

I'm not following the GTKPod discussion, I have no clue what that's supposed to be... yessss, I'm an ignorant. Hey, you can be one too, you know ? ;-) I just bought an iPod nano (4 GB) this morning, as I connected it to the computer to charge it a window popped up asking me whether to open its contents in a new window... and then... wow. Amarok did the whole thing. To save yourself from a lot of pain you can try installing amarok (my version is 1.4.5 - it's the default in the Feisty repos) - then it will simply ask you when you plug the iPod into the PC what to "do" with it. It will appear on a generic tab called "devices". From there on, you can simply drag files from your playlist into it.

As a side note: I only have USB 1.1 and it seems to "just work" (TM). Aaaand... Feisty ;-)

Good luck.

I suspect there is a difference in the way the two are recognized by the system, since nanos are flash memory  (aren't they?) and a full blown pod is recognized as a hard drive.... Hmmmm that reminds me since the pod is an /HDx or /Sdx device it needs a mount point usually /media/ipod or something similar that linux will dynamically assign every time it's plugged in and you have to feed that to gtkpod.... manually hopefully only once.....  Don't ask me how I've forgotten, sorry.

as an aside my new Zen V plugged in and popped right up ready to run, which is why I suspect the difference in the way they are recognized.

---

### Post by Evegan on 2007-05-20
> **catdriver said:**
> you need to be in the dir where the target file exists.  Also isn't it kinda out of favor to run as root user?

Gothca, so I need to get to the media directory?

While I'm at it, I've downloaded amarok, I can't update or install it direcly from the root (already tried) because hoary is no longer supported. So now amarok is downloaded to the desktop and unpacked and there is a folder called amarok-1.4.5. How do install this?

Thanks for everyone's help, it's very much appreciated.

Evan

---

### Post by reclusivemonkey on 2007-05-20
> **Evegan said:**
> Gothca, so I need to get to the media directory?

While I'm at it, I've downloaded amarok, I can't update or install it direcly from the root (already tried) because hoary is no longer supported. So now amarok is downloaded to the desktop and unpacked and there is a folder called amarok-1.4.5. How do install this?

Thanks for everyone's help, it's very much appreciated.

Evan

OMG, you're running Hoary?! I'm not surprised nothing will work. I only got the iPod working in Feisty. I would recommend upgrading to Feisty if you want everything to work.

---

### Post by reclusivemonkey on 2007-05-20
> **catdriver said:**
> iPod's suck with linux IME.

My gf's iPod works flawlessly with Feisty. Music, Pictures, Contacts, Calendar. All with a minimum of fuss.

---

### Post by Evegan on 2007-05-20
Yeah, it's annoying. I will be upgrading very soon but not until I get my laptop. In the meantime, I'd really like to get this working.

---

### Post by reclusivemonkey on 2007-05-20
> **Evegan said:**
> Yeah, it's annoying. I will be upgrading very soon but not until I get my laptop. In the meantime, I'd really like to get this working.

I can understand that, but I honestly can't say whether it will work in Hoary. It didn't work for me in Edgy, which is way beyond Hoary.

All I can suggest is adding all the iPod related stuff you can find in the repos and hoping for the best :-S

---

### Post by Evegan on 2007-05-20
At this point Hoary is going away. I'm working on the laptop as a temp replacement and once it's in my hot little hands Feisty will be going on. I've been reading a lot about it and I'm excited. All I know is, there is no way windows is going back on here, no way in you know what.

For the time being, I have iTunes at work. I'll do my syncing there till the laptop gets here. Is there a site with good, easy to understand installation instructions for Feisty? I'm in the process of searching and reading, I've ordered a copy and I'm trying to learn the right way to do things on Linux.

Thanks again

Evan

---

### Post by reclusivemonkey on 2007-05-21
Hi Evan,

This Wiki has just about everything for Feisty; it would be a good place to start before you install.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by Evegan on 2007-05-21
> **reclusivemonkey said:**
> Yes, all you are doing is removing the preferences for GTKPod, you are leaving the application alone. The easiest way would be from a terminal, just

```

rm -Rf ~/.gtkpod

```

Once you start GTKPod again, it will recreate the directory with "clean" settings.

Where is the gtkpod directory? When I open a terminal the prompt is "user@computer:~$"

The top of the window reads "user@computer: /home/user/desktop"

How do I navigate to gtkpod?

Evan

---

### Post by reclusivemonkey on 2007-05-21
> **Evegan said:**
> Where is the gtkpod directory? When I open a terminal the prompt is "user@computer:~$"

The top of the window reads "user@computer: /home/user/desktop"

How do I navigate to gtkpod?

Evan

If you haven't started GTKPod as a user, then there won't be a .gtkpod directory.

Normally the .gtkpod directory is in /home/user, but its hidden by default. Use 

```

ls -a /home/user

```

to see all the directories, including hidden ones. However, if you are using Desktop as your home directory, it will be in there.

---

### Post by Evegan on 2007-05-22
> **reclusivemonkey said:**
> If you haven't started GTKPod as a user, then there won't be a .gtkpod directory.

Normally the .gtkpod directory is in /home/user, but its hidden by default. Use 

```

ls -a /home/user

```

to see all the directories, including hidden ones. However, if you are using Desktop as your home directory, it will be in there.

So I did the "remove pref." thing and all I ended up doing was erasing everything off the ipod. So as far as I'm concerned I'm done for now. I'll try again once I get Feisty up and running.

Thanks again

Evan

---

