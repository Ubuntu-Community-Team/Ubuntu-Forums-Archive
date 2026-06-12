---
title: "Interesting issue with goobox / FLAC"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by element42 on 2007-04-19
Hi, I've just switched to Ubuntu this week. Before I left windows I converted all my music from Apple Lossless to FLAC, which I'm also new to. In Ubuntu, I can only find one application that lets me choose the FLAC level 1-8, which is goobox. For some reason it also has a level 9 setting, but that doesn't work. Anyway, when I extract from a CD, it encodes fine into FLAC, but only the first track is 'fully' compressed, ie, tracks 2 to the last track are not as compressed as much as the first track.
This was discovered when I was trying to find out what level of compression SoundJuicer did in FLAC. For the first track, goobox at FLAC level 8 compressed it higher (smaller file size), but the other tracks were less compressed. 
I can work around this by extracting each track at a time rather than the whole CD at once. This is v. annoying though! Can anyone help me to understand this? Or alternatively, suggest a CD ripping application that will let me encode at FLAC level 8? - with instructions?!

thanks!

---

### Post by solo1181 on 2007-04-25
Grip can encode at level 8, install grip and flac.  Run Grip
1. Select config tab, then the encode tab.
2. Select Flac as the encoder
3.enter -8 in the encoder command line, and thats it example: -V -8 -o %m %w

here is a link for other flac options
[http://flac.sourceforge.net/documentation_tools_flac.html#flac_options_output_name]("http://flac.sourceforge.net/documentation_tools_flac.html#flac_options_output_name")

---

