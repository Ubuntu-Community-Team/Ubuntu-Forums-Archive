---
title: "DVDwas working.. now not.New install."
date: 2009-02-04
forum: Multimedia Software
---

### Post by forestwalkerjoe on 2009-02-04
I am still in all truth , a newbe.So.. there will be things i understand.. and then all the rest. 

I have been playing with linux off and on for a couple years now.. and family friends had a hard virus issue. I was trying to set up a duel booted system for them .. so that they can use the things they want in Windows.. ( their choice) and the rest in UBUNTU LINUX IBEX. 
ran into some trouble.. so i chose to learn a bit about UBUNTU by installing DUEL BOOT onto my very old laptop. we had some issues with the install.. and functions.. most of which have been addressed by PYTHIAS22. 
EXCEPT ONE.. the DVD player.. was by default not working.. i was able to do the extra downloads.. and i played an ABBOT COSTELLO DVD on the system with no trouble. I tried my LINGO Interactive DVD language course.. NO DICE. 
thats ok.. but i took lap top to my night job.. security.. and popped in a NETFLIX Video.. and it freezes the system. IT does mount it.. but it gives errors. wont play. 
i checked anther DVD.. not NETFLIX.. same same.. freeze Crash. 
i have had a couple of the PLAYERS on here.. i am wondering if they are conflicting. 
Just a side note.. i have not actively tried any DVD other than the above .. and only right after that update from the extras area for download. 
JAVA ETC. 
yesterday i did notice on the GETTING STARTED PAGE some offerings that are good for folks to check out.. one was new to me.. MIRO.. it claims its INTERNET TV.. in a stretch of a way.. it is. I downloaded some TV news things and so forth.. and the quality is quite good.. they delete after you have watched them.. and no need to be connected to watch them. 
I am wondering if that program hijacked my Codex's or some such or if they Players conflicted or some thing. Can some one help me out here? i want to be able to show the system to the host family.. and say.. SEE ain't this GREAT!
i have two other issues.. but one is about the Dial out modem in this lappy. I will have to actually use that here and again "IF" this lappy becomes a support laptop for helping install LINUX on other systems.

---

### Post by forestwalkerjoe on 2009-02-06
ok.. some day someone will actually come and EVEN VIEW my posts here. 

I have been told to try and use mplayer not Movie player aka TOTEM.. i have downloaded and it just wont function. It opens.. says NO Disk loaded.. then closes. if i just place a DVD in the drive and close it.. TOTEM takes over.. freezes and then it becomes a big hassle to get it closed again.. and while waiting for a FORCED CLOSE pop up.. REISUB doesnt even work.
I tried GXINE.. seems simple enough.. but no dice.. VLC.. and that was a nice idea.. but nothing happends when I try and click to open the DVD for it. 
i hope some one out there is going to be willing to help a feller out. 

FWJ

---

### Post by redroad55 on 2009-02-06
This guide is a great companion for the new person..take the time and read it .. If you have any questions about a step post back here but please be willing to initiate those things which are right at your fingertips .. [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")
Best to you

---

### Post by forestwalkerjoe on 2009-02-06
well.. thank you for that posting. 
I had been reading another type of UBUNTU Guide and i was lost. 
the one you gave with a connection to help postings was great. 
I now have the DVD player working again. 
I do have one BIG issue that i can not find.. as of yet.. a fix for. 
when i added that extra repository to the apt thing.. it asked me for an update.. and the update installed MPLAYER.. which doesnt work nor does it list on the choices of open DISK with.. So i cant say how that one works.. btu i can say.. that TOTEM is not doing a good job. its jocky.. delayed and clumsy. the one that works is one a guy named pythias suggested.. VLC. 
that is just smooth as butter. BUT every time i put in a disk.. TOTEM takes over as the " MOVIE PLAYER" and i have to stop it.. force a close.. then go onto the VLC thing. 
when i use System / Control Center / preferred applications.. and GO to media.. it doesn't give me any other choices. MOVIE PLAYER aka TOTEM.. and some music only player. if i use CUSTOM.. it says add script here. I have not the first clue what "script" that would be.. i am assuming i have to tell the system HOW to find VLC player.. Have you any idea how to designate VLC as the dominate player? 
and can I now safely uninstall or i guess that would be APT-GET REMOVE TOTEM? or will that mess up other things in the web browser? 
thanks for your help.. i was kinda amazed that some one responded and it was a very workable solve. 
FWJ

---

### Post by mc4man on 2009-02-06
It's fairly easy to set vlc as the default player for dvd's in Hardy (8.04) and very easy in Intrepid (8.10)
Which one are you using?

for Intrepid 2 ways
Go to home folder -> edit -> preferences -> media and set vlc in the dvd movie drop down.
Or insert a dvd, hold down the shifht button, you'll get a pop up when the disc mounts, choose vlc in the drop down and ck. the 'alwayspreform this action' box

For Hardy

[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

---

### Post by forestwalkerjoe on 2009-02-06
WOW.. that worked nice! 
I am using the 8.10 version.. and on an older laptop by Sony Viao.. older as in more then 4 years. i cant even recall when this one came out. 
It has the support for ram and CPU. 
Some one like you guys could be very cool to talk to , if i could pick your brains on how to config a DVD system like Totem or VLC.. i have tried to config a bit on VLC to get it very smooth but there is still a tiny .. once in a while , lag. almost like it's having to check back with the disk a bit too much.. i am not sure. 
BUT for the intent and purpose.. we have solved the Thread request i made. 
thanks. 
both of you. 

I should hope I  get the same luck with the other 4 threads i have posted. 

So far no one has even viewed them. 

I am bound and determined to get this lappy up to the best quality i can.. and to learn Every thing i can.. it will be an example set up. My Desk top is next. 
FWJ

---

### Post by mc4man on 2009-02-06
You can add the nautilus 'preferences' to your main menu (disabled by default, there's many useful things in there.

Right click on Applications -> edit menus.
Highlight Preferences and in the right side box enable 'file management'

It can now be accessed from System -> Preferences -> file management

---

### Post by redroad55 on 2009-02-06
How much ram are you running .. check this link for more on vlc
[http://wiki.videolan.org/Category:How_To]("http://wiki.videolan.org/Category:How_To")
post back..Best to you

---

### Post by forestwalkerjoe on 2009-02-06
> **mc4man said:**
> You can add the nautilus 'preferences' to your main menu (disabled by default, there's many useful things in there.

Right click on Applications -> edit menus.
Highlight Preferences and in the right side box enable 'file management'

It can now be accessed from System -> Preferences -> file management

I dont want to seem dull.. but i did as you suggested.. and it gives me ability to alter the display on the desk top.. and choose which Player plays.. and s on.. but the smoothing out thing i was asking about? Is there some thing in this Nautalis thing that i am not seeing to affect that? 
or was this just in answer to the farther up post.. how do i choose the player i want? 
thanks. 
FWJ

---

### Post by forestwalkerjoe on 2009-02-06
> **redroad55 said:**
> How much ram are you running .. check this link for more on vlc
[http://wiki.videolan.org/Category:How_To]("http://wiki.videolan.org/Category:How_To")
post back..Best to you

Its been a long while since i used this lappy.. and i have had a few. I cant recall but i believe the ram is 1 GIG. 
I cant even recall what the CPU is. 
I do go out and read the stuff you all post in here.. and many of the links you suggest. 
thanks 
FWJ

---

### Post by mc4man on 2009-02-07
> but the smoothing out thing i was asking about? 

missed that, not sure, there are some setting's in vlc you could fool with.

might be good to know what your graphic's adapter is, this will give some info

```
sudo lshw -C display
```

some add. (only the first 20 lines will make much sense

glxinfo

---

### Post by forestwalkerjoe on 2009-02-07
thanks.. here is the out put.. and well.. if you are willing.. i am the ONLY one to use this computer.. and I live alone.. can some one show me how to get out of having to type a password every time i want to use command line or such? 
Sudo.. is some thing like the word super user i heard about.. but i am the only one.. and should not run in that root thing.. how do i get past that? 
I know that is not perfectly related to the original post.. sorry. 
Here is the out put on the display you asked about. 

OUT PUT:
rj@rj-laptop:~$ sudo lshw -C display
[sudo] password for rj: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 86C270-294 Savage/IX-MV
       vendor: S3 Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 11
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-1.0 bus_master cap_list
       configuration: latency=64 maxlatency=255 mingnt=4
rj@rj-laptop:~$

---

