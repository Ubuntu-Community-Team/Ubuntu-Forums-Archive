---
title: "Stopping Autoplay of Audio CD's"
date: 2009-07-12
forum: Multimedia Software
---

### Post by Black Razor on 2009-07-12
How in the hell do I make Ubuntu stop playing discs automatically when I insert them?  I already adjusted the options for the disc drives, and even set it to do nothing when a disc is inserted.  It STILL plays the damn CD. I'm getting tired of it.  Someone please help.

---

### Post by mc4man on 2009-07-12
Check in file management -> media that you have audio cd set to do nothing
```
nautilus-file-management-properties
```

If so and still autoruns then insert an audio cd and hold down the shift button.
You'll get a pop up, choose do nothing and check the box to always do that action

---

### Post by Black Razor on 2009-07-12
Well, what you said to do, did bring me up the prompt.  However, its telling me that I have nothing installed to handle CD audio.  Which is total crap, because I have like ten different audio players installed.  What now?

---

### Post by mc4man on 2009-07-12
Don't use jaunty, but took a quick look on live cd. (on it right now

For the most part the autorun (default action) is the same as it's been since hardy.

By default you should have 6 options from file management and 5 from the pop up. (and it all works fine), noting that by default only 2 apps are registered with the mimetype 'x-content/audio-cdda' - rhythmbox and braseo

If you remove all the registered apps (by default 2) and don't add any apps that register the mimetype or register them manually then the pop up or fm -> media -> audio cd becomes inactive and will remain so till an app is registered with 'x-content/audio-cdda' 

screenshot1 shows pop up with no registered apps 

Did you remove rythmbox and brasero?

What app is 'auto playing'?

If screen 1 shows what you see to get the choices back install an app that self registers (rhythmbox, brasero, vlc) or register one you have

screen 2 shows the default .....media, 6 choices

Post this if you wish and list what players you have

 ```
cat ~/.local/share/applications/mimeapps.list


```

---

### Post by Black Razor on 2009-07-12
[Added Associations]
video/mpeg=vlc.desktop;xine.desktop;
image/tiff=eog.desktop;gimp.desktop;
video/x-ms-wmv=userapp-xine-BH37NU.desktop;totem.desktop;vlc.desktop;banshee-1.desktop;mplayer.desktop;
video/mp4=VLC media player.desktop;vlc.desktop;totem.desktop;ghb.desktop;videocut.desktop;
audio/mpeg=VLC media player.desktop;vlc.desktop;totem.desktop;audacious.desktop;ghb.desktop;mplayer.desktop;videocut.desktop;soundconverter.desktop;xine.desktop;audacity.desktop;
video/x-flv=vlc.desktop;
x-content/video-dvd=totem.desktop;vlc.desktop;brasero-copy-medium.desktop;userapp-xine-BH37NU.desktop;
video/x-msvideo=vlc.desktop;
application/x-extension-drive=VLC media player.desktop;

---

### Post by Black Razor on 2009-07-12
Ok, I dont know what is going on exactly, but through trial and error, I figured out its mplayer.  Mplayer is the program that is actually playing the CD.  I killed the process and the music stopped instantly.  So, how do I stop this from happening?

---

### Post by mc4man on 2009-07-12
> Also, **it's still** doing it
What is it?

If it's rhythmbox that's opening what was opening before you re-installed it?


From post 1
> even set it to do nothing when a disc is inserted. 

What and how did you do that?

(if you've got your choices back, try switing to 'open folder' and see it that works. If it does then switch from that to 'do nothing'

---

### Post by Black Razor on 2009-07-13
OK, let me try to calm down and explain this more explicitly.  Nothing is opening, that's the problem.  The system ("it") is just playing the CD.  It's doesnt seem to matter how I configure the preferences, what program is is set to do whatever..it just mounts the Audio CD and as soon as it's mounted it starts to autoplay.  Like I said, when I kill mplayer in the services, the audio stops, but then so does ALL my audio for the entire system.

*sigh* Lack of knowledge = one bummed Ubuntu user.  I don't understand what's going on, I just want it to stop.

The part that is really irritating is that the majority of Ubuntu users seem to want this feature.  I do NOT.  I hate it, it's irritating.  I don't autoplay, I never have, and never will. I don'/t want an answer to the following question, it's rhetorical, but I just can't imagine why anyone would actually want this feature.  Why even have audio players like Amarok, Banshee, Songbird, etc, if the system is just going to play the CD anyhow, and furthermore, not give me the ability to stop it.

---

### Post by mc4man on 2009-07-13
Something was 'done', this doesn't appear to be normal behavior by any means

When you say mplayer do you mean mplayer or Movie Player (as in totem-gstreamer or totem-xine?

Maybe **for starters** try to shift the default action to rhythmbox (if not still installed then install

go from terminal

```
gedit ~/.local/share/applications/mimeapps.list
```

look for this line (wasn't there previously but look, it may be there now
x-content/audio-cdda=

If not there then copy and paste this in 
```
x-content/audio-cdda=rhythmbox.desktop;
```

If the line is  there please copy and post

---

### Post by mc4man on 2009-07-13
And one further small question
Did you at any point access file management (edit -> preferences -> media) as root? (either thru gksudo nautilus or otherwise)

---

### Post by Black Razor on 2009-07-13
Does this help?  This is the process that when I stop or kill the audio playback stops, but when I do that, I also lose all audio for the system.

[[IMG]http://img232.imageshack.us/img232/5194/screenshotigb.th.png[/IMG]](http://img232.imageshack.us/i/screenshotigb.png/)

---

### Post by mc4man on 2009-07-13
> Does this help?

Yes and no, if would be helpful if you answered any of the various questions asked in each of the previous posts or results of things to try

What you done is set mplayer as the default audio cd player with a specific command. 
That in itself is a poor idea when done without having the command executed in a 'visible' terminal. 
So in your case mplayer is running in the background with no way to control (though the command is only to play track 1, it should exit after the track is played

This probably didn't just 'happen' on it's own, but according to your posted mimeapps.list you as a user didn't set it. Without any further info can't say how this occurred.

---

### Post by robert shearer on 2009-07-13
Just to check that you have done the following.??

Places=>home=>Edit=>Preferences=>Media and then choose "do nothing" for 'cd media' and 'music player', **and** you have **unchecked** the box 'Browse media when inserted"

---

### Post by Black Razor on 2009-07-13
Well, my gurus, I have followed all of your instructions so far.  What you see in that screenshot is where I stand.   I don't know how mplayer got set that way, but like you said, I didn't do it.  

May I inquire please how I fix it?

---

### Post by Black Razor on 2009-08-07
FINALLY!  This was really starting to peeve me.  Freevo.  The reason it was doing this was because I had Freevo installed.  Thought I would share with everyone for knowledge.

---

### Post by robert shearer on 2009-08-08
Thanks for the update, good to know what works and what does not.

Looked at the Freevo documentation....
[http://doc.freevo.org/MovieUsage](http://doc.freevo.org/MovieUsage)

> Freevo shows all you rom drives in the MOVIE MAIN MENU (set the variable ROM_DRIVES in the config file if the auto detection doesn't work). You don't need to mount the disc, freevo will automatically mount and umount the drive.

Guess that was it ?.

---

