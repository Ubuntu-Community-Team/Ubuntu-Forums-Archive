---
title: "Rhythmbox + EasyTAG = Very strange tag error"
date: 2009-08-20
forum: Multimedia Software
---

### Post by 3pleT on 2009-08-20
OK, this isn't very important, but it's been puzzling me for too long.

Whenever I tag the genre as "Psychedelic Rock" in EasyTAG (ID3V2.3 or 4), Rhythmbox shows it as "Psychadelic Rock" (with an A). Then I tried tagging it in Rhythmbox and it changed back to Psychedelic. I tried tagging the files in VLC (which read them right to begin with) and it worked; Rhythmbox reads them right.

However, I'm still wondering why the combination of Rhythmbox (maybe even GStreamer) and EasyTAG corrupts the tags in such a strange way and if there is a way to fix it, so I'm asking for any kind of help: ideas, links, whatever.

I'm using Jaunty, with the latest version of both EasyTAG and Rhythmbox.


PS. I only had this problem with "Psychedelic Rock". "Psychedelic Soul", "Psychedelic Pop" and "Psychedelic Trance" are all displayed normally.

---

### Post by infinite monkey machine on 2011-05-01
I realize this thread is fairly ancient, but the issue remains unchanged and I encountered it as well.

The genre field of ID3 tags once had an integer value that corresponded to one of a list of predefined genres, one of which was "Psychedelic Rock" (I believe another was "Psychadelic"). Nowadays, ID3 tags use a string value for the genre.

My hunch is that, when confronted with one of the built-in genres, EasyTAG writes the genre code instead of a string. Then, Rhythmbox might interpret this value differently, such as by spelling it differently. When you wrote the tags in VLC, it simply treated the genre as a string and so it showed up in Rhythmbox as expected.

I find this behavior pretty annoying, because my music shows up in Rhythmbox under two different genres, "Psychedelic Rock" and "Psychadelic Rock". Although Rhythmbox is partially at fault for the non-standard spelling, the issue is mainly the result of counter-intuitive behavior on the part of EasyTAG.

---

