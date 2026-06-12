---
title: "DVD/CD Duplicator"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by caveman56 on 2007-05-14
Hey there, got a little project I'm working on and am hoping someone might have a few ideas on the subject.  Just picked up 4 new DVD burners on sale for 10 bucks apiece and was wanting to make a DVD/CD Duplicator, preferibly with linux, doesn't need to decrypt the video as it will be used to duplicate DVD projects that we make in house, would love to have a linux based solution, seen many windows based ones, but not a big fan of windows.  If anyone has any ideas on the software setup, please feel free to comment, already got the hardware lined out.

thanks,

Dave

---

### Post by srt4play on 2007-05-14
Could you elaborate on specific functions and features you need?  Somehow I get the feeling that putting a disc in one drive, right clicking the icon on the desktop and choosing 'copy disc', and selecting the drive to copy to, is not what you want and you're thinking of more complicated setups.

---

### Post by caveman56 on 2007-05-14
Basically we make yearbooks for a school I teach at, along with other DVD's for events, music cd's for concerts, and much of the same for other business, that we need multiple copies of.  Right now when we have yearbooks ready to go, it takes days to duplicate them all, but we don't run enough to make it cost effective to send them off and have them duplicated, we're talking runs of 50 or so.  What I'd like to do is have a linux based solution that I could copy the iso of the yearbook to, then run x many copies and have 4 burn at once, spit out the discs, then I'll reload and it'll be on its way again.  I've done it with usb drives on windows with nero, but I'd prefer to use a linux solution with the internal drives if possible.

thanks,

Dave

---

### Post by srt4play on 2007-05-14
Well, since you used nero to do it on Windows it may be worth downloading the neroLinux demo to see if it will do what you want. 

[http://www.nero.com/eng/NeroLinux3Beta.html](http://www.nero.com/eng/NeroLinux3Beta.html)

---

### Post by caveman56 on 2007-05-14
Yeah, I'm going to give that a try.  I was actually hoping someone had come up with a floppy based distro specifically for that.  Guess I'll have to make that my next project  lol

---

### Post by srt4play on 2007-05-14
Check this out
[http://turbojet.sourceforge.net/](http://turbojet.sourceforge.net/)

---

### Post by caveman56 on 2007-05-14
Yeah this looks promising, but haven't figured out how to install it yet, no makefiles or anything, might be keyed to run under kde already though.  Love it when there's no documention supplied.

---

### Post by srt4play on 2007-05-14
I see what you mean.. I can't figure out how to compile it either.  I sent an email to the author I'll post whatever reply I get.

---

### Post by caveman56 on 2007-05-14
Great, I did the same, hopefully one of us will get a reply  lol

---

### Post by srt4play on 2007-05-14
I got a reply, and was able to compile and run it!

You will need to download these in synaptic:

qt3-dev-tools
libqt3-mt-dev
g++

Then, in the turbojetGUI directory run:

qmake turbojet.pro
make

The turbojet binary will be in the turbojetGUI/bin/ directory.

I only have one burner so I can't test it out very well but I'm glad I have it now just in case!

---

### Post by caveman56 on 2007-05-15
I'm compiling now and have 4 DVD/RW's coming on Friday, planning on making a duplication center with them.  Wal-mart in the area was closing out the liton drives for 10 bucks each, picked up 8, build the first one and if if works gonna build a second one.  I'll let you know how it works.

---

### Post by srt4play on 2007-05-15
Great, keep us (me?) posted.

---

### Post by huanix on 2007-05-20
I have been working on a duplicator tonight to distribute a video yearbook for my wife's school (sounds like the same story as caveman) .. here's what i know: 

 NeroLinux 2.0.x.x doesn't seem to support the use of multiple burns or the ability to set a quantity of disks to burn.

 I am settling for K3B tonight to get my batch of 50 done, it is available through apt and it is easily set for quantity. The biggest drawback is [afaik] you can only run one instance of K3B at a time, which limits the burning to one drive.

 I'm excited to hear how TurboJet works for you guys, it would be a dream to automate this process!

---

### Post by caveman56 on 2007-05-21
Well guys, it works, like a champ.  I built a machine with 3 drives in it, burned 3 copies of a 4.3gig DVD at the same time on 4x media, finished all 3 in approx 15mins.  Definetly acceptable for my needs.  Going to build a second one so I can dupe 6 at a time.  Built it on a PIII 800mhz system with 512megs SDRAM, 30 gig IDE Drive, 3 LiteOn 16X DVD+-RW DL drives, running StudioUbuntu 7.04  was easy to setup, the only issue was StudioUbuntu uses the old HDC HDD naming convetions, wheras Fiesty uses SCD0 and SCD1 etc for its drives.  Besides that little glitch there was no problems setting up.  If you guys want to buidl one and need any help, just post.

Dave

---

### Post by srt4play on 2007-05-22
Glad to hear turbojet worked out for you.  

I'm thinking it needs to be packaged up and put in the repos.  As far as I know through searching, it's the only linux app of its kind.

---

### Post by caveman56 on 2007-05-23
Yeah, I was thinking along those lines too.  I've been planning on making a donation to the guys church if I could get it going, so I'm going to do that and email him and see if he minds if I package it up with some documentation so others can use it.  It works great, have two duplicators up and running now, no more swapping 50 discs in and out everytime I run a yearbook.

Dave

---

### Post by srt4play on 2007-05-23
And this, my friend, is what open source is all about.  We are all in this together.

---

### Post by caveman56 on 2007-05-24
Amen, we had all windows workstations here at the school I teach at when I started, kids were getting viruses on them, had to clean off viruses and adware almost every day.  Over my first summer I switched everything over to Linux, we still have a few windows machines that some of the teachers use because they like to use publisher, but all the student work with ubuntu on a daily basis.  This next year we have a smart board comming, with linux software, the teachers that use the ubuntu system and the students love em.  Since we run on totatly donated computers it's great not having to buy XP licenses for them all.

---

### Post by DavidWeisgerber on 2007-09-01
Hello together,
cool to hear that there are other guys outside who are using my software. If you need any help please post at this thread I will try to answer as soon as possible.
Btw, please check out the project's website [http://turbojet.sf.net]("http://turbojet.sf.net") because it has further information about hardware setup which is more important than the software itself in my opinion.

---

### Post by ElSeeDee on 2007-09-01
OK, I started off with a HD and 3 CDRWs in a case, connected to the motherboard. TJ started normally, I assigned the CDRWs according to the results of a "wodim -scanbus". TJ would recognize each drive correctly, but when I would try to do a burn, the two CDRWs on the same cable would show an error.

 I emailed the author, David Weisgerber, and he said I should have each CDRW on a separate cable (thanks for the quick reply, David!). 

I got a PCI controller and now each burner has its own cable. But... now the program won't start. The jet engine splash screen appears/disappears, but the program never launches. Any ideas?

---

### Post by ElSeeDee on 2007-09-02
OK. I figured it out. I remembered I installed Kubuntu after I got back from the store with my PCI IDE card. David, I don't think TurboJet likes Kubuntu. #-o Which is a bummer, 'cuz I think I like the look and "feel" of Kubuntu better.

So... I put Ubuntu back on and everything comes up normally. Yay!\\:D/

I now have a new question:
I have a total of 4 CDRWs. Two are plugged into the PCI card and two are plugged into the motherboard. When I run TJ, the 2 PCI drives copy but the 2 mobo drives give errors. Will the 2 mobo IDE not support CDRWs in TJ?

---

### Post by ElSeeDee on 2007-09-02
Wow. Talk about an experience... Ok. TJ doesn't like for a burner to be on the same cable as a HD. I guess that's what was messing up my two mobo CDRWs. I disconnected the one from the HD cable and rebooted. I started TJ and it saw the 3 remaining drives. And they burned! woot! woot!

---

### Post by DavidWeisgerber on 2007-09-02
> **ElSeeDee said:**
> Ok. TJ doesn't like for a burner to be on the same cable as a HD. I guess that's what was messing up my two mobo CDRWs. I disconnected the one from the HD cable and rebooted. I started TJ and it saw the 3 remaining drives. And they burned! woot! woot!

That's a common IDE/ATAPI problem. A CD writer will block the whole channel while burning so you really need to attach it to a single channel.

Some tips:
a) Do not use cdrecord with setuid root - It will grab real time priority which will block the rest of the system. Instead set the CD writers device files to be accessible by your normal user.

b) Use S-ATA CD Writers with kernel versions 2.6.18 and above. Today's mainboards have many connections for it, the cables are not so fat like the IDE ones and you do not have the problems like above.

c) If you have IDE CD Writers you want to use you can try to connect it via USB. There are IDE->USB adaptors available and USB 2.0 should have enough throughput.

d) Use device files (like /dev/sr0) instead of the SCSI device numbers.

---

### Post by ElSeeDee on 2007-09-02
OK. "wodim -scanbus" returns the SCSI numbers. How do I get the device files?

---

### Post by DavidWeisgerber on 2007-09-02
That's easy
hda = first ide channel master
hdb = first ide channel slave
hdc = second ide channel master
.
.
.
For SCSI:
/dev/srX (x = number, eg /dev/sr0) or
/dev/sgX or
/dev/scdX
just try out. If you are right, turbojet will display the name of the drive after detection phase. If you are just using device numbers, growisofs and cdrdao will fail so you can only use cdrecord (iso cds and audio cds).

---

### Post by ElSeeDee on 2007-09-03
OK. I need to correct myself. I had a drive problem. I picked up some new drives and plugged all four of them into the PCI card. All four worked like a dream! =D> So I guess it was my other drives that just weren't working; not a problem with the software or the card/cables. 

David, may God bless you, your church and your ministry!:KS

---

### Post by kevpatts on 2007-09-04
Hey guys,

This looks very useful for something I'm looking to do. One question: How do I get 12/13 SATA ports in one machine without spending a fortune on PCI cards?? I need them for 11 SATA DVD-RW drives and one/two hard drive(s).

Am I going too far? I'll be using a Thermaltake Armour case so I can fit them.

Kevpatts

---

### Post by ElSeeDee on 2007-09-04
Don't know where you're from, but you might want to do a check on Craigslist for your area. There may be someone selling one or two for $10 or $15.

---

### Post by kevpatts on 2007-09-04
Thanks man. I live in Dublin, Ireland though so there's no Craig's list for me! I like to buy new equipment anyway.

---

### Post by ElSeeDee on 2007-09-05
[http://dublin.craigslist.org/]("http://dublin.craigslist.org/")

---

### Post by DavidWeisgerber on 2007-09-05
I would suggest buying a mainboard with six S-ATA connectors and a S-ATA PCI card with six connectors. I got a bulk S-ATA PCI card with 6 connectors one month ago from ebay for just 25€...

---

### Post by kevpatts on 2007-09-05
> **ElSeeDee said:**
> [http://dublin.craigslist.org/]("http://dublin.craigslist.org/")
ElSeeDee, I can't find anything in the computer section that is actually in Ireland at all! Thanks for the link though, I didn't know it existed.

> **DavidWeisgerber said:**
> I would suggest buying a mainboard with six S-ATA connectors and a S-ATA PCI card with six connectors. I got a bulk S-ATA PCI card with 6 connectors one month ago from ebay for just 25&#8364;...
David, thanks for the heads up. All the new ones I've seen on Komplett.ie are RAID controllers and about &#8364;500! I'll keep my eyes peeled.

I've been told by an IT guy in work that SATA controllers are build for Hard disks and that DVD-R drives may not work on some of them. I didn't think this was the case. Has anyone seen this problem?

---

### Post by DavidWeisgerber on 2007-09-05
> **kevpatts said:**
> I've been told by an IT guy in work that SATA controllers are build for Hard disks and that DVD-R drives may not work on some of them. I didn't think this was the case. Has anyone seen this problem?

I had this problem with my mainboard (before I did a BIOS upgrade) and the Linux kernel with version <2.6.17 but now it is working perfectly (why shouldn't it work?).

---

### Post by DavidWeisgerber on 2007-09-05
Hi people,
I am currently finishing turbojet2 which I will put online soon.
Features:
+ Better GUI -> more place for controlling CD Writer
+ Place where you can leave notes
+ Ability to burn MP3/Ogg Vorbis files directly (will be converted before burning them)
+ Optimized for 1280x1024
+ You do not need to restart after changing configuration

Screenshot:
[http://home.in.tum.de/~weisgerb/turbojet2.png](http://home.in.tum.de/~weisgerb/turbojet2.png)

---

### Post by ElSeeDee on 2007-09-05
Woohoo! \\:D/ You da man!=D> Can't wait.

---

### Post by SCS on 2007-11-07
Im using a quadcore with Ubuntu 64bit and a combination of USB and SATA drives.  Turbojet will compile using the instructions in this thread but none of the drives are seen.

---

### Post by DavidWeisgerber on 2007-11-08
You need to configure the drives yourself, turbojet does not detect them automatically.
Go to the File->Configuration menu and adjust the number of drives you have. Next configure each drive and restart the application. If you have given the correct device file at configuration, the manufacturers name and the model name should be displayed.

---

### Post by DavidWeisgerber on 2007-11-10
TurboJet 2 Release Candidate 1 is out now. Grab it from
[http://sourceforge.net/project/platformdownload.php?group_id=141613]("http://sourceforge.net/project/platformdownload.php?group_id=141613")

Changes to the version we are using for some months in our church are:
+ Better colors: In order to distinguish between two devices, there are two kinds of colors: A darker and a brighter one.
+ Corrected one little bug (missing initialization)
+ Added icon

You will need:
- Qt4
- cdrecord / wodim (for Audio CDs / ISO images)
- cdrdao (for .toc/.cue images)
- growisofs (for DVD images)
- eject
- ogg123 (for burning Ogg Vorbis files to Audio CDs)
- mpg123 (for burning MP3 files to Audio CDs)

On the sourceforge site there are source packages and the compiled executable for x86 Linux available.
And also a Debian / Ubuntu package now!

---

### Post by SCS on 2007-11-24
Is there a config file somewhere that can be edited?  With the RC1, i am able to compile and run.  The first time i went to the config and set up a burner incorrectly. Now everytime I try to go back to the config I get: 

Error-All CD Writers must be idle!

Basically I want to flush the settings and reconfigure.

---

### Post by DavidWeisgerber on 2007-11-25
Strange because all burners should be idle at startup (even if some are misconfigured).
However, you can find the configration file in you home directory at this place:
.config/FEGMM/turbojet2.conf (this reminds me that I should change the place of the configuration file)

other notation: 
~/.config/FEGMM/turbojet2.conf

---

### Post by SCS on 2007-11-28
So now I have deleted the conf and recreated it several times.  I am at the point were I am adding all the drives properly as far as I can tell.  I am getting the /dev file from K3b and mine look like:

/dev/scd1 (USB)
/dev/scd2 (USB)
/dev/scd0 (SATA)

and I need to set them in that order for devices 1-2-3 respectively.  I can eject the devices within TJ but I do not see the device name. I have attempted to burn both a toc and cue style image but there is only an error. The log doesn' t tell much, only the name of the image I am trying to burn.  I really want this thing to work and will help testing it anyway I can.

Update:  If I use 9,0,0 instead of /dev/scd0, it will tell me the manufacturer of the drive but thats it.

---

### Post by uberben on 2008-03-04
I am working at starting up a small recording studio and also work in my church's multimedia ministry, so I am very interested in setting one of these bad boys up. Has a final version of TJ2.0 been released yet?

---

### Post by DavidWeisgerber on 2008-03-05
The RC1 can be considered as final version. There will be a new release the next months with some (minor) bug fixes.

---

