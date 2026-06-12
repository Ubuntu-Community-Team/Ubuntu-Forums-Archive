---
title: "How to set mediainfo output to a different language?"
date: 2014-05-05
forum: Multimedia Software
---

### Post by shantiq on 2014-05-05
i wish to output the info output of a video to a language other than ENG

How do i do this?


I found this [here]("https://mediaarea.net/en/MediaInfo/Support/SDK/More_Info#Format")


which tells me

> Set the language of the library

The library is by default set in English.
You can change the language with a language string.
MediaInfo::Options("Language", "**LANGUAGE_STRING**")
**LANGUAGE_STRING** is CSV-like string :
Internal name1;translation1
Internal name2;translation2



but i do not understand the syntax;   how to do this

i do not want the language permanently changed   just for the one-time output

Any of you done this before or understand the syntax?    thanx   shan

---

