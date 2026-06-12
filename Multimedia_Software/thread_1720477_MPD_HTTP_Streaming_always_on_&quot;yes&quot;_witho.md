---
title: "MPD: HTTP Streaming: always_on &quot;yes&quot; without effect"
date: 2011-04-03
forum: Multimedia Software
---

### Post by aaaaalex on 2011-04-03
I set up my MPD to stream to the network. Every time i pause it or replace songs on the current play queue the stream seems to stop.

I found that adding the option to the stream set-up to be always_on should make mpd keep the stream alive even when nothing is currently playing. Does not seem to work however. 

Anyone tackled this already?

Here is my Stream source set-up:
```
audio_output {
	type		"httpd"
	name		"My HTTP Stream"
	always_on 	"yes"
	encoder		"lame"		# optional, vorbis or lame
	port		"8000"
#	quality		"5.0"			# do not define if bitrate is defined
	bitrate		"128"			# do not define if quality is defined
	format		"44100:16:1"
}
```

---

