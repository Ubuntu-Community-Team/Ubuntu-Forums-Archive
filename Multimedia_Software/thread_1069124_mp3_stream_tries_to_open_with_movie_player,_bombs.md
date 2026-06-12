---
title: "mp3 stream tries to open with movie player, bombs"
date: 2009-02-13
forum: Multimedia Software
---

### Post by kline on 2009-02-13
Can anybody tell me what apps in "Edit->Preferences" in Firefox I need to set to have an MP3 stream Just-Work?  I used to be able to listen by simply clicking on the ``listen live/MP3'' area; seconds later the stream would play.  About an hour ago I tried, and firefox asked if I wanted to save the file or listen with "Movie Player".  

When I accept this player, the application open, then file loads, and a few seconds later a dialog opens that reads:

"An error occurred\n\tFailed to connect stream; Invalid argument"

If I save the file, "listen.pls" to ~/Desktop I can listed to the stream by pointing, say, vlc at it.  For the time being, I'm wedged.

Slightly OT is that Miro now fails to play mp4 audio... but this is another question.  Hopefully one of the audio wizards can clue me in!

tia, guys.

---

### Post by mc4man on 2009-02-13
I'm actually no fan of totem or gstreamer in general but I have to say it works quite well playing .mp3's from websites.

For files listed as .mp3 a d. click and they start playing. For .pls I get a pop up (only because I haven't checked 'Do this auto....' and the default of totem works fine.

I have tried 'open with other' from the pop up and pointed it (browsed) to /usr/bin/vlc which also works fine.

Can you play any .mp3 with totem-gstreamer? (requires the gstreamer0.10-ffmpeg plugin

---

### Post by kline on 2009-02-13
Hm, I see an error to stderr/stdout::



(totem-gstreamer:5719): GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed

(totem-gstreamer:5719): GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed
                                 
so obviously I'm missing something, or have messed something up.  Any idea why this assertion fails?

---

### Post by mc4man on 2009-02-13
That's a very generic error message, if there's a problem with audio, video settings or the file or stream itself that's what your liable to see.

I'm not that up on gstreamer issues, did anything change recently with your sound settings.

It would seem your plugins are ok. you could run these 2 commands to see what's installed

 ```
dpkg -l '*gstreamer*' | grep '^ii'
```

```
dpkg -l '*totem*' | grep '^ii'

```

Did you try running vlc from the pop up?

---

### Post by kline on 2009-02-13
The pop-up wouldn't let me select vlc; but

% vlc listen.pls 

works just fine.

Now, how-to include my output from your dpkg listing!

(okay, i had to rename the /tmp file to end in ".txt".  but it says it is there.  i can't tell if i have anything duplicated.  wouldn't think so)

Ah, _yes_, :-), it is listed ....

If you can figure this out, I'll be a very happy camper!

---

### Post by mc4man on 2009-02-14
I didn't get a chance to read your .txt (next time just copy from the terminal and paste into your reply

There is a sticky here that has a big section on browser plugins, you might want to read thru

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

> The pop-up wouldn't let me select vlc; but

I'm surprised about that you don't get what's in the screenshot( the 'other' choice, not vlc which appeared after below action

From there you would browse to /usr/bin/vlc and choose it.

I'll download that .txt and see if anything interesting is in it

 (try the 'other' -> ...vlc thing again


Edit: looks like you have almost all the gstreamer plugins ect.., no problem there.
Still wondering, can you play mp3's in totem locally? 
Looks like your using pulseaudio in 8.04, that's always a wild card.
Maybe try playing some mp3's both locally and online with totem and have top running in a terminal, see if pulse appears and if it crashes ( just enter top in a terminal

2nd screen shows were I can change plugin for mp3's in firefox (only for mp3's, not the pls

---

### Post by kline on 2009-02-15
> **mc4man said:**
> I didn't get a chance to read your .txt (next time just copy from the terminal and paste into your reply

[FONT="Times New Roman"]Apologies; the text was to long to mouse and paste from my Konsole, then I remembered that there was a means of including attachments...  Sorry for the delay, but Real-Life intervened today... .

[/FONT]
There is a sticky here that has a big section on browser plugins, you might want to read thru

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

[FONT="Times New Roman"]I will read this, thanks; I've been using Ubuntu going on 4 years and usually everything works out-of-the-box.  This time I may have put in too many A/V binaries.
[/FONT]

I'm surprised about that you don't get what's in the screenshot( the 'other' choice, not vlc which appeared after below action

From there you would browse to /usr/bin/vlc and choose it.

[FONT="Times New Roman"]According to my FF3 Prefs, I had "ask me" set on some filetypes, not all.
I just switched to Kmplayer for most ``Content Types'' -- not all.  Still checking things out.
[/FONT]
I'll download that .txt and see if anything interesting is in it

 (try the 'other' -> ...vlc thing again


Edit: looks like you have almost all the gstreamer plugins ect.., no problem there.
Still wondering, can you play mp3's in totem locally? 
Looks like your using pulseaudio in 8.04, that's always a wild card.
Maybe try playing some mp3's both locally and online with totem and have top running in a terminal, see if pulse appears and if it crashes ( just enter top in a terminal

[FONT="Times New Roman"]totem works with my mps files jus' fine, thank you.  Maybe I'll move pulseaudio out of the way and see what happens.  If this is a bug, I'll look around and from a PR/bug-report/<<whatever>>.
[/FONT]

2nd screen shows were I can change plugin for mp3's in firefox (only for mp3's, not the pls

Vary cool (thumbnails)!   This is a seriously neat forum application.

Bottom line, running kmplayer against most things does seem to work; in the one case where I was streaming radio at 32K, it took at least 90 secs to play.  15mins commercial, the rest probably buffering.  [??]

I've just installed Ubuntu on a second desktop, and probably will install it on a third soon.  When I have figured out what I'm doing _wrong_, I'll write up my bunch of how-to's and post them on my website [thought.org].  Hope it helps ... .[FONT="Times New Roman"][/FONT]

---

