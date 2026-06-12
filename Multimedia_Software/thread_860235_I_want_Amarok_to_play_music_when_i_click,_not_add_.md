---
title: "I want Amarok to play music when i click, not add to playlist"
date: 2008-07-15
forum: Multimedia Software
---

### Post by Duranxl on 2008-07-15
E.g. i'm listening to song A...and want to listen to another song.
I search for Song B in my collection, and double click it.
But it adds it to the playlist! I don't wanna add it to do playlist but i want to play it instantly!

Any way to do this?

thanks

---

### Post by mc4man on 2008-07-15
> Any way to do this
(this is only for if you use nautilus)

If you access the files directly, yes it's very easy. I use 3 r. click actions to run amarok that give me complete control of what's playing, the current playlist, creating a new one, adding and appending. The thing is it's for using where and how you stored your music vs. importing and collections ect. In your case one r.click action would suffice, basically a slight change to what i have as 'Enqueue in Amarok'

Some screenshots of the parameters of the 3 i use, tool tips describes what happens
[http://ubuntuforums.org/showthread.php?p=5287915#post5287915](http://ubuntuforums.org/showthread.php?p=5287915#post5287915)
a somewhat rambling thread on
[http://ubuntuforums.org/showthread.php?t=830427](http://ubuntuforums.org/showthread.php?t=830427)

As far as what you want I'd set one up as below, the conditions can be edited to suit your needs, as shown will show up all the time in your r. click menu. You could limit it to files only or even certain kinds of files only - I think that's unnecessary though
If so you'll need to install nautilus-actions

the complete tool tip for below is 'adds to current list below current selection starts now'

A small note about 'playlists' - anytime you play a song or group of, a playlist is created, it's not possible to use amarok without this happening, that's why I use the 'load in amarok' all the time - it wipes out any current list and starts new

---

### Post by Duranxl on 2008-07-16
Thanks, very handy indeed!
But it's not exactly what i mean.

On XP, i used WMP11's library a LOT!!
E.g.: i want to listen to "fix you" by coldplay.
So i enter "fix you", it finds the song, and i double click to play it.

But in Amarok, it add the song to the playlist, instead of playing it directly. If it's the 1st song in the playlist, it'll play ..But if i want to change to song B, i have to search for "song B", double click it, and then double click it again in my playlist:confused:

Banshee player does exactly what i want it to do, but it has less features than amarok..

---

### Post by mc4man on 2008-07-16
I never had a 'collection' so I created one to see.

The double click from  a collection acts like the 'load in amarok' only when there is no playlist, if there a current list it will append.

The 3 basic parameters i use in nautilus are available when in the gui (playlist) by r. clicking on your collection area, but only append works in a totally useful manner (adds to end of list)
The other two, load and queue, work somewhat as expected. Load creates a new list with the song but has no --play parameter so it just sits there.

The queue is okay - it adds below the current playing selection the _first time you use it_, but again there is no --play parameter. The other limiting factor with queue is it seems to create a 'queue' list within your playlist and any additional queued songs are always added below a previously queued song. 
If you have already moved past your 'queue list' then you're adding songs that will never be played. (seems dumb to me)(unless you only use queue to populate a list)
The only way around all this using the gui and 'collections lists' would be if you could modify the built-in parameters - don't see a way as yet.

Thanks for bringing this up, I never thought an action --queue --play would be useful, I've added it to the other three

---

### Post by geb666 on 2008-10-07
Here's how to get the double-click to work in Nautilus:

Right click on the audio file, go to "Open With", and then "Open with Other Application".

Then click the arrow at the bottom that's labeled "Use a custom command".
Type this command into the text box:

/usr/bin/amarok --append --play

Click "Open" and then all files of that audio type should now open with that command which will automatically append to the playlist and immediately play the song.  If you have multiple audio formats you use, then you may have to do this same thing for all of them.

Be aware that doing this will change Amarok so that if you double-click in Nautilus on a song that is already in the Amarok play list, it will append another copy of that song at the end of the list.

---

### Post by MrBucket101 on 2008-12-03
> **geb666 said:**
> Here's how to get the double-click to work in Nautilus:

Right click on the audio file, go to "Open With", and then "Open with Other Application".

Then click the arrow at the bottom that's labeled "Use a custom command".
Type this command into the text box:

/usr/bin/amarok --append --play

Click "Open" and then all files of that audio type should now open with that command which will automatically append to the playlist and immediately play the song.  If you have multiple audio formats you use, then you may have to do this same thing for all of them.

Be aware that doing this will change Amarok so that if you double-click in Nautilus on a song that is already in the Amarok play list, it will append another copy of that song at the end of the list.

That fixed my problem in nautilus, but I use amarok to browse and play files from my collection, any way to fix that problem?

---

### Post by bugoga on 2008-12-09
I'm wondering if this is still not posted here. File associations can be set up to behave more intuitive, i.e. amarok to create new playlist every time you open file by clicking on it from file browser: amarok --load --play ...

---

### Post by mc4man on 2008-12-09
> I'm wondering if this is still not posted here.

well the Op only wanted to know how to change the l. click action inside of Amarok's gui/playlist/collection.
Myself I don't use a collection and do as you mentioned, d. left click is set to amarok --load --play.

Additionally i use 3 right click nautilus actions for amarok which I find very useful. (i think most people want to use the collection, playlist 

[http://ubuntuforums.org/showthread.php?p=5287915#post5287915](http://ubuntuforums.org/showthread.php?p=5287915#post5287915)

And I even set a portion of my music to be available off of r.click nautilus scripts where each script is an album. (it's actually grown quite a bit with folders, sub folders and a couple of sub sub folders.

[http://ubuntuforums.org/showthread.php?p=5797640#post5797640](http://ubuntuforums.org/showthread.php?p=5797640#post5797640)

---

### Post by ShadowfoxXXX on 2008-12-28
ok people are going in circles here. i love amarok, but i might switch to foobar if no one solves this. I want to DOUBLE CLICK A SONG IN AMAROK and have it play immediately. It has absolutely NOTHING TO DO WITH NAUTILUS, Thanks.

---

### Post by mc4man on 2008-12-28
> I want to DOUBLE CLICK A SONG IN AMAROK and have it play immediately
It only happens when the playlist is empty, after that the track is appended and there is no apparent way to change.

The 3 relevant actions are available on r. click anyway.

---

### Post by listless on 2009-01-24
Hi,
If you're using a new version of amarok just add all the songs in your collection to a playlist. then search the playlist rather than the collection (cos you can double click playlist songs to play instantly etc). Hope that helps.
l

---

