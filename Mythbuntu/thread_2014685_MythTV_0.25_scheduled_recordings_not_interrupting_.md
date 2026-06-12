---
title: "MythTV 0.25 scheduled recordings not interrupting LiveTV"
date: 2012-07-02
forum: Mythbuntu
---

### Post by anonymousdog on 2012-07-02
This is surely not a MB issue, but this forum is friendly; so, I'm looking at whether others are seeing this issue in production:

Watching LiveTV when a scheduled recording approaches, I get (as expected) a notification of the scheduled recording and the "I need the tuner; what do you want me to do?" question.  By default, the answer is, "record and watch", and, if I respond in time, that's usually what I choose anyway.  All that is fine and expected.

Now the issue: If I allow the timeout to occur OR choose the (default) "record and watch" option, nothing happens...there is no change.  In all prior MythTV versions I've used (up to 0.23), the system would tune to the scheduled recording's channel and present the recording as LiveTV as well.  The recording would show up in the Default recording group in the listing (if checked later), and, if LiveTV was stopped, the recording would run to expected/scheduled completion time anyway.

In 0.25, LiveTV proceeds happily along with the previously-selected channel as if nothing at all has happened; the channel is not changed, and the scheduled recording does not happen.  The scheduled program does not get recorded even if another tuner could handle the request.  Moreover, if you exit LiveTV and check the Upcoming Recordings screen, it will show the scheduled recording as if it were recording (even though Watch Recordings does not list the show, and System Status shows no busy tuners).

"Allow LiveTV to move scheduled shows" IS checked (as it always has been in all prior versions).  Also, PVR-500 is the only tuner card in his backend.  It is fed by Dish STB over RCA and S-Video connections.  The STB channels are changed by mceusb IR blaster and a well-working script using irsend.

This started on 0.25 upgrade over MB 10.04 x86_64/0.23, but I didn't address it immediately as I had bigger 0.25 upgrade issues.  With those potentially resolved now, I've rebuilt the system using a new root ("/") file system (128MB SSD) disk and clean install of MB 12.04 x86_64/0.25 restoring the db from backup and mounting existing storage groups in the expected locations.  No hostname changes or other rookie mistakes.  Symptoms are precisely the same as on the MB10.04 x86_64/0.25 build on the prior disk. So, I'm pretty sure this is a MythTV thing, and not MB thing (since it persists across distros and a fresh install on virgin file system).

Has anyone else encountered 0.25 failing to retune from LiveTV for scheduled recordings?

---

### Post by anonymousdog on 2012-07-02
I found the MythTV trac ticket: [http://code.mythtv.org/trac/ticket/10726](http://code.mythtv.org/trac/ticket/10726).

Combine this bug with the ivtv issues, and it impacts our usage enough that I'm teetering on the brink of stepping everything back to 10.04/0.23 (if I can find an old DB backup).

---

