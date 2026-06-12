---
title: "trying to record audio from pulseaudio"
date: 2019-07-29
forum: Multimedia Software
---

### Post by Skaperen on 2019-07-29
search results here and in search sites (like qwant) have suggested **audacity** and **pavucontrol**.  the latter is already installed so i tried it.  the man page tells very little.  running it, i see tabs for **Playback**, **Recording**, and **Output Devices**.  shouldn't there also be input devices?  **Playback** show a lot of sources with **speech-dispatcher** showing up 6 times (why so many?).  the one that lets me adjust the volume of the music i am playing from YouTube in Firefox is named "**AudioIPC Server**: AudioStream". but, Recording just has *No application is currently recording audio* and shows no applications.  is **pavucontrol** useful to get a recording made?  i see that **audacity** is also already installed so i started it up.  it sure looks like a many featured audio editor and even has a record button.  but it looks like something that will take some time to learn. _is there a quick way (simple tool) to record audio from pulseaudio to a file, preferably in .flac format, but .wav is OK?_  _is there documentation for an API to get the audio in a C or Python program?_

---

### Post by Dennis N on 2019-07-30
I use Audacity and pavucontrol. Input devices in pavucontrol on my computer are Microphone and Line-in, but those don't apply for recording streaming audio like you are doing. Just the recording tab is used. Nothing shows in the Recording tab unless the recorder (audacity) is actually recording or monitoring. So with audacity, you start monitoring the stream first, set the volume in the recording tab, then when ready to start the actual recording press record in Audacity. See the attached screenshot made when recording some streaming audio.

To save a recording to a file, you export it from Audacity (File > export) in the desired audio format. (Audacity does not record directly to mp3, flac, or other formats.)

Usually, you want to do some editing of the Audacity recording first - like normalizing, trimming and so forth before exporting.

---

### Post by Skaperen on 2019-07-30
does audacity write out the audio file as it records or does it just buffer it in memory?  i want to do recordings that run for many hours.

---

### Post by Dennis N on 2019-07-30
It writes to disk. When recording, it indicates at the bottom of the Audacity window how much recording time you have left for your disk space.

---

### Post by Skaperen on 2019-08-06
i'm lost on this.  i have some audio playing in another userid. pulseaudio is running in system mode so i continue to hear the same audio when i switch userids in lightdm ([FONT=courier new]dm-tool switch-to-user[/FONT] <username>).  i have both pavucontrol and audacity started in one virtual desktop with very little there.  i run Xfce with panel plugins that include a volume control that spans users (probably because of PA's system mode).

i don't understand what to do first, second, and so on.  how can i know when i have the volume set right?  do i set it in pavucontrol or in audacity?  what file will it write out and what format?  i assume it can read that format back in.

---

### Post by andrew.46 on 2019-08-06
Some wise words [here]("https://askubuntu.com/a/682793/57576") that may help you out...

---

### Post by Dennis N on 2019-08-06
The volume control on panel doesn't affect recording level in Audacity - it only affects the speaker output on the computer. You must set Audacity recording level in pulseaudio's recording tab while monotoring the audio stream in audacity. The recording level is reflected in the Recording Meter in Audacity while monitoring and recording.

_A few comments and concerns_: Audacity has a little recording level slider on the toolbar (also a slider for output level), but those don't seem to work. The playback meter doesn't work on mine when playing back the recording in Audacity. I set record level at 100% or up to maximum level in pavucontrol when recording a TED talk, but even that seems a bit weak with streaming audio - peaks should be closer to 0 db. If the maximum recording level you can get still seems too low on playback in Audacity, try Effect > Amplify after making the recording. I would like a higher possible input level, but I don't know of a way to boost the recording level outside of pulseaudio. The scale of the recording amplitude graph created while recording is too small for me. Click on the y-axis at 0.00 and it will zoom in.

(See post #16 for updates to these comments) 

Audacity Manual
[https://manual.audacityteam.org/index.html](https://manual.audacityteam.org/index.html)
Audacity Toolbars
[https://manual.audacityteam.org/man/toolbars_overview.html](https://manual.audacityteam.org/man/toolbars_overview.html)

---

### Post by Dennis N on 2019-08-06
I found that Xubuntu (18.04) has another volume adjustment that affects Audacity's recording level. The little microphone slider in the regular volume control popup gives a boost to whatever input level pavucontrol has set. See the attachment. With this, you can adjust the Audacity peak recording level close to 0.00 as it should be possible to do. Ubuntu using the same source is peaking at about -9.00 db setting the pavucontrol recording level at the max. Not high enough.

---

### Post by Skaperen on 2019-08-06
i did read something in what i had googled about this that hinted to me that the recording is happening through the sound card analog feedback layer, i.e. it goes through the D/A, then through a volume control or two, then through A/D.  i'd rather stay digital all the way, such as creating a new playback device that saves to a file or loops back to where some process can pick up that digital stream.

---

### Post by Dennis N on 2019-08-07
_Solutions to Gnome recording levels_. After some poking about, I found how to increase the recording input volume in Gnome Desktop. There is now a setting in puavucontrol Playback Tab for AudioIPC Server. It's not shown unless you are monitoring or recording. Setting this, together with ALSA plugin level in Recording Tab, allow boosting the input to an acceptable level. Even Settings > Sound in Gnome also has adjustment of this in its Applications tab, but there is no readout of the % setting as there is in pavucontrol. Both of these utilities are manipulating the same sound settings, just different GUIs.

(See post #16 for updates to these comments)

---

### Post by Skaperen on 2019-08-07
the audio system in Linux seems so overly complex.  there appears to be overlapping roles between ALSA, PulseAudio, and even Audacity.  we should not need an editpr to just save the output to a file.  i'm lost.  i think i need to understand where the audio is flowing.

---

### Post by Dennis N on 2019-08-07
You probably are going to want to edit recordings. Seems essential. Audacity does it all and can export your audio to a file in a variety of formats and quality. It's worth learning to use if you do much audio recording or conversions*. I also looked into what is "AudioIPC Server" and found its Firefox's clever name for its audio stream into pulse audio. I don't recall ever seeing that in pulse audio before, but also haven't actually done any recording for a while now.

There is simpler software, like recently-revived [Audio Recorder]("https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa"), but also less options; and it's not an editor.

*Maybe 10 years ago converted all my old cassette collection to digital files. Audacity did that job.

---

### Post by Holger_Gehrke on 2019-08-07
This [old discussion on AskUbuntu]("https://askubuntu.com/questions/60837/record-a-programs-output-with-pulseaudio") seems relevant to the topic at hand ...

Holger

---

### Post by Skaperen on 2019-08-08
5 answers.  i will spend some time this evening looking them over plus the man pages of new (to me) commands.  i like scripting action more than interactive programs (unless they have a built-in scripting system that is simple, has smart logic, and can operate from files somewhere.  i tend to forget something (old age) when i do interactive things.  memory is a file system with some space, a good editor, and a decent language to write in (used to be paper, and a sharp pencil).

---

### Post by Skaperen on 2019-08-08
very quickly, things are not working:
```

lt2a/forums /home/forums 41> pacmd list-sinks
No PulseAudio daemon running, or not running as session daemon.
lt2a/forums /home/forums 42> ps -ef|egrep '^forums '|fgrep -i pulseaudio
forums    2553  2432  0 Jul30 ?        00:11:16 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-2.0 /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libpulseaudio-plugin.so 8 6291
forums   10131 32681  0 19:52 pts/9    00:00:00 grep -F -i pulseaudio
lt2a/forums /home/forums 43>

```

---

### Post by Dennis N on 2019-08-11
Clearly you are into something else beyond my comprehension with talk of sinks and such, but I should update the Audacity recording comments: 

I'll add this little update on the concerns in post #7 (weak input volume) and AudioIPC Server (post #10 and #12). All these comments were based on Firefox. AudioIPC Server is Firefox's device, and there is a solution to the low levels by adjusting this device. But I found that there is a problem in that whatever setting you have for the Audio IPC Server is lost when you stop or even pause your recording. Repeated resetting is required. It's very annoying to have to do this.

I then tested recording through Chrome, and found settings for it's device (called Chrome Browser in pavucontrol Playback Tab) are persistent through stops, pauses, and even if you close and restart pavucontrol. The default 100% setting for Chrome Browser in Playback tab actually produces an adequate recording level (adjustment probably not necessary as in Firefox), and any adjusting can be done in the Audacity Plugin recording level only. So, for these reasons, I intend to use Chrome from now on for such tasks. Chromium may work well too, but I haven't tested it.

---

### Post by Skaperen on 2019-10-18
the "rec" command (a symlink alias of "sox") records OK to a .flac file.  mp3 does not work.  ffmpeg (from a link) did not work (recorded silence).

---

### Post by slickymaster on 2019-10-18
*Thread moved to **Multimedia Software**.*

---

### Post by Skaperen on 2019-10-18
i remember reading that Audacity recorded this way.  i discovered that "rec" is doing the recording from a re-digitized monitor of the analog audio in the sound card/chip(s).  this will add slight distortion due to the extra conversion : -->D/A-->A/D-->  but it should still be way better than rigging a cable and connector feedback.

---

### Post by moma on 2019-10-29
What about audio-recorder?
[https://ubuntuforums.org/showthread.php?t=2430059](https://ubuntuforums.org/showthread.php?t=2430059)

---

### Post by Skaperen on 2019-10-29
i'll find out if they reply to the email i sent to their mailing list.

---

