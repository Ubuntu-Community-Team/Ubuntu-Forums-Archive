---
title: "Video wont play"
date: 2009-05-31
forum: Multimedia Software
---

### Post by atk_nut on 2009-05-31
Ever since I upgraded to 9.04 none of my videos will play.

The flash for a second and I get a blip of sound, but then the player disappears.  No error message or anything.  I've tried mplayer and movie player.

Any hints?

Thanks.

---

### Post by xc3RnbFO8P on 2009-06-01
Start VLC or Totem in Terminal ( show the error message if any here):
> vlc
> totem

---

### Post by utnubuuser on 2009-06-01
xine

---

### Post by atk_nut on 2009-07-13
OK here it goes.  It's taken a while to get back to this:

Here's the error:

henry@henry-laptop:~$ totem
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 82 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
henry@henry-laptop:~$ 


Any ideas?

THanks.

---

### Post by k956411 on 2009-07-13
have you managed to solve this issue yet?

i get exactly the same problem since i upgraded to 9.04
i have tried mplayer, totem and vlc and all do the same. it appears, the window resizes to the video size then disappears.

---

### Post by atk_nut on 2009-07-13
Nope, haven't solved it yet.  I'm hoping someone will help.

Thanks.

---

### Post by Randymanme on 2009-07-13
When the video players shut of, I get a message box that says "Component missing.  The player does not have the capabilities to play back this content."  The message box also includes a "detail button," that says "The following components are required: Video/X-HX-AVCI.'  Well, that's pretty straight forward; *but* I don't know what to do with that information.  Will somebody walk me through?  Thanks.

---

### Post by Randymanme on 2009-07-13
Oh, I forgot; I have Linux 9.04 and Firefox 3.5.

---

### Post by mc4man on 2009-07-13
Change your video output from 'default' (probably Xv) to X11

for gstreamer apps go in terminal

```
gstreamer-properties
```

Under video tab choose " X Window System (No Xv)

For other players adjust in the players settings, preferences, ect.

For vlc
 tools -> preferences, highlight the video icon, on the right side is a drop down box for "Output'. Switch from default to X11 video output.

Other players are similar.

---

### Post by atk_nut on 2009-07-14
Thanks for the tip.

I tried the gstreamer settings.  Same problem.  It just appears for a moment, then disappears.  Error:

totem
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 82 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
henry@henry-laptop:~$

---

### Post by mc4man on 2009-07-14
you may want to see  if a player other than totem works using X11.

Otherwise search specific to your display adapter and possibly the intial line
> /var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead

There certainly seems to be some issues with jaunty and intel video and some ati cards (and totem in general

these could provide you with some basic info on your system

```
 sudo lshw -C display
```

```
 glxinfo | grep render
```


(( myself only have nvidia and while have tried jaunty have returned/stayed with hardy till something better comes along

---

### Post by k956411 on 2009-07-14
I have it running on a thin light laptop with the intel graphics onboard so i may be having a known issue.

i will try the fix here [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) and let you know if it works

---

### Post by ronjan41 on 2009-07-14
I get the same as atk_nut. Used to work fine on 8.10

---

### Post by k956411 on 2009-07-14
Ok i tried the fix in the link above but all that succeeded in doing is leaving me with a black screen.

the boot splash screen comes up briefly then disappears and then nothing.

had to boot to recovery mode and automatically fix graphics problems to get back to where i was. so still in the same boat. players open then disappear again straight away.

Mine also worked fine before upgrading to 9.04

---

### Post by ehamman on 2009-07-21
I had the same issue after I upgraded, but thanks to the preference setting have got VLC and MPlayer going.  Only Xine seems to crash even just trying to open it.

---

### Post by igorzwx on 2009-07-21
Friends!

What are you doing with players?

I cannot understand.

Do you have all codecs installed?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

