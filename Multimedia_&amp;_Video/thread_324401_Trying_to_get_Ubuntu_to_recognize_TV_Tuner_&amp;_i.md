---
title: "Trying to get Ubuntu to recognize TV Tuner &amp; install Myth"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by StanMeis on 2006-12-23
I am baffled.  When I posted the type of tuner I've got I was directed to this page with the suggestion that I try this link:  [https://help.ubuntu.com/community/Install_IVTV_Dapper](https://help.ubuntu.com/community/Install_IVTV_Dapper)  

OK, I enabled universe and multiverse then pasted     sudo nano /etc/apt/sources.list  into the terminal and this is what I get:

GNU nano 1.3.10          File: /etc/apt/sources.list

# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy mai$

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
                               [ Read 55 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

As a new Ubuntu user who is used to windows installation CD's that come bundled with hardware this terminal stuff in Ubuntu flat out baffles me.  I have told my story about how I ended up using Ubuntu on my wife's computer and I'll admit it's a rock solid system for the basics but it's proving to be a huge waste of time trying to get some hardware and multimedia applications to work.  It appears that I don't have a prayer getting the tuner and MythTV working unless I had one of the Ubuntu experts looking over my shoulder and telling me what to type in terminal.

Frustration reigns supreme because I'm under pressure by the family to get this thing working and I'm lost.  I think I'm going to have to give it up and go buy a USB video capture device for my windows computer so I can get the holiday videos from the camera onto DVD.  Any last ditch suggestions before I give it up?  I mananged to get Ubuntu installed and everything works great except for the TV tuner.  I plan on sticking with Ubuntu on the wife's computer but I don't see myself migrating both computers to Ubuntu anytime soon.  

The Ubuntu community has been very understanding and I'm happy with the installation with the exception of this one nagging problem.

---

### Post by SyvanX on 2006-12-24
Maybe I missed it, but what tuner are you using?

Also, if you've seen the MythTV Ubuntu Community Docs, I apologize in advance.
But these were really helpful for me as a former Knoppmyth user, getting an Ubuntu system up and running.

[MythTV - Community Ubuntu...]("https://help.ubuntu.com/community/MythTV")

Good luck, and if you haven't had MythTV operational yet, it's worth it.

---

### Post by StanMeis on 2006-12-24
Here's the story.  Two years ago I bought a Sony Vaio Multimedia computer.  Last August it stopped working and was out of warranty.  I took it to the store where I bought it and they quoted me $500 for the Sony board and a minimum of $130 for labor.  I used to build my own computers so I opted to not get it repaired and bought a replacement computer instead.  The wife was still using the last 486 PC that I had built so the plan was to replace the 486 with the rebuilt Sony.

I bought a new motherboard and case, pulled the processor, fan, drives and TV tuner out of the burnt out Sony.  The Sony OEM version of XP would not load due to the motherboard change and I couldn't get them to issue me a new key because I didn't have the rebuild done by an "authorized dealer."  

The tuner is an Asus made for Sony and I used a command that someone posted in one of my previous requests to get the info on the card.  This is what came up:

0000:02:03.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
Subsystem: Sony Corporation: Unknown device 813d
Flags: bus master, medium devsel, latency 32, IRQ 10
Memory at f0000000 (32-bit, prefetchable) [size=64M]
Capabilities: <available only to root>

In response someone suggested that I try this link:
[https://help.ubuntu.com/community/Install_IVTV_Dapper](https://help.ubuntu.com/community/Install_IVTV_Dapper)

I only got as far as the first command in terminal and the message that I posted in this thread was the response.  I have been successful when I cut-n-paste terminal commands found online but whenever something that is not shown in the tutorial happens I'm dead in the water.

---

### Post by SyvanX on 2006-12-24
That Sony card reports that it could use the IVTV driver, but for some reason it hasn't been reported to work.  [IVTV supported hardware]("http://ivtvdriver.org/index.php/Supported_hardware")

It's in the currently unknown section, so there's hope it might work in the future.

I'm not really sure this applies to you, but I know there are some problems with VIA motherboards but it might be something to look into.  It probably doesn't apply, since it sounds like you bought a newer motherboard.
[VIA Motherboard Problems]("http://ivtvdriver.org/index.php/Via_motherboard_problems")

If MythTV is critical you might just want to consider picking up a PVR-150, it's probably worth your time trying to figure out the Sony version.

---

### Post by majoridiot on 2006-12-24
no worries, stan... instead of 

```
sudo nano /etc/apt/sources.list
```

do:

```
 sudo gedit /etc/apt/sources.list
```

which will pull the file up in a gui text editor.

you can cut and paste commands from the guide into a terminal 
window, just make sure the cursor is at the correct position in 
the terminal where you want to paste to.

use right-click to do the cut and paste operations, NOT control x,
v, etc.  if you cut from the guide and paste into the terminal, you
guarantee no typos. :D

holla if you get stuck further into the guide.  i used it and had
total success the first time thru with no probs at all- it's a very
good guide.

good luck!

---

### Post by StanMeis on 2006-12-25
Thank you.  I will try this and see what happens.

---

### Post by StanMeis on 2006-12-25
I tried pasting the code for Mythe and I really fouled something up.  When I start her computer the update icon on the lower right says:

"E: Type 'xX' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem."

No offense to you fine folks who are so generously attempting to help me but I'm seriously frustrated.  Not because of the TVtuner card, it's Sony proprietory so I knew there might be a problem getting it to work, but this "terminal" command stuff is too time consuming to learn.  Every time I connect a new piece of hardware I end up spending hours fooling around with terminal commands and doing google searches trying to research why it won't work.  

I bought the wife a new  scanner, copier, printer that I'm supposed to be setting up for her this morning (it was under the tree).  Now I have to tell her that I fouled up her computer trying to get Myth working and won't be able install her new printer until I resolve the problem.  [-( 

So where is this "repository dialogue" located and how do I correct this problem?

---

### Post by StanMeis on 2006-12-25
I did a search of the error message and found that I had inadvertantly added a couple of X's to the sources list.  It appears that I managed to correct the problem on my own.

I might be a dummy when it comes to "terminal" commands but I must a little smarter than your average dummy  :-? 

I am giving up on the tv tuner and Myth because my research seems to indicate that nobody has had much luck with the Sony Vaio tv cards in Dapper.  There is a gift that is going to be returned to our local CompUSA and the store credit will cover the expense of an external USB video capture.  I'm going to play it safe and use it on my XP box. 

Ubuntu has been a little frustrating at times but stumbling on an answer to correct this error (even though it was my fault) boosted my confidence.  I will need to read the "how to install anything in Ubuntu" tutorial in detail so I don't back myself into a corner again.

Thanks to everyone for their patience with this rookie.

---

### Post by SyvanX on 2006-12-25
Good luck Stan.

---

### Post by majoridiot on 2006-12-25
probably best to give up on it if it's frustrating you and nobody has seen much progress with
it.  as far as the terminal stuff goes... yes, it can be frustrating, but the learning curve really
isn't that bad once you get the hang of things.  it can be intimidating if you're used to gui only.

i recommend checking this book out, stan- it covers TONS of need-to-know and good-to-know
things.  if nothing else, it will alleviate some of the frustration and get you loving ubuntu.

[http://www.amazon.com/Ubuntu-Unleashed-Andrew-Hudson/dp/0672329093](http://www.amazon.com/Ubuntu-Unleashed-Andrew-Hudson/dp/0672329093)

i paid full over at the local book shop... and it was worth every penny.

also, if your printer/scanner is an hp, i suggest the hplip driver and guide-

[http://hplip.sourceforge.net/supported_devices/index.html](http://hplip.sourceforge.net/supported_devices/index.html)

it was a painless install for me and everything functions as it should.

---

### Post by StanMeis on 2006-12-25
Thank you.  The printer is an HP and I have the information so that install shouldn't be too difficult.  If I was learning the Ubuntu OS for my PC I'd be devoting the time to learning it but we're using it on my wife's PC.  The only time I log onto Ubuntu is when I'm installing or trouble shooting something for her.  Eventually I'll probably install Ubuntu on my main box but it's an Athlon 64 and I understand there are still some issues on those systems.  I'll have to a) be way more familiar with Ubuntu b) be certain that wine is working on the 64 bit systems so I can run a few specialty programs that aren't available for Linux and c) be sure that drivers are available for all of my hardware.  That probably won't happen until Microsoft announces that they're going to stop supporting XP.  

I am trying out a podcast called Linux desktop for beginners in addition to the Ubuntu podcasts.  I'll read some online tutorials and see if I can find a book as well.  If Ubuntu was on my main computer I'd be learning a lot faster.

---

### Post by ronacc on 2006-12-25
take heart the learning curve on terminal useage is worth the effort and applicable even in windows ( yes windows does have a terminal they just call it a cmd prompt) and also quite usefull once you get the hang of it , don't blame Ubuntu or linux in general for hardware problems , blame the manufactures who chose not to support linux or even make available enough info so someone in the linux community can write a driver for their stuff , reward the ones taht DO support us by giveing THEM your buisness.

---

### Post by ronacc on 2006-12-25
addition to above , I diddn't see your last post . I have been running both suse and ubuntu on an amd64bit athalon box fo 2 years now with no major issues and almost no minor ones .I dont use wine much but havent had any problems with what I have used it for. I have been "windows free" since the late 90's and don't miss it a bit .

---

### Post by Saubazi on 2006-12-26
Couple of recommendations. Don't try installing mythtv before you have your hardware working
there are easier ways to start and concentrate on television than piling up all the possible problems simultaneously.

This is to say for analogue TV-card perhaps try first simply tvtime to see you got your hardware up and running and first then try myth. For DVB-T try kaffeine, it is the easiest way - once you get the stuff running proceed to mythtv.

For mythtv this is one useful forum [www.mythtvtalk.com](www.mythtvtalk.com)

after a short google it would appear to me that your card should really use ivtv.

You should use dmesg command first before you give modprobe ivtv command and afterwards
to see what it reports about loading the driver. There should be no errors there.
Additionally lsmod should list lateron the ivtv driver among the other things.

---

### Post by majoridiot on 2006-12-26
> **StanMeis said:**
> Eventually I'll probably install Ubuntu on my main box but it's an Athlon 64 and I understand there are still some issues on those systems.  I'll have to a) be way more familiar with Ubuntu b) be certain that wine is working on the 64 bit systems so I can run a few specialty programs that aren't available for Linux and c) be sure that drivers are available for all of my hardware.

i run the 32 bit ubuntu distro on my amd64 box and it runs very, very well.  i initially went
with the 64 bit distro, but was annoyed by the lack of 64 bit apps and frustrations with some
32 bit apps that didn't like a 64 bit environment.  after an ill-considered "upgrade" to edgy,
i did a fresh install of 32 bit dapper and the box has never run so well.

as far as mythtv guides go, i recommend mario's EXCELLENT ubuntu mythtv/ivtv guides-

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by StanMeis on 2006-12-26
Thanks to all for your help.

I gave up on the Sony Proprietory TVtuner card because I don't have enough spare time to trouble shoot these issues.  I'm thinking that even if I had been using a standard version of XP (not the Sony bundled version) I probably would have had a hard time finding drivers for that card.  

Consequently, I used an in-store credit from returning another item that we got two of to purchase a USB video capture device for my windows box.  I'm sure that Ubuntu is a good OS but I'm not getting anything done because I've been so busy researching how to get things working or how the Linux applications work.  

Before switching my Compaq AMD Athlon 64 to Ubuntu I would need to be certain of several things.  1) That my Wacom tablet, Epson Stylus Photo R800 and external fire wire hard drive would work 2) Noise Ninja as well as several other specialty programs only available in windows would have to work.

In other words I would have to be 100% sure that all of those items would work before making the switch.  January and March to October are out of the question because I can't afford to be floundering during the racing season.  

I see going 100% to Ubuntu somewhere in the future but there's a lot of research to do before I ever think about that.

---

### Post by ronacc on 2007-01-07
I don't know if this Idea will help much but why dont you do what I do , harddrives are cheap theese days if you have an open bay just stuff in another drive and use grub to dual boot , that way you dont have to partition your existing drive and the chance is just about 0 that you would screwup your xp install. I have one box with quintuple boot on 4 hd's 2 suse(9.2 &10.1)  2 ubuntu(edgy 1 default kernal one custom compiled kernal) and puppy2.12 also a laptop (hp amd64bit with xp and suse10.0) the only gotcha is xp has to be installed first , if its already there you're good to go. if you are going to partition a drive that xp is already on you have to go through some monkey motion to get it to work , xp puts its swap file at the end of the drive which prevents linux from repartioning it , so if xp is already using that drive, turn off the swap file , run diskcleanup ,run defrag   in that order . just turning off the swapfile only deactivates it , its still there just not being used and defrag wont move the swap file so it has to be done in just that order , easier to toss in another drive if you have the open bay.

---

### Post by StanMeis on 2007-01-07
> **ronacc said:**
> I don't know if this Idea will help much but why dont you do what I do , harddrives are cheap theese days if you have an open bay just stuff in another drive and use grub to dual boot , that way you dont have to partition your existing drive and the chance is just about 0 that you would screwup your xp install. I have one box with quintuple boot on 4 hd's 2 suse(9.2 &10.1)  2 ubuntu(edgy 1 default kernal one custom compiled kernal) and puppy2.12 also a laptop (hp amd64bit with xp and suse10.0) the only gotcha is xp has to be installed first , if its already there you're good to go. if you are going to partition a drive that xp is already on you have to go through some monkey motion to get it to work , xp puts its swap file at the end of the drive which prevents linux from repartioning it , so if xp is already using that drive, turn off the swap file , run diskcleanup ,run defrag   in that order . just turning off the swapfile only deactivates it , its still there just not being used and defrag wont move the swap file so it has to be done in just that order , easier to toss in another drive if you have the open bay.

That's not going to work because I don't have a copy of XP.  The motherboard burned out out on my Vaio so rather than pay close to $600 to have the out-of-warranty box repaired I rebuilt it myself.  Sony puts XP on a hard drive partition, the user is prompted to back up XP the first time they use their new computer by burning it onto a series of CD's.  Because I culled the parts out of the Sony and did the rebuild (for $170 instead of $600) Sony wouldn't issue a key to reactivate their OEM version of XP.  Without that I didn't have an OS so that's how I was introduced to Ubuntu.  The Sony OEM tuner was made by Asus but I couldn't locate Linux drivers for it so I went out and bought a USB devise to transfer my VHS tapes onto my XP box.  Even if I had a standard XP install disc my guess is that I might have still not been able to find drivers for the tuner.  Sony (and all the builders for that matter) do a good job of making sure people go to one of their dealers for repairs by restricting access to software.  

When the Vaio board burnt out and I bought a Compaq and set the Sony aside until I had time to rebuild it.  My wife was still using an old 486 with Win98se so we needed another computer anyways.  Now she's using Ubuntu and it's running great with the tuner being the only casualty of the rebuild.  A couple weeks ago I setup an HP printer/scanner/copier and she has been using Gimp to scan family photos.  Sometimes she has to have me help her find things because she's not familiar with Linux.  I'm not either but aside from having to cut-n-paste Terminal commands I'm finding everything else quite easily.  

One of these days I'll probably switch the Compaq over to Ubuntu too and then I'll probably go with a dual boot.  I have the backup copies of XP for the Compaq so that wouldn't be a problem.  There are two hard drives in the old 486 but they aren't big enough for an OS and video editing.  

Thanks for the suggestion but I'm happy with how things turned out and done tearing open boxes for a while.  The nice thing about Ubuntu is that it's so reliable I hardly have to touch her PC unless she's got a question.  She's happy because it's faster and I'm having fun learning Linux on her computer and checking out all the open source software.

---

