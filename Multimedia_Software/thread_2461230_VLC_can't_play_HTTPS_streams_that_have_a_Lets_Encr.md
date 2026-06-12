---
title: "VLC can't play HTTPS streams that have a Lets Encrypt cert"
date: 2021-04-26
forum: Multimedia Software
---

### Post by &amp;KyT$0P# on 2021-04-26
When trying to use VLC media player to listen to a HTTPS stream that has a Lets Encrypt certificate, VLC does not recognize the stream's certificate as valid.  One example of such stream is [here]("https://dogglounge.com/"), but I have the same issue with other streams that use Lets Encrypt certificates.  Firefox can play these HTTPS streams without issue.

I'm using Xubuntu 20.04 and VLC version 3.0.9.2-1 installed as a deb from the standard repositories.

How to get VLC to recognize these valid HTTPS certificates?

* Forgot to add: VLC has no problem with other, non-Lets-Encrypt HTTPS streams.

---

### Post by &amp;KyT$0P# on 2021-05-07
Ok so I got this working in a test environment by finding the relevant intermediate certificate Firefox has on file, exporting it into [FONT=Courier New]/usr/local/share/ca-certificates[/FONT] and running [FONT=Courier New]sudo update-ca-certificates[/FONT] , only to discover that none of the HTTPS streams I want to listen to show the metadata of what song is currently playing.  So I'm giving up on this and just sticking with the plain-HTTP versions of those streams. :|

---

### Post by Holger_Gehrke on 2021-05-08
You could try passing the URL of the actual stream to mpv. For the link you gave, running "mpv 'https://dogglounge.com:8000/;stream.mp3'" (got the URL by looking at the src-attribute of the audio-tag in the source of the player-popup; the single quotes are necessary because of the ';' in the URL) results in mpv playing the stream and printing 'icy-title:' tag information. mpv does complain about not being able to verify the certificate, but plays it. Seems they use ShoutCast-tags in this stream and vlc seems to be somewhat finicky about those because neither the encoding nor an escape mechanism for special characters is standardized. When playing web radio from the 'internet' -> 'Icecast Radio  Directory' part of the playlist in vlc a lot of the stations don't show tags or  send a 'station identifier' instead of a song title.

Holger

---

### Post by &amp;KyT$0P# on 2021-05-08
Thanks Holger, I do already have SMPlayer+mpv also installed and it does seem to work there, and I get no complaints about the certificate :D

---

### Post by monkeybrain20122 on 2021-06-04
I am a bit late but I tried the stream with vlc and it works. It complains about the certificate but offers options to abort, accept, or accept for 24 hrs. I chose accept for 24 hrs and it works. I am using vlc 3.0.14 installed with flatpak.

---

