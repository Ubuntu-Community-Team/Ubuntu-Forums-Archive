---
title: "Hey Scripting gurus!  Need ideas for unattended automatic recordi"
date: 2014-07-15
forum: Multimedia Software
---

### Post by stickjam on 2014-07-15
I think this is something that can be accomplished with a craftily-written script.  Just looking for ideas and possible pitfalls to watch out for...

I have need to be able to automatically record in stereo from an external audio interface--in this case two channels of the X-UF card on the Behringer X32, which has both USB and FireWire.  I'm looking at this for two purposes:  one for our church to automatically record any service that is done, and another for my studio to enable an automatic "always recording" policy to ensure any inspiring musical moments are captured.

I'm currently doing this at our church--with cron jobs running scripts at specific times, recording WAV files, which I then run through a custom program to extract the longer stretches of audio between silence and then encode to produce timestamped MP3 files.

The current problems with this is...  There is no flexibility in recording because it requires changing the crontab to vary from the schedule, and I'm not running pulseaudio in system mode which means the computer has to be logged in and locked.  This is a problem in the event that there is a power outage, the computer eventually powers back up, but the script will fail to run until somebody logs in.

Here what I'm trying to accomplish with this new script
[LIST]
[*]It must function even if nobody is logged in to the computer (system mode)
[*]It must record for virtually the entire time that the USB/FireWire interface is available.
[*]There needs to be a means to abort and disable it when necessary (for maintenance, or if interactively using Audacity to do multitrack recording)
[/LIST]

What I'm thinking is a script that spawns continuously that:
[LIST]
[*]Checks if the script is already running in another process.  If so, sleep a couple seconds and abort.
[*]Check if a "disable" file is present.  If so, sleep for a minute and abort.
[*]Attempt to discern the presence of the X-UF interface.  If absent, sleep a couple seconds and abort.
[*]Attempt to record audio from the first two channels of the X-UF interface to a timestamp-named file on a very large drive.
[*]Record continuously until the interface goes unavailable.  When the interface becomes unavailable...
[*]Check the file size.
[*]If the file has no data
[LIST]
[*]Remove the empty file
[/LIST]

[*]Else
[LIST]
[*]Write a file in a "to-do" directory with date/time and reference to the recorded file.  (I'll have a cron job run another script to check this directory every 15 minutes or so to do that trimming and MP3 encoding.)
[/LIST]

[*]Exit
[/LIST]

I'm sure the tricky part will be ensuring that the plug&play with the audio interface works cleanly and handling the recording application exception when the interface disappears to the OS.  Obviously I'd want whatever recording application to simply direct the stream to the file until it aborts.  The most undesirable scenario would be a recording app that hangs on errors or leaves an audio file that is unreadable (losing the last buffered bit of audio that came in as it was powering down is no concern.)   

Any ideas of what audio subsystem should be used for this?    What interface would be better: USB or FireWire?   Best way to spawn the process: cron vs. /etc/init?  Any ideas or possible gochas?

Thanks!

---

### Post by sedawk on 2014-07-17
Here is a tool that works like an audio spy/audio bug/audio surveillance and only records stuff when there is sound: [http://www.vanheusden.com/listener/](http://www.vanheusden.com/listener/)
Keep in mind that it might be illegal to run such a tool at public places, in your country, or requires warning signs like "CCTV" warnings at public places like a church.

---

