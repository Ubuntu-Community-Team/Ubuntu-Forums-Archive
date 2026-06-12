---
title: "Play video encoded with surround sound to stereo TV"
date: 2024-06-06
forum: Multimedia Software
---

### Post by lloyd61 on 2024-06-06
Hello,

I am wanting to play my home collection of movies, which are surround sound versions, in our caravan on a TV which only has stereo.

The issue is that I am finding that the voice channel is very weak and the the surround audio is very loud. We are constantly changing the volume up and down.

My laptop, which I am playing from, has Ubuntu operating system.

Is there a particular media player which will convert surround sound to stereo on the fly, or do I need to recode all the movies to just stereo?

Thank you

---

### Post by TheFu on 2024-06-06
Check the TV for audio controls that handle the issue.  If that doesn't work, re-encoding just the audio isn't hard and should be nearly as fast as copying the file since you wouldn't touch the video or captions or subtitles.  It can be automated with ffmpeg.

Something like 
```
#!/bin/bash

for filename in "$@"; do
   ROOT="${filename/%.mkv/}"

   # Create an 2ch Ogg/vorbis file.
    ffmpeg -i "${filename}"  -vn -codec:a libvorbis -ac 2 -qscale:a 6 -vn "${ROOT}.ogg"

   # Mux the original file and the newly created Stereo ogg file into a new mkv
    mkvmerge -o "${ROOT}-ogg.mkv" "$filename" "${ROOT}.ogg"

   # Remove the temporary ogg file
    rm "${ROOT}.ogg"
done

```

Should copy the existing video, all audio, subtitles, captions and add a vorbis audio track. You make change the extension in the "ROOT=" like, if you like, but it is safe to run without it, just the other filenames will have any non-mkv extension included, which can be easily renamed later.

Took about 25 seconds to create an ogg file from a 82 minute AC3 TV recording. Then add 14 seconds to copy and mux into a new file.
```
4.7G    Frontline-Netanyahu,_America_&_the_Road_to_War_in_Gaza-h.mkv
4.8G    Frontline-Netanyahu,_America_&_the_Road_to_War_in_Gaza-h-ogg.mkv
```
And the resulting MKV container has:
```
===[ Frontline-Netanyahu,_America_&_the_Road_to_War_in_Gaza-h-ogg.mkv ]===

| + Duration: 01:22:21.638000000
|  + Track number: 1 (track ID for mkvmerge & mkvextract: 0)
|  + Codec ID: V_MPEG2
|  + Track number: 2 (track ID for mkvmerge & mkvextract: 1)
|  + Codec ID: A_AC3
|   + Channels: 2
|  + Track number: 3 (track ID for mkvmerge & mkvextract: 2)
|  + Codec ID: A_AC3
|  + Language: spa
|   + Channels: 2
|  + Track number: 4 (track ID for mkvmerge & mkvextract: 3)
|  + Codec ID: A_AC3
|  + Language: fre
|   + Channels: 2
|  + Track number: 5 (track ID for mkvmerge & mkvextract: 4)
|  + Codec ID: S_TEXT/UTF8
[B]|  + Track number: 6 (track ID for mkvmerge & mkvextract: 5)
|  + Codec ID: A_VORBIS
|   + Channels: 2[/B]

```
The first audio track with the highest number of channels will be selected.  MKV containers are very powerful and allow adding removing tracks (video/audio/subs/captions) very fast.  I have little use for the Spanish or French audio tracks, so using mkvtoolnix-gui to remove those would be the easiest way. It can be used to add tracks or shift any track(s) too.  The muxing takes the time to copy the files, not the time to transcode.  Fast storage is required for best results.

---

### Post by qyot27 on 2024-06-07
mpv can be configured to do it on playback:
```
[downmix]
af=lavfi="pan=stereo|FL < 0.5*FC + 0.3*FLC + 0.3*FL + 0.3*BL + 0.3*SL + 0.5*LFE | FR < 0.5*FC + 0.3*FRC + 0.3*FR + 0.3*BR + 0.3*SR + 0.5*LFE",lavfi="acompressor=10"
```
Shown above is the profile I have in my ~/.mpv/config to do exactly this, each of the floats in the pan command control the general mix level going into each of the two channels from 5.1->2, the lavfi command at the end just boosts the volume of the stereo mix afterward.

Which I can then optionally invoke like so:
```
mpv <other options> -profile downmix inputfile
```

---

