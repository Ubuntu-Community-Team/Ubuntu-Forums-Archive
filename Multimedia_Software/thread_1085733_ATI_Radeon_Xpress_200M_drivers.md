---
title: "ATI Radeon Xpress 200M drivers"
date: 2009-03-03
forum: Multimedia Software
---

### Post by porchrat on 2009-03-03
No need to tell me how horrific this chip is, I have already experienced the horror through XP. The new catalyst drivers on the windows system were OK, giving reasonable openGL support, but nothing near what the card was capable of.

Was wondering if there was a fglrx driver for this card on a 64bit Ubuntu system as the open source stuff is kind of disappointing in terms of desktop responsiveness.  I have had amazing experiences before with the fglrx drivers, but I can't find evidence of the Xpress 200M being supported (only the Xpress 200).

If there is no fglrx can anyone recommend any particular driver or solution for me to optimise this cowpat of a chip?

---

### Post by markbuntu on 2009-03-03
According to the release notes the X200 series is supported by the latest drivers. I assume this would include the X200M. I have Intrepid installed on an old machine with a 200M and fglrx works just fine. The latest drivers are way better thant the ones in the repos, no doubt about that.
Do not use Envy to install the driver and read the release notes and installer notes.
Driver

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Install guide

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

I just run the automatic installer myself but that does not seem to work all the time for all cards so you can use the directions above.

---

### Post by DownTown22 on 2009-03-03
My wife has this same chipset on her Toshiba laptop (running 8.04.1 - 32 bit) and I can say we've never had any problems running the latest driver in the repo's - in both 8.04 and 7.04.  And yes, Compiz is running very smoothly.

I know you're running 64 bit (Intrepid/Hardy?), but I just thought I'd give my two cents.

---

### Post by porchrat on 2009-03-04
> **markbuntu said:**
> According to the release notes the X200 series is supported by the latest drivers. I assume this would include the X200M. I have Intrepid installed on an old machine with a 200M and fglrx works just fine. The latest drivers are way better thant the ones in the repos, no doubt about that.
Do not use Envy to install the driver and read the release notes and installer notes.
Driver

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Install guide

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

I just run the automatic installer myself but that does not seem to work all the time for all cards so you can use the directions above.

I have used these fglrx drivers before so luccily I'm already relatively familiar with how to install them. I have seen that there is 64bit support for the X200 series, but if you look under the Windows 64bit section for example, they mention both the X200 and the X200M, I don't think they are the same card.

I agree with you, I also wouldn't use envy it just causes extra problems.

Then again if you say that your 200M is running with that latest drivers maybe I'll just get them and see what happens, suppose I can always fix the X-server afterwards if it goes to pot.

> My wife has this same chipset on her Toshiba laptop (running 8.04.1 - 32 bit) and I can say we've never had any problems running the latest driver in the repo's - in both 8.04 and 7.04. And yes, Compiz is running very smoothly.

I know you're running 64 bit (Intrepid/Hardy?), but I just thought I'd give my two cents.

I'm not saying those drivers don't work acceptably, but I have not had good experiences with them.  I'm glad they work for you, but I've found that with these X200M chips the drivers have only very recently become usable on the Microsoft side and that has left me with an outlook that says always get the latest driver because it will be much better than the one before.

Anyway thank you both for your help and advice, I'm going to try the fglrx drivers from ATI, if those don't work I'll fix the X-server and install from the repositories.

---

### Post by sky5564 on 2009-03-16
> **markbuntu said:**
> According to the release notes the X200 series is supported by the latest drivers. I assume this would include the X200M. I have Intrepid installed on an old machine with a 200M and fglrx works just fine. The latest drivers are way better thant the ones in the repos, no doubt about that.
Do not use Envy to install the driver and read the release notes and installer notes.
Driver

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Install guide

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

I just run the automatic installer myself but that does not seem to work all the time for all cards so you can use the directions above.

im still having problems getting my radeon xpress 200m to work i have a toshiba satellite a105 laptop with ubuntu 8.04 hardy .

i followed the instructions you listed above and edited the x.org file and when i restarted it would not work .

i have tried installing it the "automatic way" by going to admin>hardware drivers but when i restart it will not recognize the drivers .

edit*

this is what the compiz check shows for my machine

user1@user1-laptop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RC410 [Radeon Xpress 200M]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Laptop using radeon driver. 

Would you like to know more? (Y/n) y

 It has been detected, that you are running a laptop with an ATI chip.
 The radeon driver supports Compiz out-of-the-box but because of a nasty bug
 in the driver that causes X to freeze on some cards, this particular
 combination had to be blacklisted in Ubuntu "Hardy Heron".

 In case you already used Compiz successfully on Ubuntu 7.10 (Gutsy), it is
 safe to skip the blacklist. 

help please

---

### Post by Forlong on 2009-03-16
Didn't it ask you to skip the blacklist for you afterwards?

---

### Post by sky5564 on 2009-03-16
> **Forlong said:**
> Didn't it ask you to skip the blacklist for you afterwards?

doh!!!! XD

i also edited the file wrong to from those instructions lol oops.

but i have it working now.

this is how i did it.

first i followed all the instructions (correctly this time) from above.

then i downloaded and installed compiz check then i ran it this was the printout 

user1@user1-laptop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RC410 [Radeon Xpress 200M]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Laptop using radeon driver. 

Would you like to know more? (Y/n) y

 It has been detected, that you are running a laptop with an ATI chip.
 The radeon driver supports Compiz out-of-the-box but because of a nasty bug
 in the driver that causes X to freeze on some cards, this particular
 combination had to be blacklisted in Ubuntu "Hardy Heron".

 In case you already used Compiz successfully on Ubuntu 7.10 (Gutsy), it is
 safe to skip the blacklist. 

Do you want to skip blacklist checks by Compiz? (y/N) y
user1@user1-laptop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RC410 [Radeon Xpress 200M]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

user1@user1-laptop:~$ 

so it's working now.

---

### Post by porchrat on 2009-03-20
OK just to put the final nail in the coffin of this thread here is an update:

I tried out the new catalyst drivers and, as others had said, it did indeed work. I didn't even need to unpack it manually, I just did a: ```
chmod u+x
```

I then just ran it and installed using the GUI installer it comes with. They have really made this a lot less of a hassle than it used to be, bravo ATI. It wasn't exactly difficult to install the catalyst drivers when you had to unpack them and build them yourself, but I believe it was putting off a lot of new users, this is definitely a positive move.

Everything runs quite smoothly. It is a little slow, but is really to do with the limitations of my machine, not the drivers themselves.

Thanks everyone for your suggestions and advice, and I'm glad that sky5564 got it sorted out too.

Now I use XP for the few games I play and the few applications without native Linux versions and use Ubuntu for pretty much everything else.

---

### Post by max_power on 2009-05-11
hello my fellow 200m users. My card seems be working just fine but with one exception, i cant run at 1280x1024.

ive tried to add the mode in xrandr but get errors. Has anyone had success running at this resolution with this card?

Thanks,

---

