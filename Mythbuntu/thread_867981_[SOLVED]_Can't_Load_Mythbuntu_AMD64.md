---
title: "[SOLVED] Can't Load Mythbuntu AMD64"
date: 2008-07-23
forum: Mythbuntu
---

### Post by Ronno6 on 2008-07-23
I finally learned how to check my downloaded disk on a machine with ubuntu. Indications are that everything is OK. 

Machine is Asus M2NPV-VM motherboard, AMD Athlon X2 4600, 2 gigs of RAM, 40gig and 150gig SATA Hard drives, on board nVidea 6300 video, IDE DVD RW drive, no tuner card yet.

When attempting to load Mythbuntu AMD64 build in the live environment, the load proceeds past the completion of the progress bar to a blank screen with only a mouse pointer (arrow), but no further. 
Attempting to install yields the same, except a, X as the mouse pointer. Both pointers respond to mouse movements, but no further loading occurs. 
Anybody have any ideas?

---

### Post by tgm4883 on 2008-07-23
have you tried safe graphics mode?

---

### Post by Ronno6 on 2008-07-23
How do I do that? Machine is new with formatted HD.
Nevermind. I figured that one out. Trying now.

---

### Post by Ronno6 on 2008-07-23
No difference. Same result. Gets to arrow pointer, then all disk activity stops. No further load.

---

### Post by nickrout on 2008-07-23
boot the cd and run the option to check the cd. If it checks out it is OK. It is almost impossible to properly check a burned cd as there are sometimes extra padded blocks at the end of the burn, the don't affect operation of the cd. However if you really want to try checking it:

cat /dev/scd0 |md5sum

where /dev/scd0 is your cd reader device.

Sounds like you have a problem with your video card, likely its running but not showing up properly.

Once booted can you get to a console? (ctrl-alt-f1 key combo).

Have you tried the various boot options (noapic, etc etc)?

---

### Post by tgm4883 on 2008-07-23
Can you get to the terminal when you hit that point?(ctrl-alt-F1)  What speed are you burning at?

---

### Post by Ronno6 on 2008-07-23
I have tried to Check CD for Errors, but the computer ALWAYS hangs up with the progress bar just barely off the left end(starting end.) 

I have tried booting with limited graphics, and that only yields a smaller mouse pointer.

I'm waiting for a new graphics card. I'm currently using the onboard nVidea 6300 for graphics. Thing is, that nothing is running but the fans when things grind to a halt- installing,running live, checking for errors, the whole bit. Things just stop.

The slowest I've been able to burn disks is 8X. I can't slow anything down lower than that. Maybe I need different burning software? I've used Nero, DVDFab platinum,and IsoRecorder. 8X is slowest I've been able to set speed.

Ctrl alt F1 does nothing.

---

### Post by Ronno6 on 2008-07-23
Ctrl-alt-F1 has no effect. 
Slowest I've been able to burn is 8X. I can't seem to set Nero , DVDFabPlatinum, or IsoRecorder slower than that. I would gladly try 4x,2x, or 1x if it would cure the problem, and I could figure out how.

---

### Post by nickrout on 2008-07-23
sounds like a bad burn. You could try a different brand of CDs?

---

### Post by Ronno6 on 2008-07-23
I might have to do that. I finally figured how to burn more slowly via DVDFabPlatinim. Just did one at 4X. I'm reformatting the HDD so as to have a clean starting point. We'll see how it goes. Thanks.

Well, on one attempt it got past the pointer only screen, to the Loading screen with the ubuntu disclaimers.  Then I got hit with some SQUASHFS errors that could not read sections. Now further attempts just do as before: pointer only. I'm going to try slower burn speed, say 1x. Then, i will pretty much give up.

BTW, I'm using Verbatim DVD recordables. Don't get much better than that...............

---

### Post by nickrout on 2008-07-23
> **Ronno6 said:**
> I might have to do that. I finally figured how to burn more slowly via DVDFabPlatinim. Just did one at 4X. I'm reformatting the HDD so as to have a clean starting point. We'll see how it goes. Thanks.

Well, on one attempt it got past the pointer only screen, to the Loading screen with the ubuntu disclaimers.  Then I got hit with some SQUASHFS errors that could not read sections. Now further attempts just do as before: pointer only. I'm going to try slower burn speed, say 1x. Then, i will pretty much give up.

BTW, I'm using Verbatim DVD recordables. Don't get much better than that...............

Yes and no, its where the disks are actually made and in what batch that really counts. 

And is there a particular reason you are using a DVD not a CD?

---

### Post by Ronno6 on 2008-07-23
I'm down to my last out. Burned at 2X on Verbatim DVD. No luck loading. I'm attempting to Check Disk for Errors. The progress bar has gone farther than usual, but disc activity has halted again. I'll give it a while, but it doesn't look good. 
I've tried the Direct Desktop Download, as well as the Desktop ISO Torrent. Nothing works. Must be something in the computer itself. 
It loaded Hardy Heron without any complication, and it loads the Alternate install CD OK as well.I've downloaded and installed the i386 version on my old P3.  I can't understand why the only one that will not work (yet) is the one that I want.
Now I have to wait for hardware.

---

### Post by Ronno6 on 2008-07-23
nickrout wrote:
"And is there a particular reason you are using a DVD not a CD? "

I've burned several CD's, but I cant get my CD burning programs to go slower than 16X burn speed. I don't know if DVDFabPlatinum will burn to CD. That's the only program I seem to be able to slow down to 4X or 2X.

---

### Post by nickrout on 2008-07-23
you say you have a ubuntu machine. Why not use that to burn? k3b is the best burning programme on any platform (IMHO)

---

### Post by Ronno6 on 2008-07-23
I will have to move that machine in from the garage to connect to the LAN. That'll be a task for tomorrow. Thanks for the tip. Is it possible that downloading through the LAN is a problem?

---

### Post by nickrout on 2008-07-23
why would it. if the md5sum of the iso file and the md5sum of the burned disk is ok, then you are fine.

But just to check the burn, mount the cd in your usual working ubuntu system and run md5sum manually like this:

```
cd /media/cdrom
md5sum -c md5sum.txt
```

md5sum.txt is a text file with the md5sum of every file on the cd. the command md5sum -c checks all of those files one by one.

---

### Post by volkswagner on 2008-07-23
I had a similar problem.  Someone recommended using a torrent to download a new image.  Worked like a charm.

---

### Post by nickrout on 2008-07-23
yes that suggestion has already been made (and ignored)

---

### Post by gndprx on 2008-07-23
In post #12 he says that he used the torrent.

I had to use the alternate download just recently as the desktop version would pretend to do an install but fail on reboot.  Once I did the alternate it worked fine and I just had to configure some parts manually.

---

### Post by nickrout on 2008-07-23
oops you are right, yes torrenting is a very good way to fix a slightly broken iso download - in fact its the best way to get the file in the first place!

---

### Post by Ronno6 on 2008-07-24
Yes, As indicated I had to receive an indoctrination into the world of torrents. The final attempt last night was a 2x speed burned disk of the torrent .iso image , on a newly formatted hard drive. 
That having failed, I am going to try again after I receive and install my video card and tuner.
My forehead is flat enough.......................Thanks to all for their help to date. I'll resurrect the thread when the above hardware is installed.
BTW- I have run the md5sum check on the ubuntu machine and all files checked "OK"

---

### Post by Ronno6 on 2008-07-24
A point of interest: When i boot the Mythbunu CD the first screen presented is a white screen that allows you to select your language. This screen is overlaid on the Mythbuntu installation selection type options screen. This screen disappears in 30 seconds or so (there is a countdown on the left side) or as soon as you select your language and hit enter. This is not addressed in the installation manual, which indicates that you will first get the install option screen. Moreover, I see that there is an option listed at the bottom of the options screen for language.
Is this normal, or a clue to what is going on? (Or, NOT going on?)

---

### Post by tgm4883 on 2008-07-24
Nope.  That is a completely normal thing that comes up.  You select your language, then get to the boot menu.  This is where you select live environment or install

---

### Post by Ronno6 on 2008-07-24
When one runs the Check CD for Errors option, Does the program tell you if the disk is correct? I've tried several on another AMD64 machine I have,and all that happens is that the progress bar proceeds all the way across its field, then all stops. CD, HDD, all stop. No indication of good, bad, or ugly! 
That's more than the intended machine does. The progress bar only goes a short distance, then stops. 
If the disk is bad (or good) shouldn't something let you know?

---

### Post by gndprx on 2008-07-24
I believe mine returned a message to the effect of no errors found.

---

### Post by nickrout on 2008-07-24
> **Ronno6 said:**
> When one runs the Check CD for Errors option, Does the program tell you if the disk is correct? I've tried several on another AMD64 machine I have,and all that happens is that the progress bar proceeds all the way across its field, then all stops. CD, HDD, all stop. No indication of good, bad, or ugly! 
That's more than the intended machine does. The progress bar only goes a short distance, then stops. 
If the disk is bad (or good) shouldn't something let you know?

It tells you. But how long are you waiting for the check to finish? It takes a while.

And two posts ago you said > BTW- I have run the md5sum check on the ubuntu machine and all files checked "OK" - was that by manually running md5sum -c md5sum.txt as I suggested? But when you run the check media from the cd boot menu it appears to hang?

As I say it takes a long time to check a cd full of files. The boot menu option is pretty well doing the same as the manual method.

---

### Post by tgm4883 on 2008-07-24
Not really a solution, but have you tried the 8.04.1 alternate amd64 disk?

---

### Post by Ronno6 on 2008-07-24
When I checked the disk on the ubuntu machine, I used the command line md5sum -c md5sum.txt | grep 'OK$'

This returned a line-by-line program check with 'OK' at the end of every line. 
When I run 'Check disk for errors' from the Mythbuntu install option nenu, I have left it for hours and, best case scenario, the progress bar completly moves across the screen, then.....nothing. This  was on my HTPC, which is NOT the intended machine. But, with exception of tuner and vid card, they are pretty much the same. 
The machine that I want to install Mythbuntu on  just hangs up early in the progress bar's trek acroll the field. It never moves more than about 5% of the way across.

A note, when the HTPC sat for an hour with the progress bar completely across, I tried ctrl-alt-F1, and the screen flipped to a blank screen that said........Loading,please wait........
Which I did for about a half an hour with no further progress. 
MOST frustrating.
I have burned an ALTERNATE INSTALL CD, and it appears to work. Should I just quit beating my head against the wall with the Regular version? I've read that the full version is more automated than the alternate. The alternate requires more set-up operations. Maybe I should go that route, but it bothers me that this can't be sorted out to work as it is intended.

---

### Post by tgm4883 on 2008-07-24
This 
```
md5sum -c md5sum.txt | grep 'OK$'
```

Is bad.  This will always give you OK and not tell you anything useful.  If I told you to do that, then I appoligize for wasting your time, for I must have been drinking.

instead just do

```
md5sum -c md5sum.txt
```

If you can't be bothered with every line being displayed, at least grep for the right thing.  You want to grep for the opposite of OK, whether it be failed, error, whatever it is that is what you want to grep.

---

### Post by nickrout on 2008-07-24
> **Ronno6 said:**
> When I checked the disk on the ubuntu machine, I used the command line md5sum -c md5sum.txt | grep 'OK$'



Well... |grep OK$ will return the lines with OK in them, it won't return any failed lines!

---

### Post by Ronno6 on 2008-07-24
First of all, I want to thank you guys for your ongoing interest and support on these issues. I am new to Mythbuntu,ubuntu, and Linux, so I'm learning as I go along. 

The liine I used came from here: 
[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20CD](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20CD)

(except I had to delete the '-v'option in the commnd line)


OK. Having tried your command line still returns all files 'OK' However, the file 
./casper/filesystem.squashfs takes quite a while to read. I have experienced SQUASHFS errors in the past, but reformatting the hard drive pretty much eliminated them, except for the one time I got to the ubuntu disclaimer screen.

---

### Post by nickrout on 2008-07-24
grep -v does the opposite of grep

ie grep OK will show all lines that have OK in them, grep -v OK shows all lines that DON'T have OK in them. You can see why the difference is important.

the squashfs file is by far the biggest file on the CD, thats why it takes the longest time to check its md5sum. 

In realtion to earlier posts, if you use ctrl-alt-f1 to get away from the visual screen during the media check you never get back to the visual screen (at least I haven't been able to).

I can't remember where the success message appears once the cd has been checked.

But if the md5sum -c command returns OK for every file then the CD is definitely OK. 

Another possibility is that the machine you are trying to boot on has a different CD drive that doesn't like the CD you have burned. Interactions between different CD writers, blanks and readers are difficult to analyse.

The problem is most likely to be in the interaction of the live CD system and your graphics card. Sometimes you need to use one of the boot options to get a particular graphics card to work properly on the live cd. I can't recall what all the options are, but they are available from the boot screen. I'm sure they will be documented somewhere in ubuntu's online docs too.

---

### Post by Ronno6 on 2008-07-24
Cd drive is Sony Optiarc, can't remember the model. It is IDE. HD is Seagate Barracuda 40gig SATA. I've also tried the Maxtor 150gig SATA with no difference. Video is onboard nVidea GeForce 6150, I think it is HD capable. Do you think there is an IDE/SATA issue? The HTPC (the other AMD64 X2  machine) is the same MB,processor, but with PNY nVidea Verto 7600GS video card. It has a Samsung CD/DVD burner, but I can't recall if it is IDE or SATA. It generally takes the process farther, but still won't boot, as I've indicated earlier.Maybe I should burn and attempt to install on that machine ??Maybe the same burner for both would do the trick?
I've tried booting in the "Safe Graphics" mode, but no difference except a smaller pointer arrow.

---

### Post by nickrout on 2008-07-24
And how long have you left it after the arrow appears? I know you have left the cd check for some considerable time, but what about the boot process? Normally the arrow appears as X is starting, then the desktop builds itself. It can take a little while. The mythbuntu desktop is basically black with only a couple of icons showing, and a menu bar along the top.

Theres an outside chance that your monitor is putting the icons and menubar off the top of the screen. Does anything happen of you right click the mouse?

Anyway, if the bloody alternate cd works, go with that!! Its nice to know why something isn't working, but I am all out of ideas and its even nicer to find an "alternate" way to make it work!

---

### Post by Ronno6 on 2008-07-25
I have left the pointer screen sit for an hour or so as well. As there is no disk or HDD activity I have to believe that there is nothing going on.
I had considered the possibility that there was information that was off the screen, but when I move the pointer around to the edges, it is always visible when it hits the edge (except at the bottom, it  is only barely visible. 
I never get to the screen that says "Home entertainment just got entertaining again." 

When I attempt the 'install' option, I get the 'X'. when I attempt the live option, I get the arrow. 

Once I get my video card I will proceed with an alternate installation if the full version still does not work. My nature makes it difficult to just walk away from anything that is supposed to work for anyone, but does not work for me, without understanding WHY? 
I did try burning a CD and installing on the same machine as it was burned, with the same result as other attempts.
Thanks again for your continued support.

---

### Post by SiHa on 2008-07-25
I'll add my experience to the pot.

I've burnt both Hardy & Mythbuntu (AMD64 Desktop version) to CD and installed on the **Same** machine with no problems apart from the first disk which was bad.

Now

I get the new system destined to be the Mythbox in the loft. Using a different CD drive (still a CDR/RW one though). I could not get the either of the above to install no matter what I did. Slowing down the burn, interestingly produces worse results, and the CD wouldn't even verify after the burn. I reckon it was some incompatibility btw the two drives.

The solution (for me) was to install from a USB key. I installed to a 1GB flashdrive following the Manual Approach here: 

[[COLOR="Blue"]Install from USB Stick[/COLOR]]("https://help.ubuntu.com/community/Installation/FromUSBStick#head-a45f469b0b7ec2750cdedce449b76003c391416d")

Although, the LiveUSB creator option wasn't there before - might be worth a punt?

Ubuntu installs in ~5mins off a USB2 flashdrive - I'm never going back to CD again! 

Important, if you do this, you might need to edit /etc/fstab as described at the end of the article.
Also - the bit about editing syslinux.cfg - for Hardy, the bit about editing out instances of /casper/ and /install/ should be ignored. 

HTH

Simon

---

### Post by Ronno6 on 2008-07-25
Thanks for sharing your experience and the suggestion. That looks interesting. I am not extremely computer savvy, however. Nearly all of my experience is in Windows. I am learning as I go along about Linux,Ubuntu, and Mythbuntu .  Most of what I have learned is that I don't know enough to use these tools.

Maybe I need to take a correspondence course.............

---

### Post by SiHa on 2008-07-30
Go on - get stuck in. I'd never touched Linux until two months ago, it's fun to learn!
If you have any command-line experience from DOS / UNIX, it's quite easy to pick up.

---

### Post by Ronno6 on 2008-08-02
Well, installing video card and tuner didn't help. as a last resort I installed a new CD/DVD DL RW drive. A Lightscribe SATA unit. Boom. Mythbuntu loads right up! After all that. I don't know whether the old Sony Optiarc itself was the problem, or the IDE CD vs. SATA HDD was the issue. At any rate, it loads the live environment just fine. Now, I have to learn how to configure Mythbuntu front/back ends. Time to hit the posts and manual! 

Thanks to all for your input.

---

