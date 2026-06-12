---
title: "Does Banshee watch folders for new/deleted media files?"
date: 2008-05-27
forum: Multimedia Software
---

### Post by sicofante on 2008-05-27
By "watch folders" I mean if it does automatically update my music library based on what's in the folders containing the actual music files. I'm hoping for it to automatically add new titles when I move new files to specific folders, or delete from the library those titles from files removed from specific folders.

If Banshee doesn't do that currently, are there any plans about it?

Are there other media organizers that do automate this task?

(I've searched Banshee's mailing list with no luck, but maybe "watch folders" is not the way they call it. English is not my native language.)

---

### Post by edd07 on 2008-06-06
Hello.I found your thread while googling the same question you're asking. I don't know whether Banshee can do it, but Rythmbox can. Go into Edit>Preferences>Music and check 'Watch my library for new files'. I hope this helps.

And if someone knows how to get Banshee to watch folders, I would appreciate your help.

---

### Post by isaacj87 on 2008-06-06
> **sicofante said:**
> By "watch folders" I mean if it does automatically update my music library based on what's in the folders containing the actual music files. I'm hoping for it to automatically add new titles when I move new files to specific folders, or delete from the library those titles from files removed from specific folders.

If Banshee doesn't do that currently, are there any plans about it?

Are there other media organizers that do automate this task?

(I've searched Banshee's mailing list with no luck, but maybe "watch folders" is not the way they call it. English is not my native language.)

No. At least it doesn't do it for me (Banshee 0.13.2). It definitely doesn't update the "collection" the same way Amarok does. It may be implemented into the Banshee-1 series, but the current RC doesn't do it if I remember correctly.

---

### Post by edd07 on 2008-06-06
> **isaacj87 said:**
> No. At least it doesn't do it for me (Banshee 0.13.2). It definitely doesn't update the "collection" the same way Amarok does. It may be implemented into the Banshee-1 series, but the current RC doesn't do it if I remember correctly.
Oh, too bad. That's a feature I really need. Well, I'll try Banshee again when/if that gets implemented.

Thank you.

---

### Post by isaacj87 on 2008-06-06
> **edd07 said:**
> Oh, too bad. That's a feature I really need. Well, I'll try Banshee again when/if that gets implemented.

Thank you.

Ah! I found some good news. And it's apparently targeted for the 1.x series...I asked about it on the Banshee #IRC channel. Have a look :)

[http://bugzilla.gnome.org/show_bug.cgi?id=421376]("http://bugzilla.gnome.org/show_bug.cgi?id=421376")

---

### Post by sicofante on 2008-06-07
It's great Rythmbox supports this already and it's great news Banshee has it planned for its final release.

I'm happy. :)

---

### Post by priegog on 2008-12-02
If anyone still cares, Banshee 1.4 now does exactly this. Well, at least sometimes it seems to. Either way, now you have a menu option "rescan collection".

edit: Oops, forgot to mention. To have the latest banshee version (including this one) add the banshee ppa repo [https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive)

---

### Post by madverb on 2008-12-06
It's weird that so many people say to use banshee when it doesn't have the watch folder option. It's the most useful feature available to me.
I will definitely stick with Rhythmbox... I had changed to Banshee the other day and now that I have realised it doesn't watch folders it is bye bye Banshee.

---

### Post by KongKNoob on 2008-12-20
Madverb, I see what you mean, it sucks to manually add new music to Banshee all the time. But I have to say that in most other aspects Banshee is superior to Rhythmbox (perhaps with the exception of cover management and music sharing). In my opinion Rhythmbox lacks a lot of features that, after using Banshee, seems essential.

When 1.4 hits the repos...

---

### Post by sicofante on 2008-12-22
> **KongKNoob said:**
> Rhythmbox lacks a lot of features that, after using Banshee, seems essential.
Which features is Rythmbox lacking that Banshee provides?

---

### Post by Joe_Bishop on 2009-01-31
> Which features is Rythmbox lacking that Banshee provides?

Really? It provides nothing significant I think. I've tried 1.3, and it looks bloated and really needs some more attention to its user interface and logic, there were many inconsistencies such as dividing album into group of albums with one track in each - banshee devs tried to explain this is not banshee fault, but track metadata - all other players suppose it's one album with many tracks.

---

### Post by whaevr on 2009-01-31
I have tried the old Banshee and didn't really like it that much. Although just recently I installed Banshee 1.4.2 and I love it. I got rid of Rhythmbox and exaile after I installed it.

It even recognizes video files on my ipod and sets them aside in a video category just like iTunes, nothing has ever done that before.

Ipod managing part looks like iTunes also (good thing I think)
[[IMG]http://img297.imageshack.us/img297/8282/screenshothe5.th.jpg[/IMG]](http://img297.imageshack.us/my.php?image=screenshothe5.jpg)

Yes I named my iPod eyePod..so what

:D

---

### Post by `GooZ´ on 2009-02-17
> **priegog said:**
> If anyone still cares, Banshee 1.4 now does exactly this. Well, at least sometimes it seems to. Either way, now you have a menu option "rescan collection".

edit: Oops, forgot to mention. To have the latest banshee version (including this one) add the banshee ppa repo [https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive)

Thanks! :)

---

### Post by amdlintuxos on 2009-02-22
if i am not mistaking new media files autoddetection will be part of V1.6 features

---

### Post by SourPatch on 2010-01-08
I'm using 1.6 Beta 2 in Karmic and it does not have the autoscan feature. A similar feature that is quite useful is to update the library when file metadata changes. Rhythmbox will do that for you.

---

### Post by drewsus on 2010-11-14
FYI Banshee does have this feature (extension)... it just doesn't seem to work. 
You can easily manually rescan your library. Not that hard, but not automatic and its a deal breaker for me. 
However, I do love how it scans beats per minute (bpm) and will make auto playlists based on the bpms of songs. Pretty rad.

ps- Im using the daily build PPA so I have 1.9, but this has been the same for a number of versions now.

---

### Post by lolobu on 2010-11-21
It seems that this feature works if you add some new music files while banshee is running. If you add the files when banshee is not running, it won't see the changes when restarted. You'll have to rescan the library.

---

