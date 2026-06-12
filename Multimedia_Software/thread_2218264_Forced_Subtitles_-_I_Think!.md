---
title: "Forced Subtitles - I Think!"
date: 2014-04-20
forum: Multimedia Software
---

### Post by AlexHudghton on 2014-04-20
I use my Linux system as a home theatre  - over 500 films and the same in TV programs work happily through VLC.

However, there are a select few, which I now know contain solmething called 'forced subtitles' which will not play the subtitle at all. (these are subtitles that play when someone is speaking a language foreign to the principle English on the fiilm)

So far I have identified Battle of Britain, A Bridge Too Far, and X-Men First Class. Now I have many others that have subtitles and play them fine - The Way Back for example, so I guess they don't used the 'forced' option

What I cannot understand is why there is no Liunx player that will play these DVD's 'out of the box'. I'm sorry to say Windows Media Player has no trouble.

I have even ripped the DVD to disk and put the files through Handbrake following all the instructions carefully to capture the subtitles, but no; they will not display. 

I have tried VLC, mplayer, SMplayer, several different ripping tools and still no result

Has anyone any success in this area?

---

### Post by shantiq on 2014-04-20
hmmm     i would suggest take a  VOB [insert disc and drag to desktop]from one of those dvds that DO NOT play subs and run through mediainfo    [in repo]   to see which format they are in  and if forced   etc      there are so many formats for subs

if not srt    you may have  to convert them first

else    go to a search engine then find appropriate srt for the film you want      then attach with handbrake or mkvmerge or ffmpeg

PS     **and more basically**    run the film you say does not show in vlc    then toggle the V key     and see if they appear [but you probably know this]

**Subtitle formats[FONT=sans-serif][[edit]("http://en.wikipedia.org/w/index.php?title=Subtitle_(captioning)&action=edit&section=23")][/FONT]**

**For software video players[[edit]("http://en.wikipedia.org/w/index.php?title=Subtitle_(captioning)&action=edit&section=24")]**

[TABLE="class: wikitable"]
[TR]
[TH="bgcolor: #F2F2F2, align: center"]Name[/TH]
[TH="bgcolor: #F2F2F2, align: center"]Extension[/TH]
[TH="bgcolor: #F2F2F2, align: center"]Type[/TH]
[TH="bgcolor: #F2F2F2, align: center"]Text Styling[/TH]
[TH="bgcolor: #F2F2F2, align: center"]Metadata[/TH]
[TH="bgcolor: #F2F2F2, align: center"]Timings[/TH]
[TH="bgcolor: #F2F2F2, align: center"]Timing Precision[/TH]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"][AQTitle]("http://en.wikipedia.org/w/index.php?title=AQTitle&action=edit&redlink=1")[/TH]
[TD].aqt[/TD]
[TD]Text[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD]Framings[/TD]
[TD]Dependent on [Frame]("http://en.wikipedia.org/wiki/Film_frame")[/TD]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"][Gloss Subtitle]("http://en.wikipedia.org/w/index.php?title=Gloss_Subtitle&action=edit&redlink=1")[/TH]
[TD].gsub[/TD]
[TD]HTML/XML[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD]Elapsed Time[/TD]
[TD]10 Milliseconds[/TD]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"][JACOSub]("http://en.wikipedia.org/w/index.php?title=JACOSub&action=edit&redlink=1")[SUP][[12]]("http://en.wikipedia.org/wiki/Subtitle_(captioning)#cite_note-12")[/SUP][/TH]
[TD].jss[/TD]
[TD]Text w/markup[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD="class: table-no, bgcolor: #FF9999, align: center"]No[/TD]
[TD]Elapsed Time[/TD]
[TD]Dependent on frame[/TD]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"][MicroDVD]("http://en.wikipedia.org/wiki/MicroDVD")[/TH]
[TD].sub[/TD]
[TD]Text[/TD]
[TD="class: table-no, bgcolor: #FF9999, align: center"]No[/TD]
[TD="class: table-no, bgcolor: #FF9999, align: center"]No[/TD]
[TD]Framings[/TD]
[TD]Dependent on Frame[/TD]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"][MPEG-4 Timed Text]("http://en.wikipedia.org/wiki/MPEG-4_Part_17")[/TH]
[TD].ttxt (or mixed with A/V stream)[/TD]
[TD][XML]("http://en.wikipedia.org/wiki/XML")[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD="class: table-no, bgcolor: #FF9999, align: center"]No[/TD]
[TD]Elapsed Time[/TD]
[TD]1 Millisecond[/TD]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"][MPSub]("http://en.wikipedia.org/wiki/MPlayer")[/TH]
[TD].sub[/TD]
[TD]Text[/TD]
[TD="class: table-no, bgcolor: #FF9999, align: center"]No[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD]Sequential Time[/TD]
[TD]10 Milliseconds[/TD]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"][Ogg Writ]("http://en.wikipedia.org/wiki/Ogg_Writ")[/TH]
[TD]N/A (mixed with audio/video stream)[/TD]
[TD]Text[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD]Sequential Granules[/TD]
[TD]Dependent on [Bitstream]("http://en.wikipedia.org/wiki/Bitstream")[/TD]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"][Phoenix Subtitle]("http://en.wikipedia.org/w/index.php?title=Phoenix_Subtitle&action=edit&redlink=1")[/TH]
[TD].pjs[/TD]
[TD]Text[/TD]
[TD="class: table-no, bgcolor: #FF9999, align: center"]No[/TD]
[TD="class: table-no, bgcolor: #FF9999, align: center"]No[/TD]
[TD]Framings[/TD]
[TD]Dependent on Frame[/TD]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"][PowerDivX]("http://en.wikipedia.org/w/index.php?title=PowerDivX&action=edit&redlink=1")[/TH]
[TD].psb[/TD]
[TD]Text[/TD]
[TD="class: table-no, bgcolor: #FF9999, align: center"]No[/TD]
[TD="class: table-no, bgcolor: #FF9999, align: center"]No[/TD]
[TD]Elapsed Time[/TD]
[TD]1 Second[/TD]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"][RealText]("http://en.wikipedia.org/w/index.php?title=RealText&action=edit&redlink=1")[SUP][[13]]("http://en.wikipedia.org/wiki/Subtitle_(captioning)#cite_note-13")[/SUP][/TH]
[TD].rt[/TD]
[TD][HTML]("http://en.wikipedia.org/wiki/HTML")[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD="class: table-no, bgcolor: #FF9999, align: center"]No[/TD]
[TD]Elapsed Time[/TD]
[TD]10 Milliseconds[/TD]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"][SAMI]("http://en.wikipedia.org/wiki/SAMI")[/TH]
[TD].smi[/TD]
[TD]HTML[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD]Framings[/TD]
[TD]Dependent on Frame[/TD]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"]Spruce subtitle format[SUP][[14]]("http://en.wikipedia.org/wiki/Subtitle_(captioning)#cite_note-14")[/SUP][/TH]
[TD].stl[/TD]
[TD]Text[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD]Sequential Time+Frames[/TD]
[TD]Sequential Time+Frames[/TD]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"][Structured Subtitle Format]("http://en.wikipedia.org/w/index.php?title=Structured_Subtitle_Format&action=edit&redlink=1")[/TH]
[TD].ssf[/TD]
[TD]XML[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD]Elapsed Time[/TD]
[TD]1 Millisecond[/TD]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"][SubRip]("http://en.wikipedia.org/wiki/SubRip")[/TH]
[TD].srt[/TD]
[TD]Text[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD="class: table-no, bgcolor: #FF9999, align: center"]No[/TD]
[TD]Elapsed Time[/TD]
[TD]1 Millisecond[/TD]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"][(Advanced)]("http://en.wikipedia.org/wiki/Advanced_SubStation_Alpha") [SubStation Alpha]("http://en.wikipedia.org/wiki/SubStation_Alpha")[/TH]
[TD].ssa or .ass (advanced)[/TD]
[TD]Text[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD]Elapsed Time[/TD]
[TD]10 Milliseconds[/TD]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"][SubViewer]("http://en.wikipedia.org/wiki/SubViewer")[/TH]
[TD].sub[/TD]
[TD]Text[/TD]
[TD="class: table-no, bgcolor: #FF9999, align: center"]No[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD]Elapsed Time[/TD]
[TD]10 Milliseconds[/TD]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"][Universal Subtitle Format]("http://en.wikipedia.org/wiki/Universal_Subtitle_Format")[/TH]
[TD].usf[/TD]
[TD]XML[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD="class: table-yes, bgcolor: #99FF99, align: center"]Yes[/TD]
[TD]Elapsed Time[/TD]
[TD]1 Millisecond[/TD]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"][VobSub]("http://en.wikipedia.org/wiki/VSFilter")[/TH]
[TD].sub + .idx[/TD]
[TD]Image[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[TD]Elapsed Time[/TD]
[TD]1 Millisecond[/TD]
[/TR]
[TR]
[TH="bgcolor: #F2F2F2, align: center"][XSUB]("http://en.wikipedia.org/wiki/XSUB")[/TH]
[TD]N/A (embedded in [.divx]("http://en.wikipedia.org/wiki/Divx#DivX_Media_Format_.28DMF.29") container)[/TD]
[TD]Image[/TD]
[TD]N/A[/TD]
[TD]N/A[/TD]
[TD]Elapsed Time[/TD]
[TD]1 Millisecond[/TD]
[/TR]
[/TABLE]
[COLOR=#252525][FONT=sans-serif]There are still many more uncommon formats. Most of them are text-based and have the extension .txt.[/FONT][/COLOR]

---

### Post by AlexHudghton on 2014-04-21
Thanks for the excellent reply!

I took the easy option and got a file from the web, well, several until i found one that worked properly.

I also found one for Battle of Britain, but had a bit of trouble syncing with the video

Amazing what a minefield it all is - I'm thankful that my first language is English and I don't have to do too much messing around .

Thanks again

Alex

---

### Post by shantiq on 2014-04-21
:KS  yes Alex glad you cracked it    can be a right palaver

---

### Post by andrew.46 on 2014-04-22
MPlayer has an option that you could perhaps experiment with:

```

       -forcedsubsonly
              Display only forced subtitles for the DVD  subtitle  stream  se-
              lected by e.g. -slang.

```

although I admit that I have no experience with this option but I see that SMPlayer has an option for this under 'Subtitles'...

---

