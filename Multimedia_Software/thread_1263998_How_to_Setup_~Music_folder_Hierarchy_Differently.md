---
title: "How to Setup ~/Music folder Hierarchy Differently"
date: 2009-09-11
forum: Multimedia Software
---

### Post by justinmiller87 on 2009-09-11
I'm trying to find a program that will allow me to sort my library easily by Genre. I've tried Rhythmbox, Banshee, and Amarok so far to no avail. All seem to not allow that method of sorting. Is this possible or am I just out of my mind?

Currently I have it set up as:
~/Music/Artist/Album/File

I'd love if it could be sorted as:
~/Music/Genre/Artist/Album/File

Any suggestions on what program I could use or some kind of shell script to do it quickly?

Basically I want to do this because my collection has grown larger than 80G and using Rockbox, I just want to be able to copy over genres I want to listen to at a time to my iPod.

Thanks
Justin

---

### Post by justinmiller87 on 2009-09-18
I'm bumping my thread and modifying the question.

Is there any software for Ubuntu or Linux in general that will work like MediaMonkey Gold does in Windows? That's basically what I'm looking for.

---

### Post by Random-penguin on 2009-09-18
Although I haven't got it installed at the moment, I'm sure Amarok offers a smart playlist in which you could create a genre based playlist (or many genre based playlists). Amarok also support the Ipod (or at least my ancient Ipod shuffle)... Perhaps I'm missing something in your question?

---

### Post by Chronon on 2009-09-18
> 
I'd love if it could be sorted as:
~/Music/Genre/Artist/Album/File

You can store your files in whatever file tree you want.  Amarok does allow you to browse your music by Genre > Artist > Album > File, I just checked this.

---

### Post by justinmiller87 on 2009-09-18
I run Rockbox on my iPod, so I don't want genre-based playlists. I just copy over directories and run them natively from there. That's basically what I'm going for. In MediaMonkey, you can set up your folder as the following:

x:\<base music folder>\<genre>\<album artist>\<album>\filename.mp3

So what I want is:
~/Music/<genre>/<album artist>/<album>/filename.mp3

So if in the morning I feel like listening to Alternative and Disco I can just copy those folders over to my iPod and listen to them happily through RockBox. That's what I'm going for, but don't know of any programs similar to MM in Linux. That's basically what I'm going for.

But if there's some way to change in settings somewhere Banshee, Rhythmbox, or <insert awesome Linux media player program here> to actually allow sorting by genre, that would be preferred. It seems hard-coded and I don't have enough programming experience to figure out how to change it. If it's not, I'd love to know where a .conf file for the program is.

---

### Post by tgalati4 on 2009-09-18
Use easytag to check your genre tags in the ID3 headers.

Most of the big players support smart playlists.  Simply create some smart playlists where genre=disco and copy those playlists over to the ipod.

It's a lot of work to move files around simply to create genre directories.  Most of the players are designed to parse the standard artist/album/song directory tree.  If you change it, you might create other problems.

---

### Post by MJWitter on 2009-09-18
In Rhythmbox you can have three panes: Genre/Artist/Album...  Isn't that what you are looking for?

---

### Post by justinmiller87 on 2009-09-18
I'm not syncing the iPod in any program. I drag them onto the iPod directly and store them in a /Music folder from Nautilus/Explorer window to Nautilus/Explorer window. In RockBox I navigate to and play songs out of. I don't sync under iTunes or MediaMonkey in Windows, I don't sync under Banshee, Rhythmbox, Amarok, or whatever player you can come up with in Ubuntu. I just drag and drop.

I was able to successfully get what I wanted using MediaMonkey as I said earlier. My tree structure is setup the way I wanted. I just wanted to be able to do it without using a program I had to pay $19.99 for, is closed source, and runs exclusively under Windows.

I was able, with abcde, to configure my new CD rips to the tree structure that I desire, but the issue is not wanting to manually look through my library in a music program, go "Avril Lavigne," okay. Let's drag her folder into the "Alternative" folder.

---

### Post by mobilediesel on 2009-09-18
Try MusicBrainz Picard [http://musicbrainz.org/doc/PicardDownload](http://musicbrainz.org/doc/PicardDownload)
It's in the repo
```
sudo apt-get install picard
```

You can set it up to organize how you want
I currently have mine set up as ~/Music/<Artist>/<Album>/
but you can put genre in there instead of artist or pretty much whatever you want.
It will also create/rename directories and move the actual music files to their new homes. It handles pretty much every format, mp3, ogg, wma etc.

---

### Post by Chronon on 2009-09-19
AFAIK, Amarok doesn't place any restrictions on the folder structure of your music.  You can even select as many different file trees as you want to be scanned for media.

This means you can have a genre layer in the path to your files and just drag these over to your Rockbox player using your file manager.

Is your question how to add new tracks into the path hierarchy you have chosen?  If so, easytag has pretty powerful renaming capabilities that allow you to scan metadata from your files and sort them into a new set of folders accordingly.  This is good for large scale rearrangements.  For ripping single albums into my hierarchy I have used soundkonverter in the past and am using abcde, currently.

---

### Post by ufugu on 2009-10-06
I had the same issue as you, wanting to re-organize my folder structure so I could navigate like that in Rockbox. (Everybody, he is talking about reorganizing the actual files, not tagging). 

I've done some pretty awesome file renaming and tagging with the logic available in EasyTag, but I found no solution to being able to reorganize files in this way.  Ended up spending a couple hours and doing it manually (for 22,000 tracks) which was less time than I spent googling for solutions...

---

### Post by secondstage on 2010-09-01
This posting is pretty high on Google, so I think there should be some sort of closure to the thread. 

Install EasyTag. Through aptitude, the software center, or command line.
```
sudo apt-get install easytag
```

Open EasyTag(Applications > Sound & Video > EasyTAG). Select the directory you wish to organize. It should begin to list to the files in the right column. Hit Ctrl-a to select all the files in the right column. Now in the top bar, click on the half-green half-white file icon. This will open the scanner prompt. Using the %tags, write out how you want the files to be organized. 
```
%a/%b/%n - %t
``` means artist/album/track number - track name. More %tags are available [here]("http://easytag.sourceforge.net/") Under documentation. click the half-green file icon in the pop up. Your files should be scanned now. Now close that little prompt window. 

The final step is save the new organization method. Select a single file in the right column. Hit Ctrl-a, then Ctrl-s. You might be prompted, just say yes. 

Your files should be organized according to the ID3 tags now.


This was hastily thrown together. But it should be pretty accurate.

---

### Post by justinmiller87 on 2010-09-03
Still none of these have answered my question. EasyTag looks like it does nothing but edit the ID3 tags. I can do that in my sleep. I want them to be moved from wherever I download or import from into /Media/Shared/Tunes/<genre>/<album artist>/<album>/<track#> - <artist> - <title>.<extension>.

---

