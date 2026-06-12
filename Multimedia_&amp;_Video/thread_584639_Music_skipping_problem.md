---
title: "Music skipping problem"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by busfahrer on 2007-10-21
Hi,

I have been using Kubuntu 7.04 (now 7.10) happily for a few months now, but a week or so ago I noticed that music files that used to play back fine (using Amarok 1.4.7) skip sometimes. I also have the feeling that it occurs more often with FLAC files than with MP3s. I don't think that I did any change to my system that could've caused the glitches to appear.

My first question would be if anybody has an idea on how to fix that.
The second question is: How can I try to narrow down the problem to being either a hardware or software problem?

Greetings

---

### Post by berZirker on 2007-10-24
I am having a similar problem.  I did a clean upgrade to 7.10 on a new harddrive and now there are little pauses in the music.  Depending on the app, it happens more or less frequently.  I don't know if this is the same problem, but it sounds similar enough that I thought I would bump it in case anybody has any ideas.

---

### Post by Jumbs on 2007-10-27
I would love to offer an answer, but i found this post looking for the same issue.

I have the transformers soundtrack in flac. It sounds great, except for the occasional skip.

I will reboot into windows and see if its the files.

Stupid windows... everything works in it, but its boring as hell

---

### Post by cessna on 2007-10-27
> **Jumbs said:**
> I would love to offer an answer, but i found this post looking for the same issue.

I have the transformers soundtrack in flac. It sounds great, except for the occasional skip.

I will reboot into windows and see if its the files.

Stupid windows... everything works in it, but its boring as hell


Some time ago with older linux versions, I found that you had to set a better value for the Real Time Clock (RTC) to get smoother video playback and better music playback too. You could try this and see if it helps...if it doesn't, just reboot to get back to the default value.

Simply execute the following command from a shell:

sudo -s
echo 1024 > /proc/sys/dev/rtc/max-user-freq

Hope this helps!

Regards,
Dean

---

### Post by bunny_basher on 2008-03-11
Worth a bump i suppose. I AM HAVING THE SAME PROBLEM! lol

Tried what you said cessna but it sadly didn't work for me :(

bunny basher

---

