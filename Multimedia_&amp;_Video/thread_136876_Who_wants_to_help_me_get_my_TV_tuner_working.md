---
title: "Who wants to help me get my TV tuner working?"
date: 2006-02-26
forum: Multimedia &amp; Video
---

### Post by Donshyoku on 2006-02-26
I just recently bought a new TV tuner.  The Compro I had before it was really racked out, so I got a Leadtek WinTV2000 XP (RM version).  It works nice in WindowsXP, but I want to set up a more media-center-like setup instead of using their software.  

I installed Breezy and updated it on the system.  I immediately installed TVTime just to check the picture.  I just had a blue screen on each channel.  I scanned for channels and it went through to 99 and stopped with no channels found.  I then installed Zappign and again had no picture/channels.  

Finally, I checked the Device Manager and found my card.  It recognized it and set it up with the BT878 driver.  

That's as far as I got.  I have a card recognized and a driver arranged for it, but no video output.

I am going to push MythTV on it, but I really want to get a signal first.

Thanks in advance for any and all help!

---

### Post by Donshyoku on 2006-03-01
Bump! \\:D/

---

### Post by nvn on 2006-03-01
You can find a lot of information by searching the forum, as many users could have the same kind of problems. While setting up my own TV card, I found this post that helped a lot:

[http://www.ubuntuforums.org/showpost.php?p=695955&postcount=4](http://www.ubuntuforums.org/showpost.php?p=695955&postcount=4)

To find out your card and tuner number, go to this page:

[http://www.bttv-gallery.de/](http://www.bttv-gallery.de/)

Hope this helps
nvn

---

### Post by bumpusth on 2006-03-02
I have the same card I believe, NTSC version. Make sure card=34 tuner=2 is passed when loading the module, for ntsc tuner=2 otherwise look up the appropriate tuner. I'm not sure if autodetection will work.

Edit here: I read the message again and just realized you asked for the RM version, which according to what I've read uses a different tuner (TVision TVF-8533-B/DF). From bttv-gallery

tuner=58 - Ymec TVision TVF-8531MF/8831MF/8731MF
tuner=59 - Ymec TVision TVF-5533MF
tuner=65 - Ymec TVF66T5-B/DFF

Sorry about that. Not sure if the tuner on board is covered by one of those.

---

### Post by Donshyoku on 2006-04-07
Hey everyone, I am not giving this another go.  I finally have a weekend without too much work to do, and a few updates to Dapper are really helping me along (new ALSA supports my sound chip) and the new Diva video editor is something that I can really use (no more going to Windows to use my free Arcsoft video editor)!

Now, I've gone through what has been posted here again.  My tuner is autodetected as card=34 in the dmesg command.  It chose to be card=34 and tuner=5, but I am still getting no video.  Now, when I go into the Device Manager, my card is found with the correct name and company.  However, it has not chosen the bttv driver, but V4L instead.

Is this something I should change?  If not, can I direct tvtime (a good test app!) to bttv or another driver?

Thanks, again!  I really hope I can get it up and running this weekend!

---

### Post by Donshyoku on 2006-04-07
The BTTV website says that it is working under Linux with card=35 tuner=38...

The tvtime howto says:

```
unload bttv and tuner again, and try specifying the tuner type as well using "modprobe bttv card=X tuner=Y".
```

However, I cannot unload the driver.  using ```
rmmod bttv
rmmod tuner
``` as it says to do just before that.

It gives me an error ```
module bttv is in use by bt878
```

Is there another way to change the values for my tuner?

Thanks, again!

---

### Post by Donshyoku on 2006-04-07
Miraculous!  I found this thread while digging on Google:  [http://ubuntuforums.org/showthread.php?t=45220](http://ubuntuforums.org/showthread.php?t=45220)

It has exactly what I need!  ::Wonders why he hasn't come across this until now::

Great community, even if it was a bit indirect!:p

---

### Post by Donshyoku on 2006-04-07
Sorry to rehash this, but I am having one more problem...

Specifiying the tuner gave me video, but no audio!   I've been following [this thread]("http://www.ubuntuforums.org/showthread.php?t=154656") about a very similar problem.

My Gnome volume is on, the line in and CD both (in Windows it used CD) have both been enabled and the sound turned up.  But still no sound...

I don't mean to sound like the stereotypical discouraged Linux user, but I am about to turn back to Windows for this.  My desktop is used solely for TV/PVR and I don't own a regular television set so as to be able to watch anything.  This dorm room gets pretty boring sometimes!

So please, if you have any more advice, fire away, but if there is nothing by morning, I will probably head back into WinXP for the tuning capabilities.  Thanks again for the help so far, and I am really hoping for a solution!

---

