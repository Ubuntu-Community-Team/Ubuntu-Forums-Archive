---
title: "Splitting WavPack files when the .cue file and .wv file have different names?"
date: 2011-04-24
forum: Multimedia Software
---

### Post by pedrogent on 2011-04-24
If a directory contains an album encoded as one large .wv file and a .cue file, splitting the entire album into individual .flac tracks is a simple task:

```
$ cuebreakpoints foo.cue | shnsplit -o flac foo.wv
```

What I'd like to know is how to split a file where the names don't match up, e.g.: 'foobar.wv' and 'foo.cue'. If I attempt this I get this error message:

```
shnsplit: warning: none of the builtin format modules handle input file: [foobar.wv]
shnsplit: error: cannot continue due to error(s) shown above
```

Do I need to alter the .cue file? Because simply renaming 'foobar.wv' to 'foo.wv' prior to splitting doesn't seem to work for me. Or is there something wrong with the wavpack package?

---

### Post by satanselbow on 2011-04-25
The actual **filename** of the cue file should be irrelevant and does not have to match the flac / wvpack / ape file it references.

What **is** important is that the cue file is looking for the correct file internally - it is quite unusual to have a cue/wvpack pair with different names and sounds that  one or other has been (accidentally) renamed in error at some point.

 If you open the cue file in a text editor you can check which file it is looking for ;) It is not unknown for a cue file to incorrectly looking for the wrong filetype (ie WAV when you have a single FLAC) so check that the cue is infact matched to you wvpack and not the original source WAVE.

Reading your original post again you may also be missing the wvpack codecs to read the file in the 1st place ;) and may need to install **wavpack** or **gstreamer** via synaptic 

Can you play the wvpack file in your media player?

---

### Post by pedrogent on 2011-04-25
> **satanselbow said:**
> If you open the cue file in a text editor you can check which file it is looking for ;) It is not unknown for a cue file to incorrectly looking for the wrong filetype (ie WAV when you have a single FLAC) so check that the cue is infact matched to you wvpack and not the original source WAVE.

Reading your original post again you may also be missing the wvpack codecs to read the file in the 1st place ;) and may need to install **wavpack** or **gstreamer** via synaptic 

Can you play the wvpack file in your media player?

Hey satanselbow, thanks for the reply.

I've matched up a few of these .cue/.wv combos that aren't working. The .cue files are pointing to the correct files in each case.

wavpack is installed and is the latest version.

I can play the .wv files in various media players.

In short: I have no idea what's going on. Luckily .wv files make up a tiny proportion of my lossless music collection.

---

### Post by shantiq on 2011-04-26
hi there you could use[ **gcue2tracks**]("http://ubuntuforums.org/attachment.php?attachmentid=189776&d=1303558349") for this task 

**nb: **Seems to work better if i split the wv to flacs on system

from post [**here**]("http://ubuntuforums.org/showthread.php?t=1662709")

---

### Post by pedrogent on 2011-04-26
shantiq: Many thanks for the suggestion. I'll give that script a go a little later tonight and report back.

Cheers.

:)

---

### Post by pedrogent on 2011-04-27
I didn't try the script as I'm having a bit of luck, for whatever reason, with decompressing the .wv to .wav and then altering the .cue file accordingly.

Not ideal but it's working so far.

---

### Post by shantiq on 2011-04-28
fine if you are happy that way

looked at your original post again and had a think and tested it

this is the line of code i have used from [**here**]("http://aidanjm.wordpress.com/2007/02/15/split-lossless-audio-ape-flac-wv-wav-by-cue-file/")

Place wv file and cuefile in a folder and cd to it

then

```
cuebreakpoints *.cue | shnsplit -o wv  *.wv

```

First make sure you open the cuesheet and that the name of the music file is the same in the cuesheet 
the name of the cuesheet does not matter and can be **different** from the name of the music file but the name of the music file [COLOR="Red"]written[/COLOR] in the cuesheet must match

in my case here my music file is **Willits + Sakamoto - Ocean Fire.wv**

```
REM DATE 2008
REM DISCID 5A0D2407
REM COMMENT ExactAudioCopy v0.99pb4
PERFORMER "Willits + Sakamoto"
TITLE "Ocean Fire"
[COLOR="Red"]FILE "Willits + Sakamoto - Ocean Fire.wv" WAVE
[/COLOR]  TRACK 01 AUDIO
    TITLE "Toward Water"
    INDEX 01 00:00:00
  TRACK 02 AUDIO
    TITLE "Umi"
    INDEX 01 08:11:39
  TRACK 03 AUDIO
    TITLE "Sea Plains"
    INDEX 01 11:07:53
  TRACK 04 AUDIO
    TITLE "Sentience"
    INDEX 01 20:10:66
  TRACK 05 AUDIO
    TITLE "Chi-Yu"
    INDEX 01 28:28:22
  TRACK 06 AUDIO
    TITLE "Cold Heat"
    INDEX 01 36:57:74
  TRACK 07 AUDIO
    TITLE "Ocean Sky Remains"
    INDEX 01 44:44:17
```


**And it** should go through fine  (no tags sadly)

---

### Post by pedrogent on 2011-04-28
> **shantiq said:**
> First make sure you open the cuesheet and that the name of the music file is the same in the cuesheet 
the name of the cuesheet does not matter and can be **different** from the name of the music file but the name of the music file [COLOR="Red"]written[/COLOR] in the cuesheet must match...

I think you've hit on the problem precisely. And I think I was having success by decompressing to .wav first purely because I then altered the .cue file to expect a .wav (the line you've marked in red). In this way I made sure the two agreed with each other.

Thanks a lot for your help with this **shantiq**. Much appreciated.

:)

---

