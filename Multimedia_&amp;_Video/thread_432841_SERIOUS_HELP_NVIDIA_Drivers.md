---
title: "SERIOUS HELP NVIDIA Drivers"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by lebron_jordan_kobe on 2007-05-04
Good Morning Ubuntu,

I am a broken man, at my wits end with installing and tweaking Ubuntu, if this is the bleeding edge I need a transfusion....here is my system:

3.0 Ghz Pentium 
1    Gig Ram
1  160 Gig Drive
1 120 Gig Drive
52x DVD burner
1 Audigy 2 Platinum ZS
1 Geforce 7600GT 256 MB Ram Dual DVI
1 Haupauge 500 MCE
1 GV42L 42" HD TV connected via DVI
NO INTERNET CONNECT

I was a hardcore windows user until XP began giving me issues with Media Portal, so I decided to switch to Linux, plus everyone else was doin it. I don't have internet access at home so I can't use apt-get or ENVY.

I am having serious issues with screen resolution and drivers, since it is a HTPC, it is very much a concern.

Problems:
 Screen resolution stuck at 800 x 600

Tried Solutions:
1) Edit xorg.conf by adding 

```
 "ignoreEdid" [/CODE"]

[CODE]"UseEDID" "false"
```

 or
Changing the monitor, screen, sections
```
 MODES      "1200 x 768"  "800 x 600" 
```

2) Reran xcongif  to autodetect monitor


Installing Nvidia Drivers
1) Downloaded  nvidia-glx, linux-image-386, linux-image, linux-restricted-modules

I installed them in this order:

linux-image
linux-386
linux-restricted-modules
nvidia-glx

Changed my xorg.conf file to say:

[CODE] Driver "nvidia"

Ubuntu booted then it broke, (I didn't know linux has a blue screen of death too???), it said X-server has failed because it was setup improperly and it returned me to the command-line.

I looked at the log file and it said the error was:

"nvidia driver not found"

So I used dpkg ...... xconfig again to change my driver to nvidia manually, still my GUI won't load.

-------------------
Folks I am almost ready to go back to windows, I have been on this forum and every other one for the past week, lunch breaks, nights, PLEASE HELP!
"nvidia driver not found"

---

### Post by kidders on 2007-05-06
Hi there,

What version of Ubuntu are you using? Assuming it's Feisty, why not use the Restricted Driver Manager to get you started?

---

### Post by tseliot on 2007-05-06
Follow "Method 1 Offline" in my guide:
[http://ubuntuforums.org/showthread.php?p=2587126](http://ubuntuforums.org/showthread.php?p=2587126)

---

### Post by lebron_jordan_kobe on 2007-05-08
Kidders- Thanks for the response, I am using Fiesty,  should I install the newest version and what is the manager?

TS- Thanks for producing about the only useful guide- I was following yours to the T, where do you think I went wrong


Prec. Guys

---

### Post by lebron_jordan_kobe on 2007-05-08
TS-

I believe my problem is trying to identify which driver I need for my Nvidia Geforce 7600GT Dual DVI unit, which one of the three will work for my system:

DRIVER 9755, 9631 or 7184

I am running the 32 bit version of Ubuntu, also do I need to download the linux-generic kernel or will it come from the CD rom

```
 sudo apt-cdrom add 
             sudo apt-get update
            sudo apt-get install linux-generic


```


I am completely offline with that computer, nowhere near internet access, I need to download all the packages from a seperate system.

---

### Post by kidders on 2007-05-08
> **lebron_jordan_kobe said:**
> I believe my problem is trying to identify which driver I need for my Nvidia Geforce 7600GT Dual DVI unit, which one of the three will work for my systemIt looks as though version 9755 will work for you. You can check though, at [http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp)

(Sorry... I know that wasn't addressed to me.)

---

### Post by lebron_jordan_kobe on 2007-05-08
No apologies neccessary lol I appreciate it

---

### Post by GSF1200S on 2007-05-11
> **kidders said:**
> It looks as though version 9755 will work for you. You can check though, at [http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp)

(Sorry... I know that wasn't addressed to me.)

Im seriously wondering if Id have better luck with another distro in terms of video drivers. I have the famed NVIDIA video card, and the situation still sucks. Ive been using the 9755 driver for a while now, installed via the command prompt manually (running the official NVIDIA binary). Ive had flashing black screens, and often times (ive had LINUX freeze far more than WinXP) completely freeze right after a nice black screen flash. Ive tried the envy installer, and it fails at installing the NVIDIA common kernel. I would really like trying the NVIDIA 9631 driver, but according to the NVIDIA website, its a legacy driver? I dont know how anyone can get the one in Adept working.. it gives me an API mismatch every time I try it. 

Its frustrating, because my reason for Linux was stability. (K)ubuntu hasnt had a single freeze, unless im doing something OpenGL related. Nobody seems to know how to fix these problems, and it seems like theyve grown accustomed to a hard power off once a day (about the frequency for me). Ive even done presentations on OpenOffice at work with Windows because im too afraid of Linux freezing in the middle of my presentation. Just sad- plain and simple...

---

### Post by kidders on 2007-05-11
In graphics terms, most Linux distros are virtually identical. The drivers all come either from the kernel or Nvidia itself, and Xorg is effectively a de facto standard. In general terms, regular crashing could be caused by:

[LIST=1]
[*]Using the wrong kernel
[*]Using the wrong graphics drivers
[*]A bug in either of the above (the 9755 Nvidia driver has several)
[*]Misconfiguring Xorg
[*]Hardware failure
[/LIST]

Having said that, there is no reason not to try a few different distros, and see what you think. :-)

---

### Post by GSF1200S on 2007-05-11
> **kidders said:**
> In graphics terms, most Linux distros are virtually identical. The drivers all come either from the kernel or Nvidia itself, and Xorg is effectively a de facto standard. In general terms, regular crashing could be caused by:

[LIST=1]
[*]Using the wrong kernel
[*]Using the wrong graphics drivers
[*]A bug in either of the above (the 9755 Nvidia driver has several)
[*]Misconfiguring Xorg
[*]Hardware failure
[/LIST]

Having said that, there is no reason not to try a few different distros, and see what you think. :-)

The only other distros that attract me are PCLinuxOS, Gentoo, and Arch.. Overall, I really like (K)Ubuntu alot.. I think its a great distro for beginner to advanced Linux users. With your knowledge, do you know of any way for me to get the 9631 driver installed for my card? Im pretty sure my Xorg is configured right. I load the dbe module, I have all the visuals associated with Beryl added for when I actually use it (rarely), and Ive edited out all the wacom entries. As far as hardware, my computer is but a few months old, and it works on windows flawlessly. Its frustrating that Im having all these NVIDIA issues.. its supposed to be the better card for linux. I dont hear of ATI users having these problems.. other than a hard install and no control over the video card...

---

### Post by kidders on 2007-05-11
Hey again,

> **GSF1200S said:**
> The only other distros that attract me are PCLinuxOS, Gentoo, and Arch.I'm also a Gentoo fan ... it's quite a different world though!

> **GSF1200S said:**
> With your knowledge, do you know of any way for me to get the 9631 driver installed for my card?Whenever something graphical goes funny for me, I tend to forget about package repositories, and go for manual configuration. I'm not familiar with how (or whether) version 9631 of Nvidia's graphics drivers works with Ubuntu, but my first stop would be Nvidia's website's driver download page. There are a number of downsides (in the long term) to the manual approach, but at least you would get to try the driver out, and see if it makes any difference.

The other place that might be worth a look is Nvidia's support forums.

---

### Post by GSF1200S on 2007-05-11
> **kidders said:**
> Hey again,

I'm also a Gentoo fan ... it's quite a different world though!

Whenever something graphical goes funny for me, I tend to forget about package repositories, and go for manual configuration. I'm not familiar with how (or whether) version 9631 of Nvidia's graphics drivers works with Ubuntu, but my first stop would be Nvidia's website's driver download page. There are a number of downsides (in the long term) to the manual approach, but at least you would get to try the driver out, and see if it makes any difference.

The other place that might be worth a look is Nvidia's support forums.

Yeah, I might actually get in NVIDIA's forums and try to find a solution. If I find a solution, Ill post it in these forums.

I have never been able to use the repos, or envy, and Ive never wanted to use Automatix. Ive been installing the official 9755 NVIDIA binary via the command prompt for quite a while, but once again with freezes, etc. Maybe there is some reference im not familar with pertaining to tweaking video drivers? Ill do anything to get these problems resolved. Whats weird is it seems that KDE has alot less problems with freezing and black screen flashes. It makes no sense to me, but I know for a fact at least in my case that this is the truth. XFCE isnt too bad, but GNOME is horribly unstable. Also.. I know im missing some things on config, because my CPU usage is strange. For example, on the rare occasion I use beryl for converting windows users, Ill notice just zooming out to the cube will cause 1 core to reach 90% while the other stays at 2%. Reinstalling Beryl fixed this. Firefox jumps the usage far more than Opera when scrolling.. Just weird things that make me question the quality of these NVIDIA drivers...

According to the NVIDIA website, it seems like 9631 is legacy, yet in the repos, 9631 is a regular GLX driver. 9755 is glx-new, and then there is a seperate glx-legacy driver. Confusing- I havent been able to find an answer with Google yet. It sucks, because it seems like the people using older video cards are having less conflict then people with the newer ones. I think at this point its obvious NVIDIA isnt placing a high priority on quality...

PClinuxOS looks cool as its RPM based (larger but lower quality selection of packages), yet it still has apt-get and synaptic, and KDE which I like...

Gentoo seems AWESOME, but the compiling times is kind of turning me away.. I havent really been able to find a specific article about compile times variant to the system you run... I have a pretty nice laptop, but im guessing there will still be stretches of 6-10 hours of compiling stuff..

---

### Post by kidders on 2007-05-12
> **GSF1200S said:**
> Maybe there is some reference im not familar with pertaining to tweaking video drivers? Ill do anything to get these problems resolved.You might be right. I've found that getting graphics cards to cooperate with Linux often requires far more intimate knowledge of how they work than seems reasonable. Some of the most frustrating issues I've had with Linux have been graphics related, so I sympathise. Unfortunately, these things can be incredibly difficult to diagnose when you're not sitting in front of the PC. :-(

I wonder what would happen if you posted a new thread, with your card's model number in the title. Imo, the ideal would be to find someone with a working configuration, who has exactly the same hardware you have. I'd be perfectly happy to post my config files, or let your poke around my system ... but I have an 8800, so you might not discover anything useful.

> **GSF1200S said:**
> Gentoo seems AWESOME, but the compiling times is kind of turning me awayGentoo's selling point is all the compiling, really. If you wouldn't get much out of it, then it might not be the right choice for you. As a _rough_ guide, setting up KDE from scratch could take 24 hours. Compile times can vary very dramatically though, since no two users' KDEs need be the same.

---

### Post by Visceral Monkey on 2007-05-13
I'm also an 8800 owner and have issues getting the card to work. FYI, if you want to try out a gentoo based distro, try Sabayon. It's actually easier to set up than Ubuntu and will install the correct 8800 drivers and set up beryl by default with no work on your wend.

[http://www.sabayonlinux.org/](http://www.sabayonlinux.org/)

---

### Post by tseliot on 2007-05-13
> **GSF1200S said:**
> Ive tried the envy installer, and it fails at installing the NVIDIA common kernel.
I would like to see your /etc/apt/sources.list

---

