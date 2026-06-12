---
title: "Try Ubuntu hangs at blank screen on Aspire 3000"
date: 2014-03-26
forum: Multimedia Software
---

### Post by winsbury on 2014-03-26
32bit 12.04 boots and runs the 'Try Ubuntu' demo perfectly on one laptop but refuses to run on an Acer Aspire 3000....(EDIT - 14.04LTS solves this issue but read on for how to solve for 12.04 too)

 On the Aspire 3000 after the initial bootup sequence it briefly shows a screen with mouse cursor (arrow) which can be moved around but quickly then changes to a black screen with the backlight cycling through different brightnesses.

Ive tried various things:


[LIST]
[*]nomodeset as per advice in [http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997](http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997) which looked promising but nothing seemed to work for me. 
[*]running the startup without quiet splash - the only thing that looks wrong is one message: *Starting load fallback graphics devices [fail]* 
[*]modifed the bootupwith -- vga=771 as suggested in the included help menu 
[*]modifed the bootupwith -- vga=771 and nomodeset ; this combination got a little further - the screen was alternating between black and some text from the bootup - this was promising so tried ctrl-alt-f1 and a few other function buttons and somehow ended up  at an ubuntu@ubuntu: system prompt and can issue linux commands. 
[/LIST]

So, it  seems to me the graphical desktop is not starting correctly.

There seem to be other threads on the forum with similar issues on machines being upgraded to 12.04 but since this isnt an installed system yet the advice for their fixes doesnt apply to just running the demo.

As noob to Ubuntu Ive come to the end of the road being able to sort this out without asking for some help;  so any help you can suggest would be gratefully received.

---

### Post by stalkingwolf on 2014-03-26
it can take what seems an interminal amount of time to boot completely.  I have one system with only 1 gb of ram that takes several minutes from dvd but is quite fast from a usb stick.  The speed of your dvd can also be a factor.

---

### Post by winsbury on 2014-03-27
That doesn't appear to be the problem - it will sit at the blank (black) screen indefinitely; all that happens is the backlight keeps changing intensity.

---

### Post by Rob Sayer on 2014-03-27
Probably need more info ... go into system information in windows and post the specs.  The graphics adapter may be the problem.  You may not have enough ram to run the graphical installer either.  Some of those laptops had less than 512Mb ram according to a quick search.

Also on my quick web search of "spec Aspire 3000" it said that the gma is SIS Mirage 2 M760, which can't be verified just by that.  I doubt there's just one Aspire 3000.

But SIS video adapters are knoiwn to be a problem in linux in general.

---

### Post by holycow131415 on 2014-03-27
My laptop starts black too on linux distros. All i have to do is use function+up or down to change the brightness to get my screen to come on.

---

### Post by winsbury on 2014-03-27
Okay , a bit more info for those of you kind enough to be lending a hand:

The laptop has a 1.25Gb ram which passes all memory tests. The embedded graphics card is indeed a SIS M760GX and is I suspect the root of all evil, although since XP can run it, it seems perverse that linux is having such problems. There seems to be tons of threads about problems with this particular adaptor but none that give a definitive solution that I can find.

If I leave it to boot for a REALLY long time the backlight does eventually stop flashing and a X cursor comes up then some questions stating low graphics mode is needed. Interestingly I can briefly see a normal mouse arrow cursor during some of the flashes; its as though X starts then immediately fails. Anyway, after selecting the low graphics mode option the screen goes blank again but will then echo anything I type ( so the brightness is in fact okay at that stage.) alt-ctl-f1 gets me to a shell prompt so it seems linux has booted but X is having problems.

Just tried the b43.blacklist=yes trick found in this thread [http://ubuntuforums.org/showthread.php?t=1966655&page=2](http://ubuntuforums.org/showthread.php?t=1966655&page=2) but same symptoms as above.

---

### Post by Bucky Ball on 2014-03-27
*Thread moved to **Multimedia & Video**.*

I know you only just got here, and welcome, but SIS can be troublesome and you may get more help here. I'm just wondering if that will run Unity. You might try something like Xubuntu, Lubuntu or a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD"), which is text based, and working your way up, finding out what works and doesn't ... :-k

PS: You have 1.25Gb of RAM, but the embedded graphics is using some of that. How much? You can generally find out, and set it, in the BIOS.

---

### Post by winsbury on 2014-03-27
bit more info...

after the long delay during the boot process a window opens with an X cursor that says:
*Your screen, graphics card and input device settings could not be detected correctly. You will need to configure these yourself*

options to
*run on low graphics mode for one session* - see previous posts as to what happens if I chose this option.
*reconfigure graphics*
        -->    *use default (generic)* - does nothing, just loops back to submenu
        -->    *use backed up configuration* - does nothing, just loops back to submenu
*troubleshoot the error*
    -->    *review the x server log*
        -->    message in among the text stating that SIS 76x and AMD processors use shared memory and performace is limited. 
        -->    review startup errors - no errors
        -->    edit configuration file - loops
        -->    archive configuration logs - saves to /var/log/failsafeX-backup-140327143105.tar ????
*exit to console login* - shows a bunch of startup [ok] messages ending with **starting load fallback graphics devices [fail]* , this screen echoes anything I type and ctl-alt f1-f6 gives a console prompt, ctl-alt-f7 returns to error message screen, ctl-alt-f8 to f12 blank screen.

If I type 'startx' at any of the consoles I briefly get a arrow mouse cursor then it fails with messages:
[I]segmentation fault at address 0x0
Fatal server error 
caught signal 11
server aborting
terminated with error (1)[/I]

---

### Post by Bucky Ball on 2014-03-27
If you are running Ubuntu you need to type:

```
sudo service lightdm start
```

or

```
sudo start lightdm
```

Like I said, with those specs you'd be better off going for something lighter. Unity will probably crush a Gb of RAM.

---

### Post by winsbury on 2014-03-27
Hi Bucky Ball, no prob; you moved me while putting that last post in so previous post wasnt replying to that so hope that didn't confuse anyone.

The issue for me is that I'm trying to find an alternative for XP that doesnt involve throwing all our hardware away and thowing pots of money at Msoft for new licenses and training when the existing systems 'can' already do what we need. I was therefore looking for a turnkey linux graphics based desktop that we could run on all our pcs and laptops and put wine on top with ms-office to get the basics up and running reasonably quickly. As far as I can tell Ubuntu is the distro that seems most mature for the transition of MS office users and figured if I could get the demo version to run on each machine I might stand a chance of migrating. I dont think I'm alone in this as it seems to be a common need among other noob threads here as there are a lot of IT managers that dont want anything to do with windows 8 and finding an alternate OS is top of the to do list. The learning curve is vertical for me so I would like to avoid text based systems although I have used unix, vms, rsx , dos and plenty of other OSs over the years I am very rusty and certainly dont expect any of our users to be accepting of a text interface. I was expecting , perhaps naively, that ubuntu would be as clean as windows xp to install by now. Seems that's not the case. I'm particularly surprised that threads citing SIS problems go back to 2012 or earlier and yet are still not easily resolved, as you probably know, its a very popular chipset on lower spec business machines where gaming 3d graphics just aren't needed, this is clearly going to put a lot of potential users off until its addressed.

---

### Post by winsbury on 2014-03-27
Its the 32 bit distro which says it should run on much less memory - in fact Ive had it running on other laptops without any issue with less so dont think thats the root problem.

lightdm doesnt seem to work either - blank screen with backlight flashing again now.... will see what happens but it doesnt look promising at the moment.

edit:
.... it bombed out with the same symptoms

Bios shows System memory 640KB, Extended memory 1214MB, Video Memory 64MB, VGA BIOS SiS 2.27.g8

I've a 1GB sodimm winging its way to us for this machine which will max it out at 2GB but thats not going to change the video settings.

---

### Post by Bucky Ball on 2014-03-27
Slight misunderstanding. I meant the minimal installer is a text-based install. You then add whatever desktop environment you like; xfce, lxde, openbox, Unity (which is what Ubuntu uses) ... whatever works best for you (and on a low-spec machine you'd be looking at xfce or lxde for starters). ;) This way, you can design exactly what you need with no added fat!

There was, once upon a time not that long ago, the text-based alternate install disk along with the desktop installer for machines that couldn't handle the desktop installers disco all bells and whistles graphic install. You still ended up with the same install (and the install process was the same, just looked different). ;)

Be aware that the actual Ubuntu kernel used by all the Ubuntu flavours (Xubuntu, Kubuntu, Ubuntu, Lubuntu and others) is identical, it's what goes on top that creates the differences (desktop environment, default apps, window managers, etc.).

---

### Post by mörgæs on 2014-03-30
If you want to get Lubuntu 13.10 running on SIS graphics there are instructions in the link in my signature.

---

### Post by winsbury on 2014-03-31
Thanks guys; but I'm going back to Windows...

FWIW Over the past few days Ive tried various flavours of Suse and Debian on these machines all with similar results; the SiS adaptor is unsupported on all of them as standard ISO installs, no doubt there are work arounds with enough effort expended but thats just not good enough. I have installed standard Red Hat linux on much older 386 based machines in the past without any of this level of difficulty. It strikes me that the Linux and Microsoft worlds have more recently come to the conclusion that no one should use old hardware any more. The ONLY reason I wanted to change now because the new windows 8.1 requires changing all our hardware and a good chunk of our software out too but the barriers to entry for Linux are proving just too steep.

I am really dissapointed to come to this conclusion;  imho there needs to be a concerted effort to help Microsoft users migrate more smoothly; CLI based operating systems are just too damn difficult for the vast majority, a graphical desktop is essential nowadays, as is a common look and feel to the applications that run on it and an install process that detects and adjusts to the hardware its presented with. I consider myself to be pretty IT literate but getting a desktop working with this popular graphics chip working has proven way beyond me and it seems the same for many many others that want to migrate judging by the hundreds of similar threads about SiS and linux; 

...this stuff should just work out of the box or it will stay marginalised for the IT elite only.

---

### Post by mörgæs on 2014-03-31
I would say that the workaround requires very little effort, actually you just have to copy a few commands as mentioned in the other thread. You don't even have to experiment. 

When you consider that SIS has not done much to support Linux I think that's a quite good solution.

---

### Post by winsbury on 2014-03-31
On the face of it you're absolutely right but it would be a heck of a lot easier if the full install detected an SiS chip and automatically installed the patch especially since its been around for a quite while and clearly needed by so many. It begs the question why is this critical info so hard to find and more importantly why isn't it integrated within the main release ?

Anyway thank you for the links, I'm giving it a go right now, I suspect the next fight will be getting the wifi card to work. Oh well, more anon...

---

### Post by winsbury on 2014-04-01
An update: We're nearly there .... reinstalled windows, installed lubuntu as dual boot, applied patch, rebooted and hey presto we have a graphical desktop albeit pretty basic looking, Yippee. 

Network access is still very shaky though - on ethernet connection it works fine and Ive installed the b43 installer and that has woken up the network card and connected to our local wifi. While boot on eth0 is okay it wont change over to wlan if eth0 gets disconnected. Boot on wlan is very slow 'waiting for network' but does eventually start on wlan. Clearly the hardware and drivers are okay but something is getting in the way of cleanly selecting the most appropriate connection.  Presumably there's some auto/manual setting for the connections somewhere but there's no two-computer nmapplet as described here [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager) so struggling again at the moment.

---

### Post by mörgæs on 2014-04-01
Congratulations. 

I think best is to mark this thread 'solved' and open a new one in [Networking and Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336"). Please also see the sticky notes there.

---

### Post by winsbury on 2014-04-22
Ive just been playing with full version of Ubuntu 14.04LTS on the very same Aspire 3000 ; the really good news is that the display issue is now completely resolved with the standard installation. Important: do not elect to install with the options to install upgrades or 3rd party software as that causes a hang during in the install process. The standard install does not include the drivers for my broadcom wifi card so that looks like it will still require some manual tweaking. The bad news is that even fully upgraded with 2GiB ram and 80GiB hdd 14.04 it is VERY slow to the point of being almost unusable. It might be possible to turn off some of the pretty graphical dissolves and animation which I'm sure would help but Ive not yet got far enough below the hood yet to work that out.

---

### Post by mörgæs on 2014-04-22
Ubuntu is far too heavy for a 10-12 years old card. Lubuntu is a better option.
When you posted #17 wasn't Lubuntu behaving well?

---

