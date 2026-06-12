---
title: "Ubuntu newbie"
date: 2007-10-15
forum: Multimedia &amp; Video
---

### Post by Ciwan on 2007-10-15
Hello all

I downloaded Ubuntu today, and I must say I'm enjoying it so far. its really fast (compared to windows) and no virus worries and its free !! very nice :-)

I tried playing a DVD 10 minutes ago. But I couldn't !!!

What do I need to do, so that I can watch DVDs in perfect quality ?

ohh and how do I know if my GPU drivers are loaded and if they are the latest ?

Thanks guys :)

---

### Post by pbcartwright on 2007-10-15
most distros do not come complete with what you need to play DVD movies, because of NON-free codecs and drivers..
my suggestion would be to install mplayer, which will also install win32codecs.
sudo aptitude install mplayer win32codecs

installing vlc might also work
as for your drivers, it depends on the video card you have. If you have an NVIDIA card, you will want to install envy ( sudo aptitude install envy) to configure it with the non-free up-to-date drivers, or just go to nvidia.com and download the latest and read teh README and install it. I'm not sure about ATI cards, I think they also have issues you need to work on.

---

### Post by rsambuca on 2007-10-15
Just follow the instructions on [this help page]("https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-dvd") to install the dvd codecs.  Let us know either way whether it works.

---

### Post by Ciwan on 2007-10-16
Hi guys

Right I just finished installing [ gxine ] but when I insert a DVD, nothing comes up (like an autoplay that asks you what you want to do) or is that not present in Ubuntu like it is in windows.

A dvd icon has been created on my desktop, but when I right click on there I get [ Open ]...when I click [ Open ] I get into the DVD files folders.

I thought clicking open would make the film work. How do I check if DVDs are now playable in [ gxine ] ??

Thanks

---

### Post by Soarer on 2007-10-16
It should work if you have followed the instructions.

I would install vlc - it will play pretty much anything in my experience.

---

### Post by Ciwan on 2007-10-16
I followed the instructions !! although I don't know what the reason is for terminals and how terminals work, but I copied and pasted the [ "command line" ] into the terminal and I clicked Enter.

I then went and did the other steps about going into multimedia and typing a code there under [ Play DVD disc ].

When I insert a DVD into my PC, a little DVD icon appears on my desktop ( I'm guessing that is what is suppose to happen)....But where do I go from there ?? Do I need to click on something for the DVD to start playing ? or is it suppose to play automaticaly? cause on mine nothing happens !!!

---

### Post by rock-hopper on 2007-10-16
Hello Ciwan.

I am very much a newbie here myself and I am more than aware of the 'panic' that can seize beginners when things don't seem to go exactly to plan.  I had a very similar feeling of panic with a problem of my own only last week.

I would say; read very carefully all the information you are being offered.  Take yourself out for a walk and a pint and forget about PCs for an hour or two.  Come back to it fresh and it will all fit into place.

Good luck.  Let us know how it goes.

rock-hopper.

---

### Post by Ciwan on 2007-10-16
Ohh and about my GPU drivers. here are my specs first of all

Intel Core 2 Quad Q6660
Asus P5k-E Wifi
EVGA Geforce 8800 GTX 720MB
500GB Samsung Spinpoint HDD
(2x) Samsung WriteMaster DVDRW

I went to the EVGA site and navigated to my GPU, but they do not have Ubuntu drivers, only windows XP/Vista

and why is it that only one of my DVDRW drives are present when I click on my computer in Ubuntu.

I'm sorry to ask all these questions, but I want everything to work well. And I'm a new to the whole Ubuntu world (the only OS I had used before was Windows) I love Ubuntu, I didn't know it'll look and feel so good. before I was so scared of trying Ubuntu/ Linux but now that I have, I'm very happy :)

---

### Post by Ciwan on 2007-10-16
There is a video player called [ totem ] or something similar I think. that came with the OS when I installed it.

Can't I make that play DVDs ??? I don't like getting new programes. I always like making the programes that came with the OS to do everything. e.g. play MP3, DVDs, VCDs...etc

---

### Post by Soarer on 2007-10-16
I tried this too - put in a DVD to see what happens (Merry Christmas Mr Lawrence, if you are interested).

Anyway, Totem (which is called Movie Player in the menus under Sound & Video) opened up automatically and played only the soundtrack!

So I opened vlc and went to 'Open Disk'. It played it just fine.

So I would suggest opening a terminal and pasting:

```
sudo aptitude install vlc
```

and see how you like it.

I guess I *could* try & figure out why Totem won't work, but vlc does and that's all I care about.

HTH.

---

### Post by Ciwan on 2007-10-16
Alright, I'll try VLC when I get home, I'm currentley at work. I'll be home for about 5 oclock.

Thanks

---

### Post by Ciwan on 2007-10-16
Hello again

Right I installed VLC and still I can't play DVDs

In VLC when I went to file>open disc>DVD ...........I got the following error

[ Unable to open 'dvdsimple:///dev/scd0' ]

someone please help :confused:

---

### Post by yabbies on 2007-10-16
is it only dvd's that won't play?
are you able to play music from a cd?

---

### Post by Ciwan on 2007-10-16
I just played an MP3 disc, and that worked fine !!!

---

### Post by yabbies on 2007-10-16
have you opened all your repos before  you installed all the codecs?
multiverse, restricted, etc?

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by Ciwan on 2007-10-16
I have no idea what you are talking about ? so No I have done what you just said !!

If I do it now, will i have to uninstall and then reinstall VLC again ??? or will it just work !!!?????

no one told me I had to do what you said !! :confused:

---

### Post by Ciwan on 2007-10-16
by the way that link is for Ubuntu 6.0#.

I think my version is higher. It had a 7 in it. and it was the latest.

When I go to System > Administration > I do not have software properties like that page says !!!

---

### Post by yabbies on 2007-10-16
you are probably running fiesty

so go to System>Administration>Software Sources

Ubuntu Software tab
check the boxes
(main)
(universe)
(multiverse)
(restricted)

then open a terminal and type
```
sudo apt-get install libdvdread3 libxine1-ffmpeg
```

---

### Post by Ciwan on 2007-10-16
OK I'll do that now, and let you know if succesful

---

### Post by Ciwan on 2007-10-16
OK I just did that, and it is still the same

I get the same error with VLC

Are you sure there isn't anything that need changing in VLC before playing a DVD ??

---

### Post by yabbies on 2007-10-16
does it work with Totem or Mplayer?

---

### Post by Ciwan on 2007-10-16
Hi no it does

that is what I get when I try to play the DVD in totem

[ Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.

Please install the necessary plugins and restart Totem to be able to play this media. ] :(

---

### Post by amlucent23 on 2007-10-16
> **Ciwan said:**
> OK I just did that, and it is still the same

I get the same error with VLC

Are you sure there isn't anything that need changing in VLC before playing a DVD ??

you dont have to do any installing from the terminal if you arnt comfortable with it. to install with out the terminal go to (im not in front of a ubuntu box at the moment but). First you'll need to enable programs that arnt officially supported by ubuntu.

Click Applications-> Add/Remove Programs 

at the top right hand cornor of the window that comes up there is a drop down box that might say "supported applications" or something like that... choose "all applications" from the drop down box. now close the add/remove programs utility.


now to actually install it-

 System->Administration->Synaptic Package Manager

after it opens click search and type in "libdvdcss" (without the quotes of course). it should return results and you will have to check the package with a check box then hit apply or update or something. After this package is installed you should be able to play any dvd in totem- the default ubuntu movie player.

---

### Post by Ciwan on 2007-10-16
It still didn't work, I get the same message again :-?

OK here is what I did

I went to Applications > Add/ Remove Programs >> At the top right hand corner I changed whatever was there to >> All Applications

I then went to System > Administration > Synaptic Package Manager and I entered my Admin Password. I then clicked on the Search button at the top and typed [ libdvdcss ] >> Search

I got these results

gxine
libdvdcss2
libdvdread3
libdvdread-dev
ogle
ogle-mmx

two of the ones starting with libs had green boxes and the final one (libdvdread-dev) didn't so I ticked that for installation >> clicked Apply > something downloaded and installed.

I then restarted my PC and went to Totem clicked on file and clicked on Play DVD but again I got the same error :-(

any more suggestions :-(

---

### Post by amlucent23 on 2007-10-16
> **Ciwan said:**
> It still didn't work, I get the same message again :-?

OK here is what I did

I went to Applications > Add/ Remove Programs >> At the top right hand corner I changed whatever was there to >> All Applications

I then went to System > Administration > Synaptic Package Manager and I entered my Admin Password. I then clicked on the Search button at the top and typed [ libdvdcss ] >> Search

I got these results

gxine
libdvdcss2
libdvdread3
libdvdread-dev
ogle
ogle-mmx

two of the ones starting with libs had green boxes and the final one (libdvdread-dev) didn't so I ticked that for installation >> clicked Apply > something downloaded and installed.

I then restarted my PC and went to Totem clicked on file and clicked on Play DVD but again I got the same error :-(

any more suggestions :-(


Hmm.. that should have worked without a hitch but not to worry we will get you straightened out.

you are using ubuntu 7.04 correct?

if you are, follow the directions in this section of "How to install multi media codecs" and the following section "How to install DVD playback capability" on this website. 

Note: this websites instructions tell you how to do it through the terminal (faster but a bit daunting, you can do it i believe in you) also some of the programs may already be installed but its ok just follow the instructions.

[URL="http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Codecs_.26_Browser_Plug-ins"]http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Codecs_.26_Browser_Plug-ins
[/URL]

report back if it fixes it or not please. If it does not dont get discouraged, we will get it

---

### Post by Ciwan on 2007-10-16
here is what I got when I did the second command on the link you sent me, for the first command it said that them plugins were already the newest on there !

ciwan@Ciwan-PC:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
ciwan@Ciwan-PC:~$ 

Should I move onto the third command ?

---

### Post by Ciwan on 2007-10-16
here is what I got with the third command:

-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxine1-ffmpeg
E: Package libxine-extracodecs has no installation candidate
ciwan@Ciwan-PC:~$ 


same problem as second I think ! :confused:

---

### Post by Ciwan on 2007-10-16
aaand here is the end command that I entered into the terminal

ciwan@Ciwan-PC:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ciwan@Ciwan-PC:~$ 

that 0 newly installed worries me a bit

I'll try playing a DVD now and see if it works

---

### Post by Samhain13 on 2007-10-16
Hi, you can check out this page for added stuff:

[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

---

### Post by amlucent23 on 2007-10-16
> **Ciwan said:**
> here is what I got with the third command:

-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxine1-ffmpeg
E: Package libxine-extracodecs has no installation candidate
ciwan@Ciwan-PC:~$ 


same problem as second I think ! :confused:

Im pretty sure that means that you do not have the extra repositories activated correctly. this part of my previous post. see if it still says "all programs" you may not have saved the configuration.

Click Applications-> Add/Remove Programs

at the top right hand cornor of the window that comes up there is a drop down box that might say "supported applications" or something like that... choose "all applications" from the drop down box. now close the add/remove programs utility.

Does it still say all programs?

---

### Post by Ciwan on 2007-10-16
I just check Add/ Remove programs and it says [ All Available Applications ] in the right hand corner. Which is what you said it should be set at.

When I tried playing the DVD this time....the little warning plays along with the BBC logo thing, but when it gets to the actual film it stops and I get the error message :-

[ An Error Occurred

The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss? ]

any ideas what this could mean :confused: I was so happy when I saw the warning, cause I thought it'll work this time :(

---

### Post by amlucent23 on 2007-10-16
that means that "it believes" libdvdcss is not installed. (this is a program that decodes a commercially encrypted dvd) I had you install it in this step-

> now to actually install it-

System->Administration->Synaptic Package Manager

after it opens click search and type in "libdvdcss" (without the quotes of course). it should return results and you will have to check the package with a check box then hit apply or update or something. After this package is installed you should be able to play any dvd in totem- the default ubuntu movie player.

double check in synaptec that it is installed (has a check next to it).

what is the out put of this command?

```
sudo apt-get install libdvdcss2
```

---

### Post by Ciwan on 2007-10-16
this DVD that I'm trying to play by the way is Life In The Under Growth (complete series) by none other than the great David Attenbrough.

---

### Post by Ciwan on 2007-10-16
The output of the command you sent me is

[ ciwan@Ciwan-PC:~$ sudo apt-get install libdvdcss2
E: Type 'sudo' is not known on line 57 in source list /etc/apt/sources.list
E: The list of sources could not be read.
ciwan@Ciwan-PC:~$  ]

What does this mean ? :(

---

### Post by rsambuca on 2007-10-16
Your repository list is messed up.  Post the output of ```
cat /etc/apt/sources.list
```

---

### Post by yabbies on 2007-10-16
you either don't have the new medibuntu repository or as Sambuca said your repos are messed up.

[http://ubuntuforums.org/showthread.php?t=413626]("http://ubuntuforums.org/showthread.php?t=413626")

---

### Post by Ciwan on 2007-10-16
OK here is what I got

ciwan@Ciwan-PC:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release Candidate i386 (20071010)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
sudo apt-key add - && sudo apt-get update

ciwan@Ciwan-PC:~$ 


why is it messed up ?? I haven't done anything wrong :(

---

### Post by amlucent23 on 2007-10-16
> **Ciwan said:**
> The output of the command you sent me is

[ ciwan@Ciwan-PC:~$ sudo apt-get install libdvdcss2
E: Type 'sudo' is not known on line 57 in source list /etc/apt/sources.list
E: The list of sources could not be read.
ciwan@Ciwan-PC:~$  ]

What does this mean ? :(

sounds like your sources.list is fubar, there is an error in it on line 57. 

there are quite a number of different ways you could fix it. this is an already documented way fairly easy way.

follow these steps in this section-

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Manually_edit_sources.list]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Manually_edit_sources.list")

it will overwrite any errors in your sources.list.

---

### Post by yabbies on 2007-10-16
now it's all clear!

you are running gutsy not feisty

---

### Post by rsambuca on 2007-10-16
You should have told us yesterday that you were using Gutsy.  It would have changed a lot of things!  Anyways, you will have to delete the last two lines from your sources.list.

---

### Post by Ciwan on 2007-10-16
I don't know what Gusty/ feisty are ?? So which is better Gusty OR Feisty ?? And how do I install the better one If I don't already have it.

When I delete the last two lines ?? will everything be fine ??

---

### Post by amlucent23 on 2007-10-16
> **amlucent23 said:**
> Hmm.. that should have worked without a hitch but not to worry we will get you straightened out.

**you are using ubuntu 7.04 correct?**

if you are...

lol.. no worries man. we were all new once.

---

### Post by Ciwan on 2007-10-16
which is the latest version of Ubuntu ?? and how do I get it ?? :(

---

### Post by amlucent23 on 2007-10-16
> **Ciwan said:**
> I don't know what Gusty/ feisty are ?? So which is better Gusty OR Feisty ?? And how do I install the better one If I don't already have it.

When I delete the last two lines ?? will everything be fine ??

Gutsy is the new version of Ubuntu that will be released in 2 days. Feisty is the current release of ubuntu. Generally I wouldnt recommend a new user use a OS before it was released, but its ALMOST here and its very stable now so..... do as you like. 

it was a big deal because we just installed a bunch of software designed for a different OS.. who knows what we broke. My advise.. if you dont have anything too much already invested into your install is to just wipe your drive (backup personal files first) then reinstall.

It is very simple to play a dvd in gutsy.. just insert it and play with totem.. it will ask you if you want it to install what it needs then it will install them and it just works- very easy.

---

### Post by Ciwan on 2007-10-16
How do I delete the last two lines ???

When I retype the code you gave me earlier I get the source list but I can't delete any line or alter any thing !!

---

### Post by Ciwan on 2007-10-16
alright cool amlucent23

I don't have anything important YET !! only a Johnny Cash album that I just downloaded :) ( I love J. Cash)

So I'll back that up now and install Gutsy*, but can you give me a link for downloading Gutsy image that I can then burn onto a CD or DVD ??

Thanks

---

### Post by amlucent23 on 2007-10-16
> **Ciwan said:**
> which is the latest version of Ubuntu ?? and how do I get it ?? :(

the latest version (in two days) is 7.10  a.k.a Gutsy the previous version (in two days) is 7.04 a.k.a Feisty-

Feisty, Gutsy, Edgy, Breezy.. these are the developers codenames for the OS

the numbering system is the year.month the os was released

so 7.04 was released in the fourth month of 2007

and 7.10 will be released in the tenth month of 2007

dont worry.. i didnt understand it at first either

---

### Post by Ciwan on 2007-10-16
I go to download section on Ubuntu's site and it asks me what type of computer I have !!

What do I put ??

my specs are

Intel Core 2 Quad Q6660
Asus P5K-E Wifi Motherboard
EVGA Geforce 8800 GTX 720 MB
500 GB Samsung spinpoint HDD
(2x) Samsung DVDRW writemaster drives

thanks

---

### Post by amlucent23 on 2007-10-16
> **Ciwan said:**
> alright cool amlucent23

I don't have anything important YET !! only a Johnny Cash album that I just downloaded :) ( I love J. Cash)

So I'll back that up now and install Gutsy*, but can you give me a link for downloading Gutsy image that I can then burn onto a CD or DVD ??

Thanks

sounds like you had Gutsy (7.10) the first time. you should just use that cd. but incase you still need it.

[http://releases.ubuntu.com/releases/7.10/]("http://releases.ubuntu.com/releases/7.10/")

you want the desktop version.

---

### Post by amlucent23 on 2007-10-16
> **Ciwan said:**
> I go to download section on Ubuntu's site and it asks me what type of computer I have !!

What do I put ??

my specs are

Intel Core 2 Quad Q6660
Asus P5K-E Wifi Motherboard
EVGA Geforce 8800 GTX 720 MB
500 GB Samsung spinpoint HDD
(2x) Samsung DVDRW writemaster drives

thanks
you have a intel architecture x86 processor (most PCs are)

download this one- [http://releases.ubuntu.com/releases/7.10/ubuntu-7.10-rc-desktop-i386.iso](http://releases.ubuntu.com/releases/7.10/ubuntu-7.10-rc-desktop-i386.iso)[URL="http://releases.ubuntu.
com/releases/7.10/ubuntu-7.10-rc-desktop-i386.iso"]http://releases.ubuntu.com/releases/7.10/ubuntu-7.10-rc-desktop-i386.iso[/URL]

also.. after you get it all set up- as a new user these might help you out- [http://screencasts.ubuntu.com/node]("http://screencasts.ubuntu.com/node")

---

### Post by Ciwan on 2007-10-16
How is it that you can get Gutsy even though it hasn't been released yet ??

Just to make sure ....that link you sent me (the CD/DVD image) is for Gutsy (aka 7.10 aka latest version)  right ??

Thanks amlucent23 :)

---

### Post by Ciwan on 2007-10-16
Ohh I just remembered...How do I burn that image onto a DVD if I don't have Nero ???

---

### Post by TNakos on 2007-10-16
for most drivers justs search " (type of card) drivers) youll get something if you have nvidia i reccomend the nvidia-glx-new driver

---

### Post by Siph0n on 2007-10-16
You can get Gutsy before its been released because people are testing it :)

---

### Post by kayvortex on 2007-10-16
[This link]("https://help.ubuntu.com/community/BurningIsoHowto") will explain how to burn the ISO. It's easiest if you are still running Ubuntu: you basically put a blank CD in, close the pop-up box that opens (i.e. ignore it), find where you saved the iso file, right click it and select "Write to disk".

Maybe someone ought to clear a few things up, just so that you know what's going on; so let me have a go:

A new version of Ubuntu is released every six months. The current version is 7.04, called "Feisty Fawn". The next release (which will be officially released in two days time in fact) is "Gutsy Gibbon" and is version 7.10. Each version of the OS is designed to work on a certain type of processor: the most common one (which is what you also have) is x86; so you should download this one. You can also choose to download a 64bit version (called x86_64, or amd64, or intel64 -- mostly, these are synonymous). I'd recommend not downloading a 64bit OS right now because you need to mess around with it a bit in order to get some things working.

In order to do certain things, you may need to download certain packages and libraries and stuff from "repositories". These are basically locations where you can download this stuff and the OS will install them automatically. You tell the OS where to find these repositories in the file /etc/apt/sources.list . You can edit this file with "gedit": go to Applications -> Accessories -> Text Editor. Click Open, and then enter "/etc/apt/sources.list" in the Location bar.

In general, a good place (apart from this forum) to find out how to do certain things (like editing the sources.list file and installing dvd codecs) is [this guide.]("http://ubuntuguide.org/wiki/Main_Page") The Gutsy stuff hasn't been filed in yet, but click on the Feisty guide and take a look.

---

### Post by Ciwan on 2007-10-16
Hello again

Right I'm back. This time I'm on Ubuntu 7.10 Gutsy.

And guess what I still can't play DVDs..LOL

so what do I do now ?

---

### Post by Ciwan on 2007-10-16
I downloaded and installed the [ libdvdcss ] but totem gives me the same old message, saying that I can't play this encrypted DVD :(

Are you Ubuntu can play DVDs ?? I've trying to get it to play a DVD through the whole day...but no success.

someone please please HELP :( I like Ubuntu and I wan to keep it.

---

### Post by yabbies on 2007-10-17
go back through the check list that we gave you and like before post your outcome.
make sure all your repositories are open before installing
w32, libdvdcss2, and gstreamer

some highly encrypted movies WILL NOT play in Totem.
vlc is a better player than totem and will have a higher success rate of what you are trying to play.

---

### Post by jayaramk on 2007-10-17
> **Ciwan said:**
> I downloaded and installed the [ libdvdcss ] but totem gives me the same old message, saying that I can't play this encrypted DVD :(

Are you Ubuntu can play DVDs ?? I've trying to get it to play a DVD through the whole day...but no success.

someone please please HELP :( I like Ubuntu and I wan to keep it.



better either install vlc or mplayer.... these are available in the repositotries or install them via the synaptic package manager........ else install the gstreamer plugins.....

---

### Post by amlucent23 on 2007-10-20
In case anyone has any further questions about the correct way to install/configure Gutsy for DVD playback please take a look at this wonderful screen cast the ubuntu screencast team has put together.
[URL="http://screencasts.ubuntu.com/Watching_Video"]
http://screencasts.ubuntu.com/Watching_Video[/URL]

---

