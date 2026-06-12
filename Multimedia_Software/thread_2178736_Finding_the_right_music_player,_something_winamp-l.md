---
title: "Finding the right music player, something winamp-like"
date: 2013-10-04
forum: Multimedia Software
---

### Post by jewisharific on 2013-10-04
OS: Ubuntu 13.04 x64

I'm having trouble finding the ideal music player.
I use Winamp in Windows, and most of these features are found in that.

**Must Have Features:**
[LIST=1]
[*]*3 Tiered Media Library (with search)*
Winamp's media library is split into 3 panes (by default): One for the artists, one for the albums, and one for results.  This is similar to Banshee's default.
The artist and album panes show a single artist/album, and do not care about letter case. There is also a listing for "All" at the top of each pane.
The results pane shows matches from the first 2 panes, and from the search bar.
Clicking the All button in the artist/album panes will cause the results pane to display all matches from the search bar and other pane selection.
[*]*Always Visible Play Queue*
Banshee has a play queue, but I can't see it at the same time as the media library.
In Winamp, (by default) double clicking an item in the Results Pane will cause the contents of the pane to move into the Play Queue, replacing the queue's contents.  It then begins to play the item that was clicked.
I would also be okay with "add-to-play-queue" being the double click behavior.
[/LIST]
**Desired Features:**
[LIST=1]
[*]*Tag Editing*
Artist, Album, Title, Track number, and Album art are all I care about
[*]*Unity Integration*
I'd like something that integrates well with the app menu, and is snappable
[*]*Hotkey Support*
Basic Play/Pause, Next track
[*]*USB Device Support*
Winamp had a feature where I could specify (per device, including flash drives) what I wanted the maximum bitrate of a track to be.  I could also specify only certain compatible filetypes.
My car will play MP3s off of a flash drive.  So I set it up so that anything I copy to the device would automatically convert to mp3 (if it wasn't already), and would convert to vbr (with specific settings) if it was above 320 kbps.  This doesn't necessarily need to be part of the media player, but I would like a media library-like display for the contents of the drive, and the ability to drag tracks from the player's library into the device.
[/LIST]

Just looking for suggestions.  I'll give anything a chance.

---

### Post by Yellow Pasque on 2013-10-05
Have you tried Clementine?

---

### Post by jewisharific on 2013-10-05
Clementine is great! Thanks for the suggestion.  It's my fave until I can find something better.

The only thing it's missing is the three pane library.  The whole library shows up in one pane, with artist and album being collapsible (like foobar's default).
I don't see a way to configure my desired behavior.

Otherwise, this is perfect.  It has a play queue with configurable double-click behavior, a decent tag editor, blends well with unity, supports hotkeys, and has a built-in transcoder that I can use with flash drives.  Why isn't this more popular?

---

### Post by drmrgd on 2013-10-05
> **jewisharific said:**
> Clementine is great! <snip> Why isn't this more popular?

Great question that can only be furthered by asking 'Why isn't it the default?'  Over the years I've been hard pressed to find anything that works quite as nicely as Clementine!

---

### Post by Yellow Pasque on 2013-10-05
Clementine probably has more users than you think. Ubuntu used to keep their installers to CD size, which meant that Qt apps like Clementine would force inclusion of Qt libraries, and that was a decent chunk of space. So the Ubuntu devs made rbox default since it didn't require as many extra libraries and it was a sane choice. The same thing happened when Banshee replaced rbox as the default and it got switched back in the next release because the devs didn't want to include Mono libs in the installer.

---

### Post by jewisharific on 2013-10-26
Marking as solved.  Clementine is great; I've learned to ignore the things it's missing.

---

