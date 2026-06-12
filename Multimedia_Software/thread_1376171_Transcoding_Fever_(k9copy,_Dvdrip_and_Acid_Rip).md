---
title: "Transcoding Fever (k9copy, Dvd::rip and Acid Rip)"
date: 2010-01-08
forum: Multimedia Software
---

### Post by timZZ on 2010-01-08
Hi,

So I have been converting my old dvds into avi's.

I have developed a few questions.

**1. What is the advantage of backing up into avi's or mp4's over dvd iso's?**

Is it size? quality achievable?

[B]2. I have been playing with k9copy, dvd::rip and acid rip.

Any hardcore transcoders having any recommendations with these products?[/B]

---

### Post by bryanl on 2010-01-08
Go get Handbrake ([support FAQ](http://trac.handbrake.fr/wiki/SupportFAQ)). K9copy and the others are OK but Handbrake is a bit more convenient. K9copy tends to create a lot of separate files while Avidemux and Handbrake will make one file for the DVD title group.

Note that Handbrake is focused on transcoding, not DVD ripping. If you've got the libdvdcss installed, though, it does find at ripping DVD's a title group at a time.

An iso can be 5 GB or more for a DVD. The mp4 of the movie will be under 2 so the space savings is greater than 2:1. The quality of the mp4 is close enough to that of the DVD that you'd need a good imagination to find it.

You can get multiple audio tracks in an mp4 and VLC or the default media player can access them but the menu structure and special goodies don't transfer. It does mot appear that the Western Digital media player can handle multiple audio tracks nor the AAC 5.1 audio sometimes found on DVD's. Handbrake does the translation to dolby encoded 2 track by default.

Also note that there is a war on and you can find some strange things on DVD's intended to foil even making an appropriate backup copy. Know the rules for copyright and so on for where you live!

---

### Post by timZZ on 2010-01-08
Handbrake ... My friend is helping with the ports.

I tried (not very hard) to use Handbrake but they are only supporting 9.10 or fedora core 12. (neither I am running currently)

Would you recommend the older version of Handbrake for Ubuntu 9.04?

I am interested in using Handbrake and seeing how it goes.

Handbrake versus Dvd::rip?

---

### Post by Junkieman on 2010-01-27
I used AcidRip for about a year, it works good for easy rips.

Now I'm using dvd::rip for about a year, since it allows ripping multiple chapters at once, and has better subtitle support. Suddenly the final files turn out much smaller than I specify, strange. Maybe a codec issue? Still great for ripping though.

Handbrake is now on the menu, for transcoding. 

Thoggen is another one you might wana try, it only encodes to open formats, .ogv :)

As for ISO's vs encoded video, for me it's just a matter of features: Some DVD's have special menus, extras etc that is just easier to keep as an ISO, instead of encoding them all individually. It's personal preference.

---

### Post by timZZ on 2010-02-03
For me ...

I have been using Handbrake and Dvd::Rip.

The division between the two is ... if you are looking for best possible results dvd:rip will provide.  A lengthy time cost.  Handbrake can come close visually but the stats say the quality will be less.

both are valuable projects.

---

### Post by Melcar on 2010-02-03
Dvd:rip I find to be the most capable DVD ripper and transcoder out there.  Lots more options than the other ones; faster and produces the best quality at default settings.  I use Handbrake though, since it's simple (I don't need a lot from it anyway) and I could never get subtitles to work correctly with dvd:rip.
As for the format differences, it's like previous posters had pointed out.  An .avi/.mp4 rip will take out less space and (depending on the settings you use) still keep the same basic quality as the original source; you will loose DVD menus and any other DVD features though (unless you rip them individually).  An .iso rip, while much more space consuming, will give you an exact DVD replica. It all depends on what you want to do.  If you want to copy a DVD exactly as is then rip as an .iso; if you just want a small rip that you can easily back up and store then make an .avi/.mp4 instead.

---

### Post by tobemem on 2010-04-28
My little contribution to the ripping & encoding issue: ANDREW ([http://tobemem.memebot.com]("http://tobemem.memebot.com/")).

---

### Post by cdavid13 on 2010-04-28
I am kinda new to Linux and Ubuntu and am enjoying it so far.

One thing that I am having problems with is Playing my files that i have made from k9copy on my Windows based computer which is the one hooked up to my projector. 

Does anyone know if there is a way to take these files and play them on Windows?

---

### Post by tobemem on 2010-04-29
Are yours DVD-Video .iso files? If so, [VLC]("http://www.videolan.org/vlc/") should be able to play them.

---

### Post by Statik on 2010-05-09
The difference between DVD.ISO and AVI is:

DVD.ISO uses MPEG, which takes more space for same resolution as AVI, AND it includes the menus, extras, other languages, etc. (unless your software allows you to remove them) This essentially means that for a 4.4GiB DVD, you get less quality for your movie than ...

AVI uses any one of a variety of codecs, XVid seeming to be the most popular for standard TV resolutions, to encode ONLY the movie. This means that all of the space the file occupies is used by the movie. Between the better quality encoding, and the elimination of extras, an AVI will usually have a higher quality video when compared to the DVD.ISO.

So, if you want to copy your DVDs to DVD-R or you want to keep the menus and extras, use DVD.ISO. Otherwise, always use the AVI.

Statik

---

