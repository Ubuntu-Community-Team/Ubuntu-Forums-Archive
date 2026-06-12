---
title: "Recording internet radio using VLC"
date: 2011-08-10
forum: Multimedia Software
---

### Post by Langstracht on 2011-08-10
I am seemingly having a problem with the command "vlc://quit".

I have an .sh file which accesses a streaming url.  If I leave "vlc://quit" in the .sh file it executes immediately - i.e. supposedly goes through all the preceding commands but closes down (quits) before anything happens.

If I take it out everything is fine ( vlc opens, finds, plays/records & stops). But, of course, I'm left with vlc still open.

Anyone have any idea what I am, or my OS is, doing wrong or otherwise what's going on here?

---

### Post by andrew.46 on 2011-08-10
Are you actually using cvlc? If so perhaps use the following in ~/.bashrc:

```

alias cvlc='cvlc --play-and-exit'

```

or incorporate this option into your script.

---

### Post by Langstracht on 2011-08-10
Actually I have been using both.  Switching from cvlc to vlc when it didn't work to see if I could figure out what was going on - I could not.  And, I understood - incorrectly I guess - that closing (quit-ting) a cvlc session was accomplished with the same vlc command.

All of that to say that your suggestion worked.  And now it opens, plays, records, shuts down and goes away.  So thank you SO MUCH for that.

But ... now I have another problem.  The above works just fine for an .mp3 stream.  But does NOT work at all for an .asf(x) stream even if the .asf stream works just fine using the vlc GUI and clicking on record (as opposed to using --sout).

Any idea what might be going on there?

---

### Post by andrew.46 on 2011-08-10
Glad to hear that you have at least partial resolution of your issue :). Unfortunately I am not much of a vlc man really and certainly not much of an expert with the vlc commandline. However if your stream is actually an asx one bear in mind that this is actually an xml metafile that may have several streams and/or different urls embedded within it. Perhaps this is is mucking with your script?

---

### Post by Langstracht on 2011-08-11
Well, thanks anyway for your assistance, it's good to get (c)vlc performing "as it should".

Alas the streams really are asx - thanks Bloomberg and BBC!

I'd like to think perhaps someone can take on the difference between a CLI --sout and a GUI click on record.  Whether to explain what it is, get it fixed or offer a work-around. 

Thanks again.

---

