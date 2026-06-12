---
title: "can't play video"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by robpick on 2006-06-09
I recently bought a JVC DV camera and am trying to playback/ edit the video on my computer. I'm a newbie so please bear with the description.

I'm running **Dapper Drake **on a 1 GHz Duron with 256mb ram.
I have Kino v 0.8.0 and dvgrab 1.8 installed.

If I play back the captured video in totem, I get the following message:
[FONT="Courier New"]totem dvgrab-001.avi
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
(Details: serial 47 error_code 11 request_code 142 minor_code 19)
(Note to programmers: normally, X errors are reported asynchronously;
that is, you will receive the error a while after causing it.
To debug your program, run it with the --sync command line
option to change this behavior. You can then get a meaningful
backtrace from your debugger if you break on the gdk_x_error() function.)[/FONT]

I get the same message if I use Kino to playback when using the XVideo display option. If I use GDK, I can paly the video back but it is in super slow motion and the audio is chopped up. If I use MPlayer, the video is super slow and the audio finished way before the video does.

Overall it feels like there is something misconfigured with my display driver. Please help.

Thanks
Rob

---

