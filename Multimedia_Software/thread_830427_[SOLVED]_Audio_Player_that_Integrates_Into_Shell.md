---
title: "[SOLVED] Audio Player that Integrates Into Shell?"
date: 2008-06-15
forum: Multimedia Software
---

### Post by Funky_Junk on 2008-06-15
Hi, I have a large music collection that (in Windows) I liked to manage through the shell. Now, in Linux, I'm looking for a audio player that can integrate itself into the shell, i.e. with a right click on a folder I can click "Play" and it it will send all of the songs in that folder to be played. 

Thanks.

---

### Post by mc4man on 2008-06-15
Normally you'd import your music files and set up playlists ect. i don't do to much of that but I'm sure there's ton's of people that could help you there. 
As far as just right clicking on a folder with music files inside and having them load and start playing in order I have 2 apps that will do that, amarok and vlc. Amarok _sometimes_ crashes if it's not running before right clicking on a folder so I usually have it open first. (in top panel) While it's not really a music player vlc works no matter what.
You would have to r.click -> open with -> open with amarok

---

### Post by ChameleonDave on 2008-06-15
Are you talking about the command-line shell?  You confuse me with this talk of clicking.

If you want to play music from the shell, use the "play" command; e.g.:

```

play ~/My\ Music/Hotel_California.ogg &

```

---

### Post by mc4man on 2008-06-15
Actually there's a way to eliminate the open with part. I'm sure there's a more proper way to configure ect. but it does work (at least with amarok)
Install nautilus actions. 
In system -> preferences -> nautilus actions configuration click add.
On the opening box add a label (I used open with amarok, call it play if you'd like) If you want to add an icon you can (i didn't). In the path insert /usr/bin/amarok
For parameters insert %M
In conditions leave first 2 boxes alone, below them check only folders and appears if selection.... 
In advanced ck. local files
Now when you right click on a folder (or file) theres an option open with amarok (or whatever you label it), choose it and amarok opens, the songs load and start playing.

Edit; if you use amarok in settings -> configure amarok uncheck remember current playlist on exit (bottom of general settings)
found some better parameters as noted below

---

### Post by Funky_Junk on 2008-06-16
mc4man, that is exactly what I'm looking for!

However, I cant seem to find anything called "Nautilus Actions". I'm using Hardy Heron, has it been renamed or something?

Sorry for my newb questions by the way.

---

### Post by mc4man on 2008-06-16
search for it in synaptic package manager or run in terminal
```
sudo apt-get install nautilus-actions
```
then you'll find it in system -> preferences
Do you have amarok installed and does it work good sound wise?
this is what your doing, set label as you want, the only icons that seem to work are from the drop down list

---

### Post by mc4man on 2008-06-17
@ Funky_Junk
as per your message maybe this ?
What you could do is make a third action (or 2nd if your not using 'play')
Open up nautilus actions configuration, highlight the Enqueue in Amarok action and choose duplicate. Now highlight either one of those Enqueue actions and choose edit. Change the name to Load in amarok (or whatever you want) and change the parameters to ```
--load %M
``` This way you can use Enqueue to add files and or folders and Load to replace the current playlist with a new one. Your current playing song will finish and then the new playlist will start. (or use win+b which will still be active because you only have/had 1 instance running)

edit : the enqueue and load actions are set to work on both files and folders - more useful that way
The enqueue parameter (--queue %M) adds whatever (file or folder) right below current playing song (when used after opening and playing). If you change that to (--append %M ) it will add it/them to end of current list, or make a seperate append action
For some other options you could change the Enqueue and or Load  parameter to (--queue --play %M) or (--load --play %M) - will immediately start playing what you r. clicked on. (probably more useful for the Load action)

I'm going to have 3 (got rid of the 'play' one cause of the multiple instance thing)
Enqueue      (  --queue %M   ) - adds whatever you r.click on to top of playlist, play starts right after current track
Append       (  --append %M   ) - adds whatever you r. click on to bottom of current playlist
Load         (  --load --play %M  ) - loads whatever you r. click on and starts playing, removes any existing playlist, if any

Additional way to append and or open
If amarok is open a left click/spacebar will append any file to current list if Amarok was set as default for that filetype
If it's not open it will open and start playing

---

