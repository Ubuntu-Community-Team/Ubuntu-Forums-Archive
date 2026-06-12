---
title: "Japanese Subtitles Don't Display"
date: 2012-04-09
forum: Multimedia Software
---

### Post by Mr. Matt on 2012-04-09
When I try to watch videos with Japanese subtitles, they just display as boxes.  This happens in VLC, Gnome Media Player and online streaming Flash video.  I've installed Japanese language support.  I can see Japanese properly on everything else - web pages, text files, etc.  It is only video subtitles that doesn't display.  How can I fix this?  Thanks

---

### Post by Mr. Matt on 2012-04-18
Bump.  Any ideas?

---

### Post by giogovick on 2012-08-25
wow! I have the same problem, I find nothing on the web about this :'(

Have you solved this problem?

---

### Post by SeijiSensei on 2012-08-25
Japanese characters are represented by a variety of different character sets, UTF-8 and SHIFT-JIS being the most common.

I suggest you install SMPlayer (sudo apt-get install smplayer) and take a look at the character set choices under Options > Preferences > Subtitles.  The default is UTF-8.  Try SHIFT-JIS instead.

---

### Post by giogovick on 2012-08-25
How I install these character sets? I can't find them in "ubuntu software manager"

however I have this problem only in flash videos. Kanji, hiragana and katakana are displayed in normal web page.

I'm doing some japanese exercises on Livemocha.com. These exercises are done in flash and in these video every words are boxes.

---

### Post by SeijiSensei on 2012-08-25
Flash is its own little world.  Perhaps [this](http://forums.adobe.com/message/2746540) will give you some ideas.  It sounds like you can install the Japanese version of Flash.  How to make it co-exist with the English version is a task I leave to you.  If you figure it out, please post your solution here so others can benefit as well.

---

### Post by giogovick on 2012-08-25
Well, now it works!

I've installed these packages:
ttf-ipafont-gothic
ttf-ipafont-mincho
ttf-ipafont
ttf-ipafont-uigothic
ttf-ipafont-jisx0208
ack
libsuikyo-ruby1.8
suikyo-table

I don't know which of them solved the problem, but now it works! :)

---

### Post by 700 on 2013-01-09
giogovick:

These packages are not working for:
- Ubuntu 11.10 / 64bit
- Google Chrome 23.0.1271.97
- Tool: Flash 11,2,202,228

Chromium Browser 18.0.1025.168 (Build 134367 Linux) doesn't display livemocha flash content at all (while it's visible on Google Chrome browser, but without kanji fonts).

---

