---
title: "Delay when playing notes"
date: 2008-03-27
forum: Multimedia Production
---

### Post by contactMW on 2008-03-27
Hi everyone,

If you could help me try and fix this problem that would be great.  See my attached screen shots to see my MIDI configuration.

My problem is that there is a delay when trying to play GM MIDI instruments ( in Rosegarden ) but there is no such delay at all using a synthesizer program ( ZynAddSubFX ).  I've got both the Virtual MIDI keyboard and my M-Audio keyboard connected and both create the same problem.

Surely just using GM MIDI and not any fancy Soundfont wouldn't require a high CPU load/dedicated hardware to create.  I've got a Time laptop running at 2.4Ghz with 768MB of RAM.

If anyone knows how I can overcome this 0.5s delay when playing notes please let me know!

Thanks in advance,

Martin

(added 2008-03-27 @ 12:35)

if you can replicate the application connections as per mine in the screenshots, you will be able to hear this delay if there is a general problem doing what I am trying to do.  If you get the same results as me then you will hear the ZynAddSubFX output immediately when you play the notes followed by the Rosegarden output after (1/4 to 1/2 second)

(added 2008-03-27 @ 12:57)

I've had a look on Google to see if this has been answered anywhere else and found the following links:
[http://forum.cakewalk.com/tm.asp?m=760084&mpage=1&#55974;&#56724;](http://forum.cakewalk.com/tm.asp?m=760084&mpage=1&#55974;&#56724;)
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/568645.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/568645.html)
[http://groups.google.com/group/comp.music.midi/browse_thread/thread/f3d213b93c69389f/2bc13354df06a631](http://groups.google.com/group/comp.music.midi/browse_thread/thread/f3d213b93c69389f/2bc13354df06a631)

Looks like something to do with "ASIO latency", only I don't have a clue how to check if this is the problem.  If anyone could show me where such settings are so I can check it that would be great.

(added 2008-04-01 @ 10:25 )

It looks like it's something to do with Timidity as this happens when Rosegarden isn't even loaded.  It looks like Rosegarden just controls the preset.

If anyone can diagnose further I would be very grateful!

---

### Post by ethanay on 2008-05-04
are you using timidity as a performance synthesizer, or just to play back midi data?  i can't imagine using it for performance reasons.

---

