---
title: "Flash 10.2 beta Youtube HD 720p playback"
date: 2010-12-30
forum: Multimedia Software
---

### Post by lyk13 on 2010-12-30
Hi all,

would like to know, as in the subject title, the use of Flash 10.2 beta + vdpau extension smoothens out 720p youtube playback but not significantly.

The machine I am currently using is Acer Aspire Revo R3610. Graphics in it is a Nvidia 9400M.

The thing here is this, I would like to know if there's any other methods to smoothen the playback as well as playback with clarity as of current, some jerkiness may still be felt.

It's being compared to devices of a lower CPU capability than the one in the R3610 and that machine was able to playback much better than currently.

Any advice or technologies that I have missed out using to get it to playback even better?

Thank you!

---

### Post by cchhrriiss121212 on 2010-12-30
Try using [URL="https://addons.mozilla.org/en-US/firefox/addon/161869/"]Flash Replacer.
[/URL]

---

### Post by lyk13 on 2010-12-30
> **cchhrriiss121212 said:**
> Try using [URL="https://addons.mozilla.org/en-US/firefox/addon/161869/"]Flash Replacer.
[/URL]
Needs to be played natively on Flash, quuicktime/wmp replacement may not cut it? Anyway couldn't get it to load the 720p video though.

---

### Post by Yellow Pasque on 2010-12-30
> Any advice or technologies that I have missed out using to get it to playback even better?
No, if you've got Flash with accelerated GPU video content, then you're luckier than most.

---

### Post by lyk13 on 2010-12-30
> **Temüjin said:**
> No, if you've got Flash with accelerated GPU video content, then you're luckier than most.
Really? How so?

I thought this is readily available to everyone? 

Unless my video is not accelerated at all, though I do notice some difference before/after enabling vdpau by copying that one file into firefox extensions.

---

### Post by Yellow Pasque on 2010-12-30
[RANT]No, Adobe sucks and decided to only support VDPAU (i.e. recent Nvidia cards running the binary driver) on 32-bit platforms. If you run anything else and/or(GASP!) a 64-bit platform, then you need a beast of a CPU to play Adobe's inefficient HD Flash videos smoothly.[/RANT]

One more reason to use something other than Flash.

---

### Post by lovinglinux on 2010-12-31
> **lyk13 said:**
> Needs to be played natively on Flash, quuicktime/wmp replacement may not cut it? Anyway couldn't get it to load the 720p video though.

Make sure you get the [latest 2.0.2 version]("http://www.webgapps.org/addons/flashvideoreplacer"). The one still available at Mozilla site was released in a hurry, to deal with YouTube changes, but it is not working good. Unfortunately, it takes a week for Mozilla to review a new version and publish it. Version 2.0 has tons of new features and fixes the YouTube and Vimeo issues.

---

### Post by Yellow Pasque on 2010-12-31
@lovinglinux, thank you for your work. Although you don't address the root of the issue, you make life much better for the majority of linux users.

---

### Post by lovinglinux on 2010-12-31
> **Temüjin said:**
> @lovinglinux, thank you for your work. Although you don't address the root of the issue, you make life much better for the majority of linux users.

I'm glad to read that. Thanks a lot.

---

### Post by lyk13 on 2010-12-31
> **Temüjin said:**
> [RANT]No, Adobe sucks and decided to only support VDPAU (i.e. recent Nvidia cards running the binary driver) on 32-bit platforms. If you run anything else and/or(GASP!) a 64-bit platform, then you need a beast of a CPU to play Adobe's inefficient HD Flash videos smoothly.[/RANT]

One more reason to use something other than Flash.
Ok thanks for the clarification. It's not a problem for me to run Ubuntu 10.10 on 32-bit for now since my hardware isn't up to 64-bit addressing needs.


> **lovinglinux said:**
> Make sure you get the [latest 2.0.2 version]("http://www.webgapps.org/addons/flashvideoreplacer"). The one still available at Mozilla site was released in a hurry, to deal with YouTube changes, but it is not working good. Unfortunately, it takes a week for Mozilla to review a new version and publish it. Version 2.0 has tons of new features and fixes the YouTube and Vimeo issues.
Thanks! Just ran a search on my addons and realise it's...1.07? WTH....

I will try the new version again on monday.

But besides this method, why do I see extra crisp and clear 720p youtube player videos on some lower-end systems?

---

