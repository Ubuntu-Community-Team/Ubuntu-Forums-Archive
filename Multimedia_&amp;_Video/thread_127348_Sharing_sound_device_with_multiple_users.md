---
title: "Sharing sound device with multiple users"
date: 2006-02-08
forum: Multimedia &amp; Video
---

### Post by drberg1000 on 2006-02-08
I'm trying to solve a situation such as the following:

dberg starts a playlist in xmms on loop.
dberg walks away and his screen locks.
tberg wants to watch a movie.

Has anyone else considered how to address this issue?

Perhaps the best solution I've been able to come up with is to have any playlists played process owned by a user "music".  Each user in the audio group would then be allowed send commands to this process to stop playback, adjust the volume, change the playlist, etc.  I don't know the best (or any) way to impliment this though.  Any ideas of where to start would be great.  I would prefer that the "music" user doesn't run anything but a script to handle the playlist and mpg321, ogg123 and similar players.  

Problem with this solution is it only addresses mp3s/oggs.  The same problem occurs with any audio that lasts for an extented period of time (movie, playlist, radio stream, ...) or repeats (logins from gaim or other obnoxious noises).  Does anyone know how windows 2000 handles the problem?

Other not so good ideas:

Ownership of the device could be transfered when the VT is switched, but this would mean a playlist stops even if the new user wants it to continue.

There could be a list of programs that should be silenced when a new user is at the console, a list that should be mixed, a list that should be stopped etcetera.  Combined with another set of lists of programs that silence other programs.  This seems far too complicated though and I feel there must be a better solution.

Any help with this is appreciated.  It is starting to really irritate my wife, and I want it fixed before she decides she wants windows installed. 

Thanks in advance.

--Dave

---

