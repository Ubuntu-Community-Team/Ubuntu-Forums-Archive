---
title: "Can't get songs from Rhythmbox to iPod - 10.10 Maverick Meercat"
date: 2010-10-19
forum: Multimedia Software
---

### Post by MorrisseyJ on 2010-10-19
Having updated to 10.10 I am having a problem getting songs from Rhythmbox to my iPod. 

When i plug in the iPod it mounts fine and opens in Rhythmbox. I then transfer the songs that i just pulled off amazon/ubuntu one onto the iPod by drag and drop. In Rhythmbox, the songs appear to be on the iPod and i can even play them off the ipod while it is mounted to Rhythmbox - i.e. when i am browsing the music selection on the ipod through rythmbox the songs will play, which makes me think they are on the ipod. 

The problem is that when i try and play a song off the ipod, through speakers or headphones, then nothing plays. The song simply sits silent on the ipod. The track timer doesn't move and the tracks count up at around 4 second intervals. 

This simple drag and drop approach worked in 10.04. 

I see that there are some problems syncing ipods in 10.10. The most relevant appears to be a bug reported here: [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/654105](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/654105)

This bug however appears to be about taking songs off an ipod, not putting them on. That said i think the problem might be related (about copying appropriate extensions). The issue is that the ipod organises music in such a bizarre fashion that i can't find the songs to check the extension that has come off Rhytmbox. I don't want to duplicate the bug if its the same or related. 

Any ideas on how i might fix this or what i might do about the checking if the bug is the same would be appreciated.

Thanks.

---

### Post by dandescendant on 2010-10-19
Same problem here.

---

### Post by MorrisseyJ on 2010-10-20
So i have found one of the songs that is on my iPod but which won't play through it. 

In the file system on the iPod it knows that the file is an mp3 and if i double click it, it will open and play it in movie player.

I have no idea why the iPod won't read these new songs. 

@ dandescendant this doesn't seem like a widely experienced problem. I doubt its a hardware thing but mind if i ask you what you are using. I am on a Asus A6Rp Entertainment notebook and i can't seem to find the model of my ipod.

---

### Post by ryanferreri on 2010-10-20
I have the same problem. 10.10 x64 running on desktop machine with Asus Motherboard

---

### Post by lucasnogueira on 2010-10-23
I can't play songs uploaded using Rhythmbox on my iPod Touch 3g, like everyone. 
However, I uploaded some songs using Banshee Media Player and I can listen to them :P

---

### Post by mabo1 on 2010-10-23
I am having the same problem with my ipod and ubuntu 10.10.

I have just completed a clean install straight from the disk and it is still not working.

I even upgraded my ipod software to the latest version with no success.

I have noticed the new files added to my ipod don't have a file extension, so I renamed the file adding the 'mp3' extension, but this doesn't work either.

Does anyone know if its possible to install an older version of Rhythmbox?

---

### Post by rouge_sheep on 2010-10-24
Same problem. Songs transfer but won't play.

> **mabo1 said:**
> I have noticed the new files added to my ipod don't have a file extension, so I renamed the file adding the 'mp3' extension, but this doesn't work either.

I noticed the same thing, and when I right click on my ipod and say sync I get the error message "None of the tracks to be transferred are in a format supported by the target device, and no encoders are available for the supported formats."

This is with an ipod nano 4g that worked in lucid
10.10 x64 upgrade
asus p5ne-sli mobo

@lucasnogueira I might give Banshee a try, as I will rather miss my music

---

### Post by ianstump on 2010-10-24
Hellomy fellas, to do so you need to install the proper codecs...
Just do:
[HTML]sudo apt-get install gstreamer0.10-plugins*
[/HTML]
This surely works (tried it)
Cheers! :guitar:

---

### Post by DriftingSamurai7 on 2010-10-26
Ive been having the same issue with my 6th gen 80gb classic in 10.10 using Rhythmbox. I'll give it a shot after i install the plugins as advised and post some results.

Results: worked. totally worked. ive been trying to get this stuff to work since 10.10 came out. Thanks ianstump

---

### Post by MorrisseyJ on 2010-10-26
Worked for me too. 

Thanks very much ianstump.

I'll mark this as solved, if anyone is still having problems i think it'd be best to start a new thread and ref this one.

---

### Post by VTphilipv on 2010-10-26
A big 'ata boy' goes to ianstump!

---

### Post by mokodev on 2010-10-26
I had the same problem , and installing the gstream packages didn't work for me. This was not only a Rhythmbox problem, because it did not work in banshee either. But after i installed gtkpod everything worked again...

---

### Post by Sam Lars on 2010-10-26
Installing all of the plugins is a good solution, but is not optimal...

```
65 newly installed, 0 to remove and 0 not upgraded.
Need to get 37.7MB of archives.
After this operation, 144MB of additional disk space will be used.
```

I'd rather just install the one I need.
I was getting the same error as another person in the thread:

```
"None of the tracks to be transferred are in a format supported by the target device, and no encoders are available for the supported formats."
```

The **gstreamer0.10-plugins-ugly** did it for me.

---

### Post by andresv on 2010-10-27
Thanks! Also worked for me... :)

---

### Post by cphayes0914 on 2010-10-28
I tried your method with the gstreamer installs, nothing.   Now my rhythmbox will detect my ipod but wont show any songs, which are on there.   Banshee doesnt even detect my ipod, however exaile will read my ipod, cant write.  when i first installed 10.10, rhythmbox would at least read my ipod, now it wont even do that.  argh

---

### Post by cerda on 2010-10-31
Same problem here. Just updated to 10.10 and now my rhythmbox detects my iPod (nano 2gb) but won't show any of it's songs or let me transfer any song to it. Really annoying bug.

---

### Post by ryon.sherman on 2010-11-02
> **ianstump said:**
> 
```
 sudo apt-get install gstreamer0.10-plugins*
```

This worked for me as well. iPod Nano 5G on 10.10. Anyone able to narrow down which package is specifically required? I tried **gstreamer0.10-plugins-ugly** only but was still a no go.

I know for sure **gstreamer0.10-plugins-*****-**[**dbg,doc**] are not required.

---

### Post by b4ss00k4 on 2010-11-08
**gstreamer0.10-plugins-ugly-multiverse** is the correct plugin. Works in my case (10.10 64bit, iPod Touch 2g). Of course you must have enabled the multiverse-repository

---

### Post by Haziqonfire on 2010-11-15
Mine also doesn't work, even after I run the terminal command. I'm using a 3G iPod Nano.

---

### Post by MorrisseyJ on 2010-11-15
Have you enabled the multiverse repository?

Failing that it looks like there might be a problem with the ipod nano as this i what people seem unable to get working.

I am not sure how to fix this, perhaps try the people at rhythmbox.

---

### Post by jamesthorne on 2010-11-15
> **MorrisseyJ said:**
> Failing that it looks like there might be a problem with the ipod nano as this i what people seem unable to get working.

Glad I stumbled on this.  The gstreamer plugins trick worked for me on a fresh install of Maverick.  I have an ipod nano 5g so not all nanos are having problems.

---

### Post by ar3s on 2010-11-29
Installing the gstreamer plugins with 

```
sudo apt-get install gstreamer0.10-plugins*
```

Worked for me, however it seems a bit of problem when simply by updating to 10.10 it breaks iPod support in Rhythmbox (and probably others) 

Surely this should be a addressed, unless it's only isolated users? And if so why only a few?

---

### Post by conzfc on 2011-03-27
i was having this same problem, the solution was quite simple.  the ipod was last formatted/restored on a mac, so it was using the hfs+ file system and none of the linux pod management software was able to deal with permissions in this without all sort of hassle; basically, i could read from but not write to the pod. 

i used a windows install of itunes to "restore" the pod - which erases the content and formats the internal drive - and now all of the linux ipod management software is able to both write and read to it.  i'm currently rebuilding the pod using rhythmbox music player in ubuntu 10.10, works fine now that the pod drive is formatted to fat32.

hope this helps!  --josh (buffalo creek, co)

---

### Post by Max Williams on 2013-01-03
I was having a *different* problem - i couldn't transfer the files from Rhythmbox to my Ipod in the first place.  Ianstump's solution worked for me too.

---

### Post by howefield on 2013-01-03
Old thread closed.

---

