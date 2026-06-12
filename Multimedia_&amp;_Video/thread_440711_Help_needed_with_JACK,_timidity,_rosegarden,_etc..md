---
title: "Help needed with JACK, timidity, rosegarden, etc."
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by bobertfishbone on 2007-05-11
I just installed Ubuntu Studio and am anxious to get working with MIDI sequencing and audio production. I have an M-Audio Radium 61 MIDI controller, which I have up and running with the firmware loader. I can hit keys when I'm in Rosegarden and it'll put a blip on the bar, and add the notes to the track. I can't hear anything when I do this.

I then went about setting up Timidity++ to get the MIDI working, since it didn't seem to be. Ubuntu Studio did a good job of setting it up for me, but I couldn't run the "timidity *.MID" command and have sound. Additionally, the Rosegarden MIDI instrument suddenly became 128:0 Timidity port 0 instead of the MIDI controller.

As I would come to find out, the problem with the "timidity *.MID" command happened because I had the JACK server running. When the JACK server was off, I was able to play any MIDI I wanted to through the terminal.

This brings me to a couple questions.

1) Is it possible to have JACK and timidity coexist peacefully? 
2) If so, and once I get that figured out, what should my JACK connections look like between the MIDI controller, Rosegarden, and ALSA?
3) Is there some sort of manual or help site for any of these problems? I feel like some of them are fairly simple to figure out (JACK settings and such)
4) I now have Rosegarden working. Is there a way so I can have Rosegarden and another program play audio at the same time?


If you need more information I'll be happy to provide.

EDIT: Through some trial and error I got Rosegarden to work WITHOUT JACK. I still need help with JACK/Timidity compatibility, and I'd also like to know about the audio issue.

---

### Post by pavo on 2008-02-06
> **bobertfishbone said:**
> 
1) Is it possible to have JACK and timidity coexist peacefully? 

Timidity will cooperate with JACK when timidity option "-Oj" is used instead of "-Os"
So the Timidity server can be started e.g. using command:
timidity -iA -B2,8 **-Oj** -s 44100

---

