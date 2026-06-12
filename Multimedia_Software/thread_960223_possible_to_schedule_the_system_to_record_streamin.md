---
title: "possible to schedule the system to record streaming video at a later time?"
date: 2008-10-27
forum: Multimedia Software
---

### Post by hcaleman on 2008-10-27
I know you can record streaming video via VLC and other players, however haven't tried it with the source I'm concerned with (should probably do that first).  The problem is the things I want to stream, mostly football matches from the US, start in the middle of the night for me here in the middle east.  Worse off I can't really stay up till 2 on Sat to watch/record a game since our work week is sun-thurs.

So... I want to be able to schedule my system to say start recording a certain stream at 2am and stop when its done or at a time I tell it to.  

Is there any utility that will allow me to do this, or does anyone know of how I can go about trying to get this started?  I usually use channelsurfing.net for football coverage, not sure if it normally being a broswer-based stream affects anything.  

Go figure, of course when I move overseas is when Alabama has a killer season.

---

### Post by aeiah on 2008-10-27
if you can record using the command line, you can schedule this command to be run at a specific time. if you can stop the recording with a command on the command line, you can also specify a time when this will be issued. the commandline method for this is by using a program called cron. there are guis available though which will make this far less painful if you arent used to the commandline (check out gnome-schedule), but i think you'll still be issuing commands via the cli. i imagine this is possible with vlc. it certainly is with xine and mplayer.

---

### Post by hcaleman on 2008-10-27
I'm fine with the CLI just usually a matter of reading up on it a bit.  So if I can figure out how to do it with vlc or mplayer via cli, then reading up on cron on top of that should get me what I need?

---

### Post by andrew.46 on 2008-10-31
Hi hcalemen:

> **hcaleman said:**
> I'm fine with the CLI just usually a matter of reading up on it a bit.  So if I can figure out how to do it with vlc or mplayer via cli, then reading up on cron on top of that should get me what I need?

I have a script to download and convert a streaming Real Audio broadcast at a set time each Sunday night. Have a look at:

[http://andrews-corner.org/ftgws.html](http://andrews-corner.org/ftgws.html)

Just ignore all the Slackware references and have a look at the script and very simple cron settings.

   Andrew

---

