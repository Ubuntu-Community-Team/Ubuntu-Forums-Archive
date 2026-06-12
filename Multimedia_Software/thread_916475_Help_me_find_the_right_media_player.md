---
title: "Help me find the right media player"
date: 2008-09-10
forum: Multimedia Software
---

### Post by ezzieyguywuf on 2008-09-10
Really, all I want is to be able to browse my files in the media player, and when I click on a file, a playlist is automagically created that overwrites any current playlist and starts at the track that I clicked on. This is what happens in MediaMonkey and its a feature that I really miss. Is there a linux player out there that has similar functionality? Amarok doesn't, I don't think, but if there is a script I can use that I'm overlooking, please let me know. Thanks

---

### Post by mc4man on 2008-09-11
> to browse my files in the media player,
If you were to change that to 'browse my music files' then you can do pretty much anything with amarok. ( and to some extent audacious

This is based on 3 very useful parameters 'load', 'queue' and 'append', any of which can be paired with 'play'.

for instance '--load --play'  - loads selection(s), removes any current list, starts playback immediately

So if 'amarok --load --play' was invoked on a single file any existing playlist would be removed and the song would start. If it was used on a folder then again any existing list would be removed and the contents of the folder would be loaded in the order listed in the folder with immediate playback. 

There are many ways to use these commands, from r. click - nautilus actions, and or nautilus scripts. (I use 3 nautilus actions and 1 nautilus script) Setting a couple of file associations is also very useful.

Example of a file association - d. left clicking on a song 'loads and plays' (using mp3 as example

Pick any mp3, right click -> **properties** -> open with, if you see amarok **ignore**. Click - add -> use a custom command. Use this as comm.
```
amarok --load --play
```
and click **add**. You should now see a listing for amarok (**lowercase**) with a radio button enabled. If so, your good and d. clicking on any mp3 will open amarok and play song. (if not enable radio button for amarok (**lowercase**

Once you've created the association with one type then in properties -> open with you'll see amarok (**lowercase**) available, just ck. the radio button to set same association for other formats (if you have songs in multiple formats.
 It's possible to give that file association a different name if you wish. (useful if you want to create several associations and switch around or not confuse with the default Amarok (uppercase A)

You can also set the same association for m3u files - d. click on a m3u and all the songs listed are loaded and play starts.

Add some right click options using the above load & play along with queue and append and you can control anything from your desktop and home dir.

actions and useful parameters for r. click action, scripts and or file associations ( the %M is only for nautilus-actions

[http://ubuntuforums.org/showthread.php?p=5287915#post5287915](http://ubuntuforums.org/showthread.php?p=5287915#post5287915)

Also includes some stuff for audacious

---

### Post by hildebrand_us on 2008-09-11
You could consider using kaffeine. It seems to be what you want.

---

### Post by ezzieyguywuf on 2008-09-11
alright mc4man! I was actually messin with amarok yesterday, and when right clicking noticed the the load command was exactly what I wanted to do. I get what your suggesting, more or less, and will give it a try when I have a chance. One question: what do you mean by d. click?

Also, what would be most suitable for me is to write a script for amarok so that when i double click on a music file, within amarok, while browsing the Files tab, it performs the "--load --play" command on that file along with all files in that folder. How hard of a script would this be to implement? I'm somewhat familiar with bash scripting, and I'm alright on FORTRAN (lol, It was part of my major here at NCSU) but I'm pretty sure Amarok uses Perl scripts or somethin?

---

### Post by mc4man on 2008-09-12
> d. click?
double left click

The set file association determines what happens when you d. left click on a file (mp3, wav, wma, flac, ect. or a m3u
It will also become available as the very first (top line) right click -> 'open with' option
> 
.....within amarok

I actually never 'see' amarok other than to change a setting or when using ipod so not familiar with how that works. (I'm sure others would know more in that area

In other words my 'collection' is just how the music is stored - 
artist (folder), albums (subfolders)
mixes (folders)
loose songs on desktop

 The only 'playlists' I have are m3u's inside of folders/subfolders (either same as album/mix or edited to current preference) or are created on the fly with a 'load & play' to start, and then using the right click nautilus- actions.  
'queue' (added to current list below current playing track) and or 'append' (added to current list after last listed track.

---

### Post by mc4man on 2008-09-15
needs a little work

---

### Post by modmadmike on 2008-09-15
I personally use Songbird for music and VLC for video playback although songbird is still in beta it is extremely stable for me. I used to use Amarok but that requires the KDE runtime.

---

### Post by ezzieyguywuf on 2008-09-15
mc4man : i will give these suggestion a try, but it'd be great if there was a media player that did what I asked for in my first post, specially if was a gnome-native i.e. exaile or something more stable. any other suggestions guys?

---

### Post by PlainShane on 2008-09-16
Good luck trying to find a Media Monkey replacement. It can not be done. The best thing I have found so far is Banshee or plain old RhythmBox - neither of which seem to ease the pain of leaving the monkey behind.

---

### Post by greenleaf on 2008-09-17
[COLOR="White"].[/COLOR]

[FONT="Lucida Sans Unicode"][SIZE="2"]There is no alternative for mediamonkey in linux.[IMG]http://i37.tinypic.com/29vb8jn.gif[/IMG] Period.

If any of you are suggesting me to try amarok/rhythmbox... i tried every player there is in repository.... nothing comes even close.... the day i find a reasonable alternative to mediamonkey... i'll kiss my windows good bye.... It's shocking that there are so many music players in linux but none of them are good enough ... why not they conc. on improving a single player? (just do a search for mediamonkey in forums & you know how many newbies miss it or better take mediamonkey for a ride & see for yourself) [/SIZE]  [/FONT]

[COLOR="white"]n[/COLOR]

---

