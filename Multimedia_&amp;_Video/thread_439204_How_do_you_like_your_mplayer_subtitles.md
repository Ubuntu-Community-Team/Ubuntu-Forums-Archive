---
title: "How do you like your mplayer subtitles?"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by fearpi on 2007-05-10
When I use Windows, I watch videos using Media Player Classic and ffmpeg. So far, I have found nothing on any platform that matches the quality of that combination, especially when it comes to subtitles. mplayer in particular falls short on the visual quality of subtitles. The fonts don't quite look like they should, they are often proportioned incorrectly on videos that are rendered in a different aspect ratio than they actually are, and the surrounding colors seem to sort of bleed into the edges.

 I want to get mplayer's subtitles looking like they do in mplayer, if possible. If you like your subs, post your config and if possible, a screenshot.

---

### Post by fearpi on 2007-05-10
Here's a comparison - using the *same font* - MPC on the left, mplayer on the right [see next post].

---

### Post by fearpi on 2007-05-26
Screenshots:

---

### Post by aidanr on 2007-05-26
haven't played around with that much but mplayer has tonnes of subtitle options for you to play around with
[http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html#OSD/SUBTITLE OPTIONS](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html#OSD/SUBTITLE OPTIONS)

---

### Post by fearpi on 2007-05-26
Thanks, but I've read the manpages and played around with options. I'm interested in more specific setups and results.

---

### Post by taisao on 2007-09-16
Are you still using mplayer. How is yours subtitles setup now?

---

### Post by shirilover on 2007-09-16
Are you using a recent build of mplayer?
Does the file in question use soft-subs with styling?
Are you using the (-*** -embeddedfonts -correct-pts) switches?
Keep in mind if you enable ssa/*** subtitle rendering, libass will also render srt subtitles which may make them appear very different.

---

### Post by fearpi on 2007-09-23
[QUOTE=taisao]Are you still using mplayer. How is yours subtitles setup now?[/QUOTE]

Yes I am. My subtitles are set up as following:

```
fontconfig = 1
slang = 'en'
font = 'Zurich Cn BT'
ffactor = 4
subpos = 95
subfont-outline = 2
subfont-text-scale = 4
```

I think this is all the same as when I took the above screenshot, except for subfont-outline.

[QUOTE=shirilover]Are you using a recent build of mplayer?
Does the file in question use soft-subs with styling?
Are you using the (-*** -embeddedfonts -correct-pts) switches?[/QUOTE]

Yes; yes but no styling is specified; no, but I do find that I have a little improvement in quality with libass. What does -correct-pts do? I can't find any mention of it in the manpage.

---

### Post by shirilover on 2007-09-24
From the MPlayer man page:
```

&#8722;correct-pts (experimental)
	

Switches MPlayer to an experimental mode where timestamps for video frames are calculated differently and video filters which add new frames or modify timestamps of existing ones are supported. The more accurate timestamps can be visible for example when playing subtitles timed to scene changes with the &#8722;ass option. Without &#8722;correct-pts the subtitle timing will typically be off by some frames. This option does not work correctly with some demuxers and codecs.

```

By subtitles with styling, I mean those normally found in matroska containers which are usually Advanced SubStation Alpha(***), which contains various aspects of subtitle placement, font-family, font-weight, font-style, outlining and shadows.

Example:
```

[V4+ Styles]

Format: Name, Fontname, Fontsize, PrimaryColour, SecondaryColour, OutlineColour, BackColour, Bold, Italic, Underline, StrikeOut, ScaleX, ScaleY, Spacing, Angle, BorderStyle, Outline, Shadow, Alignment, MarginL, MarginR, MarginV, Encoding

Style: ichigo_mashimaro_opening_jap,Hey Gorgeous,29,&H00BB8577,&H0000FFFF,&H00FFFFFF,&H32FFFFFF,0,0,0,0,70,100,2,0,1,2.6,0.5,8,12,12,15,1

Style: ichigo_mashimaro_opening_eng,Hey Gorgeous,29,&H007670C7,&H0000FFFF,&H00FFFFFF,&H32FFFFFF,0,0,0,0,70,100,2,0,1,2.6,0.5,8,12,12,15,1

Style: ichigo_mashimaro_standard,Freestyle,38,&H00FFFFFF,&H0000FFFF,&H00714F4A,&H00714F4A,-1,0,0,0,90,100,0,0,1,2.1,0.5,2,12,12,15,1

Style: ichigo_mashimaro_alternative,Freestyle,38,&H00FFFFFF,&H0000FFFF,&H00815954,&H00815954,-1,0,0,0,90,100,0,0,1,2.1,0.5,2,12,12,15,1

Style: ichigo_mashimaro_fo,VAGRounded LT Light,40,&H00FFFFFF,&H0000FFFF,&H00935E92,&H00935E92,0,0,0,0,100,100,0,0,1,1.8,1,2,12,12,15,1

Style: ichigo_mashimaro_ending_jap,Book Antiqua,36,&H00EBEBF6,&H0000FFFF,&H005D5DBC,&H325D5DBC,0,0,0,0,87,100,2,0,1,2.1,0.5,7,12,12,12,1

Style: ichigo_mashimaro_ending_eng,Book Antiqua,36,&H00F6F2EF,&H0000FFFF,&H00A57354,&H32BB927A,0,0,0,0,87,100,2,0,1,2.1,0.5,1,12,12,12,1

```

---

### Post by fearpi on 2007-11-27
Just to follow up, passing

```
-vo gl
```

in conjunction with libass subtitles and its various options makes subs look great. The key here is that using the gl filter scales the video up first, and *then* renders subtitles, so that they are at the screen resolution, rather than the video resolution and scaled up.

---

