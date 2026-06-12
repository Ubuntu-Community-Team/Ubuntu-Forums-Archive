---
title: "True Lossless CD Audio Ripping, ideas?"
date: 2012-02-26
forum: Multimedia Software
---

### Post by Willard on 2012-02-26
Hi folks,

I want to digitize my music collection, consisting of several hundred CDs. I have two major objectives in mind:

[list]
[*]**Integrity:** My CDs will get ruined by age; I want to preserve the data that I paid for.
[*]**Accessibility / Portability:** Popping a physical CD into a drive to hear digital music playback is stupid, annoying, cumbersome and unnecessary.
[/list]

Which file formats should I go for, and which applications and means to you recommend to produce them?

(is there an ISO format I can use? Should I use BIN/CUE? FLAC/CUE? UDF? Pack everything into a Matroska container?)

I have some constraints; I have looked around on the Web to see what others have done, but from what I see, most people are contempt with storing a lossy audio encoding, or to just store FLAC files. However, in these approaches, important information on the CD is lost. For instance:
[list=1]
[*]I want playback to be [gapless](http://en.wikipedia.org/wiki/Gapless_playback) when the artists intended it to be, as in the transition to a track from its intro track (example: artist: "Dimmu Borgir", album: "Puritanical Euphoric Misanthropia", tracks: 1 and 2). This breaks immersion.

[*]I also want the silence between tracks to be exactly like what the artists intended. Sometimes, artists let a song fade out, give a moment of pause, and then start the next track. If this moment of pause is omitted/shortened, the next track feels "sudden", again breaking immersion.

[*]I want the waveforms to be unchanged in my digitization of the CD. For instance, there used to be a song "Prevail" by "Kreator" on YouTube which, after the brief moment of silence at 3:17, had the waveforms amplified, compared to the CD version, for a fraction of a second (*EDIT:* [this YouTube rip](http://www.youtube.com/watch?v=Er1b8X2plzo) of "I C?m Blood" by "Cannibal Corpse" has this issue, particularly prominent at 2:31). This literally sent me flying out of my seat when I heard it because I thought someone had suddenly, sneakily, cranked up the volume of my speakers. I also don't want my digitization to introduce [clipping](http://en.wikipedia.org/wiki/Clipping_(audio)). On Spotify, on "King of the Grey Islands" by "Candlemass", track 1 leads into the lower-volume track 2, resulting in an experience not nearly as overwhelming as the artist intended.

[*]I want hidden tracks to be present.

[*]Sometimes a music CD comes with multimedia content on a separate track. Just doing an ISO copy of the CD is thus [insufficient](http://en.wikipedia.org/wiki/ISO_image). However, I would like to back up this multimedia information as well.
[/list]

What comes closest to what I desire is what is described in [this 6 years old thread](http://ubuntuforums.org/showthread.php?t=164119). However, in his approach, benbruscella's reproduction of a digitized CD did not yield a CD which was identical to the original. Is this impossible? Will each read of a CD be different for mechanical reasons?

Thanks,
Willard.

---

### Post by sidzen on 2012-02-26
Check this [link to CDDA]("http://freecode.com/projects/burncdda") out.  See if you like it.  It's easy and configurable.

---

### Post by boydrice on 2012-02-26
I rip all my music into FLAC and mp3 using [abcde]("http://www.andrews-corner.org/abcde.html") might be an option for you.

---

### Post by nothingspecial on 2012-02-27
*Thread moved to **Multimedia & Video**.*

---

### Post by andrew.46 on 2012-02-27
If you experiment with abcde, as suggested by bodyrice, you will see that abcde has an option to rip the entire cd as a single track. This would cover some of your requirements?

---

### Post by Willard on 2012-02-27
> **sidzen said:**
> Check this [link to CDDA]("http://freecode.com/projects/burncdda") out.  See if you like it.  It's easy and configurable.
I'll check it out.

> **boydrice said:**
> I rip all my music into FLAC and mp3 using [abcde]("http://www.andrews-corner.org/abcde.html") might be an option for you.
I started ripping my library once, one track on each CD into its own FLAC file, using this approach (abcde is an incredibly simple tool), and stopped when I realized I was losing CD structure information this way (my points 1 through 5).

> **andrew.46 said:**
> If you experiment with abcde, as suggested by bodyrice, you will see that abcde has an option to rip the entire cd as a single track. This would cover some of your requirements?
Ah; and abcde also has the feature of extracting a CUE sheet. I'll play with this.

So, FLAC + CUE seems to be the best way to go.

Do you know of music players (preferably headless ones) which can play specific tracks inside a whole-CD-as-one-FLAC file with help of the corresponding CUE file, or could I need to have one-{FLAC,OGG,MP3}-per-track alongside my backup?

---

### Post by shantiq on 2012-02-28
Audacious qmmp and xmms all play from cue



also nvlc from commandline   [ATTACH]213394[/ATTACH]   cd to folder and enter

```
nvlc *.cue
```


[**XMMS **]("http://ubuntuforums.org/showthread.php?t=1525072")  is the most rational with cue as it has cueinfo which lets you stack many thus and pick your track[s] from the cueinfo with up and down arrow you see there


[[IMG]http://img196.imageshack.us/img196/5079/xmmswithcueinfo.th.png[/IMG]](http://img196.imageshack.us/img196/5079/xmmswithcueinfo.png)



as regards ripping i would suggest [pacpl or rubyripper]("http://ubuntuforums.org/showpost.php?p=10292500&postcount=5")    rubyripper does cue pacpl does not but is fast


also here info on [automatic ripping]("http://ubuntuforums.org/showpost.php?p=10651024&postcount=2")

---

### Post by shantiq on 2012-02-28
just worked out a nice way to play all cue file in nvlc   [looks good in Guake]



[CENTER][ATTACH]213421[/ATTACH][/CENTER]

> for i in */
do
  cd "$i"
nvlc *.cue
  cd ..
done     save as nvlc.sh   and make executable and save in Music


```
cd Music
```    [assuming all your music folders containing cues are in Music   if not change obviously]

enter   ```
./nvlc.sh
```     it will open and play your first cuefile


CTRL +C   takes you to the next cuefile
n and p take you to next and previous track in current cuefile
SHIFT b lets you navigate all your folders on your computer
h   TO SEE ALL OPTIONS
c   to go black and white

---

