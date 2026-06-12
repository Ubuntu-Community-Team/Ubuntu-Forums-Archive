---
title: "Bin and Cue files"
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by rbgCODE on 2006-06-17
I have downloaded some video bin and cue files.  Now in windows I could use iso buster and it would output the mpg files.  How would I be able to do this with linux?  I know I can just play the bin file with VLC but it is very choppy.

---

### Post by glotz on 2006-06-17
Install **bchunk** to translate the non-standard image to .iso. Then use the archive manager to open the .iso.

---

### Post by rbgCODE on 2006-06-17
I did install bchunk and when I run
bchunk -r file.bin file.cue myISO

it makes 2 isos one 700MB one 900k and neither of them can be opened or mounted

---

### Post by glotz on 2006-06-17
bchunk works, at least for me. Try again. **bchunk --help** will probably be of use.

---

### Post by jolene on 2006-08-22
Newbie here! Please could somebody explain what this means:

```
Usage: bchunk [-v] [-r] [-p (PSX)] [-w (wav)] [-s (swabaudio)]
         <image.bin> <image.cue> <basename>
Example: bchunk foo.bin foo.cue foo
  -v  Verbose mode
  -r  Raw mode for MODE2/2352: write all 2352 bytes from offset 0 (VCD/MPEG)
  -p  PSX mode for MODE2/2352: write 2336 bytes from offset 24
      (default MODE2/2352 mode writes 2048 bytes from offset 24)
  -w  Output audio files in WAV format
  -s  swabaudio: swap byte order in audio tracks

```

I want to convert .bin and .cue film downloads into a format I can play (.mpg ideal), but the above just confuses me in so many ways. Thanks for your patience!

J

---

### Post by whatever on 2006-08-22
with mplayer you can play the .bin file directly, no need to extract the mpg.

---

### Post by bluenova on 2006-08-22
This may be of interest:
[http://www.ubuntuforums.org/showthread.php?t=149963](http://www.ubuntuforums.org/showthread.php?t=149963)

---

