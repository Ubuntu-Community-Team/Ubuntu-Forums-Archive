---
title: "Rhythmbox not writing playlist to iPod"
date: 2010-02-28
forum: Multimedia Software
---

### Post by zachthejones on 2010-02-28
I love how Rhythmbox connects quickly and easily to my iPod, and how Rhythmbox does a pretty solid job of keeping track of changes to my library, though it is large. But I cannot seem to create playlists on the iPod through Rhythmbox. When I create them, I can see them in Rhythmbox, but when I unplug the iPod and try to play them, they don't show up. I plug the iPod back in, and Rhythmbox acts like they're there - I can even play the Playlist from the iPod in Rhythmbox.

Is there something I need to do to "write" the Playlist to the iPod from Rhythmbox? It is so irritating to have to create an "on the go" playlist on the iPod and then fire up Rhythmbox and rename it what i want it to be...

or is this a common bug?

---

### Post by bkadoctaj on 2010-03-17
> **zachthejones said:**
> I love how Rhythmbox connects quickly and easily to my iPod, and how Rhythmbox does a pretty solid job of keeping track of changes to my library, though it is large. But I cannot seem to create playlists on the iPod through Rhythmbox. When I create them, I can see them in Rhythmbox, but when I unplug the iPod and try to play them, they don't show up. I plug the iPod back in, and Rhythmbox acts like they're there - I can even play the Playlist from the iPod in Rhythmbox.

Is there something I need to do to "write" the Playlist to the iPod from Rhythmbox? It is so irritating to have to create an "on the go" playlist on the iPod and then fire up Rhythmbox and rename it what i want it to be...

or is this a common bug?

Wow man, I have to admit that's a pretty good technique for dealing with the issue, even though it's far from desirable.  What interests me most is that you've got the On-The-Go playlist functionality working on your iPod.  Do you mind if I ask which model of iPod you have and whether it was formatted in Mac OS X or Windows?  I haven't tried syncing my iPod with the newest release of Banshee yet, but Banshee is pretty good since it has autosync.  Unfortunately, I just was not able to get my On-The-Go function working when using Banshee to sync.  Thus I am back at square one, only booting into Mac OS X to sync my iPod (Classic 80 GB).

---

### Post by zachthejones on 2010-03-17
What I have is actually the 5.5 Generation. It works great, but gtkpod can't work with it because it doesn't recognize the model...

I originally formatted the iPod on a Windows machine (so Ubuntu can write to it). I enjoyed using the Banshee synch function for awhile, but it has gotten buggy on me lately and keeps getting stuck (and doesn't upload/update the iPod). At present I'm actually trying to manage it through iTunes (off a dual-boot setup), but that is increasingly frustrating because my laptop is older and iTunes really, really creeps along on it - and iTunes doesn't seem to want to manage ALL my library, just portions of it....grr....

As far as the "On the Go" function I haven't tried it since I got Banshee working with it, but it worked fine before that. I"m wondering if your problem might be more related to having formatted it in OS X - that causes the iPod to use a file format that Linux can read but can't write to...at least in my experience.

I, personally, am about to reformat the 'ole iPod again and see if Banshee will work now for me...i actually liked managing my iPod through it.

---

### Post by sarel29 on 2010-03-30
Hi,

I've just got a 5th Generation nano and I'm going crazy trying to put music onto it.  I get the same problem as described above, with Rhythmbox saying it's put the music on, but my ipod not recognising any of it.  I also tried with amarok and banshee and has the same problem.  Does anyone know how I can fix this without resorting to installing the dreaded windows on my computer?

Thanks!

---

### Post by mikecanada on 2010-03-31
Yeah it is a problem,I use Ubuntu 10.4 first with Rhythmbox then gtkpod the programs would see the Nano XC027 but the songs were not detected by the ipod.Disk use would show the files are there but I had to download Itunes on a Windows machine then hit Restore to repair it.Gktpod will now upload to the ipod,some more work needed yet.

---

### Post by bkadoctaj on 2010-04-11
It was Windows-formatted, actually.  But yeah, I use Pana (form of Amarok 1.4) now and it's great.  I highly recommend it.

---

### Post by amadis2009 on 2010-06-21
Unfortunately, saving playlists is not at this time possible in Rhythmbox. There are some other possibilities:

Amarok is supposed to work well, but is also supposed to be heavy and I haven't used so can't give any feedback. 

Banshee is supposed to do this but I had major problems with my 2nd Gen Nano. Had to find a hack that involved killall -9 nautilus and also choosing to never automount any devices thru the gconf-editor and then manually mounting (big headache) just to get Banshee to recognize the ipod. Then after all that, it wouldn't save playlists either.

There are other programs that I've heard of but not tried, like Songbird, Rockbox, etc. I couldn't find definite answers as to whether they saved playlists to the ipod. (Spent hours online trying to figure this out and admit I got kinda tired of researching this stuff.)

In the end I got gtkpod. Installed it and then configured it by adding the repository in the repository/ipod options and make sure it was looking for the name I gave my ipod. Then everything was a go. I changed the playlist command to rhythmbox (under edit>preferences>commands. Just pasted rhythmbox over xmms) cause the default xmms doesn't work. Now I use the two programs in conjunction. 

I know, you're thinking *why use two programs?* Well, I'm really sold on the new Ubuntu One music store which so far only works in Rhythmbox and Banshee(with a plug-in). So that's why I didn't bother trying Amarok. It's pretty easy with Rhythmbox and gtkpod actually and I can drag-n-drop files from one application to the other. 

Hope this helps others.

---

### Post by zachthejones on 2010-06-21
I actually had Banshee working pretty well for me on my fifth gen iPod. But with different updates it would break its ability to correctly copy music and write playlists, and then an update or two later it would be working again - alternately wonderful and frustrating. I've ended up using iTunes for the time being (as I keep a Windows 7 dual boot for specific programs and hardware that need it). 

Gtkpod had trouble with my specific iPod (which might actually be a 5.5 gen, I'm not completely sure...). It really was my hope that would work great - but alas, no such luck. I figure I'm going to use iTunes for awhile until I get tired of it again and then I'll see where gtkpod/banshee/rhythmbox are in iPod compatibility at that point.

---

### Post by newatts on 2010-06-23
I regret to say that I am unable to transfer anything to my Ipod.  Its an older one (8gb) and I have tried using rythmbox. gtkpod, amarok. all to no avail.  

the ipod is in fat32 format.  

files are a variety of extensions, wav, acc....

all to no success.  

any suggestions?

---

### Post by MikeInPdx on 2010-08-04
Hello, I'm new here, but I found a technique somewhere online (wish I remembered where???) that has been working to get playlists onto my ipod in Rhythmbox. 
 
I create the playlists, and then I quit Rhythmbox altogether. Then I right click on my ipod on the desktop, and choose "Safely Remove Drive/Device"
 
Once the ipod updates, I have the playlists I created. Haven't tried it with my Classic, but it works like a charm on my Nano 4th generation.
 
Hope this helps,
Mike

---

### Post by Seagarz on 2010-08-06
MikeInPdx,

That worked perfectly...funny how i was able to make a playlist awhile back and didn't realize what i did to have it work....then couldn't get it to create playlists again bc i forgot what i did.  Looks like ejecting the drive before rythmbox is shut down (Quit) does not keep the playlist.

Thanks for Posting !! Fixed my issue...80gig classic...:p

---

### Post by Kreme191 on 2010-08-06
Hi,

I have an ipod as well and have done a good deal of looking into this topic. I have heard of this same error before but I don't know how to fix it. However, a general consensus of what I've read says to use amarok. I tried amarok out and I really like it. It's really easy to keep your music files organized as well. I haven't yet tried it with my ipod but from what I've heard from other people it works great with ipods. Hope this is helpful.

Peace

---

### Post by joserpena on 2010-09-03
> **MikeInPdx said:**
> Hello, I'm new here, but I found a technique somewhere online (wish I remembered where???) that has been working to get playlists onto my ipod in Rhythmbox. 
 
I create the playlists, and then I quit Rhythmbox altogether. Then I right click on my ipod on the desktop, and choose "Safely Remove Drive/Device"
 
Once the ipod updates, I have the playlists I created. Haven't tried it with my Classic, but it works like a charm on my Nano 4th generation.
 
Hope this helps,
Mike

It works with Classic 160! Thanks, Mike.

---

### Post by Andrew Golightly on 2010-09-28
thanks Mike. Worked for me too.

---

### Post by pasaporte73 on 2010-12-09
I don't know if this has been fixed for you guys. If not, I'll tell you how I do it.

The way it works for me it's to rename after the playlist has files in it. I don't know if it'll make a different to you but it works for me now in my ipod touch, no need to unmounting, I'm using ubuntu 10.04.

What I do is, plug my ipod touch and click on start up with Rythmbox. Once the ipod is shown, I transfer files from pc to ipod, and keep an eye on ipod, it shows synchronizing, now and then. After that I create a new playlist, and I do not rename, just, drag the new files to new playlist, after files are shown in new playlist, synchronizing is shown again, after like 15 seconds or so, it's not immediate. After that I can see new playlist on ipod with music. Then I rename to whatever name on Rhythmbox and wait for another 15 seconds again and synchronizing is shown again. Go back to the ipod and there it is. To me it's fixed now.

I hope it works for some as it has for me.

---

### Post by dimeotane on 2010-12-22
This worked for me

> What I do is, plug my ipod touch and click on start up with Rythmbox. Once the ipod is shown, I transfer files from pc to ipod, and keep an eye on ipod, it shows synchronizing, now and then. After that I create a new playlist, and I do not rename, just, drag the new files to new playlist, after files are shown in new playlist, synchronizing is shown again, after like 15 seconds or so, it's not immediate. After that I can see new playlist on ipod with music. Then I rename to whatever name on Rhythmbox and wait for another 15 seconds again and synchronizing is shown again. Go back to the ipod and there it is.

The first time I tried using Ubuntu installed on a macbook.  The mac froze and the ipod was corrupted. It showed no music was on it, but it was. I had to install itunes 9 on virtualbox windows XP to sync.  I chose to not erase and it began to sync.  Afterwards the missing music was there. 

For my second try I used the instructions above on Ubuntu on a different PC it worked.

---

### Post by japhyr on 2011-01-17
I was finally able to create a new playlist on my 5th generation ipod classic through Rhythmbox.  This is what worked for me:
[LIST=1]
[*]Connect ipod, with Rhythmbox off
[*]Say yes to open Rhythmbox
[*]Right click on the ipod within Rhythmbox, and select New Playlist
[*]Add songs from the ipod library to the new ipod playlist
[*]Quit Rhythmbox
[*]Right-click the ipod on the desktop and click "Safely Remove"
[/LIST]
However, this only creates the playlist on the ipod.  Is there a way to copy that playlist to Rhythmbox, or better yet to create the playlist in Rhythmbox and then copy that to the ipod?

---

### Post by bowhat on 2013-01-26
Try the script provided here with rhythmbox:
[http://ubuntuforums.org/showthread.php?p=12475542](http://ubuntuforums.org/showthread.php?p=12475542)

It prompts you for all your rhythmbox playlists and lets you pick which ones to sync. Moves the files over. Creates a playlist on the device as well. It is a sync not a copy -- so other music files on your device on the Music folder get removed.

Could not be any easier. After many hours of searching that did the trick for me. Wish it was publicised more so that I did not have to waste that much time.

You can ignore managing your device in rhythmbox and just sync the playlists you want from the main rhythmbox section

---

### Post by oldos2er on 2013-01-26
Old thread closed.

---

