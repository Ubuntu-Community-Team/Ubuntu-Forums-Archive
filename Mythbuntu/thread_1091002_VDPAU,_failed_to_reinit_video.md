---
title: "VDPAU, failed to reinit video"
date: 2009-03-08
forum: Mythbuntu
---

### Post by mathog on 2009-03-08
For some reason or other tonight the vdpau version of mythtv is acting up.  The tuner is an HDHomerun.  I have not changed any of this software lately.  The failure mode is:

```
watching TV ->
EPG ->
select a program ->
m
error message:  failed to reinit video
hit enter
error message: Error was encountered displaying video
hit enter
The top level mythfrontend menu reappears
```

These seem to correlate with these messages in mythwelcome:

```
2009-03-08 19:31:13.662 AFD: Opened codec 0x90d5520, id(AC3) type(Audio)
2009-03-08 19:31:15.966 NVP: prebuffering pause
2009-03-08 19:31:23.388 NVP: prebuffering pause
2009-03-08 19:31:27.263 NVP: Prebuffer wait timed out 10 times.
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode:  145
  Minor opcode:  32
  Resource id:  0x26013a2
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode:  145
  Minor opcode:  4
  Resource id:  0x26013a2
2009-03-08 19:31:27.781 VideoOutputXv Error: Failed to initialize buffers for codec MPEG2 VDPAU
2009-03-08 19:31:27.781 VideoOutputXv Error: Failed to initialize buffers for codec MPEG2 VDPAU
2009-03-08 19:31:27.781 VideoOutputXv Error: Failed to get any video output Exiting playback.
2009-03-08 19:31:27.781 VideoOutputXv Error: InputChanged(): Failed to recreate buffers
2009-03-08 19:31:27.781 ReinitVideo(): videoOutput->IsErrored()

```

This is nvidia 180.290 the mythtv pieces are all .21.0+fixes20018-openglvdpau-0ubuntu0.

Any ideas?

---

### Post by mathog on 2009-03-09
By the way, I have NOT seen this issue when changing channels using the up/down keys to navigate while actively watching TV, and then changing the channel that way.  Only the EPG does it.  Since there is no video going in the EPG (some limitation of VDPAU) I can't help wondering if maybe there isn't some initialization step required to make VDPAU work, which is present on starting "Watch TV", and possibly not needed on a direct "change channel", but missing on exiting EPG to watch the new channel.

---

### Post by jyavenard on 2009-03-09
I've seen this issue happening when realtime priority is activated.

Disable it.

Otherwise no idea why it would do that.

---

### Post by mathog on 2009-03-09
> **jyavenard said:**
> I've seen this issue happening when realtime priority is activated.

Disable it.

Otherwise no idea why it would do that.

Realtime priority was not in use.

This might be relevant:  the system has a monitor for screen 0 and TV-OUT (NTSC) for screen 1, with mythtv shown on screen 1.  Possibly this is something like a focus issue?  Clearly the focus has changed to screen 1 when the tests are performed (or the events wouldn't be delivered to mythtv) but it could be that something in X11 besides input events didn't switch over correctly with the focus.

---

### Post by mathog on 2009-03-11
> **mathog said:**
> Possibly this is something like a focus issue?

This evening upgraded to jyavenard's latest (108.37) versions.  Same issue.

Then in trying to document this I was clicking back and forth between screen 0 and screen 1 and avoided "failed to reinit".  After some more experimentation, it turns out that the following sequence suppresses the error:

```
screen 1:  watching TV
           -> EPG
           -> select channel
screen 0:  click on any window (change focus)
screen 1:  click in EPG (change focus back)
           m
channel changes, no reinit error

```

I did this 5 times in a row with no reinit, whereas if I skipped the screen 0 step in several other attemps, it always had the reinit error.  It didn't matter if the "-> select channel" was before or after the screen 0 step.

So, I think this is somehow focus related, and perhaps only shows up on dual screen systems.  I have attached my xorg.conf, since it is probably relevant.  After posting this I will try it again with the monitor on screen 0 detached and the system rebooted.  Perhaps if there is no physical device there focus won't be an issue.

---

### Post by mathog on 2009-03-11
> **mathog said:**
> Perhaps if there is no physical device there focus won't be an issue.

No such luck.  With only the TV-OUT running it still does it, and since there is no other window visible, there is no way to avoid it.  When myth is running on screen 0 (screen 1 == TV-OUT present, but only the desktop active there) it also generates this error.

It's definitely a VDPAU issue, since mythfrontend (or mythwelcome) logs this every time it happens:

```
2009-03-10 22:12:30.831 VideoOutputXv Error: Failed to initialize buffers for codec MPEG2 VDPAU
2009-03-10 22:12:30.831 VideoOutputXv Error: Failed to initialize buffers for codec MPEG2 VDPAU
2009-03-10 22:12:30.831 VideoOutputXv Error: Failed to get any video output Exiting playback.
2009-03-10 22:12:30.831 VideoOutputXv Error: InputChanged(): Failed to recreate buffers
2009-03-10 22:12:30.831 ReinitVideo(): videoOutput->IsErrored()
2009-03-10 22:12:30.985 NVP: Prebuffer wait timed out 10 times.

```

The graphics card is an ASUS 256MB Geforce 8400GS.

---

### Post by mathog on 2009-03-11
Output from "vdpinfo" and "xdpyinfo" is attached.  The former is identical for screens 0 and 1, except for the number of the screen, and
the latter has the information for both screens.

---

### Post by jyavenard on 2009-03-28
A quick note to say that my latest vdpau patches fix this bug....

will prevent other X11 errors (bad drawable surfaces type)

---

