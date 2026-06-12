---
title: "Mythstream again 9.04"
date: 2009-09-18
forum: Mythbuntu
---

### Post by rickyble on 2009-09-18
So I finally just gave up on fixing mythstream and all the problems with my upgrade to 8 and went with an clean install to 9.04 and saving all my recordings and music and then adding the storage back to the system.  After a couple of small problems most of the things seem to be back except you guessed it,,,.....mythstream's shoutcast.  I of course did the download of shoutcast2.tar.gz and did the replacement.  Still no urls and nothing from the harvester.  Anybody any suggestions or help at all.  I really would appreciate it.  I am about to my frustration end.  Pretty much everything else I can figure out but for some reason not this.  I dont know if its a mental block or am I just stupid?  thanks

---

### Post by bsntech on 2009-09-18
Well, here is what I have.  Note that this was done on Ubuntu 8.10 and I upgraded to 9.04 after the fact.

[http://www.bsntech.com/content/view/591/281/]("http://www.bsntech.com/content/view/591/281/")

This is specific to my installation, but here are the steps I did (sounds similar to what you have):

Setup MythTV with MythStream with the ShoutCast Parser in Ubuntu Linux 8.10 Intrepid

Like I previously indicated, I use MythStream solely for the ShoutCast recordings.  Ensure you have MythStream installed:
sudo apt-get install mythstream

 Now you need to go to the creator's website and download the Shoutcast parser.  Untar the files to /home/<user>/.mythtv/mythstream/parsers

Open up MythTV, go to Media Library - Play Online Streams and you will have a "Browse Shoutcast genres" available.  All of the radio stations are available right there!

NOTE:  If you cannot hear any of the playback through SPDIF, it is because you need to update your /etc/mplayer/mplayer.conf file. 

Search for "ao" in the file and change the line to show as:
ao=alsa:device=spdif

---

### Post by rickyble on 2009-09-18
Thanks you may have hit on one of the problems.  The only place I see the mythstream directory or parser directory is in the usr\share\mythtv directory.  I dont have one in any of the home directories.  I take it should be there.  When was this suppose to be created?  what part of the installation?  BTW thanks big time

PS  I just use the shoutcast part myself.  I mostly have it playing first thing in the morning while I surf the news.

---

### Post by bsntech on 2009-09-18
I'm not sure when it was to be created.  I actually installed Ubuntu by itself and then set it all up with MythTV/MythVideo/MythStream (and just recently I'm going to try out Boxee as well).

But, I can't remember if I read that the shoutcast stuff needed to go into the ~/.mythtv/mythstream folder or if I just found that folder and put the stuff in there.

So, probably different install methods, but I installed mine using the:

sudo apt-get install mythtv mythstream mythvideo

It is possible that this way setup those folders.

But yeah - I don't think mythstream is all that useful IMO.  The only thing it is used for is the Shoutcast radio - and I'll see if Boxee incorporates that.  If it does and I like Boxee, out goes MythStream!

---

### Post by rickyble on 2009-09-18
If you like boxee post back and let me know.  I may try to install the mythstream using the apt-get install instead of the mythbuntu package.

---

### Post by tgm4883 on 2009-09-18
> **rickyble said:**
> If you like boxee post back and let me know.  I may try to install the mythstream using the apt-get install instead of the mythbuntu package.

News flash, same package.

:EDIT:

Also worth noting that mythstream won't be in Mythbuntu 9.10

---

### Post by rickyble on 2009-09-19
yea I know its the same I was just hoping maybe something that didnt get installed on the first try might on the second.

---

### Post by rickyble on 2009-09-21
Well I finally did get it to work on 9 but it was way more then just copy the new shoutcast2.tar.gz.  I had to edit several files in a step by step process.  Edit one see what changed then edit another and so on.  I gathered all the info from all over the web in many different places.  I guess its the point one of the other threads was trying to make(I give up THREAD) that this product is not for the faint of heart right out of the box types.  If you want it all to work you need to be a little of everything..programmer, hardware ace, and detective.  I had to drop the streams table in mythconverg, copy the shoutcast2 tar in two places and edit the stream res file, and edit the menu.pl file.  After that it finally worked again... until the next update/upgrade.  thanks for the suggestions and help.  I guess not many people use it in mythtv anymore but if you are interested let me know and Ill give you what I got to get it to work.

---

### Post by bsntech on 2009-09-21
Wow - so you had to dump all the stream data into the database?  The only thing I'm worried about with that is that Shoutcast sometimes chanages the stream numbers and stations won't work.  I listen to some DI.FM stations and it seems about once a month the stream numbers change.  I save them under the radio selection for easy access instead of going through all of the listings again, but then they quit working after a month or so.

In regards to getting Boxee to work - I think I either have too slow a computer or I have a problem with the video card I have.  When I open Boxee, it eats up 100% CPU and it is just a black screen - nothing happens even if I am patient and wait an hour.

I installed it on my laptop with nVidia stuff and it works just perfect.

My MythTV box has a SiS Xabre video card with TV-OUT, so I have both a monitor connected and a TV and have mirrored the displays so they are both the same.  That is the only thing I can figure - Boxee doesn't like the card.  But, there isn't anything out there on Boxee and compatibility with SiS video cards.

Boxee looks very nice - and it DOES include the Shoutcast radio lists.  I'll just have to wait on a computer upgrade to get it to work with the main MythTV computer.

---

### Post by rickyble on 2009-09-21
Yea it was a real hassle but I do use the streams on my frontends at each tv in the morning and then sometimes during the weekend ...so it was worth it.  I dont think I would have had to do that if it hadn't been a fresh install but it wasn't working anyway.   I tried the upgrade to 8 which is what started the whole thing anyway.  So I don't know how but crap had gotten into the database..apparently not uncommon.  I found it on the mythstream configuration page. I took a look at Boxee this week and a quick glance it looks ok.  I guess Ill just keep trying to fix mythbuntu for as long as I can use it.  I do use the rest of mythtv just nothing else with mythstream.

---

