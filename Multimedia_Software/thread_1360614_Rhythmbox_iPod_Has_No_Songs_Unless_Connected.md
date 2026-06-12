---
title: "Rhythmbox: iPod Has No Songs Unless Connected"
date: 2009-12-21
forum: Multimedia Software
---

### Post by kontagious on 2009-12-21
i edited songs on my ipod from rhythmbox and when i use the ipod it says no songs but when i connect it rhythmbox can still see them. any ideas?'

160GB iPod Classic w/ upto date firmware
Ubuntu 9.10
Rhythmbox 12.5

---

### Post by zenbox on 2009-12-21
I am experiencing the exact same problem.  I have not yet found a solution.

---

### Post by kontagious on 2009-12-24
I think it's because I have the newest generation iPod. I'm really hoping that's not the case, it should still work. 

Has anyone had this problem? I've been searching the internet and irc non-stop.

---

### Post by LuisGMarine on 2009-12-24
I used to have a similar problem and it all had to do with how I disconnected the iPod from the computer.  Try copying over your songs, then close down Rhythmbox.  After that right click on the iPod on your desktop and select Eject.  See if doing that shows your songs.

I know that whenever I tried to eject it through rhythmbox or hit "safely remove device" all sorts of problems started happening.  Hope this helps

---

### Post by kontagious on 2009-12-25
Thanks LuisGMarine, I tried doing that but it didn't help. It did make me try something new that did work though.

I **logged in as root and everything worked fine**.

Thanks for your help everyone.

---

### Post by LuisGMarine on 2009-12-25
Well that's still not good.  You should not have to log in or do anything as root unless your are installing software or doing something to change the configuration files to your system.  

I would check your fstab and check the permissions that are set to the ipods mount directory.  For example if your device is getting mounted to /mnt/ipod, ls -l would spit back the permissions.

---

### Post by phallusocracy on 2009-12-25
just chiming in to say i'm having the exact same problem with the same specifications. which is a bummer when you leave your computer up for an entire day syncing an ipod and it's empty. :P

edit: luis what command would i use to do that? sorry, i'm still very new to linux. :(

and i tried changing users to root to do this, but it denied me presumably for the wrong password? but i used the same one as for my profile. 

do i have to sudo it?

---

### Post by LuisGMarine on 2009-12-25
the command should be ls -l in the mount location.  I'm not sure off the top of my head where fstab is, but I'm guessing /etc/fstab.

I'm not on a ubuntu machine or near one, so I can say for sure, but I'm sure if you google it will come up.  I'll be able to help put more once I get my hands back on my computer in a week or so, away for the holidays =)

---

### Post by phallusocracy on 2009-12-26
not gonna lie. still kinda lost. i'll wait though! happy holidays!:)

---

### Post by phallusocracy on 2009-12-26
oops.

so logging in as root didn't work.

i've been looking at more stuff and downloaded some libgpod packages for karmic. i installed the deps like the instructions said ... but then i couldn't do the "./configure make" or "check install" ...

then when i tried to drag the songs onto my reformatted ipod it told me that they couldn't be moved as they were read-only.

i effed up big time, brahs. is this a permissions issue or did i screw something up badly?

---

### Post by cupoange on 2009-12-28
having a similar problem.  latest ipod classic 160GB, mounts fine, shows up in rhythmbox, and i can drag songs to it.  transfers all the music.  when the ipod is disconnected, it says "no songs" even though there is plenty of space being used.

searched and searched but can't find a solution.  don't want to use itunes!!!!!

---

### Post by phallusocracy on 2009-12-28
> **cupoange said:**
> having a similar problem.  latest ipod classic 160GB, mounts fine, shows up in rhythmbox, and i can drag songs to it.  transfers all the music.  when the ipod is disconnected, it says "no songs" even though there is plenty of space being used.

searched and searched but can't find a solution.  don't want to use itunes!!!!!

from what i've gathered we need to either hack the firmware of the device itself or install something to trick the ipod. some hash business or something. i'm relatively computer illiterate for a linux user. 

and don't bother with itunes. the 9.0 version we need won't install with WINE anyway.

---

### Post by cupoange on 2009-12-28
> **phallusocracy said:**
> from what i've gathered we need to either hack the firmware of the device itself or install something to trick the ipod. some hash business or something. i'm relatively computer illiterate for a linux user. 

and don't bother with itunes. the 9.0 version we need won't install with WINE anyway.

well my issue is that all my music is on my linux box, so it's much easier for me to sync there.  other option is to map the music drive on my windows box and use itunes, which sucks and would be slow.

i've tried songbird too and that doesn't even show up.

---

### Post by LuisGMarine on 2009-12-28
Songbird for me worked perfect until version 1.4.1 came out and then iPod support jumped off a cliff.  Right now I jacked my moms computer just so I can try out banshee again since it seems to be the "only" media player that can manage my iPod Video 5th Gen perfectly.  The only problem that I had was that there was no option to manage duplicates.

So this is going to sound a bit crazy, but I'm going to use Songbird to do the managing of my library.  As far as editing tag, organizing library, and also getting rid of duplicates and ghost files.  Then I'm going to use banshee just for uploading my songs to my iPod until songbird can get their act together.

Sounds crazy, but it's actually a bad-*** combo.  As for the post where songbird or any other media player other than rhythmbox can't detect your ipod on 9.10 follow the guide in my signature to give it a try.

---

### Post by cupoange on 2009-12-29
SUCCESS!

I think I got it to work through rhythmbox by simply doing the following:

install itunes 9 on a windows machine.  reset/format/etc the ipod.

transfer some mp3s from your collection to the ipod.  test it out.

using either gtkpod or rhythmbox, the ipod should now show up correctly and you should be able to transfer music.  disconnect ipod and check that the music is actually readable.

---

### Post by phallusocracy on 2009-12-29
ok so basically ... 

1. reformat the iPod on a windows machine
2. put some mp3s onto the iPod from the windows machine
3. then hook it up to my ubuntu computer and put more mp3s on
4. it'll work

eh?

---

### Post by cupoange on 2009-12-29
> **phallusocracy said:**
> ok so basically ... 

1. reformat the iPod on a windows machine
2. put some mp3s onto the iPod from the windows machine
3. then hook it up to my ubuntu computer and put more mp3s on
4. it'll work

eh?

try it and let me know if it works for you..

---

### Post by peaudecastor on 2009-12-29
> **cupoange said:**
> try it and let me know if it works for you..

Got me excited for a while but no luck.  As soon as I transfer song from Rythmbox,  the iPod starts to say no song again.

---

### Post by cupoange on 2009-12-29
> **peaudecastor said:**
> Got me excited for a while but no luck.  As soon as I transfer song from Rythmbox,  the iPod starts to say no song again.

can you try it again, this time with gtkpod?  not sure if there is any other thing you have to do but it worked for me....

for me it seemed like once the ipod was formated for windows and the music db was initialized with some songs, rhythmbox and gtkpod were able to transfer music just fine.  this is an 8th gen 160gb ipod classic on karmic running latest rhythmbox.

sucks...update if you get it to work

---

### Post by peaudecastor on 2009-12-29
> **cupoange said:**
> can you try it again, this time with gtkpod?  not sure if there is any other thing you have to do but it worked for me....

for me it seemed like once the ipod was formated for windows and the music db was initialized with some songs, rhythmbox and gtkpod were able to transfer music just fine.  this is an 8th gen 160gb ipod classic on karmic running latest rhythmbox.

sucks...update if you get it to work

Did you do any of the stuff explained earlier in the thread,  like the 'running as root' thing or "ejecting from nautilus" instead of Rythmbox?

---

### Post by cupoange on 2009-12-29
> **peaudecastor said:**
> Did you do any of the stuff explained earlier in the thread,  like the 'running as root' thing or "ejecting from nautilus" instead of Rythmbox?

when someone suggests running as root, i pretty much disregard it, so no.

as far as ejecting from nautilus, i believe i did try that now that i remember, but i don't remember the sequence.  anyways, that was only supposed to fix programs finding the ipod, which rhythmbox for me always showed it correctly.  but give it a try....maybe that's the key.

---

### Post by phallusocracy on 2009-12-31
eureka! i decided to clear out every music player i had. RB, exaile, gtkpod, etc.

so i then also uninstalled libgpod4 in synaptic. then i got the gtkpod package in synaptic. loaded that and it reinstalled gtkpod with it.

loaded up the iPod, dragged songs into it and it didn't work. did it again, this time remembering to hit "Save Changes" and, ta-da!, it worked!!

i only added a few albums song by song. and they all worked. so now i'm trying an en masse adding of the entire Music folder. hoping it still works (i've heard of people only being able to sync in small portions). but with over 5000 songs on 1000+ albums, i'll be damned if i'm going to be arsed to do that.

UPDATE: large syncs don't work. have to Add Files rather than Add Folders. also only works if it's only a few albums at a time for some reason. *shrugs*

whatever! it works!

---

### Post by cupoange on 2009-12-31
> **phallusocracy said:**
> eureka! i decided to clear out every music player i had. RB, exaile, gtkpod, etc.

so i then also uninstalled libgpod4 in synaptic. then i got the gtkpod package in synaptic. loaded that and it reinstalled gtkpod with it.

loaded up the iPod, dragged songs into it and it didn't work. did it again, this time remembering to hit "Save Changes" and, ta-da!, it worked!!

i only added a few albums song by song. and they all worked. so now i'm trying an en masse adding of the entire Music folder. hoping it still works (i've heard of people only being able to sync in small portions). but with over 5000 songs on 1000+ albums, i'll be damned if i'm going to be arsed to do that.

UPDATE: large syncs don't work. have to Add Files rather than Add Folders. also only works if it's only a few albums at a time for some reason. *shrugs*

whatever! it works!

interesting....did you try rhythmbox at all after you got it to work?  I was just going through drag + drop albums, had up to 2000 songs at one point and it all synced perfectly...

hey...at least it works!  awesome, no itunes needed

---

### Post by LuisGMarine on 2009-12-31
If you have bigger libraries I would give either Banshee or Songbird a try then.  It has one thing that rhythmbox lacks, library sync.  Easier for those of us with 30GB+ libraries that just want to have whatever we have on PC to be on our ipod. 

Never tried to just add my whole library at once though, so if that doesn't work maybe try doing smaller portions.

---

### Post by cupoange on 2009-12-31
> **LuisGMarine said:**
> If you have bigger libraries I would give either Banshee or Songbird a try then.  It has one thing that rhythmbox lacks, library sync.  Easier for those of us with 30GB+ libraries that just want to have whatever we have on PC to be on our ipod. 

Never tried to just add my whole library at once though, so if that doesn't work maybe try doing smaller portions.

i couldn't get songbird to work, though i like the interface.  i never liked the banshee interface, i much prefer rhythmbox.  I have something like 100+ gigs of music, but I really prefer not to sync the whole library because it is a lot of BS that I really don't listen to (or music that my wife listens to).  I prefer to just go through and drag+drop albums and playlists from rhythmbox.  a little more tedious than copying whole library, but then my ipod is cleaner :)

---

### Post by LuisGMarine on 2009-12-31
Lol then yeah that makes more sense =)

---

### Post by Acradon on 2010-01-02
Hi there and a happy New Year to you all, 

well I have encountered the same problem with my wife's new iPod (also a Classic 160GB). My old iPod works fine with Rhythmbox, but everytime I try to sync even a single song on my wife's ipod, all the music is gone. Or at leat the iPod can't access it. Rhythmbox still can. I found out that this has to do with a new security feature from Apple that prevents the use of 3rd Party software. Now apparently the best way is hacking the firmware of the iPod. I am no expert therefore I have no idea how to do it. Something with the 0x58 hash or so....Does somebody know anything more specific. I tred to find the tutorial mentioned here: [http://ipodminusitunes.blogspot.com/](http://ipodminusitunes.blogspot.com/)

but the link does not seem to work (website only shows search results for other sites)

I have all the music backed up on my computer and am willing to try the firmware change if somebody can tell me what to do in a relatively simple english. 

Greetz

Acradon

---

### Post by Acradon on 2010-01-02
okay a bit more research shows that this apparently is supposed to fix the problem:

[http://main.wtbw.co.uk/hash58.zip](http://main.wtbw.co.uk/hash58.zip)
[http://main.wtbw.co.uk/hash_linux.zip](http://main.wtbw.co.uk/hash_linux.zip)

But how am I supposed to apply these archives...or where to extract to?

Any suggestions?

---

### Post by kmdougla on 2010-01-03
@Phallusocracy:

I have the same iPod/Ubuntu version/everything and am experiencing the same issue as the initial poster. I tried your work around and it works for me as well, i.e. uninstall libgpod4 and all other music players, then install gtkpod and use that. The only difference was that I had transferred my library onto the iPod before I realized there was a problem, so all I had to do was open gtkpod and click save changes.

This method works for me, provided I do the trick that Luis suggested with killing and restarting Nautilus.

Is there a bug already open for this? Also, I'll try installing Banshee etc. to see if they work.

-kmd

---

### Post by kmdougla on 2010-01-03
Ok, following the gtkpod trick I installed Banshee and Rhythmbox. I deleted a song from my iPod and transferred it back onto the iPod in each of these programs. After ejecting the device, the iPod still recognizes that there are songs on it.

If it ever stops working, I'll post back with the details.

-kmd

---

### Post by LuisGMarine on 2010-01-04
I have mine syncing great with Banshee.  The only problem is that it tend to duplicate some songs on the iPod.  That's a bit irratating, when my library has like 15000 files, but my ipod has like 20000.  It's a pain in the but to try and track it down.

---

### Post by Chipmaster on 2010-01-05
I've had the same issue.  From what I can gather libgpod does support the ipod classic and *should* be able to determine the necessary information automatically from the ipod to perform the necessary checksum that the ipod requires to show the songs.  I assume this hasn't been happening in our cases and my suspicion (however unverified) is that the ubuntu build of libgpod was built without hal and libsgutils support which is necessary to find the "firewire id" automagically.

The folks at gtkpod have outlined how to find this information manually.  Check out the documentation here:

[http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/libgpod;a=blob_plain;f=NEWS;hb=07493e8](http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/libgpod;a=blob_plain;f=NEWS;hb=07493e8)

and here:

[http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/libgpod;a=blob_plain;f=README.SysInfo;hb=HEAD](http://gtkpod.git.sourceforge.net/git/gitweb.cgi?p=gtkpod/libgpod;a=blob_plain;f=README.SysInfo;hb=HEAD)

I won't be able to give it a shot until tonight, but it looks promising.

---

### Post by cebazoth on 2010-02-06
I've just bought a new 160GB ipod classic and had the same problem. The libgtkpod trick did not work for me. 

I looked at SysInfo in the ipod's iPod_Control/Device directory and it seemed to have picked up the firewire guid correctly. However, after a bit of head-scratching I noticed the guid was missing the initial 0x . i.e., the line should have read:
[FONT=Courier New]
FirewireGuid: 0x000B130123A888C4[/FONT]

but instead it read: 

FirewireGuid: 000B130123A888C4

I edited the 0x in and all now works fine for me.

Clare

---

