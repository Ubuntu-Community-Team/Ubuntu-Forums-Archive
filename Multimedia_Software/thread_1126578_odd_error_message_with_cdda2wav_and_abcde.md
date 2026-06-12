---
title: "odd error message with cdda2wav and abcde"
date: 2009-04-15
forum: Multimedia Software
---

### Post by logos34 on 2009-04-15
Sometimes when I rip a cd with ABCDE cdparanoia hits a bad track it can't extract, (like this):

> Ripping from sector  324921 (track 27 [0:00.00])
	  to sector  339479 (track 27 [3:14.08])

outputting to /home/user/abcde.7e11ae1b/track27.wav

[B][COLOR="Red"] (== PROGRESS == [               +V             | 339479 00 ] == 8-X * ==)   
Removing aborted file: /home/user/abcde.7e11ae1b/track27.wav[/COLOR][/B]

Done.

[ERROR] abcde: The following commands failed to run:
readtrack-27: /usr/bin/cdparanoia -v -X returned code 73
Finished. Not cleaning /home/user/abcde.7e11ae1b.

and it aborts.  So then I change the ripper in .abcde.conf to cdda2wav 
> 
# CD reader program to use - currently recognized options are 'cdparanoia',
# 'cdda2wav', 'dagrab', 'cddafs' (Mac OS X only) and 'flac'.
CDROMREADERSYNTAX=cdda2wav

to basically grab the track in burst mode without error correction,  Usually works but it outputs this curious error message (red):
> 
$ **abcde -o ogg 27**
Executing customizable pre-read function... done.
Getting CD track info... Grabbing tracks: 27
abcde: attempting to resume from /home/user/abcde.7e11ae1b..
Creating playlist...
Erase, Append to, or Keep the existing playlist file? [e/a/k] (e): a
Grabbing track 27: The Motors / Dancing The Night Away...
Type: ROM, Vendor 'ASUS    ' Model 'DRW-1608P2      ' Revision '1.41' MMC+CDDA
569344 bytes buffer memory requested, 4 buffers, 55 sectors
#icedax version 1.1.6, real time sched., soundcard, libparanoia support
AUDIOtrack pre-emphasis  copy-permitted tracktype channels
      1-27           no              no     audio    2
Table of Contents: total tracks:27, (total time 75:26.30)
  1.( 2:58.12),  2.( 2:26.24),  3.( 3:04.54),  4.( 2:42.45),  5.( 4:17.64),
  6.( 3:34.28),  7.( 3:42.65),  8.( 1:43.72),  9.( 2:26.48), 10.( 2:43.51),
 11.( 2:05.01), 12.( 2:53.08), 13.( 3:11.03), 14.( 3:00.24), 15.( 4:22.33),
 16.( 2:31.45), 17.( 3:18.50), 18.( 2:41.09), 19.( 2:06.65), 20.( 0:51.48),
 21.( 2:48.49), 22.( 2:11.72), 23.( 2:58.39), 24.( 3:34.64), 25.( 2:01.33),
 26.( 1:53.65), 27.( 3:14.09)

Table of Contents: starting sectors
  1.(       0),  2.(   13362),  3.(   24336),  4.(   38190),  5.(   50385),
  6.(   69724),  7.(   85802),  8.(  102517),  9.(  110314), 10.(  121312),
 11.(  133588), 12.(  142964), 13.(  155947), 14.(  170275), 15.(  183799),
 16.(  203482), 17.(  214852), 18.(  229752), 19.(  241836), 20.(  251351),
 21.(  255224), 22.(  267873), 23.(  277770), 24.(  291159), 25.(  307273),
 26.(  316381), 27.(  324921), lead-out(  339480)
CDINDEX discid: YGcNiG6fFcaeeZmzQt6qNO0aNdI-
CDDB discid: 0x7e11ae1b
CD-Text: not detected
CD-Extra: not detected
samplefile size will be 34242812 bytes.
recording 194.1200 seconds stereo with 16 bits @ 44100.0 Hz ->'/home/user/abcde.7e11ae1b/track27'...
**[COLOR="Red"]cdda2wav: Operation not permitted. cannot set posix realtime scheduling policy[/COLOR]**
percent_done:
100%  track 27 recorded successfully
Encoding track 27 of 27: Dancing The Night Away...
Opening with wav module: WAV file reader
Encoding "/home/user/abcde.7e11ae1b/track27.wav" to 
         "/home/user/abcde.7e11ae1b/track27.ogg" 
at quality 5.00
	[ 99.9%] [ 0m00s remaining] \ 

Done encoding file "/home/user/abcde.7e11ae1b/track27.ogg"

	File length:  3m 14.0s
	Elapsed time: 0m 15.9s
	Rate:         12.1763
	Average bitrate: 164.1 kb/s

Tagging track 27 of 27: Dancing The Night Away...
Finished.


Track seems ok afterward.  Anyone know what it means? (maybe andrew.46 does)

---

### Post by mc4man on 2009-04-15
I believe it's a somewhat irrelevant message as that (posix realtime scheduling policy) would only be a factor if the machine was under a heavy load elsewhere. (or possibly old, underpowered hardware

I would think that cdda2wav would need to be running under root to set. (posix realtime scheduling policy

Could be wrong though

---

### Post by logos34 on 2009-04-15
not under heacy load, or old hardware.

Though I am running the UbuntuStudio realtime (x64), low-latency kernel.  Wonder if that's a factor...

I'll try running abcde as root, see what happens

---

### Post by foxmulder881 on 2009-10-15
I've just been ripping some of my old CD's with **abcde+cdda2wav** and I receive the same little 'red' message and that's with running it on Fedora 11. I had a feeling it was not really an error of any kind but more of a notification of something irrelevant. Because the resulting FLAC files have been flawless so far. Woot!

---

