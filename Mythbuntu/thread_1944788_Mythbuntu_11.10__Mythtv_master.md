---
title: "Mythbuntu 11.10 / Mythtv master"
date: 2012-03-21
forum: Mythbuntu
---

### Post by uncle hammy on 2012-03-21
I have an issue with lossless transcodes running master (0.25) on Mythbuntu 11.10.  After the transcode is finished, the resulting recordings have vertical purple lines that flash in it at every point where a cut was removed by the transcode process.  To make matters worse, on 720p recordings, the purple lines flash every 50 seconds like clock work.  It's on every single file transcoded on 11.10 / 0.25, every single time.

It is exactly the issue outlined here [http://code.mythtv.org/trac/ticket/10110](http://code.mythtv.org/trac/ticket/10110) which concludes with...

> Closing at reporter request. As an aside, this was likely due to the Debian external libmpeg2 insanity.

In my troubleshooting, I ended up having one of my slave backends still running Mythbuntu 10.04 transcode some files.....no purple lines.  

I am reasonably sure that 11.10 has some kind of issues with the ffmpeg/libav* libraries it's using as the ticket suggests.  

In lieu of a reasonable solution, I am probably going to downgrade all my systems to 10.04 and skip 12.04 as well.  Any ideas?

---

### Post by nickrout on 2012-03-21
> **uncle hammy said:**
> I have an issue with lossless transcodes running master (0.25) on Mythbuntu 11.10.  After the transcode is finished, the resulting recordings have vertical purple lines that flash in it at every point where a cut was removed by the transcode process.  To make matters worse, on 720p recordings, the purple lines flash every 50 seconds like clock work.  It's on every single file transcoded on 11.10 / 0.25, every single time.

It is exactly the issue outlined here [http://code.mythtv.org/trac/ticket/10110](http://code.mythtv.org/trac/ticket/10110) which concludes with...



In my troubleshooting, I ended up having one of my slave backends still running Mythbuntu 10.04 transcode some files.....no purple lines.  

I am reasonably sure that 11.10 has some kind of issues with the ffmpeg/libav* libraries it's using as the ticket suggests.  

In lieu of a reasonable solution, I am probably going to downgrade all my systems to 10.04 and skip 12.04 as well.  Any ideas?

This is also referred to recently on the mailing list (or are you the poster there too?)

perhaps give up transcoding?

---

### Post by uncle hammy on 2012-03-22
I'm the poster there.  I figured it's starting to appear to be a Mythbuntu, not MythTV issue so I'd see what the Mythbuntu folks have to say.

I don't know that "give up transcoding" is a reasonable solution :).  

Then again, 12.04 will likely be using a whole new set of ffmpeg libraries and may not have this issue.

---

### Post by tgm4883 on 2012-03-22
I've not heard of others having this issue. I run my backend on 10.04/0.25 (and don't transcode) so I won't be much more help than that.

---

### Post by nickrout on 2012-03-22
> **uncle hammy said:**
> I'm the poster there.  I figured it's starting to appear to be a Mythbuntu, not MythTV issue so I'd see what the Mythbuntu folks have to say.

I don't know that "give up transcoding" is a reasonable solution :).  

Then again, 12.04 will likely be using a whole new set of ffmpeg libraries and may not have this issue.

mythtv uses it's own internal version of ffmpeg, so that is not distro dependent and not dependent on external ffmpeg issues.

Whether mythtranscode uses the internal mythtv libraries or external ffmpeg is unknown to me, but if it uses internal ffmpeg, the same applies.

---

### Post by uncle hammy on 2012-03-22
> **nickrout said:**
> Whether mythtranscode uses the internal mythtv libraries or external ffmpeg is unknown to me, but if it uses internal ffmpeg, the same applies.

The quote from Robert on that ticket about Debian ffmpeg insanity leads me to believe that mythtranscode may not use internal ffmpeg, though, like you, I really don't know.

I'll probably just bump down to 10.04 when I get home from vacation.  I had no intention of going to 11.10 but there were some things in 10.04 that weren't working (menu clicks) that were in 11.10 when I first tried 0.25.  However, those issues appear to be fixed because they work fine now on my 10.04 slave backend / frontend.

---

### Post by uncle hammy on 2012-03-31
I am reasonably certain it is a MYTHBUNTU 11.10 issue and NOT a MythTV 0.25 issue.

This morning I did a fresh install of 10.04 on my master backend, removing the 11.10 installation that was on it.  I then brought MythTV up to the same 0.25 level it was at under 11.10 with the repos.  

I transcoded 17 recordings this morning, 100% success, not even so much as a single blip in any of the "trouble" spots (commercial breaks or 50 second increments on 720p recordings) that I checked.  Previously with 11.10, I had 100% failure with the purple lines issue.

---

### Post by nickrout on 2012-03-31
Good detective work - hope you are relaying this info to the ticket and the mailing list too.

---

### Post by uncle hammy on 2012-03-31
I did post a follow up on the mailing list.  The ticket I mentioned earlier in this thread is closed.  I suppose  I should actually file a Mythbuntu ticket.

---

### Post by nickrout on 2012-03-31
Funny thing is that on 0.24-fixes mythtranscode does not seem to be linked to any ffmpeg libraries. It links to stuff like libmythavformat, ie the internal myth versions.

All very odd.

---

### Post by uncle hammy on 2012-04-01
> **nickrout said:**
> All very odd.

Agreed, however I can only go from what my eyes and investigation is telling me.  Though I suppose it could technically be called a MythTV issue if Myth is linking to OS ffmpeg libraries when it should be using internal stuff.

Seems this could come down on either side :).

---

### Post by notanumber67890 on 2012-05-14
I am having the same issue with mythtranscode producing vertical purple lines in the output file.

I am running Mythbuntu 11.10 and using 1080p sources. Lossless transcoding worked perfectly in earlier versions.

Is there a fix or workaround for this problem, other than downgrading to an earlier mythbuntu, which is not an option in my case?

---

### Post by nickrout on 2012-05-14
You could try using a different transcoding script.

By the way if you are transcoding recordings, I doubt they are 1080p, I am not aware of any broadcasters transmitting 1080p.

---

### Post by notanumber67890 on 2012-05-22
> **nickrout said:**
> You could try using a different transcoding script.

By the way if you are transcoding recordings, I doubt they are 1080p, I am not aware of any broadcasters transmitting 1080p.

Thanks for the response ... yeah the recordings are 1080i like you said.

Like others, I'm using --honorcutlist to remove commercials.  Don't I need to use mythtranscode for that?  Do you think I can I modify the existing script to fix whatever problem is causing the purple lines?

Thanks for your help ...

---

### Post by uncle hammy on 2012-05-22
I meant to post a follow up in here a while ago, and kind of forgot.  The issue no longer exists with 12.04 / 0.25.  

I can't tell you how to resolve it in 11.10, but upgrading to 12.04 should do it.

---

