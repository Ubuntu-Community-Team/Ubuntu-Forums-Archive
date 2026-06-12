---
title: "Video opens and immediately closes"
date: 2008-11-23
forum: Multimedia Software
---

### Post by PlainShane on 2008-11-23
The problem: I try to open a video file, the player opens and no longer than second later the program is immediately killed on all extension types (avi, wmv, mov, mkv, etc...)

Solutions attempted: Ultimatix, ubuntu restricted extras, any other codec I could find, and multiple player apps (VLC, totem, mplayer, banshee).

This is a problem that started after I did a fresh install of 8.10. Not an upgrade. In 8.04 everything worked fine with just the ubuntu restricted extras installed. Tried less codecs than I had in 8.04, the same, and all others I could find. No clue what is causing this. This is a big problem and makes my linux partition a unhealthy choice during boot. If the player is opened first, and then video selected it still closes. There was another thread or two that were older with a similar problem but in both of those there was no solution or no answer back from the poster after solutions were given (all of which I tried).

Help!

---

### Post by PlainShane on 2008-11-24
Bump por favor

---

### Post by Tomatz on 2008-11-24
Goto ***system, preferences, sound***.

Then switch each option from **autodetect** to your **mixer/device** i.e. alsa, oss, pulseaudio(_This will be displayed in the bottom dropdown menu if you dont already know_).

---

### Post by PlainShane on 2008-11-24
That does not seem to work. Video players still open and close before playback.

---

### Post by PlainShane on 2008-11-28
Anyone else, please?

---

### Post by Tomatz on 2008-11-28
> **PlainShane said:**
> Anyone else, please?

Sorry, forgot about this thread.

Open a terminal and run the command:

```
totem
```

Then play a video and when it crashes, post the terminal output here.

---

### Post by scott20 on 2008-11-28
I've have the same problem as PlainShane.  I opened totem with terminal like Tomatz advised.  I played a video and got this message.

The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 130 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

So does this mean I need to run a debugger?

---

### Post by Tomatz on 2008-11-29
You need to disable Xv in your video players and use X11 instead. Its a bug in your GPU drivers causing this.

To do this for each of the main media players:

> 
**(****helpful howto taken from** [**_here(clicky)_**]("http://ubuntuforums.org/archive/index.php/t-513822.html")**)**
GSTREAMER:
For Totem with the gstreamer backend (totem-gstreamer) open a terminal and type gstreamer-properties
Then click the Video tab and under Default Output select X Window System (No Xv) for the plugin. Then restart Totem. This will work for any video application that uses gstreamer as it's video backend.

MPLAYER:
If you use MPlayer (GMplayer) right-click on the screen and select Preferences then select the Video tab and under Available Drivers select X11 (XImage/Shm)
then restart MPlayer. The issue here is that it won't go fullscreen with the video. I suggest using VLC or totem-gstreamer.

XINE:
If you use Xine then go to File -> Configure -> Preferences.
(make sure under experience_level you select Master Of The Known Universe)
You will get a tab at the top for Video. Under driver select xshm. Then restart Xine. This also works if you are using the totem-xine backend. Just run gxine at the terminal and follow the steps.

VLC:
For VLC select Settings -> Preferences then in the bottom-right of the window check the Advanced Options box. Then expand the Video item on the left and select Output modules. Then in the list on the right for Video output module change it to X11 video output. Then restart VLC

;)

---

### Post by dpoisond on 2008-11-29
8.10 - pay for codecs.WTF.Are you rrealy need to bring me obout to Win again...

---

### Post by PlainShane on 2008-11-29
Oh my god. The gstreamer suggestion worked! Solved.

---

### Post by scott20 on 2008-11-30
Wow, thanks Tomatz. It's hard to believe is was just a simple solution.

---

### Post by lazy_bones1987 on 2008-12-17
thanx for the solution...it worked like a charm!

but do you experience a difference in the clarity? The movies seem to be 'pixelated' a bit!

Can it be coz of the video output?

---

### Post by Tomatz on 2008-12-17
> **lazy_bones1987 said:**
> thanx for the solution...it worked like a charm!

but do you experience a difference in the clarity? The movies seem to be 'pixelated' a bit!

Can it be coz of the video output?

Exactly right this is due to using X11 output instead of Xv. Hopefully intel will sort this bug out soon because its been over a year now :(

---

### Post by ibrabeicker on 2010-05-10
i solved my exactly same problem unistalling and installing again totem (the stock media player from ubuntu)

---

