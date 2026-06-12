---
title: "Video playback just stopped working"
date: 2009-08-17
forum: Multimedia Software
---

### Post by pedrotuga on 2009-08-17
Today when i trye to play a video, or mp3 song with totem, i get this message:

```
p@p-laptop:/media/disk$ totem MythBusters.S06E07.Alaska.Special.HDTV.XviD-K4RM4.avi 
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 85 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
p@p-laptop:/media/disk$ 
```

Totem simply open and closes. Other video applications (Miro, VLC, etc) have the same behaviour.

This is really annoying. I got really disappointed.


Don't know if this is related:
earlier today, I wanted to install Epiphany and typed:
```
apt-get install epiphany
```
To my surprise that installed some game rather than the browser which now is apparently on a package called epiphany-browser.
I don't know, usually games mess up with graphic definitions and stuff. I believe something in these lines might be causing all the problems. Otherwise I have no Idea why it just stoped working.

Any tips to fix this?

---

### Post by Infoteksec on 2009-09-14
Hi. Did you get anywhere with this?? My playback of AVI files stopped about at the same time as yours so I suspect it was caused by a faulty Ubuntu download.

Several multi-media players exhibit the same symptoms.

I just reloaded VLC hoping that a refresh might help. It didn't.

I thought it might be damaged AVI files on my PC but I tried to view Shoutcast TV and found that VLC exited silently as soon as I selected one. I can listen to Shoutcast radio so I suspect video codecs are broken somehow.

The same thing happened when I try to use VLC to view a DVB source. I find I can listen to DVB radio channels but not video.

Help would be appreciated.

Regards

Sorry - I forgot to mention that I'm using Ubuntu 9.04 on an Acer Aspire One.

BTW I tried to run TOTEM from the command line and got the following results:

root@Huey:/usr/share/doc/dvb-apps# totem /home/peter/Desktop/Woodworking/NYWS-9908.Table.Saw.Station.avi 

** (totem:22093): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha

The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 91 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


... and sound but no video.


Gave up and re-installed now everything works as before - I have no idea what went wrong.

---

