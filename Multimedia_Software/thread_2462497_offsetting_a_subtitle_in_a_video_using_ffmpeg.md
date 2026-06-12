---
title: "offsetting a subtitle in a video using ffmpeg"
date: 2021-05-22
forum: Multimedia Software
---

### Post by shantiq on 2021-05-22
been reading around and finding no joy thus far
i do not suppose it is all that difficult once you know as most things

I have a video in mp4 in German I have an ENG srt  1.mp4 1.srt they are separate files

I want to mux them with the srt as default but not burnt-in and export to an mkv

MY specific request here is to offset the sub by -32000 ms

Tried a few things not as yet got it this is the best i have found but it does not do it maybe the -c copy not sure maybe the way the timing is written here anyway the syntax is off

```
ffmpeg -i 1.mp4 -itsoffset 0.32 -i 1.srt -c copy  1.mkv
```


 EDIT

a bit of [further study]("https://linux.die.net/man/1/ffmpeg") yielded the answer:  [CTRL-F enter offset]

```
ffmpeg -i 1.mp4 -itsoffset -00:00:32 -i  1.srt -map 0 -map 1  -c:v copy output.mkv
```

[SIZE=1][I]obviously use 00:00:00 and not -00:00:00 if you want to offset the other way 
NB the offset applies to files which follow so to make sure the order is respected
[/I][/SIZE]


will mark as solved

---

### Post by shantiq on 2021-05-22
I have one more question here

I realize the video has the srt in the correct place but it is a default sub not burnt-in and i wish for for it to be burnt-in
How can i combine the offset and the burnt-in option? (-vf subtitles=1.srt)  they seem to antagonize each other

---

### Post by SeijiSensei on 2021-05-22
Perhaps you can edit the SRT file with a tool like [https://subtitletools.com/subtitle-sync-shifter](https://subtitletools.com/subtitle-sync-shifter). This changes all the timestamps in the SRT file to include a fixed offset. Then you could mux the edited SRT file with the video and not need to use itsoffset.

---

### Post by shantiq on 2021-05-22
> **SeijiSensei said:**
> [https://subtitletools.com/subtitle-sync-shifter](https://subtitletools.com/subtitle-sync-shifter)

thank you Seiji feels like cheating ;) but saves a lot of time
ACE TIP!

---

### Post by TheFu on 2021-05-22
**mkvmerge** can do this too - or the GUI version - **mkvtoolnix-gui**.  Great when you want to shift video, audio, or subtitles and know the offsets already.
If you don't know, then there are a number of subtitle (really caption) tools. It gets more complex if the frame rates cause misalignment for the subtitles, getting worse and worse through the entire video.

The great thing about mkv files is that we can toggle a forced-on subtitle for a specific language, but still have 10 other languages supported which can be swapped in through the player's GUI.  I'm not a fan of burning captions into the video, but I've also gone out of my way to ensure all my playback devices can handle both internal and external SRT files.

---

### Post by shantiq on 2021-05-23
> **TheFu said:**
> **mkvmerge**

Thank you TheFu had already started horsing around a bit with mkvmerge also with HandBrakeCLI to find that HandBrakeCLI did not like the concept of external srt to burn in unless i messed up 
Handbrake GUI worked but it stops offset at -30000 or rounds it up so no good to me here [needed -32000]....
With mkvextract/mkvmerge  I had all the files separated and then reassembled but the offset was not happening for me

Anyway then [COLOR=#000000]Seijisensei offered his celeritous escape/shortcut and i went for that [/COLOR];)
[COLOR=#000000]
[/COLOR]PS : I do not either usually burn but this was for Youtube which the way I understand it only accepts burnt-in or separate with the option to move EACH line but not offset the entire file timings or maybe i missed that.

PS2: Would love to know how mkvmerge can shift ALL timestamps in one go as cannot see it in the manual; if anyone knows and has the time to explain; but no hurry as task i wanted was done
Will have a play with GUI (hmm gave me no joy got a file produced but srt was all in the wrong place not sure what happened)

Thanx to all for great input

---

### Post by TheFu on 2021-05-23
**subtitleeditor** is another option.  I've used it when I was desperate.  From time to time, I've written a little perl program that used the "Subtitles" module to have complete control over the times. [https://metacpan.org/pod/Subtitles](https://metacpan.org/pod/Subtitles)  The problem I've had is that it doesn't support .ass captions.  That isn't a joke. It is a real type of caption format.

---

### Post by SeijiSensei on 2021-05-23
> **shantiq said:**
> thank you Seiji feels like cheating ;) but saves a lot of time
ACE TIP!
You're welcome. I've found there's usually some way to solve most problems like these. Just takes a bit of Googling.

---

