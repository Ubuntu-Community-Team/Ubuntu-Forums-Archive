---
title: "a code question regarding music file extensions"
date: 2012-06-18
forum: Multimedia Software
---

### Post by shantiq on 2012-06-18
if one wishes to contract this


```
nvlc */./*flac *ape *wv *shn *aac *m4a *mp3
```


so as to say all music but **music files only** is there a way to do that to simplify the line; so as to not have to write every single xtension

---

### Post by nothingspecial on 2012-06-18
Wht not make an alias

```
alias tunes='nvlc */./*flac *ape *wv *shn *aac *m4a *mp3'
```

put that at the end of ~/.bashrc then source bashrc

```
. ~/.bashrc
```

Now you just have to type ```
tunes
```

of course, it doesn't have to be "tunes" you can call it watermelon if you like

```
alias watermelon='nvlc */./*flac *ape *wv *shn *aac *m4a *mp3'
```

---

### Post by MG&amp;TL on 2012-06-18
I don't think you can do that directly, but you could cheat:

```
export MUSIC=*flac *ape...
nvlc $MUSIC
```I don't know if this reduces typing in your situation?

Edit: heh, nothingspecial, great minds think alike. :)

---

### Post by papibe on 2012-06-18
Hi shantiq.

It is very difficult to keep track of all music extensions. For example, you can put that command on a script, but if you get some ogg files, they will be ignored.

I don't always use command line music players, but when I do (that sounded familiar :) ) I load whole directories. It has the undesired side effect off also loading some text files, and pics, but it is so much easier.

For example:
```
nvlc Music
```
or
```
nvlc /path/to/musiclib1 /path/to/musiclib2 /path/to/musiclib3
```

Just some thoughts.
Regards.

---

### Post by shantiq on 2012-06-18
ok guys  thanx  > It has the undesired side effect off also loading some text files, and pics, but it is so much easier.


is my reason for asking:KS   i want to filter out all else that is NOT a music file

and was wondering whether there is a "generic" piece of code that would "know" that

---

### Post by shantiq on 2012-06-18
> **nothingspecial said:**
> Wht not make an alias

```
alias tunes='nvlc */./*flac *ape *wv *shn *aac *m4a *mp3'
```

put that at the end of ~/.bashrc then source bashrc

```
. ~/.bashrc
```

Now you just have to type ```
tunes
```

of course, it doesn't have to be "tunes" you can call it watermelon if you like

```
alias watermelon='nvlc */./*flac *ape *wv *shn *aac *m4a *mp3'
```



WOW  Nothingspecial  that is a good one    never knew thanx a lot:KS:KS



works a dream


just wrote


> alias musica='cd  ~/Music &&   nvlc */./*flac *ape *wv *shn *aac *m4a *mp3  *cue'





now the word     "musica"      is my **quickest **TERMINAL player ever   simply click r once started for random


one key to open guake/2 keys mu /[**upward arrow**]("http://ubuntuforums.org/showpost.php?p=11539401&postcount=31")/ musica appears/return/hit r  for random        get on with things    nice one:]

added bonus   **also easy way to have hotkeys to pause/play   and go to next track  **  can be set in vlc **global** preferences and will work with nvlc too  [thanx Mc4man for info on this]


Makes an invisible self-designed radio station..

====================

---

### Post by LemursDontExist on 2012-06-18
For what it's worth, you can use the file command to check the mime-type of a given file.

Specifically

```
file -b --mime-type filename
``` 

should output audio/mpeg, or audio/flac or something like that for audio files.

In principle you can then construct a list of files that have an audio mime-type in the folder and pass that to nvlc.  If you're looking to write a script, this would let you get all relevant audio formats without having to list them, though the end result is probably more total code than the solutions others have proposed!

---

### Post by David Andersson on 2012-06-18
1) What does syntax ***/./*** mean? Is it vlc specific or a new bash?

2) List audio files in current dir based on file name extension
```
shopt -s nocaseglob nullglob
ls -d *.{mp3,wav,riff,wma,au,ogg,flac,m4a,aac}
```

Add more extensions as you wish. The nocaseglob option makes bash ignore case in file name expansion. That is, it will match both mp3 and MP3. The nullglob option makes bash ignore file name patterns that does not match anything. That is, if there is no *.flac files there won't be an error "no such file *.flac".

3) List audio files in current dir by identifying their headers
```
file -Lr0 --mime-type * | awk -F\0 '$2~"audio/"{print $1}'
```
No matter if an mp3 file is called "Madonna.mp3", "Madonna.musicfile" or just "Madonna", if will be recognized as an audio file. This does not work for ogg files.

The above can be extended to search folders recursively and the result passed to a music player.

---

### Post by papibe on 2012-06-18
This is probably beyond the OP's concern but...

The command 'file' would be great, if it covered all cases. Since it's fast enough, you could generate the music list at the moment of launching the player.

However, the problem that I have with it is that for a considerable media files it just returns:
```
application/octet-stream
```
And that could be an mp3, mkv, audio flv, video flv, etc. :(

I guess you could 'repair' those files if your music collection if not to big, but it could be a lot of work for a medium to big amount of media files.

What I've used in the past is 'mediainfo'. Here's how to [install]("http://ubuntuforums.org/showthread.php?t=1941003&highlight=mediainfo") it, and here's an example on how to make a [script]("http://ubuntuforums.org/showthread.php?t=1941386&highlight=mediainfo") with it.

The only problem with mediainfo is not practical to create the music list at the moment of launching the player. It is not fast enough since it really reads more that just the "magic bits". A method using this tool would work better if you separate the functionality of creating and updating the music list from the launch of the player.

Nevertheless, this method does not have the problem of using simple file extensions: if get new music files that were not consider on the alias or script, they won't be included on the list. For instance:
```
flv ogg f4a
```

Just a few thoughts. I hope that didn't bore anybody.
Kind Regards.

---

### Post by shantiq on 2012-06-18
----------

---

