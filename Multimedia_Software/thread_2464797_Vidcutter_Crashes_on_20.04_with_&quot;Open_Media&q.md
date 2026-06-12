---
title: "Vidcutter Crashes on 20.04 with &quot;Open Media&quot; or &quot;Save Media&quot;"
date: 2021-07-12
forum: Multimedia Software
---

### Post by rbt2 on 2021-07-12
I have installed Vidcutter 6.0.5.1 on my long stable Kubuntu 20.04 both through Discover and Snap on command line followed by restarts on both occasions.  Installation was without incident and the interface launched promptly. 

When clicking "open media" the application immediately crashed on several attempts.  No warning or recognition from Kubuntu. 

I could load a video file for edit from Dolphin by selecting "Open With" > "Vidcutter".  The file and app loaded appropriately and I could use the NLE tools to manipulate the file without difficulty.  When clicking "Save Media" the app again crashed without display of a save dialogue.   The file could be reopened in a similar fashion but the edits were not persevered.

This has been recently reported on Vidcutter reviews but not this forum. 

Regards,
RBT2

---

### Post by TheFu on 2021-07-13
VidCutter's project team hasn't been too responsive the last 18 months.  He did add support for EDL files when I asked about it, which was awesome, but the tool stopped even loading on my systems about 18 months ago.  Snap dependency issues.

Posting here won't help.  Only the vidcutter project team can fix their program and their snap package.  The source python is available on github last time I checked. Feel free to fork it and fix any issues.  If it was Perl, I'd have done that already.  In the end, I decided to use mplayer's EDL marking method and a little perl script to generate an **mkvmerge** cut command based on the mplayer's EDL creation.  This avoids re-encoding the video, but cuts only happen at keyframes.  

If I want to cut with frame-level accuracy, then **shotcut** is the tool, followed by **handbrake** to transcode much more efficiently.  A 200MB shotcut clip often becomes less than 50MB post-handbrake transcode.

Here's my edl creation script:
$ more ~/bin/edl-mplayer 
```
#!/bin/bash

IN="$1"
EDLFILE="${IN%.*}".edl
mplayer -osdlevel 3  -edlout "$EDLFILE" "$IN" 

echo "Play using:
mplayer -osdlevel 3  -edl "$EDLFILE" "$IN"

vcp-2-mkvmerge.pl "$EDLFILE"
"
```
Use the 'i' key to mark keep points (both leading and trailing). That creates an EDL file which can be played using the output mplayer command.  The vcp-2-mkvmerge.pl file has some issues. The main purpose is to convert the EDL SSS.sssss timestamps into hh:mm:ss.ssss timestamps that mkvmerge requires and to generate the mkvmerge command to be run.  It isn't very finished, but converting between 12342.523004 seconds and whatever that works out to be in hh:mm:ss.ssssss is something perl handles easily.

---

### Post by rbt2 on 2021-07-13
Thanks so much for the insight into the Vidcutter culture.  I thought with a recent release they would be all over an issue especially for Ubuntu distros.   I am pretty facile in KadenLive but quickly trimming short clips without re transcodeing was appealing. 

I was eyeing shotcut as my next option but again wanted to avoid transcoding.  I have heard of handbrake but have never tried since KdenLive seemed to do the job and my DIY built system runs extremely cool even after 12 hours of continuous transcoding.  But that is my biggest objection KadenLive, hours grinding away through a 1 hour video.

I had read your mplayer script solution somewhere, very impressive, but probably beyond my skill level, although I will try it since that's how I have grown with Linux.  That and an endless list of break-fix issues I have worked through over many years playing the role of both breaker and fixer. 

I will drop a post to the Vidcutter team and look forward to giving Shotcut and handbrake a try.

Thanks again

---

### Post by TheFu on 2021-07-13
All the fancy video GUI tools transcode.  That's just a fact.
The way to avoid that is by using tools which provide control over trancoding.  mkvmerge will not transcode anything.

With a little editing, you can manually control edits.
$ more split-mkv
```
#!/bin/bash
IN="$1"
ROOT=${IN/%.*/}

# ensure the output file doesn't exist already
if [[ ! -f "$ROOT.mkv" ]] ; then
  mkvmerge -o "$ROOT.mkv" \
    --split parts:-3:05.0,+4:09.0-6:16.0,+8:20.0-09:10.0,+42:13.0- \
    "$IN"
else
  echo ERROR: Outfile file exists: "$ROOT.mkv"
fi

```

Run it as **split-mkv some-video-file.mpg**  The video needs an extension, but it doesn't matter what that extension is, provided it isn't ".mkv". There are ways to ensure the output is always unique - perhaps inserting the PID number after the "ROOT" part?  The output file will always be an MKV, but the video and audio inside that container can be anything you like.  mkvmerge is crazy flexible at holding stuff.  Put video, audio, multiple tracks, multiple subtitles, a text file with metadata, almost anything.  In my testing of about 10 different video editors, only mkvmerge correctly dealt with edits of multiple audio tracks AND multiple caption files (ASS or SRT).  Every other editor would only make the block cuts for the audio and video. They completely ignored caption and sub files in the cuts.

Just modify the block times as you like. May want to put each block onto a separate line for readability and easy edits later.

So, now that you see the typical mkvmerge command, it is easier to understand that getting the times for blocks we want to keep (or remove) into the correct format is all that remains.  The output from 1 small script can feed the input to the next one. That's called using a filter and it is how all Unix pipes work.  It is extremely common.

---

