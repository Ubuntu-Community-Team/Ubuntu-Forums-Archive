---
title: "A decent music player for Linux?"
date: 2010-01-21
forum: Multimedia Software
---

### Post by Dweomer on 2010-01-21
I've tried RhythmBox, Audacious, Amarok, BlueMindo, and I've had to fire each one for one failing or another. I'm downloading Banshee right now. I guess I'm going more or less in Alphabetical order in the software center, here, but I'm getting a bit worn out looking for a decent program. I want, without the need for additional plugin headaches: A search feature, a way to easily add entire folders of music, a way to consolidate those folders of music by artist and album (such as could be done in iTunes), and also possibly the ability to upload/download from my mp3 player -- though from what I've seen this doesn't seem to be possible in Linux. :<

The first two listed needs are must-haves. Banshee has finished installing and it looks good so far, but if you think there's something else I should look at please let me know.

---

### Post by boombox1387 on 2010-01-21
You'll probably get bunches of responses, but I just want to say that Banshee seems like a pretty good option for you.  I went through the same thing a couple years ago (I tried Rhythmbox, Amarok, Exaile, Listen, Songbird...) and I finally stuck with Banshee.  I really haven't regretted it; it's relatively snappy and the development is faster than most other projects I use.

Search: yes
Importing folders: Media > Import (Drag and Drop is broken atm, unfortunately)
Library organization: Edit > Preferences > check the options under 'File Policies'
mp3 player: most should work without any hassle.  If you have an iPod and you're using Ubuntu 9.10 you'll have a little more trouble.  If you have a new iPod or iPhone you pretty much out of luck for the time being.

Hope you enjoy Banshee, feel free to ask about anything if you have questions.

---

### Post by michael37 on 2010-01-21
My favorite for this type of job is Quodlibet.  Good combination with ExFalso, the best mp3 tag editor.

---

### Post by Dweomer on 2010-01-22
> **boombox1387 said:**
> You'll probably get bunches of responses, but I just want to say that Banshee seems like a pretty good option for you.  I went through the same thing a couple years ago (I tried Rhythmbox, Amarok, Exaile, Listen, Songbird...) and I finally stuck with Banshee.  I really haven't regretted it; it's relatively snappy and the development is faster than most other projects I use.

Search: yes
Importing folders: Media > Import (Drag and Drop is broken atm, unfortunately)
Library organization: Edit > Preferences > check the options under 'File Policies'
mp3 player: most should work without any hassle.  If you have an iPod and you're using Ubuntu 9.10 you'll have a little more trouble.  If you have a new iPod or iPhone you pretty much out of luck for the time being.

Hope you enjoy Banshee, feel free to ask about anything if you have questions.

I'm liking Banshee so far. It's a little slow to start up, compared to other things, but that doesn't bother me in the slightest. Oh no, an additional half second. If that's the worst I can think of, I'm in pretty good shape. I've marked this as solved, but if anyone wants to plug their favorite player, I'll check it out too. Going to look at Quodlibet now.

P.S. My mp3 player is an older SanDisk Sansa that has lived 4x longer than my iPod ever did, even if the cheap plastic bits cracked and broke the screen in the first month. Anyway, Linux hasn't been willing to recognize the thing so far.

---

### Post by Uncle Spellbinder on 2010-01-22
[Guayadeque Music Player](http://ubuntuforums.org/showthread.php?t=1380811)

---

### Post by Dweomer on 2010-01-22
Banshee was working well for me. I guess I wasn't working well for it. It quit the job and wouldn't start again after reboot. I'm not liking Guayadeque as much. I can't right click a song and delete it, or add a single specific file/directory. And the controls are weak; I figured it out but getting a single track to repeat is overly complicated. Gonna try to get Banshee working again. No idea what happened to it, though.

---

### Post by grndplane on 2010-01-22
This is pretty far down the alphabet, but you might want to try Songbird.

---

### Post by Dayofswords on 2010-01-22
songbird is cool

[http://en.wikipedia.org/wiki/Songbird_%28software%29](http://en.wikipedia.org/wiki/Songbird_%28software%29)

---

### Post by boombox1387 on 2010-01-22
Songbird is pretty cool, but it's also a bit bloated, the interface is almost an exact copy of iTunes (now in dark purple! ew!), and device support is pretty weak on Linux. [edit: This has been my experience, if this isn't your experience, or if my info is out of date, you have my apologies.  Everyone should use the media player that's right for him or her.  I don't want to start any flame wars.]

@Dweomer, if you open up a terminal and type 'banshee --debug' (without quotes), and press enter it will try to run Banshee from a terminal with debugging information.  This will hopefully help you figure out what's going wrong.

If you post the output here, I'll do my very best to help you.

---

### Post by Blue_Wolf on 2010-01-22
[QUOTE=Dweomer;8703747]I've tried RhythmBox, Audacious, Amarok, BlueMindo, and I've had to fire each one for one failing or another. I'm downloading Banshee right now. I guess I'm going more or less in Alphabetical order in the software center, here, but I'm getting a bit worn out looking for a decent program. I want, without the need for additional plugin headaches: A search feature, a way to easily add entire folders of music, a way to consolidate those folders of music by artist and album (such as could be done in iTunes), and also possibly the ability to upload/download from my mp3 player -- though from what I've seen this doesn't seem to be possible in Linux. :<

---

### Post by Dweomer on 2010-01-22
> boombox

```
Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with InQueue

```

That's all the output I get.

---

### Post by boombox1387 on 2010-01-22
> **Dweomer said:**
> ```
Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with InQueue

```

That's all the output I get.

I can't remember exactly, but I think that the InQueue message means that Banshee *should* be running, but it isn't quite.  You might want to open up System > Administration > System Monitor.  Look through the list under the 'Processes' tab and 'End Process' for anything that says either 'banshee' or 'banshee-1'.  Why Banshee didn't quite start right is a mystery, but hopefully it won't happen again.

If no 'banshee' processes are running, or if you can't start Banshee even after ending the process, we'll have some more investigation to do.

---

### Post by Dweomer on 2010-01-22
> **boombox1387 said:**
> I can't remember exactly, but I think that the InQueue message means that Banshee *should* be running, but it isn't quite.  You might want to open up System > Administration > System Monitor.  Look through the list under the 'Processes' tab and 'End Process' for anything that says either 'banshee' or 'banshee-1'.  Why Banshee didn't quite start right is a mystery, but hopefully it won't happen again.

If no 'banshee' processes are running, or if you can't start Banshee even after ending the process, we'll have some more investigation to do.

Yup, that did it. [IMG]http://www.modacity.net/forums/styles/smilies/extra/mysterysolved.gif[/IMG]

---

### Post by boombox1387 on 2010-01-22
> **Dweomer said:**
> Yup, that did it. [IMG]http://www.modacity.net/forums/styles/smilies/extra/mysterysolved.gif[/IMG]

Glad to hear it.  I'm not really sure what caused the problem, but hopefully it doesn't happen again.

---

### Post by michael37 on 2010-01-22
Still surprised you didn't look at QuodLibet.  

> A search feature
got it, on the first page, by name or by tag.
> a way to easily add entire folders of music
got it, first item in the menu
> a way to consolidate those folders of music by artist and album 
best tag reader and manager.  sort by title, artist, album, etc.

---

### Post by Dweomer on 2010-01-30
> **michael37 said:**
> Still surprised you didn't look at QuodLibet.  


got it, on the first page, by name or by tag.

got it, first item in the menu

best tag reader and manager.  sort by title, artist, album, etc.

I did try Quod Libet. In fact, I have tried every single audio player in the software center (though not all of the 'multimedia' players) now. I have exhausted the list now and there is none that I like. Banshee was okay with some serious issues (I think it loads the whole song to memory so if memory is strained it hesitates and skips and cracks, but I'm not sure that was why it was doing it) until I selected delete from drive on a song I didn't like, the song switched after I had already selected it but not yet confirmed, and when I confirmed it deleted the new song. I've fired a half dozen for not having a repeat one feature, others for not allowing me to play from my library or requiring playlists for certain basic features. Some players never even started up in the first place (Ahem, potamus.)

Any other suggestions? Ones I've tried and found lacking:

RhythmBox
Amarok
Audacious2
Banshee
Listen Audio Player
Quod Libet
Sonata
Muine Music Player
BlueMindo
Quark Music Player
Potamus
And even a couple non software center ones...


I'm... I'm just out of things to try. I must not understand what goes into making a music player, because I don't know why it's so hard for me to find a competent program.

---

### Post by Uncle Spellbinder on 2010-01-30
[Guayadeque Music Player](https://sourceforge.net/projects/guayadeque/)

---

### Post by Dweomer on 2010-01-30
> **Uncle Spellbinder said:**
> [Guayadeque Music Player](https://sourceforge.net/projects/guayadeque/)

Did that one, I swear. Actually it's still on here because I couldn't figure out how to uninstall it. :redface:

This whole thread is about getting suggestions for music players. If it was suggested here, I tried it, and didn't like it. Sorry! :S

---

### Post by kherring7383@yahoo.com on 2010-01-30
After switching to Ubuntu several months ago, I too tried every music player but each lacked a real graphic equalizer. About two month ago I stumbled upon aTunes which I've  been using ever since. Not only does it have a great equalizer with presets, but it also works with my Creative Muvo 100 MP3 player as well. Give it a try and see if this is what you're looking for

---

### Post by kherring7383@yahoo.com on 2010-01-30
After switching to Ubuntu several months ago, I too tried every music player but each lacked a real graphic equalizer. About two month ago I stumbled upon aTunes which I've  been using ever since. Not only does it have a great equalizer with presets, but it also works with my Creative Muvo 100 MP3 player as well. Give it a try and see if this is what you're looking for.

[http://www.atunes.org/?page_id=6](http://www.atunes.org/?page_id=6)

---

### Post by SuperSonic4 on 2010-01-30
I don't see exaile on that list. Essentially it's a GTK amarok but is more stable

---

### Post by Dweomer on 2010-01-30
> **SuperSonic4 said:**
> I don't see exaile on that list. Essentially it's a GTK amarok but is more stable

Yeah, I saw several players that said they were based on either Amarok or Audacity and I thought if I hated what they were based on I'd hate them too. I'm trying Aqualung right now, then I'll try aTunes and then Exaile. I can't seem to import folders with Aqualung, and we'll see if I get the skipping/scratching thing on it; that'd be the deal breaker. Hearing clicks and scratches in my music scrambles my brain.

EDIT: And no search feature, either.... Looking into aTunes in 3, 2... Q_Q

---

### Post by nothingspecial on 2010-01-30
You don`t seem to be someone who is easily pleased with free software.

That`s fine by me by the way. :D

The way unix software used to be developed was - do one thing and do it well -(or something like that hence the lack of quotes).

mpd plays music and plays it well, there are various frontends but gui wise I like sonata.

gtkpod manages your ipod and manages it well

easytag tags your music files and tags them well......

.....do you see where I`m going here?

---

### Post by kelvin spratt on 2010-01-30
Try Atunes you won't get any better

---

### Post by Dweomer on 2010-01-30
> **kelvin spratt said:**
> Try Atunes you won't get any better

Hope that's not true, because I just finished installing it and there's no search feature, no repeat one feature, and those are both deal breakers. I say 'no thank you' to creating a single track playlist for repeat one. It's almost a matter of principle at this point.


> Nothingspecial

What's the one that 'lets me play my damned music and does that well' called? Can someone explain to me how any audio player can exist without the most basic of controls? How do these people not include a repeat one feature? The search feature I can see occasionally being incompetently forgotten, but I can't comprehend how so many players lack the basic function of repeating a single track. Y_Y

Not easily pleased? Nono, I'm very easily pleased. I don't need an equalizer, or 7.1 sound, or gapless playing, or lyrics and cover art, or fast jumping with thousands of tracks. Nope. All I need... Is... A damned player that will let me upload my music, play it however I want without jumping through any hoops, with the most basic of controls and a search bar. You know how easily pleased I am? I can get by on Windows Media Player. Yeah, that's right. *WINDOWS MEDIA PLAYER*. I thought that was the worst player ever, until I used these.

Edit: I think I'll just download iTunes and run it in Wine. Seems ridiculous to do, but I'm just worn out and pissed off. I'll probably have to copy my music to /.wine/cdrive/programfiles/itunes too, which will be a hassle, but it's not like this hasn't been an enormous string of hassles already... Oh well, hopefully it'll work out without complication.

---

### Post by nothingspecial on 2010-01-30
>  All I need... Is... A damned player that will let me upload my music, play it however I want without jumping through any hoops, with the most basic of controls and a search bar. 



Did you try mpd yet? ;)

Never tried windows media player, is it any good?

---

### Post by nothingspecial on 2010-01-30
> What's the one that 'lets me play my damned music and does that well' called?

> **nothingspecial said:**
> 

[SIZE="4"][COLOR="Red"]mpd[/COLOR][/SIZE] plays music and plays it well, 

;)

---

### Post by Dweomer on 2010-01-30
> **nothingspecial said:**
> Did you try mpd yet? ;)

Never tried windows media player, is it any good?

No, it's horrible. Just like all Microsoft products. But I may be crawling back to Windows now. We'll see. I thank you for all your suggestions and if I stick with Ubuntu I will probably end up trying (and hating) them. :P

---

### Post by nothingspecial on 2010-01-30
Well good luck, whatever you do. Last time I tried windows I couldn`t ge iTunes to work, so I know how you feel.

---

### Post by snapback77 on 2010-02-24
Potamus gives the best quality audio sound (that is if you can it up)
Anyone interested in high quality musical sound?

---

