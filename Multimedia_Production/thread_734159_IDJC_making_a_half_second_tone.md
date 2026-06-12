---
title: "IDJC making a half second tone?"
date: 2008-03-24
forum: Multimedia Production
---

### Post by Oysterville on 2008-03-24
Several times while trying to do a recording I have been plagued with IDJC doing a half-second beep tone for no apparent reason.  I'm not touching the keyboard, so it's not like I'm hitting an errant button.  I'm using version 0.7.3 in Ubuntu Studio Gutsy.

It's happened when using mp3's from a network share and also using FLACs off of a DVD.  The beep is not present in the audio source.

Thanks for the help.

---

### Post by StephenF on 2008-03-24
Go into Preferences, click Genaral, scroll down, deselect the option labelled 'Sound an alarm when the music is due to end'.

This will turn off the alarm that sounds nine seconds before the music is about to end. The beeps don't make it into your recording so it is safe to leave this option on.

---

### Post by Oysterville on 2008-03-24
Good to know, thanks.  Now I've gotta troubleshoot the ogg files being corrupted.  I have a feeling that the way that IDJC transmits the length of the song in with the file that it's confusing the players, as they are crashing at the end of the first song.  Gonna turn that off tomorrow and see if it works.

Thank you VERY much for the help.

---

### Post by StephenF on 2008-03-25
What happens when a song title changes is a new *logical bitstream* is started in accordance with the following spec:
[http://www.ietf.org/rfc/rfc3533.txt](http://www.ietf.org/rfc/rfc3533.txt)

Since ogginfo does not throw up any errors for me (see attachment) I can only assume your player is at fault.

Have you tried playing your recordings in IDJC?

---

