---
title: "Organizing music with rhythmbox"
date: 2008-11-04
forum: Multimedia Software
---

### Post by atorch on 2008-11-04
Hi,

Does Rhythmbox have an "organize" function (similar to Amarok's or iTunes')?

For example, if I like my songs to be kept in ~/Documents/Music/Artist/Song.mp3, and I use Rhythmbox to play a dozen music files from my desktop, is it possible to have those dozen files moved automatically into my Music folder?

If so, how?

If not, why the f*#$ is this functionality missing?  I like that Rhythmbox is so lightweight, but every music player should be able to organize files.  Right now, I have to use Amarok to organize my songs, and I tell Rhythmbox to "watch" my Music folder for updates -- very inefficient / stupid.

Anyone?

---

### Post by maxmartin on 2009-02-01
Bump - I'd like to see an answer to this question as well. I don't want to have to manually create directories every time I want to add music to Rhythmbox - it's silly that this software would not have this functionality.

---

### Post by cyberkilla on 2009-02-25
Yes, I've often wondered about this myself.

Music collections can get very messy when id3 tags are changed and no longer correspond to the 'library/artist/album' folder hierarchy they reside in.

---

### Post by atorch on 2009-04-28
Could we get this written as a rhythmbox plugin?  I only know how to code in C, and I have no idea what language rhythmbox plugins are written in.

Just to make sure we're on the same page:

Rhythmbox's preferences already specify a library structure, e.g. /Artist/Title.extension on my machine.

I'd like to be able, in rbox, to right click on a song and, in addition to "add to play queue" and "move to trash," see an option to "move file to library."

For example, a friend might give me a file, and I might grab it from his usb drive and save it on my computer as ~/Desktop/The Beatles - The White Album - Side One - 08 - Happiness Is a Warm Gun.mp3.  If I drag the file into rhythmbox and use my "move to library" function, the file is moved to ~/Music/The Beatles/Happiness Is a Warm Gun.mp3, with hardly any effort on my part.  I could even do this with entire albums' worth of music, all in one click.

---

### Post by immeëmosol on 2009-06-27
I would very much appreciate the described behaviour as well.

plugins are written in python , but I also see .so -files , don't know what that is...
$ apt-file list rhythmbox | grep plug

---

### Post by atorch on 2009-07-30
Okay, well does anyone reading this...

1. agree with the idea, and

2. know python?

=P

---

### Post by atorch on 2009-10-24
[http://live.gnome.org/RhythmboxPlugins/WritingGuide](http://live.gnome.org/RhythmboxPlugins/WritingGuide)

---

### Post by bkadoctaj on 2010-05-02
Here it is folks.  Thanks to Wolter!!
[https://launchpad.net/rb-fileorganizer](https://launchpad.net/rb-fileorganizer)

---

