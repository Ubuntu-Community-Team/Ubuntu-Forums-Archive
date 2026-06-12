---
title: "True Sync of iPod"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by tommertron on 2007-08-02
Hi,

I know there's a lot of posts about 'syncing' an iPod out there, but everything I've seen so far, from Amarok to Rhythmbox seems to just let you 'transfer' music to your iPod. 

This is great, but what I want is something similar to iTunes, where I can say 'sync my whole library to the iPod.' So when I plug my iPod in, it will automatically add all the stuff I've recently added to the iPod. Because I'm not always going to remember what I've recently added, but I'd like to be on the iPod when I need it. Even if I had to press a 'sync' button I wouldn't mind. 

This is the last thing that I rely on Windows for, otherwise I'd be all Ubuntu all the time!

thanks,
Tom

---

### Post by wolfen69 on 2007-08-02
gtkpod is available in synaptic.

---

### Post by matthias_k on 2007-08-02
Those programs all suck (Rhythmbox and GtkPod). Don't know about amaroK, don't think it'll integrate nicely with Gnome. Rhythmbox constantly breaks my iPod DB or leaves it in an inconsistent state and GtkPod likes to drown you in warning and error messages just because a .txt was hanging around in one of your folders.

I just tried Floola, and it's great (comes closest to iTunes in terms of usabilit) , but asks for donations on every exit... annoying. I'm looking forward to Songbird though (Mozilla's answer to the media player question - let's hope it'll put it to a final rest). Both are rather fresh and alpha and therefore not in Ubuntu's repositories though.

Banshee seems to be pretty cool, too, but after syncing with iTunes 7, it couldn't read the iPod database anymore. Seems its iPod support is rather outdated.

At the end of the day, all Linux solutions suck in one way or another. But yeah, it's free software so what the heck. :-)

---

### Post by Incense on 2007-08-02
Banshee has a patch for the iTunes 7 db issue. Banshee is the only one that has really been able to handle my music well. Amarok does Podcasts better though. I have only gotten Video' to load through Floola, but I don't like watching video on the small screen, so I don't worry about it. 

As far as just syncing your music library, I would say Banshee. It's not iTunes, but it works.

---

### Post by comrade_chimp on 2007-08-06
I have exactly the same issue. The _single_ thing holding me back from deleting my Windows partition at home is the lack of an iPod/music library manager that can sync the library to my iPod, (including two-way sync of playcounts & ratings), without screwing up the indexing on the iPod.

Amarok supposedly can do so but in my experience it ignores playcounts and ratings (even when the checkbox in the device options is checked) and screws up the alphabetising of artists on the iPod (any band called "The..." goes under "T"). It also doesn't have a convenient "entire library" sync option - just individual playlists.

Banshee, AFAIK doesn't currently support playcount & rating sync (although 0.13.0 was released yesterday so I'll have a look into that shortly) it also messes up the alphabetising in the same way as Amarok.

---

### Post by comrade_chimp on 2007-08-08
> **comrade_chimp said:**
> Amarok supposedly can do so but in my experience it ignores playcounts and ratings (even when the checkbox in the device options is checked) and screws up the alphabetising of artists on the iPod (any band called "The..." goes under "T"). It also doesn't have a convenient "entire library" sync option - just individual playlists.

I've just noticed Amarok has also hosed all my play counts - a couple of experiments with syncing my iPod with Amarok and all the play counts on my iPod have multiplied by four! Annoyingly I didn't notice before syncing the thing back with iTunes on my Win partition.

---

### Post by LogicalDash on 2007-08-18
In Amarok:

[LIST]
[*]click on Playlists (in the sidebar)
[*]expand Smart Playlists
[*]expand Collection
[*]right-click All Collection
[*]choose Synchronize to Media Device
[*]click on Media Device (in sidebar)
[*]click Transfer (at the top)
[*]wait for it to transfer
[*]Done!
[/LIST]

Long and clunky, but functional.

---

### Post by coolen on 2007-08-19
I just tried Floola. It has its pros and cons. Personally, I'd like the option to browse to new files/directories to be added.
Main advantage I saw was automatic file conversion (both video and audio), but the lack of options and the fact that it didn't detect my iPod version correctly (with no way I could see to change the setting) turned me off of it.
Personally, gtkpod is the perfect program for me, assuming I can get it to convert video properly. All of my music is well organised, in a central location, and it won't go around deleting tracks because they're no longer on my computer.

---

### Post by comrade_chimp on 2007-08-23
> **LogicalDash said:**
> In Amarok:

[LIST]
[*]click on Playlists (in the sidebar)
[*]expand Smart Playlists
[*]expand Collection
[*]right-click All Collection
[*]choose Synchronize to Media Device
[*]click on Media Device (in sidebar)
[*]click Transfer (at the top)
[*]wait for it to transfer
[*]Done!
[/LIST]

Long and clunky, but functional.

Then:
[LIST]
[*] disconnect iPod
[*] play a track
[*] reconnect iPod
[*] repeat above steps
[*] load a playlist containing the track in Amarok and note play count / last played have not changed
[/LIST]

I've tried this with a 3g and 5g iPod, made sure I've ticked the "Synchronize with Amarok statistics" option. It simply doesn't seem to work

---

### Post by tommertron on 2007-08-23
I hate to say it, but I'd almost rather just see Apple port iTunes to Ubuntu. 

These are the requirements I have for an iPod sync that iTunes captures perfectly:

- Can set 'sync' settings to sync entire library or selected playlists
- Transfers playcounts/stars from iPod to library and from library to iPod
- Transfers podcasts automatically
- Can set to sync unheard podcasts only, or last x number of podcasts
- Can set to sync videos automatically, or just selected video playlists

---

### Post by mpgarate on 2007-08-30
songbird is close to being good enough... but its still in high development and buggy for me

---

### Post by RDaneel623 on 2007-08-30
My problem is all of my music is sitting on my media server, not localy on my laptop with Fiesty. So far the only program that I've found that allows me to use a Samba share for my library is Rhythmbox. Unfortunataly Rhythmbox's iPod support doesn't work well for me. It sees my iPod, but it doesn't allow me to create new playlists. 

This is the only issue keeping me from moving all my machines to Ubuntu. I need a program that will allow me to use a Samba share for my library and also allows me to edit my iPod playlists (I don't really care about syncing, I'd rather do that manualy). 

Anyone have any ideas?

---

### Post by FNDII on 2007-09-18
I've been looking for a way to get my iPod playcount  to update to amarok to no avail like everyone else. 


Does anyone use an device thats not an ipod?
Do you think that like a Zune player would interface better.
Or even a new OS on the iPod like "podzilla".

Is it that all the media players besides  iTunes are not programed to recive playcounts from media devises.

Or is it that no media player can read the stored iPod play count data?

---

### Post by coolen on 2007-09-19
> **FNDII said:**
> I've been looking for a way to get my iPod playcount  to update to amarok to no avail like everyone else. 


Does anyone use an device thats not an ipod?
Do you think that like a Zune player would interface better.
Or even a new OS on the iPod like "podzilla".

Is it that all the media players besides  iTunes are not programed to recive playcounts from media devises.

Or is it that no media player can read the stored iPod play count data?

podzilla is the interface to iPodLinux, which is, as the name would suggest, an implementation of Linux for the iPod. I've heard good things about it, although official support for newer iPods is lacking.
I use Rockbox along with the original iPod firmware. I'm still new to it, but it's quite promising, and it can use either a databse (its own, not the iPod's, which means it'll have to update after you sync) or read directly from the filesystem. As an added bonus, it can read ogg!

As for the playcount, I guess this just isn't a huge priority. I see no reason why we couldn't read the playcount, it may just not be implemented yet. You could search for plugins, I guess, or if you're the practical type, try to implement this yourself. Alternatively, you could put in a feature request.

---

### Post by cowanh00 on 2007-09-19
The main thing I want to do with my iPod and can't find a program that does it out of the box, is putting the album covers onto my iPod automatically! I use Rhythmbox mainly but I also have gtkPod installed. None of these put album covers onto my iPod automatically. Rhythmbox pulls them from the internet and gtkPod allows me to manually add them but I have so much music that I'm not going to do it manually!

I noticed the new version of gtkPod will support automatic album covers but when I installed it, it needed something else compiled at the same time. It also broke iPod support on all of the other programs that access my iPod.

By the way a good video converter for the Video iPods is Thin Liquid Film.

I'll check out Floola and Songbird and see if these support automatic album covers.

---

### Post by coolen on 2007-09-19
gtkPod can be set to automatically add album art of a particular name (folder.ext, by default, but I believe this could be changed).
This seems a job for the ripper to me. Rhythmbox can pull album art from the Internet and rip CDs, but it doesn't seem to put them together.
Until then, I have a fairly limited CD collection (~70), so I sacrificed an afternoon and got it all sorted.
Oh, if Rhythmbox could look for album art, too, that'd be sweet...whenever I play Evermore's Dreams, I keep getting a Disney compilation of the same name come up. I'd be happy for it to jump online in the absence of any cover art, but I'd like it to look.

---

### Post by cowanh00 on 2007-09-24
Ok, so it turns out that Banshee does exactly what I want out of the box. I have album art on my iPod again!! :)

---

### Post by comrade_chimp on 2007-09-24
> **cowanh00 said:**
> Ok, so it turns out that Banshee does exactly what I want out of the box. I have album art on my iPod again!! :)

Yeah, Banshee's pretty nice. I've looked into the code a little to try to get play count & rating syncing to work but the architecture seems to isolate the library and the device from one another. I've never coded C# before, though & really need to devote some proper time to figuring out if I can get it to do what I want.

---

### Post by wild_oscar on 2007-10-11
I haven't been able to make Amarok sync as I want yet. I'll try the method posted here.


Unfortunately, I haven't seen any player so good as iTunes when it comes to ipod interaction.

Having a 30 GB iPod, I'm starting to have the problem of space. Itunes solved that by having a tick box next to the songs, which meant "send to the ipod/ don't send it to the ipod". Have you seen this feature in any of the Linux alternatives?

---

### Post by zesty on 2008-01-21
Just wondering if anyone has had any success syncing from the ipod.  I usually just listen to music on my ipod.  I have a ton of music from 'the good ole days' but a lot of it is crap so I rate as I go on the ipod.  Having a music manager that keeps those ratings is a must for me.

If anyone has experience transferring ratings to a linux app, please share.  

So far all i've found is this: [http://zanfishen.com/delights/itunesratings.html](http://zanfishen.com/delights/itunesratings.html)

---

