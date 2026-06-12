---
title: "Play Advanced Subtitles with ubuntu"
date: 2015-07-07
forum: Multimedia Software
---

### Post by Kagu-chan on 2015-07-07
Hi,

using ubuntu 14.04, i need to play videofiles with Advanced ASS / SSA Subtitles.
This means more lines at once, high usage of ASS tags, Vector graphics via ASS commands and many more.

I need this for video creation (KaraokeFX).

On Windows i used MPC-HC, which does not run (even via wine, dont work)
VLC plays only the first line (not displayed correctly
SMPlayer display all lines wrong and without ä / ö / ü / ß letters - also its ignoring positioning and font sizes
MPlayer has enorm lags and does also dont display the lines correctly.
Ubuntu Default Video Player dont display subtiles, even if i select them

So i need a video player which can display my subtitles correctly since i need it for work :/

Ive installed most recommened codecs and libass is the newest version.

Here some pictures to show the problem:

SMPlayer (ubuntu):
[IMG]http://img5.fotos-hochladen.net/uploads/bildschirmfotoy7sc9vrz4h.png[/IMG]

Same line from windows testencode (MPC-HC)
[IMG]http://img5.fotos-hochladen.net/uploads/bildschirmfotou48lj3x5yt.png[/IMG]

First Line VLC (ubuntu) / MPlayer (ubuntu - look same, started with -ass option)
[IMG]http://img5.fotos-hochladen.net/uploads/bildschirmfotopymikv0385.png[/IMG]

Same line from testencode (windows)
[IMG]http://img5.fotos-hochladen.net/uploads/bildschirmfotoy2tb7sz9vu.png[/IMG]


The blue background are created by Shapes. The visible line is just the normal text with transparent inner color.

Which media player can i use or what have i to do to display it correctly? Font are all installed.


Thanks in advance and best regards,

Kai

---

### Post by mc4man on 2015-07-07
What release of Ubuntu (14.04, 15.04, ect.
Is there a sample i could grab online or you provide one.
(it's possible mpv or one of it's 2 decent frontends could handle

---

### Post by Kagu-chan on 2015-07-07
Oh, forgotten to write, ill extend my thread. Its ubuntu 14.04
I can upload a sample, ill edit this post then.


[https://www.dropbox.com/sh/mqtkeuyqeqnrkkp/AAD3BouLP8D-aebIObQ-VbgPa?dl=0](https://www.dropbox.com/sh/mqtkeuyqeqnrkkp/AAD3BouLP8D-aebIObQ-VbgPa?dl=0)

Here you can access all files.
testencode(1).mkv is the file ive created under windows a while ago. That is how it should look.
ED_out.mkv is the raw file, ED_out.ass is the corresponding subtitle file.

The two font files are the fonts used for the subtitles.


MPV dont lag or something and playing all lines, but no shapes / vectors :/
[IMG]http://img5.fotos-hochladen.net/uploads/bildschirmfotovbza4wdh5t.png[/IMG]

---

### Post by mc4man on 2015-07-07
Maybe try bomi which uses libmpv, it's built-in to the player. It seems quite centric to anime - 
git page - 
[http://bomi-player.github.io/](http://bomi-player.github.io/)
ubuntu ppa - 
[https://launchpad.net/~darklin20/+archive/ubuntu/bomi](https://launchpad.net/~darklin20/+archive/ubuntu/bomi)

As far as mpv itself - if you feel it should do/be better in this regard then start an issue here - 
[https://github.com/mpv-player/mpv/issues](https://github.com/mpv-player/mpv/issues)

---

### Post by mc4man on 2015-07-07
I provide an bi or tri weekly mpv based on  master here if you are using a build from elsewhere. If building yourself then use the current git before filing an issue (master git mpv, ffmpeg, libass
[https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)

(- a fairly recent mpv with vapoursynth support is here though don't think vs is of value to your issue - 
[https://launchpad.net/~djcj/+archive/ubuntu/vapoursynth](https://launchpad.net/~djcj/+archive/ubuntu/vapoursynth)

---

### Post by Kagu-chan on 2015-07-07
bomi works, thanks. I have to fix the sizes to display, but my shapes are displayed (error while creating ass file).

---

### Post by ajgreeny on 2015-07-07
In future, rather than adding large images inline, please use thumbnails instead; not everybody has fast broadband connections.

Click on the Go Advanced button, then use the paperclip icon in the toolbar and browse to the image on your hard disk and click upload.

---

### Post by monkeybrain20122 on 2015-07-07
Don't know, is this working? The one with subtitle at the bottom shows a "shadow" behind the subtitles but the one where the subtitles are on top doesn't. Smplayer with mpv as backend (subtitle on top was using secondary subtitle track from options) I compiled mpv from master.

---

### Post by ajgreeny on 2015-07-08
Your thumbnails are working fine!
Unfortunately I can not help with your sub-title problem; I never have used them.

---

