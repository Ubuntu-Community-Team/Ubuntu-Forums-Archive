---
title: "Video Help, Screen flickers"
date: 2009-10-22
forum: Multimedia Software
---

### Post by FireStorm102389 on 2009-10-22
ok, I have an [ATI Radeon HD 4870]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5034920&CatId=3669") graphics card in my computer with [M4A785-M]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5241602&CatId=3586") motherboard...I have all the drivers for the graphics card and what not, but it seems when i open any stand alone video player type of application (with the exception of the ones IN firefox, those work without problems) but the entire screen flickers...sometimes the flickering stops and sometimes it doesn't and it slows my comp WAYYY down and everything, i just built this and it works perfectly very fast with the exception of when i open media applications...How could i fix this, i am kinda a newbie, so step by step instructions and specifics would be very helpful, thank you VERY MUCH!!

Sorry, I mean any type of VIDEO MEDIA, Music types of media applications are fine, no problems at all, ONLY VIDEO

---

### Post by dustgrain on 2009-10-22
> **FireStorm102389 said:**
> ok, I have an [ATI Radeon HD 4870]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5034920&CatId=3669") graphics card in my computer with [M4A785-M]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5241602&CatId=3586") motherboard...I have all the drivers for the graphics card and what not, but it seems when i open any stand alone video player type of application (with the exception of the ones IN firefox, those work without problems) but the entire screen flickers...sometimes the flickering stops and sometimes it doesn't and it slows my comp WAYYY down and everything, i just built this and it works perfectly very fast with the exception of when i open media applications...How could i fix this, i am kinda a newbie, so step by step instructions and specifics would be very helpful, thank you VERY MUCH!!

Sorry, I mean any type of VIDEO MEDIA, Music types of media applications are fine, no problems at all, ONLY VIDEO

Do you have compiz-fusion enabled? if so either disable it or play around with the plugins in the CCSM thingy.
hope that helps (it solved it for me)

---

### Post by FireStorm102389 on 2009-10-22
There has to be a better way than disabling compiz :(

---

### Post by dustgrain on 2009-10-23
> **FireStorm102389 said:**
> There has to be a better way than disabling compiz :(

Yes. You don't have to disable compiz... but you have to enable one of the Compiz Configuration Settings Manager (CCSM) plugins (I forget the exact one, sry) so compiz won't contradict with the openGL (or something).
you might need to download the compiz plugins pack..

Good luck..

---

### Post by FireStorm102389 on 2009-10-23
ok, i installed the VLC player and that works without problems, its just the MPLAYER, HOWEVER, no matter which one i load up if I maximize it while its playing a video, my comp screen goes black and my comp shuts down...any1 know what could be causing this?

---

### Post by RedSingularity on 2009-10-23
Which VLC have you installed?  I had a similar problem with the default player that comes in the Medibuntu repositories.

---

### Post by FireStorm102389 on 2009-10-24
idk, i just went to the add/remove programs and the VLC player that shows up i downloaded...the one with the cone icon...HOWEVER, my screen still flickers randomly, idk whats wrong, this time it started flickering and slowing my computer way down when i just right click on the desktop and click change desktop background, does any1 know whats wrong with the graphics drivers that it causes this and how to fix it? its really getting annoying

---

### Post by RedSingularity on 2009-10-24
In a terminal type 

metacity --replace & exit

See if you have any improvements.  This is just temporary to see if compiz is the cause or not.

---

### Post by FireStorm102389 on 2009-10-24
well, when i did that my computer tried doin something but after a few seconds my screen went blank and my computer restarted...that can't be good...so what would that mean?

---

### Post by RedSingularity on 2009-10-24
Well that test just means that it is not compiz causing the problems because you enabled metacity and still had a shutdown.  Maybe a driver problem.  Uninstall the driver through synaptic and see if you can work freely.  Of course you wont have the nice effects but thats fine for now while this problem is being figured out.

---

### Post by RedSingularity on 2009-10-24
To uninstall from terminal:

In terminal type.....

```
sudo apt-get autoremove --purge xorg-driver-fglrx
```

Then reboot.

---

### Post by FireStorm102389 on 2009-10-24
ok, well, i just enable metacity in the compiz fusion settings and then it told me to enable fusion, so i went back to compiz and it did the screen flicker thing again...

---

### Post by FireStorm102389 on 2009-10-24
after i executed that code in the terminal my screen still flickered when i opened the movie stuff...

---

### Post by RedSingularity on 2009-10-24
Did you restart the comp?

---

### Post by FireStorm102389 on 2009-10-25
my comp crashed and I am just on the net with the live CD, i can't seem to install ubuntu either, keeps giving me errors, i even tried deleting the partitions and what not with the partition editor on ubuntu as well as a windows ME boot disk with deleting and formatting, but it doesn't seem to help, i reset the motherboard too, i think im just gonna have to use dban and start from scratch...was hoping i wouldn't have to, that's gonna take a bit of time...

---

### Post by RedSingularity on 2009-10-25
I had the exact same problem with an older computer trying to install.  I was getting all types of error messages.   It turns out i had a bad HDD.  I doubt that yours is bad though because its fairly new.  Or it could even be a bad Live CD.  Let us know if you can successful install another OS.  If this is the case you can try burning a new Ubuntu CD.  


PS:  When you are running off the live CD is there any screen flickering?

---

### Post by FireStorm102389 on 2009-10-25
i just got it up and running with the only ubuntu disc i have, but it turns out its a 32-bit ubuntu version, and im switching to a 64 bit, so im gonna overwrite this ubuntu on the hard drive...and i think i know what the problem was, ATI isn't supported really well thru ubuntu and i found  a site that helps to install them to use all their capabilities of HD and everything, so im going it try and give that a go, i hope it works, lol, tells me to change the lock file, and the xorg file and a couple other things from the manufacturer

---

### Post by RedSingularity on 2009-10-25
Sounds good.  If you remember to, come back and give us the results.

PS:  I had a Radeon 3000 series before i got the nvidia.  It worked perfectly for me.  Maybe since yours is much newer than mine was it still doesn't have great support.  And yea you are correct, ATI doesn't have such spectacular support for linux, though it is progressing.

---

### Post by FireStorm102389 on 2009-10-26
ok, i am running with the ubuntu 9.04 64bit edition, instead of the 32 bit edition i had, nodifference in the flickering, but i guess i should clarify a bit...its not so much flickering as lines flicker across the screen randomly when media like the mplayer is opened and stuff like that, and before i installed the drivers i had no problems with it, so it must be the drivers since compiz isn't even on here yet...i was looking [here]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide") for the solution, but it turns out that when i get to the part where i am supposed to edit the "/etc/X11/xorg.conf" i get a message in the terminal that says ```
david@david-desktop:~$ /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Permission denied
david@david-desktop:~$ 

```

so i can proceed no further, how can i go about finishing what i started on the guide?

---

### Post by RedSingularity on 2009-10-26
Oh no problem.  You need admin privileges to execute that command.  Use this........

sudo gedit /etc/X11/xorg.conf

Sudo gives you admin rights and gedit will give you an editor to edit the file very easily.

---

### Post by FireStorm102389 on 2009-10-26
ok, now when the [page]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide") tells me to add 
> Section "Device"
	Driver		"radeonhd"
EndSection
do they mean add it to the bottom or change the "fglxr" to "radeonhd" or replace
> Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
with the code provided above, here is my entire xorg config
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
```

---

### Post by RedSingularity on 2009-10-26
They mean replace fglrx with the radeonhd.


```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"radeonhd"
EndSection
```

---

### Post by FireStorm102389 on 2009-10-26
next question is, how do i do this?

> If you are using the x86_64 architecture (64 bit), be sure to install "ia32-libs" before proceeding!

Make sure universe and multiverse are enabled in your repository sources. 

---

### Post by RedSingularity on 2009-10-27
That is the 32 bit library for 64 bit systems.  To install just do...........

sudo apt-get install ia32-libs

---

### Post by FireStorm102389 on 2009-10-27
what about the second half, the universe and multiverse thing?...

and btw, I was reading ahead in case i might have any other questions and i found this:
> 
Which cards does ATI no longer support? The ATI Radeon 9500-9800, X300-X2100, Xpress. See the complete list here. If your card is on that list, you are restricted to the 9.3 driver - however since 9.3 driver doesn't support xorg-xserver 1.6, it will not work with Jaunty! This guide currently is for installing 9.7. !!!SO BE CAREFUL!!! 


My card isn't on the list, HOWEVER, it said the drivers wont work with jaunty,and i have 9.04 which i believe is the jaunty jackalope, so its basically telling me i can't install this? and u think it would work with the 9.10 released on the 29th?

---

### Post by RedSingularity on 2009-10-27
The multiverse thing can be found under System>admin>Software sources.  Just make sure all the check marks are there.  

As for your driver you dont need to worry about it.  The current driver release is 9.10 found [here](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English).  Should be no problems in jaunty for you.

---

### Post by FireStorm102389 on 2009-10-27
ok I'm going off my iPods wifi since I need to change that back to fglxr so my comp starts up in graphics mode... How I get that changed in a remotte login, the txt based one...

---

### Post by FireStorm102389 on 2009-10-27
Also lemme know wat TTY to b in...

---

### Post by RedSingularity on 2009-10-27
Ok so your computer is booting into a text based mode.  That means you will have to edit the file with a text based editor such as VI.  

In the text mode do.........

sudo vi /etc/X11/xorg.conf

The VI editor has keys on the keyboard to move the cursor, delete, space, etc....  Look [here](http://www.cs.rit.edu/~cslab/vi.html) for those commands.  Its easy once you look at the command page.  Once you have got the editor open change it to fglrx and save and exit.

---

### Post by FireStorm102389 on 2009-10-28
> ok, i got home from work and turned my comp on, and now it doesn't register my hard drive...its a SATA 610, and i plugged it in a different sata port on the mother board and it still doesn't register, what can i do?



above was the before affect, i got to go into the partition editor on a Live CD and deleted the old version of ubuntu, but no matter what i do, now it doesn't allow me to create an ext3 or ext4 file system to install ubuntu into...this is irritating me...

---

### Post by RedSingularity on 2009-10-28
You don't need to delete the old partition.  When you inert the live cd and install, it will give you an option to "install to whole disk".  This will overwrite your old ubuntu install and set up a fresh new one.

---

### Post by FireStorm102389 on 2009-10-28
ino, but it doesn't let me install it because every time it gets to that part with the ext3 or ext4 it gives me an error that there is no filesystem there, the partition needs formatting, or it can't read the filesystem i have no idea whats going on, and my windows boot discs aren't working either, so its not like i can use them to try and format the hard drive to then use the ubuntu CD to install ubuntu witch is what i normally do...

---

### Post by teward on 2009-10-28
> **FireStorm102389 said:**
> above was the before affect, i got to go into the partition editor on a Live CD and deleted the old version of ubuntu, but no matter what i do, now it doesn't allow me to create an ext3 or ext4 file system to install ubuntu into...this is irritating me...

perhaps because your hard drive's partition table's been messed with by installing Ubuntu multiple times, it killed/damaged your drive.  Saw this happen twice when someone decided to go and nuke his partition table and everything on the drive when something didn't work the way he wanted it to (caused even more problems, all which I fixed [and not for cheap either]).

---

### Post by FireStorm102389 on 2009-10-28
its happened to me before and ive gotten it fixed, i don't remember how i did it tho, but if you take everything off the hard drive it should put it back to start, using dban, then i would need to reset the bios/cmos only problem is, is i don't have a floppy drive to save any logs that dban can detect so it wont run :/

---

### Post by teward on 2009-10-28
> **FireStorm102389 said:**
> its happened to me before and ive gotten it fixed, i don't remember how i did it tho, but if you take everything off the hard drive it should put it back to start, using dban, then i would need to reset the bios/cmos only problem is, is i don't have a floppy drive to save any logs that dban can detect so it wont run :/

if I had the drive, I could redo the partition table with gparted, reformat it to a msdos partition table, then it would be a clean drive.  Then the only thing is to install the operating system, which could be Ubuntu, Windows, etc.

---

### Post by FireStorm102389 on 2009-10-28
thats what i usually do but my boot discs for windows ME arent comin up :( but ill try gparted thnx, but in gparted, im assuming i have to delete evrything and then format the hard drive all to Fat32? then ill try and restart and see what happens :/

---

### Post by RedSingularity on 2009-10-28
You haven't tried gparted yet?  I thought thats what you were trying.  Go ahead and try it out with a live cd.  If it is not installed by default......

sudo apt-get install gparted

---

### Post by FireStorm102389 on 2009-10-29
Well, I tried the gparted first off the live cd, but it doesn't seem to be working for helping the hard drive, idk what is ring with this thing... Too bad the video driver sucked cuz everything was just fine felt that and now idk wats went wrong cuz I can't get it to install the filesystem without some sort of error, so right now I'm trying to install windows xp hoping to get it up and running so I can run Linux on a VM and see if I can get the graphics to work prpoerly that way before I go ahead and do it myself on a regular install so I don't mess this comp up again :(

---

### Post by FireStorm102389 on 2009-10-29
Ok I ran out of ideas... It won't let me install windows either, I've tried using gparted and switching to msdos but it just doesn't seem to work, whether it's creating the filesystem in ubuntu, it has errors and while copying files to the comp for windows it fails to copy files, idk what is wrong or what to do, any ideas would be extremely helpful! How could ubuntu mess up my comp so bad?

---

### Post by RedSingularity on 2009-10-29
Ok so you booted from the live cd, chose the partition editor, formated, and had error come up?  Have any idea what the errors said?  And what files system did you format to?

---

### Post by FireStorm102389 on 2009-10-30
Well, nomater what I format it to, it has an error basically saying the. Filesystem is not recognize or has errors, it doesn't explain any further, and windows just has roblems randomly throughout the installation as far as copying files... Sometimes it copies more files and sometimes it's barely started and has problems, but it never finishes... I just spent 650 on this comp and I've only reinstalled ubuntu twice, idk what's wrong...

---

### Post by FireStorm102389 on 2009-10-30
In gparted, ihave an ntfs file system cuz I'm tying to Install windows first and it says error like missing cluster in $bitmap whatever that means

---

### Post by FireStorm102389 on 2009-10-30
Well in windows recovery console I did a format and chkdsk along with fixboot and fixmbr, and. With the chkdsk it tells me that the volume appears to contain one or more unrecogerable problems...

---

### Post by RedSingularity on 2009-10-30
I had the same problem you are describing with one of my older drives.   It would sound as if you have a bad Hard Disk.  That may also explain the problems you had earlier as well.

---

### Post by FireStorm102389 on 2009-11-01
What is meant when they say a harddrive is bad, cuz this thing is brand new, can I use it as a slave?

---

### Post by RedSingularity on 2009-11-01
Well there are many things inside it that can fail.  It is not your fault but if you email the HDD manufacturer i am sure they will send you a new one to replace the broken one.  If what you are explaining about the drive is correct then something is broken and needs to be replaced.

---

### Post by FireStorm102389 on 2009-11-03
But I can put a swap file on it with no problems

---

### Post by RedSingularity on 2009-11-03
A swap file is not really a file system.  Its just memory the computer can use if RAM runs low.

---

### Post by FireStorm102389 on 2009-11-04
ok, but now i have a new hard drive in my computer, brand new, nothing wrong with it, and it is causing the same problems my other one was having, so its not the hard drive, idk what is wrong...what else is there, i reset the BIOS/CMOS, and i got the new hard drive, this doesn't make any sense at all...

---

### Post by RedSingularity on 2009-11-04
Alright how about burning a new CD.  Have you tried that yet?  CD files may be corrupt.  If windows cd wont work either then it could be the optical lense on your CD drive.  Sound like it may not be reading the cds correctly.  If u have a spare cd drive put it in.

---

### Post by FireStorm102389 on 2009-11-05
ok, well, i forgot i had the new hard drive in, so whatever, it worked :D i am going to try and plug in the other hard drive and see if that was also the case, as far as the CDROM...both my ROM drives are pretty new aswell, maybe a few months old, but if that is the case that my CD/DVD Writer drive's lense is dirty or something, how can i clean it?

P.S~ ur a genius, lol, idk y i didn't think about using the other drive...

---

### Post by FireStorm102389 on 2009-11-05
P.S.~ idk who all reads all these things, but i think its in everyone's best interests to install a Virtual Machine with the exact system they have and make any large changes to that before applying them to ur actual machine, i wish i did that to begin with, lol...would have saved me lots of time!

---

### Post by RedSingularity on 2009-11-05
Glad you got it working! :)  What did you do?  Burn a new CD or put a new optical drive in??

---

### Post by FireStorm102389 on 2009-11-06
well, the new hard drive is in, but to be honest, i think it was my CD rom drive...i tried installing it on the new hard drive and what not and it was causing the same problems the other hard drive was having, but i switched which CD ROM drive my comp booted a system disk on startup  from, and it must have just been that my cdrom drive wasn't reading the CD right, cuz my other cdrom just started installing and its on now...guess thats what i shoulda done in the first place, but its a life lesson :D

---

### Post by FireStorm102389 on 2009-11-14
Ok, here's something new, i tried to make install windows on the new hard drive cuz i was going to install windows then ubuntu, and it seems that when i use the windows xp disk it makes this problem, i didn't have any problems before, idk what is going on...i think windows xp is messing up my hard drive, cuz what happened to that 610 hard drive i was talking about earlier also happened to this one, and i noticed it doesn't happen untill i go to use the xp disk...any thought would be much appreciated

---

### Post by RedSingularity on 2009-11-14
Did you format the Hard disk with the windows disk?  Can you boot the windows disk?

---

### Post by FireStorm102389 on 2009-11-15
yea, i boot up the windows xp disk and it goews thru the installation and then something goes wrong cuz it restarts then always gives me a blue screen of death with a stop error...

---

### Post by RedSingularity on 2009-11-15
Well it could be the windows CD then.  Too bad you cant download a new one for free like ubuntu :(

---

