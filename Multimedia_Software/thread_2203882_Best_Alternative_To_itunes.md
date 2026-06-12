---
title: "Best Alternative To itunes"
date: 2014-02-05
forum: Multimedia Software
---

### Post by CrystalDreamer59 on 2014-02-05
I have an ipod so I'm use to using itunes, but I really prefer linux, which can't run itunes. The best I have found so far is banshee, but it's music database isn't the best. What is a better alternative for syncing music to ipod that can run on linux.

---

### Post by shantiq on 2014-02-07
[clementine]("http://www.clementine-player.org/")
also [nightingale]("http://getnightingale.com/") [i have never personally tried it]
this here is almost a copy of itunes  >>   [atunes]("http://www.atunes.org/")    there is a deb [here]("http://sourceforge.net/projects/atunes/files/latest/download?source=files")

when you open the deb from terminal ```
sudo dpkg -i atunes_3.1.1-1_all.deb
```
it might say dependencies missing
so run ```
sudo apt-get -f install
``` then all should be cool

**[FAQ]("http://www.atunes.org/wiki/index.php?title=FAQ")**

[ATTACH=CONFIG]250153[/ATTACH]

---

### Post by CrystalDreamer59 on 2014-02-11
Do you know if atunes can rip CDs since I have most of my songs on CDs

---

### Post by shantiq on 2014-02-11
yes but it requires


```
sudo apt-get install [COLOR=#000000][FONT=sans-serif]cdda2wav [/FONT][/COLOR]
```   or   ```
sudo apt-get install [COLOR=#000000][FONT=sans-serif]icedax [/FONT][/COLOR]
```   depending on version of Ubuntu


then go to   Tools/import cd


but tagging facility not great 


[B]FOR RIPPING:
[/B]
better use something like this

```
sudo apt-get install pacpl
```


then to place the rips in the Music folder and  refresh   click on player and F5

example  


```
mkdir Music/'Artist - Album Title' && time pacpl --outdir ~/Music/'Artist - Album Title'  --rip all -t mp3 --bitrate 320
```
```
mkdir Music/'Artist - Album Title' && time pacpl --outdir ~/Music/'Artist - Album Title'  --rip 1,2,3,4,5    -t flac --fcomp 8 
```


enter   'Artist - Album Title'    yourself

---

### Post by monkeybrain20122 on 2014-02-11
> sudo apt-get install [COLOR=#000000][FONT=sans-serif]cdda2wav [/FONT][/COLOR]

I can't find such a thing in the repo. 

From the name presumably it rips to Wav? Why does anyone want wav? It is a Windows format and requires Windows codecs to play. I rip my CDs to flacs (with k3b), if I wants something smaller I would use ogg, or if portable use mp3.

@Op instead of using a single application for playing/managing music and ripping I use guayadeque as player/music manager and use k3b for ripping.

---

### Post by shantiq on 2014-02-12
hmmmm


sudo apt-get install cdda2wav
[sudo] password for shan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'icedax' instead of 'cdda2wav'
The following packages were automatically installed and are no longer required:
  libkeybinder0 python-gnome2 python-keybinder python-pyorbit
Use 'apt-get autoremove' to remove them.
Suggested packages:
  cdrkit-doc
The following NEW packages will be installed
  icedax
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 175 kB of archives.
After this operation, 412 kB of additional disk space will be used.
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy/universe icedax amd64 9:1.1.11-2ubuntu3 [175 kB]
Fetched 175 kB in 0s (605 kB/s)
Selecting previously unselected package icedax.
(Reading database ... 338032 files and directories currently installed.)
Unpacking icedax (from .../icedax_9%3a1.1.11-2ubuntu3_amd64.deb) ...
Processing triggers for man-db ...
Setting up icedax (9:1.1.11-2ubuntu3) ...

[ATTACH=CONFIG]250280[/ATTACH]
so maybe go for icedax instead

---

### Post by CrystalDreamer59 on 2014-02-20
By the way another question about atunes does it have a link to a music store on it like banshee had a link to amazon mp3 store. It's not that important I don't think but I'm just wondering.

---

### Post by CrystalDreamer59 on 2014-02-21
I am testing atunes on a windows OS first and for some reason my cds won't rip any suggestions.

---

### Post by andrew.46 on 2014-02-21
> **monkeybrain20122 said:**
> I can't find such a thing in the repo.

cdda2wav is part of the original cdrtools that is no longer available to Ubuntu users who have access only to the Debian fork. A long and heated story behind that particular fork....

---

### Post by andrew.46 on 2014-02-22
> **CrystalDreamer59 said:**
>  What is a better alternative for syncing music to ipod that can run on linux.

When I get home from my 2 weeks away, I have planned on having a look at gtkPOD to sync with my 'classic' ipod, I am a litle surprised that nobody has mentioned it. (I plan on ripping the audio cds with cdda2wav and then manually transcoding (and tagging) to mp3 using commandline lame.) This is perhaps a slower way of doing this but I am a big fan of slow and careful....

---

### Post by shantiq on 2014-02-23
regarding syncing i want to make sure people have seen what it says a about atunes in the [wiki]("http://www.atunes.org/wiki/index.php?title=FAQ")  ...   that is something it does NOT do

> **Is it possible to synchronize my iPod with aTunes?**

[COLOR=#000000][FONT=sans-serif]Currently aTunes can only [/FONT][/COLOR]**READ**[COLOR=#000000][FONT=sans-serif] iPod contents until 4th generation. It has not been tested with later versions. It [/FONT][/COLOR]**can't**[COLOR=#000000][FONT=sans-serif] write songs to iPod. However, aTunes can write to many generic mp3 players acting as external hard drive (i.e. mass storage devices).[/FONT][/COLOR]


> **How do I put songs on my mp3 or device?**

[COLOR=#000000][FONT=sans-serif]Go to "Device" -> "Connect". Select where your mp3 device is mounted (for Windows users select drive letter)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]In navigator panel (left). Browse to songs/artist/album you want to add to your mp3 player, right click and select "Copy to device".[/FONT][/COLOR]


personally that is not an issue since i would never buy an ipod due to the fact that you cannot move them around computers as easily as non ipod players [tends to like to be home on one computer]
atunes can also be used as a non-library player as you can drag tracks into it ...    and then benefit from the artist info youtube links etc ...

I just wanted to clarify the ipod situation for the OP   

But as Andrew says you can use [COLOR=#000000]gtkPOD  for syncing   [not sure myself how this performs since never had an ipod] [/COLOR]

---

### Post by timin on 2014-07-08
> **CrystalDreamer59 said:**
> I have an ipod so I'm use to using itunes, but I really prefer linux, which can't run itunes. The best I have found so far is banshee, but it's music database isn't the best. What is a better alternative for syncing music to ipod that can run on linux.

We use K3b to rip (after having tried many others as well) and Clementine to play and organise.  The Clementine remote (Android) works very nicely.

---

### Post by markmckee6011 on 2014-07-09
Please sign and share this petition - iTunes for Linux
[https://secure.avaaz.org/en/petition/Apple_Inc_iTunes_for_Linux](https://secure.avaaz.org/en/petition/Apple_Inc_iTunes_for_Linux)

---

### Post by BBQdave on 2014-07-09
Thoughts from a dinosaur...


[LIST]
[*]I purchase whole albums in the form of CD's
[*]music ripped with Asunder into the Ogg Vorbis format
[*]I make a folder, such as *JAMtunes*, and copy music from my library into the folder (my way of grouping music)
[*]add the folder *JAMtunes* to my Sansa Clip+
[*]Select *JAMtunes* on my Sansa Clip+ hit shuffle and enjoy a nice music mix
[/LIST]

I like Rhythmbox to organise and create playlists of my Ogg Vorbis music library. Android has a similar application to Rhythmbox, Music (android music application) and I simply add my Ogg Vorbis library for organising and playback. Plus - I appreciate the freedom to backup and save my music as I like :)

---

