---
title: "[SOLVED] 8.04/all mediaplayers close instead of play file"
date: 2008-05-06
forum: Multimedia Software
---

### Post by nae5 on 2008-05-06
not solved but nevermind i back up for reinstalls

vlc 

naes@naestwo:~$ vlc
VLC media player 0.8.6e Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85
pure virtual method called
terminate called without an active exception
Aborted
naes@naestwo:~$

totem

naes@naestwo:~$ totem
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 46 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
naes@naestwo:~$

I don't understand why videos won't work now the players just close not a single frame shows.   these errors are from an avi, but i can't play flash videos either that work in firefox, but not when i take the file out of the /tmp/ directory and try to play it.

any help? thanks in advance. anymore infos i should post?  After, i went through steps from this link   [http://ubuntuforums.org/showthread.php?t=766683&highlight=medibuntu+repo](http://ubuntuforums.org/showthread.php?t=766683&highlight=medibuntu+repo)   making sure to only use the ones for hardy.

naes@naestwo:~$ totem --sync
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 43 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
naes@naestwo:~$


turns out some videos will work, but most don't.  i have no idea what's goin on..

today, some of the videos that weren't working i was able to open with mplayer, but then a few minutes later the same thing started happening, i open the player open the file and it just closes. or i right click select open with and the media player comes up and then closes.. ...

---

