---
title: "Video playback not working!"
date: 2006-09-26
forum: Multimedia &amp; Video
---

### Post by tarman on 2006-09-26
Good evening.  I installed Dapper recently.  I followed the ubuntu customization guides to getting media codecs and installed everything in an attempt to play DVDs.  Unfortunately, I can't play any video - DVD, mov, wmv, etc.  

When I try to play anything (I've used gxine, totem, mplayer, vlc, and ogle), either the player closes itself or tells me I don't have the codecs.  I followed the guides to the letter, and other add-ons work (flash, java, etc.).  I've reinstalled all the codecs, rebooted, switched to the i686 kernel,tried to change from gstreamer to totem-xine, and still nothing.  Rhythmbox 0.9.5 works great though!

Any hints?  Thanks a lot!

Berg

---

### Post by Mr Frosti on 2006-09-26
To isolate this issue, lets stick to one environment. You can start by cleaning up any old packages that you have installed on your machine in an attempt to get this working. I am assuming that since you have followed the guides, you have modified your sources.list file and added new servers to the list. Also, you will need to "sudo apt-get update" to re-read the available software.

You will need two packages:

"sudo apt-get install xine w32codecs"

Xine is a very easy to use media player for Linux. W32codecs is a package that includes all of the codecs for all of the different audio and video formats. 

One this has been installed, try playing several media files. If they do not play, then please post any error messages you are still receiving. 

If it is working, then you will usually find a package that binds a player to Xine. For example, Kaffeine-xine will cause the Kaffeine player to use Xine as a backend. If Xine can play the file, so can Kaffeine.

---

### Post by tarman on 2006-09-27
Thanks very much, I'll have to give this a shot.  I did get the w32codecs, but I'm not sure if I got xine.  Either way a good idea to isolate the problem.  Thanks again,

Berg

---

### Post by tarman on 2006-09-27
Thanks for the help.  Unfortunately, it still doesn't work.  I try to load anything, and the player will close itself.  Command line says:

> tarman@tarman-desktop:~$ xine -check
bash: xine: command not found
tarman@tarman-desktop:~$ gxine -check
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
  sysname: Linux
  release: 2.6.15-27-686
  machine: i686
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 478 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I don't have xine, just gxine.  Any ideas?

---

### Post by dannyboy79 on 2006-09-28
the latest gstreamer ugly package is a must. did you read the unofficial wiki for ubuntu, did you try automatix, that made everything SO EAZY!!!!

---

### Post by tarman on 2006-09-29
automatix worked.  Not sure why I didn't try it before, I guess I didn't know what it did.  Thanks!

---

