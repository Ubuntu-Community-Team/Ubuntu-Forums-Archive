---
title: "Why am I bothering with linux?"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by Fingerlakes_Dave on 2006-10-01
OK.  I downloaded the newest nvidia drivers.  I found the section
in help/faq on how to install.  Printed out.

 Tried to do exactly what is written.  I now cannot get the xserver to run.  All I get is a command line login and when I do login, it's at the commandline desktop.

 Why should I contine to be frustrated by linux every time I try to do what is a simple operation undeer Windows?????!!!!!

 Install new nVidia drivers in Windows: download, click on the *.exe, let run, reboot, done.  SIMPLE!!!!
 No command line. No edit xorg.conf.  No change nv to nvidia and rebuilt the checksum. 

  I'm not saying I have never had a driver issue in Windows. However, overall, it's beats the linux way of doing things.

  This is the second major issue I have had with ubuntu/linux.  I probably will have to re-install to fix. (?)  :( 

  After the above, is there a fix?  I have no idea how to get gedit to run from the commandline. --help is worthless unless you understand all the other commands/options.  I don't.

  I've been working on computers since DOS 4,5,6,6.11 Windows 3.11.  This stuff brings back TOOOOO many bad memories of working in 3.11, Windows 95a, 95b, etc..:mad: 

  I'm not even sure I want to bother with a fix.  

  Reasons why linus won't take over the desktop?  See above.  
I still can't figure how to see all my partitons in ubuntu.  I can't figure, other than those programs "allowed", figured out how to find a program and install it.

   WAY to STEEP a learniong curve!](*,) ](*,) ](*,) ](*,)

  Any help still appreciated, however, I may have deleted the partition by the time anyone responds.

Dave

Posted using Firefox in Windows XP Pro SR2.  I have to give the devil :evil: his due: Microsoft winns this round.  :(

---

### Post by daller on 2006-10-01
While in command-line, type in:

```
sudo dpkg-reconfigure xserver-xorg
```

Then answer all the questions.

Most of the questions are self-explanatory, and if you dont know what to answer, simply press enter, and proceed!

One thing though!

Choose "Medium" when setting up the monitor! (For gods sake, not "Advanced")

After this, you should be running x again! (the command for starting x is "startx" - If you didn't know!)

If any problems, please post the essential output from running "startx" here... (Especially where it's marked (EE) - Which means Error)

---

### Post by Vorticon on 2006-10-01
I've used windows all my life too and i'm also a newbie to linux. I also have windows xp on my computer but i'm spending more time on ubuntu now (i only game on windows now) and i must say i had a bit of problems with installing things myself first. I learn more about linux now every day and i'm having fun discovering new and different functions you can do with it. You're now probably at the steepest point of your learning curve because it gets easier and easier the more you do in a short ammount of time.

Anyway, if you want to know how to install your nvidia drivers go to [this]("https://help.ubuntu.com/community/Latest_Nvidia_Dapper") tutorial (i used it too works perfectly).

---

### Post by BitTorrentBuddha on 2006-10-01
What happens when you run ```
startx
``` after logging in at the command line? The majority of the problems you're encountering come not from Microsoft Windows being a superior product, but a more supported one. If you do wind up having to reinstall I would recommend using automatix to install nvidia drivers, it worked quite well for me. Posting nondiscriptive titles such as this often get you labeled as a troll. And remember, nobody is forcing you to use Linux. If you really can't think of a reason to bother with it, just don't. There's nothing wrong with using XP if you prefer it.

---

### Post by Josh1 on 2006-10-01
Hi.
If X wont load, type into console:
```

sudo dpkg-reconfigure -phigh xserver-xorg
startx

```
Then, seeing as you want to use nVidia drivers, when you are in ubuntu, load up terminal then type in:
```

sudo aptitude install nvidia-glx sudo nano /etc/X11/xorg.conf

```
in Section "Device" change "nv" to "nvidia"
save and exit <ctrl> + <o> | <ctrl> + <x>

restart x: <ctrl> + <alt> + <backspace>.

---

### Post by tseliot on 2006-10-01
> **Fingerlakes_Dave said:**
> OK.  I downloaded the newest nvidia drivers.  I found the section
in help/faq on how to install.  Printed out.

 Tried to do exactly what is written.  I now cannot get the xserver to run.  All I get is a command line login and when I do login, it's at the commandline desktop.

 Why should I contine to be frustrated by linux every time I try to do what is a simple operation undeer Windows?????!!!!!

 Install new nVidia drivers in Windows: download, click on the *.exe, let run, reboot, done.  SIMPLE!!!!
 No command line. No edit xorg.conf.  No change nv to nvidia and rebuilt the checksum. 

  I'm not saying I have never had a driver issue in Windows. However, overall, it's beats the linux way of doing things.

  This is the second major issue I have had with ubuntu/linux.  I probably will have to re-install to fix. (?)  :( 

  After the above, is there a fix?  I have no idea how to get gedit to run from the commandline. --help is worthless unless you understand all the other commands/options.  I don't.

  I've been working on computers since DOS 4,5,6,6.11 Windows 3.11.  This stuff brings back TOOOOO many bad memories of working in 3.11, Windows 95a, 95b, etc..:mad: 

  I'm not even sure I want to bother with a fix.  

  Reasons why linus won't take over the desktop?  See above.  
I still can't figure how to see all my partitons in ubuntu.  I can't figure, other than those programs "allowed", figured out how to find a program and install it.

   WAY to STEEP a learniong curve!](*,) ](*,) ](*,) ](*,)

  Any help still appreciated, however, I may have deleted the partition by the time anyone responds.

Dave

Posted using Firefox in Windows XP Pro SR2.  I have to give the devil :evil: his due: Microsoft winns this round.  :(

Did you read my guide?
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

or did you try envy?
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Fingerlakes_Dave on 2006-10-01
> **BitTorrentBuddha said:**
> What happens when you run ```
startx
``` after logging in at the command line? 
 
Since I never heard of startx until now, how would i know to try it?

> The majority of the problems you're encountering come not from Microsoft Windows being a superior product, but a more supported one. 

  Ever try to get MS support?  That concept evaporated years ago with MS.

>  If you do wind up having to reinstall I would recommend using automatix to install nvidia drivers, it worked quite well for me. 

  And automatix is?  A program?  A command?  Might be a great suggestion.  Without a frame of reference....????

>  Posting nondiscriptive titles such as this often get you labeled as a troll. 

   **I don't really care what others think.**

   Your opinion.  Opinions are like.......:twisted: 

  I've already had two supportive, and helpful posts to this one, out of the three responses.    _Those that get the frustration in the post also read the detail I posted._

>  And remember, nobody is forcing you to use Linux. If you really can't think of a reason to bother with it, just don't. There's nothing wrong with using XP if you prefer it.

  True.  However being under the thumb of M$ isn't my idea of the best way to go.  I was hoping linux had matured to the point of being less of a P.I.A. than the last time I tried it.  ubuntu is close.  Jury is still out.

---

### Post by daller on 2006-10-01
> **Josh1 said:**
> sudo dpkg-reconfigure -phigh xserver-xorg


Damn, that command is effective...

It wiped my custom-build xorg.conf, but I like it anyway!

BTW: see this: [https://help.ubuntu.com/community/XDisaster](https://help.ubuntu.com/community/XDisaster)

---

### Post by Fingerlakes_Dave on 2006-10-01
> **tseliot said:**
> Did you read my guide?
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

or did you try envy?
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

 Concern:
NOTE: Envy will REMOVE your RESTRICTED MODULES. Therefore if you need the restricted modules for a hardware device of yours (e.g. for your wireless card) DO NOT use Envy

 Since I can't even get the drivers set up using the help/faq on the main site, how would I know this script wouldn't kill my system?

---

### Post by Josh1 on 2006-10-01
> **daller said:**
> Damn, that command is effective...

It wiped my custom-build xorg.conf, but I like it anyway!

BTW: see this: [https://help.ubuntu.com/community/XDisaster](https://help.ubuntu.com/community/XDisaster)

Its only suppose to be used in emergencies I guess... I accidently screwed up the install for an nVidia once and that saved my life. :P.
- Josh

---

### Post by tseliot on 2006-10-01
> **Fingerlakes_Dave said:**
> **I don't really care what others think.**
Your opinion.  Opinions are like.......:twisted:
Being descriptive will help you to get more support.

---

### Post by chajuram on 2006-10-01
> **Fingerlakes_Dave said:**
> 
  Ever try to get MS support?  That concept evaporated years ago with MS.


U misunderstand, by support is ment that the guy who is making the hardware is also making the essential drivers to sell his stuff to 95% of the people who use windows.


> **Fingerlakes_Dave said:**
> And automatix is?  A program?  A command?  Might be a great suggestion.  Without a frame of reference....????

Try google. People here are trying to help you out.

---

### Post by Fingerlakes_Dave on 2006-10-01
see new thread

---

### Post by TheFlamingBush on 2006-10-01
deep breathe Dave!.....deep breathe mate!...the people here will definately help you mate, if they can!....which im sure they can!;)

---

