---
title: "Error when playing dvd - libdvdcss IS installed"
date: 2008-04-25
forum: Multimedia Software
---

### Post by mykrob on 2008-04-25
Hey-

did a fresh install of 8.04, Kubuntu. No matter what app i try to play a dvd in, i get the same response:

> 
The source can't be read.
Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (/dev/dvd)

all the libdvd's are installed (read, nav, play, css)

When i put a dvd in, i can browse the dvd and see all the files/folders on it with no trouble. I get this same message even if i try to directly play a .vob file. 

I cannot use Xine, player, or kaffeine.

Any ideas?

Thanks,
-myk

PS - libdvdcss came from debian-multimedia.  I tried the one from medibuntu as well, and from the multiverse repository, i get the same results regardless..

---

### Post by cor2y on 2008-04-25
you say you cannot use xine?
So that means you are using totem-gstreamer which doesn't do dvd menu/chapter navigation
Install the gstreamer plugins, all of them, because i am not to sure which ones are needed for dvd playback in addition with libdvdcss2.
Then try again.
The error you are getting i know occurs for totem-gstreamer in 7.10, gstreamer was broken in that but 8.04 works once the plugins are installed.

---

### Post by mykrob on 2008-04-25
I am using Kubuntu. I normally use Kaffeine to play my dvd's with xine as the backend. Worked fine in Gutsy, never used gstreamer before..

---

### Post by mc4man on 2008-04-25
Don't know or use Kubuntu or kaffeine but sometimes the cli output is informative. Maybe run kaffeine from konsole and post

---

### Post by marlin on 2008-04-26
I "upgraded" from Gutsy (everything worked) to Hardy and have the exact same situation with the exact same errors and results. Sorry I am no help but misery loves company. I have been searching for two days now trying to fix this but to no avail.

---

### Post by styphon on 2008-04-26
> **cor2y said:**
> you say you cannot use xine?
So that means you are using totem-gstreamer which doesn't do dvd menu/chapter navigation
Install the gstreamer plugins, all of them, because i am not to sure which ones are needed for dvd playback in addition with libdvdcss2.
Then try again.
The error you are getting i know occurs for totem-gstreamer in 7.10, gstreamer was broken in that but 8.04 works once the plugins are installed.

I was having the same problems. I'm running Ubuntu for the first time, installed from within XP. I tried this method (I'm using Xine) and at first I right-clicked on the icon on the desktop and told it to load using Xine. It came up with the same error. Then I clicked "DVD" on the Xine Panel and it worked fine.

Thanks for the tip.

---

### Post by gwpritch on 2008-04-26
I've been having the same problem in Ubuntu. I could browse the files on a dvd but it would not play even though I had libdvdcss2, libdvdnav etc installed. 
After much hair pulling I finally figured it out.
Under Add/Remove... install Ubuntu Restricted Extras package.
I'm up and running...good luck.

---

### Post by Nathan.Flow on 2008-04-28
I'm having the same problem... I wonder what was the method each of you used? is other media playing.. IE. flash, mpeg, wma, ect?  Hardy is apposed to install the appropriate codec when you try to play the media with kaffine.. 

I installed the codec with apt.. package name: kubuntu-restricted-extras or something similar? 

I had a problem when I installed the kubunturestrectedextras package then tried to play a media file with kaffine. kaffine would try to download and install something but would wind up not then error-ing out or wind up in an infinite loop.

Please post>>> what you did..  IE: Did you use kaffine to install the codec, or did you get the coedx another way??

I'm using 64bit kubuntu so please post what flavor your using and if it's 32 or 64..

lets try to figure this out..

---

### Post by Nathan.Flow on 2008-05-03
Good news. After some investigation, I believe I figured out my problem... The region on my dvd player was set to 0. this is a problem. after I set it to 1 ex: "any thing other than 0" my dvd player and Linux now plays dvd..  :-) If you set your dvd player to a region, you should be able to play dvd's as well normally dvd players are set to 0 and that is not a recognized region so the dvd player will error out or show cropped media

---

### Post by Nathan.Flow on 2008-05-05
looks like i spoke too soon, I'm still unable to play dvd's well they play just scrambled and distorted.

---

### Post by odin79 on 2008-05-05
Mykrob, that sounds like the problem I had. Check out this page: [http://ubuntuforums.org/showthread.php?t=767449&page=9](http://ubuntuforums.org/showthread.php?t=767449&page=9) . See if it cant help you.

---

### Post by mc4man on 2008-05-05
> looks like i spoke too soon, I'm still unable to play dvd's well they play just scrambled and distortedDouble check that you have libdvdcss2 installed. If you do/did and where trying to playback without the region code set you _may_ have corrupted keys in your .dvdcss folder, delete all the folders inside and retry
while you don't have to use it I'd install vlc - that way you know you have all the libs needed and running vlc from konsole can be informative for troubleshooting

edit; just installed kubuntu - kaffeine works fine as long as the device the dvd is in is linked from dev/dvd. If you only have 1 dvd drive and it's linked from /dev/dvd1 you get the error from 1st. post and need to either change kaffeine ? or create a link named dvd linked to dvd1 in /dev.
re edit in kaffeine settings->xine engine paramaters->media you can set dvd device in beginner and raw dvd device in expert, change both to /dev/dvd1 if applicable

---

### Post by hplehn on 2008-05-06
Sorry, I came to believe that there is no simple/trivial solution (as missing links in /dev or missing libdvdcss) here. 

After upgrade from mythbuntu gutsy to hardy on amd64 I can't reliably read dvds by any means. I even can't mount data dvds or data cds right now. But I *sometimes* can read media without having found a systematic way to reproduce/solve the error. Once deleting .dvdcss seemed to help, right now it doesn't help.

I already was convinced that it is an hardware issue before I found this (and some similar) threads.

---

### Post by hplehn on 2008-05-09
After some more tests with several drives and systems I am now quite sure that my problems were caused by a defect (but sometimes working) GSA-H66N :(

---

### Post by richardjones on 2008-05-20
When I upgraded from Gutsy to Hardy my /dev/dvd went away and I had to manually configure kaffeine (well, xine) to look directly at /dev/scd0 to make it work again

---

### Post by mc4man on 2008-05-21
> When I upgraded from Gutsy to Hardy my /dev/dvd went away
if you want to fix that post from /etc/udev/rules.d - the contents of 70-persistent-cd rules
and just to double ck. your setup run and post ```
sudo lshw -C disk
```

---

### Post by mykrob on 2008-05-21
i just dont get it.. Is there no real fix for this? I tried editing Kaffeine/Xine settings to use /dev/scd0 for the device, now instead of getting the normal error message, Kaffeine just crashes..

What's a guy got to do to play a dvd???

on a side note, heres the output of the command lshw -C disk: (or at least the portion pertaining to the dvd drive)

> 
  *-cdrom
       description: DVD writer
       product: DVD_RW ND-3550A
       vendor: _NEC
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.05
       serial: [_NEC    DVD_RW ND-3550A 1.0505093000
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom



thanks,
-myk

---

### Post by mykrob on 2008-05-21
just to confirm, i can duplicate the problem using the xine-ui. It just crashes too...

---

### Post by mykrob on 2008-05-21
strange, now it is working..... Not sure what i did..... Anyone have a clear cut guide for how this works??

---

### Post by Jvaldezjr on 2009-01-09
mc4man mentioned the fix...at least it worked for me.
> kaffeine works fine as long as the device the dvd is in is linked from dev/dvd...

Here's how I made Kaffeine work properly:
* I have libdvdcss from medibuntu installed.
* I'm running Kubuntu 8.04 Hardy -32 bit with 2.6.24-24 kernel (generic)

Open the XINE settings from Kaffeine
Settings -> Xine Engine Parameters
In the beginners tab, click on the media icon on the left, then look at the 6th entry, it should say dvd.device, and in the box have a path of your DVD device (default is /dev/dvd).  This is what my settings look like.

Open a konsole and type in the following:
```
ls -l /dev/dvd
```

My system had /dev/dvd linked to /dev/scd1, however on my system my DVD device was recognized as /dev/scd0 according to my fstab.  These two settings need to match in order for Kaffeine to work properly.  I changed the device link to match my FSTAB device, since I know that's my DVD drive I use for playing DVDs.  Here's how I fixed it.

```
rm /dev/dvd
ln -s /dev/scd0 /dev/dvd
```
scd0 is the device for your DVD player (yours may be sdd1, or scd1, etc, just refrence your fstab file to be sure).

Try playing DVDs again, and Kaffeine should work propery.

---

### Post by mikerobinson on 2009-05-29
> **mc4man said:**
> in kaffeine settings->xine engine paramaters->media you can set dvd device in beginner and raw dvd device in expert, change both to /dev/dvd1 if applicable

This worked for me except my DVD device is /dev/scd0. You can check that by running the "mount" command from the console.

---

