---
title: "Can't embed subtitles to an .mpg file..."
date: 2009-01-18
forum: Multimedia Software
---

### Post by hopelessone on 2009-01-18
Hi All,

I can't do it? it's weird...

a snippet of the **movie.srt** file:
> 
1
00:01:09,320 --> 00:01:11,379
Pay attention!

2
00:01:11,522 --> 00:01:14,286
Ah, yes sir.

3
00:01:14,425 --> 00:01:20,295
Take this map to Kanemaru now

the file is **movie.mpg**

the **subtitle.xml** is:
> <subpictures> <stream> <textsub filename="dvd.srt" characterset="ISO8859-1" fontsize="18.0" font="devedesans.ttf" horizontal-alignment="center" vertical-alignment="bottom" left-margin="60" right-margin="60" top-margin="20" bottom-margin="30" subtitle-fps="29.97" movie-fps="29.97" movie-width="720" movie-height="478"/> </stream> </subpictures>

the command:
> spumux -s0 /home/some/DVD/subtitle.xml < /home/some/DVD/dvd.mpg > /home/some/DVD/dvd.mpg.temp

driving me nuts...

Command line output:
> some@some-one:~/DVD$ spumux -s0 /home/some/DVD/subtitle.xml < /home/some/DVD/dvd.mpg > /home/some/DVD/dvd.mpg.temp
DVDAuthor::spumux, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_US.UTF-8
INFO: Converting filenames to UTF-8
INFO: Detected subtitle file format: subviewer
INFO: Opened iconv descriptor. *UTF-8* *ISO8859-1*
INFO: Read 918 subtitles
INFO: Adjusted 5 subtitle(s).
INFO: Unicode font: 2976 glyphs.
INFO: Found EOF in .sub file.
INFO: 918 subtitles added, 0 subtitles skipped, stream: 32, offset: 0.23

Statistics:
- Processed 918 subtitles.
- The longest display line had 39 characters.
- The maximum number of displayed lines was 2.
- The normal display height of the font devedesans.ttf was 23.
- The bottom display height of the font devedesans.ttf was 36.
- The biggest subtitle box had 1928 bytes.
some@some-one:~/DVD$ 


There is no subtitles when i watch it...What did I do wrong...??

Thanks a bunch in advance..

---

### Post by Ingo88 on 2009-03-11
I'm having the same problem :(

Anyone who has a clue?

---

