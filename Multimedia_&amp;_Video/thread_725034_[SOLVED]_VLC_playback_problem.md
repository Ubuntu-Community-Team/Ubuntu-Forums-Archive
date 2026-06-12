---
title: "[SOLVED] VLC playback problem"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by Nelis on 2008-03-15
hi people

I can't play anything (.avi, .mpeg) in my VLC player. When I open an avi file in VLC this is what happens:

```
VLC media player 0.8.6c Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  83
  Current serial number in output stream:  84
pure virtual method called
terminate called without an active exception
Afgebroken (core dumped)
```

I don't know what it means and I'm also quite new to linux but the VLC worked fine in windows....
please help me

greetz, nelis

---

### Post by xc3RnbFO8P on 2008-03-15
It seems to be a bug:

> [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

---

### Post by Nelis on 2008-03-15
okey, so I have tried:

```
niels@AluMinie:~$ vlc --sync
VLC media player 0.8.6c Janus
vlc: unknown option or missing mandatory argument `--sync'
Try `vlc --help' for more information.
niels@AluMinie:~$ 
```

this what happens...
maybe I forgot to type anything but I couldn't find the --sync in the help file....

---

### Post by xc3RnbFO8P on 2008-03-15
Did you check the link, there is many solution, for example:


> I just reconfigured the xserver-xorg-core package.... (I have 2:1.3.0.0.dfsg-12ubuntu8.3)

$ sudo dpkg-reconfigure xserver-xorg-core

My Eclipse install is working fine again... (technically, I dpkg-reconfigure'd the xserver-xorg package as well, but not sure if that was necessary)

> completly resolved with : sudo ln -sf /usr/lib/xorg/modules/extensions/libglx.so.169.07 /usr/lib/xorg/modules/extensions/libglx.so

i dont know why...


---

### Post by Nelis on 2008-03-15
I've tried the 2 solutions that you mentioned in your previous post, but they didn't work :(
I even tried downgrading the xserver-xorg-core from version 8,3 to 8,0 like it said in the post but still no go :(

maybe something is wrong with my video driver??
I have an VIA Unichrome CL266 or something

---

### Post by xc3RnbFO8P on 2008-03-15
At your own risk you could try this:

> sudo aptitude install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8
sudo aptitude safe-upgrade

---

### Post by Nelis on 2008-03-18
i have tried it, but the xserver-xorg-core is version 8,3 now
is that right?
it still does not work by the way...

gr. nelis

---

### Post by xc3RnbFO8P on 2008-03-19
Try one simple thing:

I use Pcman file manager to do this:
in tools> Open current folder as root (it will open a new window)
in new window: View> Show hidden files (in home folder)
Rename **.vlc** to **.vlc.old**

Try to play .avi and if it plays:

In VLC player: 
In preferences , just **save**.
Then you can compare the **vlcrc** file in **old** and **new** in the **.vlc** folder.
Search AVI. 
If you find something interesting, post it here.

---

### Post by Nelis on 2008-03-20
It works!!!!!!! :)
I noticed that in the .vlc.old map, there is an extra map called cache, wich isn't there in the .vlc map
but thanks a bunch, 

gr. Nelis

---

### Post by xc3RnbFO8P on 2008-03-20
:(

---

### Post by Nelis on 2008-03-20
ok maybe I was a little fast but now it doesn't work anymore :(

I updated ubuntu and logged of, then logged in again and now vlc has the same error as before

:(

---

### Post by xc3RnbFO8P on 2008-03-20
Do you get same error?

---

### Post by xc3RnbFO8P on 2008-03-20
In the file **vlcrc** I got this:

> [avi] # AVI demuxer

# Force interleaved method (boolean)
#avi-interleaved=0
# Force index creation (integer)
#avi-index=0

---

### Post by xc3RnbFO8P on 2008-03-20
Just install this again:

> wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb)
sudo dpkg -i w32codecs_20071007-0medibuntu1_i386.deb

---

### Post by Nelis on 2008-03-22
> **Ringi said:**
> In the file **vlcrc** I got this:

I looked up my vlcrc file and got this
from the .vlc.old map:
```
[avi] # AVI demuxer

# Forceer de interleave methode (boolean)
#avi-interleaved=0
# forceer de creatie van een index (heel getal)
#avi-index=0
```

and the normal .vlc map:
```
[avi] # AVI demuxer

# Forceer de interleave methode (boolean)
#avi-interleaved=0
# forceer de creatie van een index (heel getal)
#avi-index=0
```

It's all in dutch by the way :)
but there is no difference between them

---

### Post by xc3RnbFO8P on 2008-03-23
Did you install the codecs again?

---

### Post by Nelis on 2008-03-24
Yes, I did but still the same...

I've tried to play an .avi file in totem and I got the same error as in vlc:
```
(totem:6856): GStreamer-CRITICAL **: gst_value_set_fraction: assertion `denominator != 0' failed

** (totem:6856): CRITICAL **: gst_video_calculate_display_ratio: assertion `num > 0' failed
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 56 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```
It also says it received an X Window System error or something...
maybe that's where the problem is...:confused:

---

### Post by xc3RnbFO8P on 2008-03-25
It is up to you, install Ubuntu again!
Check md5sum (K3B shows it automatically when you choose the ISO file) 
compare fx. with 32 bit Gutsy Gibbon 
(d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso)
Burn new Live Disk, max 8x.

---

### Post by Nelis on 2008-03-29
I found out the problem was caused by the screen resolution being set to high
I've tried to run VLC in 1024x748 and it stopped working,
but when I ran VLC in 640x480, it worked flawlessly!

I tried to boost the performance of my pc a little bit by putting in more RAM memory.
Sadly however, I destroyed the motherboard and RAM altogether because the RAM wasn't placed properly. :(

So after buying a fresh new (and expensive) motherboard and RAM memory, I installed Ubuntu again and now VLC works fine again

but anyway, thanks for your help! :)

---

### Post by Nelis on 2008-03-29
o, just one more question:
how do I mark this post as "solved"?

yes, I'm a newbie :)

---

### Post by xc3RnbFO8P on 2008-03-29
In thread tools.
640x480 it is like going back to the 90's :(

---

### Post by Nelis on 2008-04-01
good old MS-DOS :)

---

