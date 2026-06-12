---
title: "Totem movie player won't work...."
date: 2009-08-12
forum: Multimedia Software
---

### Post by Dr.AMA on 2009-08-12
[B][COLOR="DimGray"]Hi all....

All of a sudden totem movie player won't play any video...

It opens up all right, but when i click on play file, it just closes and winds up.... It was able to play the same movie a day earlier....

what I did in between was installing my updates via synaptic,   what i think IS the cause of it all, installing the kde4  using synaptic....

But even after i totally removed the kde4 envt totem won't play...?
I know that the info i'm giving is inadequate, but then I'm a linux newbie, and don't know what exactly I need to tell you people to help me fix the issue...

Please help.

---------------------------------------------------------
[same problem]("http://linuxgator.org/forums/viewtopic.php?f=21&t=826#p3877")[/COLOR][/B]

---

### Post by doas777 on 2009-08-12
try reinstalling totem:
```
sudo apt-get install totem-gstreamer --reinstall
```

---

### Post by Dr.AMA on 2009-08-12
i really try to install totem again but doesn't work ...............

---

### Post by bottlehead on 2009-08-15
Hi, I have what appears to be the same problem.

I upgraded from 8.10 to 9.04 and find that Totem and VLC both quit as soon as I try to play anything.

I started Totem from the command line, with the avi I wanted as the first argument, and got this message:

The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 88 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Running VLC generated a similar response:

[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82

Not sure what I can do to fix this.

---

### Post by Dr.AMA on 2009-08-16
[B]I observed something too,i think it related to the problem , the compiz doesn't work .??!!
is there any one noted that ???[/B]

---

### Post by doas777 on 2009-08-18
> **bottlehead said:**
> Hi, I have what appears to be the same problem.

I upgraded from 8.10 to 9.04 and find that Totem and VLC both quit as soon as I try to play anything.

I started Totem from the command line, with the avi I wanted as the first argument, and got this message:

The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 88 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Running VLC generated a similar response:

[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82

Not sure what I can do to fix this.

is the file you want to open smaller than the amount of free ram you posses?

---

### Post by doas777 on 2009-08-18
> **Dr.AMA said:**
> [B]I observed something too,i think it related to the problem , the compiz doesn't work .??!!
is there any one noted that ???[/B]

that can affect matters, but totem shouldn't care about whether compiz is there or not (i use it on boxes both with and without compiz). do you have a compiz capable vidcard/driver installed?

---

### Post by EpoxyRepair on 2009-10-18
I recently started seeing this error recently for both VLC and Totem. Removing compiz or reinstalling VLC and Totem made no difference to me.

Both VLC and Totem crashed with BadAlloc when trying to play video media from files regardless of format or DVD.   

As a shot in the dark I removed the /etc/X11/xorg.conf (after backing up)
and ran dpkg-reconfigure -phigh xserver-xorg. After I restarted X everything worked ok, and is still going ok today. 

I can't see why this worked as the new xorg.conf looks exactly like the old one to me.

---

