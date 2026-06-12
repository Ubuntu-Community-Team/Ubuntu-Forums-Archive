---
title: "How to upgrade Ubuntu 10.04 (Wubi install) to Ubuntu 10.10?"
date: 2010-06-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by sanoelk on 2010-06-06
I am trying to upgrade Ubuntu 10.04 (Wubi install) to Ubuntu 10.10 alpha using the update manager but to no avail. It downloads the packages at first but it fails at the end saying that the internet connection failed, when in fact my connection is perfectly fine.

Help please?

---

### Post by pr0t3g3 on 2010-06-06
try downloading and then burning the image to disk and then ubuntu 10.10 maverick merkeet should work fine... albeit a bit glitchy... [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

that should work just fine ^_^

---

### Post by sanoelk on 2010-06-06
I'm doing that right now. But I'm afraid that if I use that method, some of my current files/programs would be erased.

I'm also trying this: [http://ubuntuforums.org/showthread.php?t=1494974&highlight=ubuntu+maverick+meerkat](http://ubuntuforums.org/showthread.php?t=1494974&highlight=ubuntu+maverick+meerkat)

Terminal is still downloading packages. Hopefully this works.

---

### Post by wojox on 2010-06-06
> **pr0t3g3 said:**
> try downloading and then burning the image to disk and then ubuntu 10.10 maverick merkeet should work fine... albeit a bit glitchy... [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

that should work just fine ^_^

There's no Wubi installer on that page. :confused:



> **sanoelk said:**
> I'm doing that right now. But I'm afraid that if I use that method, some of my current files/programs would be erased.

I'm also trying this: [http://ubuntuforums.org/showthread.php?t=1494974&highlight=ubuntu+maverick+meerkat](http://ubuntuforums.org/showthread.php?t=1494974&highlight=ubuntu+maverick+meerkat)

Terminal is still downloading packages. Hopefully this works.

What does that link in your post have anything to do with upgrading Wubi? :confused:

---

### Post by Paddy Landau on 2010-06-06
Take care. Wubi has had issues with upgrading; it seems to be pot luck. Wubi is fantastic, especially for beginners, to play and experiment, but it does become unreliable for long-term use.

If you really need to play around with Ubuntu, may I suggest that you uninstall Wubi (back up your data first!) and then install Ubuntu properly as dual-boot.

Not only will it be more robust, but also you can back up your entire partition before you upgrade, and restore if you truly mess up (I've done this myself, and the restore was painless). I use [CloneZilla]("http://clonezilla.org/") to do this.

---

### Post by sanoelk on 2010-06-06
Ok. So that didn't work.

This error came up:
W: Failed to fetch [http://ppa.launchpad.net/THE_PPA/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/THE_PPA/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found

---

### Post by sanoelk on 2010-06-06
> **wojox said:**
> What does that link in your post have anything to do with upgrading Wubi? :confused:

Well, I thought the reason why I was not able to download all the packages was because of that key. I'm sorry if that doesn't make sense to you. I'm just trying things out to make upgrading to Ubuntu 10.10 work. :)

What can you suggest that I try? :)

---

### Post by sanoelk on 2010-06-06
> **Paddy Landau said:**
> Take care. Wubi has had issues with upgrading; it seems to be pot luck. Wubi is fantastic, especially for beginners, to play and experiment, but it does become unreliable for long-term use.

If you really need to play around with Ubuntu, may I suggest that you uninstall Wubi (back up your data first!) and then install Ubuntu properly as dual-boot.

Not only will it be more robust, but also you can back up your entire partition before you upgrade, and restore if you truly mess up (I've done this myself, and the restore was painless). I use [CloneZilla]("http://clonezilla.org/") to do this.

Thanks. Yeah, I probably should just properly install Ubuntu. I used Wubi because I was afraid I would mess up my system, but now that I like Ubuntu so much, I'd give proper dual-boot a try. I'd have to find out first if I can backup my files in Wubi and copy it to the dual-boot.

---

### Post by wojox on 2010-06-06
> **sanoelk said:**
> Well, I thought the reason why I was not able to download all the packages was because of that key. I'm sorry if that doesn't make sense to you. I'm just trying things out to make upgrading to Ubuntu 10.10 work. :)

What can you suggest that I try? :)

I just looked at both the post's and they never mentioned Wubi 10.10.

As Paddy Landau suggested you should be using Ubuntu. Wubi was made and designed to try out for a very short time to see if you like what you see and feel without messing with your Windows partition. :)

---

### Post by louieb on 2010-06-06
> **sanoelk said:**
> I'm doing that right now. But I'm afraid that if I use that method, some of my current files/programs would be erased.

The alpha releases do break - Having to reinstall completely is not unheard of - I got lucky with the Lucid Alpha(s) - the system became unusable only twice. Both times got it fixed without a reinstall. And that was normal - not wubi install.      

Check out the Maverick section of [Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310")  this thread should be move there.

Also checkout  			 			[Please help testing Wubi 10.04]("http://ubuntuforums.org/showthread.php?t=1439526") - it still applies to the upcoming 10.10 release. 

Good luck and happy testing. :P

---

### Post by sanoelk on 2010-06-06
> **wojox said:**
> I just looked at both the post's and they never mentioned Wubi 10.10.

As Paddy Landau suggested you should be using Ubuntu. Wubi was made and designed to try out for a very short time to see if you like what you see and feel without messing with your Windows partition. :)

Got it. ^^d

> **louieb said:**
> The alpha releases do break - Having to reinstall completely is not unheard of - I got lucky with the Lucid Alpha(s) - the system became unusable only twice. Both times got it fixed without a reinstall. And that was normal - not wubi install.      

Check out the Maverick section of [Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310")  this thread should be move there.

Also checkout                           [Please help testing Wubi 10.04]("http://ubuntuforums.org/showthread.php?t=1439526") - it still applies to the upcoming 10.10 release. 

Good luck and happy testing. :P

Guess I'd really have little luck in upgrading to 10.10. So it's hello normal dual-boot for me.

And I have to transfer this thread too. :)

---

### Post by ibuclaw on 2010-06-06
Moved to MM Forum. :)

Please could you keep all development talk in here, and out of the main channels.

Have a nice day!

---

### Post by sanoelk on 2010-06-06
> **ibuclaw said:**
> Moved to MM Forum. :)

Please could you keep all development talk in here, and out of the main channels.

Have a nice day!

Noted. Sorry, I didn't know that there is a dedicated section of the forum for this (plus, I didn't know that this topic belongs to development).  :D

Have a good one too. :)

---

### Post by ranch hand on 2010-06-06
> **sanoelk said:**
> Noted. Sorry, I didn't know that there is a dedicated section of the forum for this (plus, I didn't know that this topic belongs to development).  :D

Have a good one too. :)
Seeing as how 10.10 stands for October 2010 it would seem obvious that this is a development project.

There is probably no way at this point to install 10.10 with wubi.  This has been the case early on with the last 2 releases anyway.

This should not be being used as a production OS.  Before proceeding read all the stickies (top of every index page on this forum).  Do not do a thing until you have read at least the first post of every one of them.

Understand the risks before you do something you will regret.

I would not install an early pre-release on the same drive as my main OS.  I am sure many do but if you do not have more experience with Linux than your join date indicates you could easily screw your entire system.

---

### Post by sanoelk on 2010-06-06
> **ranch hand said:**
> Seeing as how 10.10 stands for October 2010 it would seem obvious that this is a development project.

There is probably no way at this point to install 10.10 with wubi.  This has been the case early on with the last 2 releases anyway.

This should not be being used as a production OS.  Before proceeding read all the stickies (top of every index page on this forum).  Do not do a thing until you have read at least the first post of every one of them.

Understand the risks before you do something you will regret.

I would not install an early pre-release on the same drive as my main OS.  I am sure many do but if you do not have more experience with Linux than your join date indicates you could easily screw your entire system.

You're right. And I'm still trying to learn all I can about Linux (just out of interest). 
Again, my apologies.

---

### Post by Paddy Landau on 2010-06-06
> **sanoelk said:**
> I'd have to find out first if I can backup my files in Wubi and copy it to the dual-boot.
OK, some important points for you to note. Installing Ubuntu, while highly reliable, does carry a tiny risk of Windows corruption. Therefore:

[LIST=1]
[*]Before you uninstall Wubi, you can back up your data to your Windows folders. Just mount your Windows (from Wubi) and copy your data there. Boot into Windows to double-check that the copy was successful.
[*]After you've uninstalled Wubi, but before you install Ubuntu, back up **all** your data from Windows (including the stuff you saved from Wubi). Reason: The small chance of disk corruption that you get with installing Ubuntu.
[/LIST]
Here is how I back up Windows before I install Ubuntu on a new Windows machine.

[LIST=1]
[*]Do a normal backup of the data.
[*]Boot into a Live CD, load up GParted, and note the size of the Windows partition. You will need this information if you restore the partition (see point 3).
[*]Back up the entire Windows partition using [CloneZilla]("http://clonezilla.org/"). That way, if there is a Windows corruption, I don't have to go through the hassle of reinstalling Windows; I simply plug in CloneZilla and restore the partition!
[/LIST]
The backups are nothing more than insurance; they're a pain, and you're unlikely to need them, but if you do need them you'll thank yourself.

---

### Post by autocrosser on 2010-06-06
> **sanoelk said:**
> You're right. And I'm still trying to learn all I can about Linux (just out of interest). 
Again, my apologies.

No apologies needed--as it is said---there are no stupid questions---only stupid answers. 

I quad boot my system (two testing installs--one backdated a week from the other, one stable & Elive for fun)--the last stable install in case everything goes foobar--which it will....you also should have a separated / & /home so you can reinstall easily without loosing your data. As ranchhand noted, read the stickys & THINK about it before you do this...

Welcome to the testing group---We don't bite (much) & we do watch each others back...testing can be pretty wild at times:P

---

### Post by ranch hand on 2010-06-06
It is important to realize that we are really here for one very important purpose and that is to file bugs.

We find the stuff that doesn't work, file the bugs, the devs fix it.  At least this is the theory.

This will break.  If you look at the rest of this forum you will see problems that folks have had so far.

There should be an increase in breakage as time goes on for a while.  This is where the FUN is.

---

