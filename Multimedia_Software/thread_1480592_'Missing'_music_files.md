---
title: "'Missing' music files"
date: 2010-05-11
forum: Multimedia Software
---

### Post by Jon_D on 2010-05-11
I was using Rhythmbox with no problems. Today though it was listing every song twice. So I selected all of my music (in Rhythmbox) and hit 'remove'. Now it will not see any of my music, just the folders and the albumn art within the folders. This is true within Rhythmbox and within the file browser.

I am using Ubuntu 9.1, dual booting with Vista and Windows 7. Windows media player in Vista and 7 still 'sees' and plays the music. The music is on an NTFS partion, and was ripped the the drive via Windows media player. The music is MP3's. I do have a small amount of music that was not in the orginal folder that Rhythmbox was linked to, and they are ok and will play.

---

### Post by Jon_D on 2010-05-12
I found out what happened. By hitting remove in RhythmBox it actually deleted all of the files on my NTFS drive. They did not go to the trash can, they went to a trashes folder, and thankfully Vista has a feature to restore folders to previous version and all of the music was restored to it's orginal file location.

---

### Post by Jammanuser on 2010-05-12
> **Jon_D said:**
> I found out what happened. By hitting remove in RhythmBox it actually deleted all of the files on my NTFS drive. They did not go to the trash can, they went to a trashes folder, and thankfully Vista has a feature to restore folders to previous version and all of the music was restored to it's orginal file location.
And where was the "trashes" folder?
I just tried what you say you did myself in RythmnBox, but hitting Remove just seems to have removed the music from my library, and did not actually delete any files. But when I reimported my whole music folder (which it did successfully), i got a message saying the folder "Jason Mraz" didn't exist. I just looked, and its true. It doesn't exist anymore. And now trying to play a song in RythmnBox always gives the message:
> 
Couldn't stop playback

Unknown playback error
But I think that's probably an un-related problem, because I've been recently changing settings in System->Preferences->Sound, and I may have something set wrong or something.
So it seems it may have deleted at least one folder, but doesn't appear to have deleted anything else, because the music files exist inside their folders.

---

### Post by Jon_D on 2010-05-12
it was in the root directory of my C:\ drive

---

### Post by Jammanuser on 2010-05-12
> **Jon_D said:**
> it was in the root directory of my C:\ drive
And it was named "trashes"?
Hmm...seeing as I'm using a different partition than my OS partition (i.e. a partition called "DATA") for storing my music files and folders on, I would think there would be a similar folder in the root of that partition in my case, but no such folder exists. I even tried showing hidden files in the file browser. However, there is a "RECYCLER" folder in the root, but that is empty. If RythmnBox put any of my stuff somewhere, it wasn't there, obviously.

Hmm...I love the problems I face on my computer every day. :popcorn:

---

### Post by Jammanuser on 2010-05-12
Ok, now that is weird. It seems Rythmnbox took some music files out of their folders, and stuck them in a folder which it created called "Countdown". It then deleted their original folders.

I don't understand why it did this. I did not give it permission to mess up my music folder... :lolflag:
Its a music program. Its basic function should be to only store a profile based on music you select, and play the music I tell it to. Why does it **** with my music folders, especially when I tell it to do something as mundane as remove all the music in the library, and then import the whole "iTunes Music" folder's contents?

I think I'm going to go have a chat with the Rythmnbox developers, to find out what's in their heads...

-Jam Man

:guitar:

---

