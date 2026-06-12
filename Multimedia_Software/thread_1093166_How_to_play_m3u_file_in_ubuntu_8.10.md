---
title: "How to play m3u file in ubuntu 8.10"
date: 2009-03-11
forum: Multimedia Software
---

### Post by vishrok on 2009-03-11
I just install the ubuntu 8.10 in and right away i faced a problem, the problem is i am not able to play the m3u file , i tried the Totem Movie Player it says it doesnt have the text/html decoder plugin , so i searched the net for solution i could find it , but i found a alternative to play that is mplayer , they said that it will play m3u but when i installed and tried to play it didn't even play , is there any codec needed to play this file in the if there where can i get it ....:popcorn:, i am trying a watch a m3u video and audio files with it ....

---

### Post by 5BallJuggler on 2009-03-11
The m3u file is generally a playlist file, for mp3's

Have you downloaded the mp3 codecs?

you will need to enable "restricted" sources.

to do this go to system - administration - software sources, then click on 4th box down to enable

once this is done, you need to try to open the file again, it should ask you to download codec.

---

### Post by lovinglinux on 2009-03-11
Please read the quote from Wikipedia below:
> An M3U file is a plain text file that contains the locations of one or more media files that the mediaplayer should play. Each location is placed on a new line. The locations can be either absolute or relative local pathnames (e.g., "C:\My Music\Heavysets.mp3" or "Heavysets.mp3") or they can be URLs. The file can also include comments, prefaced by the "#" character. In extended M3U, "#" also introduces extended M3U directives.

So open the file with a text editor and check if there is any path to real media files inside it. If you copied the m3u file from your previous Windows installation, then it probably has Windows paths, starting with **C:\**. This won't work properly on Linux, since your paths should start with something like ```
/home/vishrok/
``` 

Besides, if you copied from Windows installation, then it will have completely wrong paths, because the folder structure of you previous installation is different. Then you need to update the paths, locating where those video and audio files are stored now.

You could also try to open the video file alone to check if it is a codec issue.

---

### Post by lukon on 2009-03-30
If m3u playlists are just lists of media file locations, why do Linux media players find them impossible to decipher on Windows file-systems? It should be really easy to make a file-location translator such that when it sees "C:\blah blah blah" it should go to "media\blah blah blah" or whatever. Why are we users stuck with having to make copies of our Windows m3u files just for our Linux media players and doing global file-location path replacements just so our media players can find them?
The duplicity alone is a nightmare to maintain over several changes to the playlists.

Yo! Linux media player developers! Many of us are dual booters and migrators from Windows. We keep our playlists on Windows file-systems and don't want to move and translate them. Could you please accommodate us on this one?

---

### Post by change_mode on 2009-03-30
> **lukon said:**
> Why are we users stuck with having to make copies of our Windows m3u files just for our Linux media players and doing global file-location path replacements just so our media players can find them?

You aren't. Just use relative paths.

---

