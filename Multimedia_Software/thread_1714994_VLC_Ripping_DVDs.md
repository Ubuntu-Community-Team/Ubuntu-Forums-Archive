---
title: "VLC Ripping DVDs"
date: 2011-03-26
forum: Multimedia Software
---

### Post by DavidG24 on 2011-03-26
hi guys,

I have a massive DVD collection that I want to backup so I can play on my new Asus O!Play (bday gift). I have never ripped DVD's before in either Windoze or Ubuntu. I tried Thoggen (as it came up in a search in the Software Centre) and although it was dummy proof, it didn't allow me configure it properly (would  auto assign language/subtitles etc etc).

Anyways I was told that VLC was an easy alternative, so I installed via Software Centre, and at first it seemed rather simple

Insert DVD - Open VLC

Media --> Open Disk
give it the start position, assign the audio and subtitle etc.
The only issue for me came to when I went to the config settings for the encoding.

I was told the the H264 Encoding was great, so I chose that, but when I went to the config, I was (and am still) completely lost about how to set the video codec (i.e. Bitrate, fps, type) and audio codec.

Now I'm now worried at all about size, I don't care if the files turn out to be 3GB+ or whatever, as long as they are top quality - So my question is, can anyone tell what config I should set to get the best possible quality from the Rip? and if possible the full config settings (so that a noob like me can easily follow)

Please help me, very frustrating working in the dark here!

Thanks in Advance, and I really appreciate any help

David

---

### Post by cchhrriiss121212 on 2011-03-26
Try using handbrake. Just select the DVD and choose the high profile setting, if you want higher quality select the video tab and set the bitrate to 2500kbps or higher. There are more settings, but you don't need to know about them.

---

### Post by JohnAStebbins on 2011-03-26
> **cchhrriiss121212 said:**
> Try using handbrake. Just select the DVD and choose the high profile setting, if you want higher quality select the video tab and set the bitrate to 2500kbps or higher. There are more settings, but you don't need to know about them.

Using bitrate to control quality would be a poor choice.  Use the apply named quality control to control quality.  Just slide the slider further to the right.

Different video sources will require a different bitrate to achieve the same quality.  For example, animation requires much lower bitrates to achieve a given quality than fast action, grainy movies.  The difference in bitrate needed can be quite drastic.  I've seen up to a factor of 6.

---

