---
title: "Music suddenly stopped playing in lucid lynx"
date: 2010-06-07
forum: Multimedia Software
---

### Post by lilychef on 2010-06-07
Hey, there!  After a successful upgrade to lucid, everything was going GREAT (including FINALLY having surround output) until now all of the sudden music files won't play... When I double-click a file, Totem opens automatically, and it says it's playing,but there's no sound and the bar does not move across at the bottom.  In VLC, the bar moves like it's playing, but there is still no sound.  Doesn't work when I hover the cursor over a file, either.  In previous versions of Ubuntu, a simple reboot would fix this, but that doesn't work with Lucid...  Online streaming works fine.

Anybody have any ideas?  The system-preferences-sound window is totally different than previous versions so none of the fixes I've found in the forum apply...

---

### Post by Breambutt on 2010-06-07
Did the music suddenly stop playing while you were logged in / playing something, or one day when you booted up and found out it wouldn't budge any more? And what kind of a soundcard is it anyway? Seems strange if streaming media plays fine. Are you trying to play mp3s and other fugly formats? Do wavs and oggs work? I would've thought VLC could still play those as well.

I'm not too hot on remotely solving problems that occurred after an upgrade since it spells and smells like trouble.

My 2 top **un**educated guesses for all audio problems: the output level is set down to zero for no apparent reason (try alsamixer) or PulseAudio is being PulseAudio (killall [with fire and brimstones] pulseaudio).

---

### Post by lilychef on 2010-06-07
I shut down the machine every day, so it must have happened upon reboot... I wasn't in the middle of playing tunes, if that's what you mean...  Just trying to play mp3's... I still don't know how to play WMV's...  I just stuck a CD in and VLC shows the bar moving but no sound...  Neither Wav's nor ogg's work.  Sound card is a VT1720/24 [Envy24PT/HT] PCI

---

### Post by Breambutt on 2010-06-07
Sorry, I'm baffled. This is so Windows-y.

Normally you'd need all kinds of gstreamer0.10-plugins (-bad, -ugly, -fugly etc.) in order play mp3, wmv and so forth in Totem but it can't be that in this case. What does *aplay -L* say?

Did you try killing pulseaudio to see if it made any difference? It's a little stupid and can't always handle sound cards if their mixer elements are named unconventionally.

---

### Post by lilychef on 2010-06-07
Well, camaron1's suggestion from [here]("http://newyork.ubuntuforums.org/showthread.php?t=1477872") worked.... where he says "to get your sound working".... although my line #'s were slightly different than the ones he said... So I'm not going to mess with anything else for now... I will get back to this thread, however, if it acts up again... I will also get back if it keeps working from that fix... Why this stuff gets changed from boot to boot is a mystery to me...  Thanks for your prompt reply, BB

---

### Post by Breambutt on 2010-06-07
Duh-huh, I thought they fixed that at some point. Oh well, glad it's working now.

---

### Post by lilychef on 2010-06-15
Well - I'm back again with a new and strange issue!  Now, it seems, that when I reboot, everything works fine... but after a while, the sound preferences comes up "waiting for sound system to respond", and I cannot get sound from flash (ie YouTube) or other online streaming media....  UGH!

Why it works for a while, but then doesn't, is a real mystery.... The only thing that I can think of is maybe the screensaver... I haven't always used one...  In Windows I know screensavers always caused a ton of problems, but I would think Ubuntu would have a handle on such a simple thing...  I'm going to try disabling it and rebooting, and will report back.. That is, unless somebody gets back here with a fix... After much forum-searching, I'm seeing this issue come up a lot, but none of the fixes fix my issue...

Maybe somebody out there can figure this out for all those novice users out there like me...  I understand how it all works, but I am NOT a programmer or experienced user...  Thanks in advance.

---

### Post by lilychef on 2010-06-15
Ok - screensaver had nothing to do with it.  Don't laff those who already knew better... but here's where it stands:

MP3's play fine in Totem.

Streaming audio does not play at all.

"Waiting for sound system to respond" comes up when trying to go to "system-preferences-sound"

Clicking the volume icon does not allow to adjust volume, but gives a sound preferences option, which also gives the "waiting" message

Dear lord.  This is strange.

---

