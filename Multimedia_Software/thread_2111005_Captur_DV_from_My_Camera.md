---
title: "Captur DV from My Camera"
date: 2013-01-31
forum: Multimedia Software
---

### Post by DonyRaz on 2013-01-31
Hello guys.
I am a noob in Linux, but I install Xubuntu 12.04 and I try now to male it to capture movie from my DV Camera, using the firewire - IEEE 1394.
I don't know how to do it. 
Can somebody give me some recommendations?

Thanks for your kind support.:D

```
Linux razvan-A7N8X-E 3.2.0-37-generic #58-Ubuntu SMP Thu Jan 24 15:28:57 UTC 2013 i686 athlon i386 GNU/Linux
```

---

### Post by DonyRaz on 2013-02-01
Hello I install Cheese but when I open it, I got on the scree the info -Device not Found.
And the camera is plunged into computer using fire-wire cable and it is powered on the play mode.

What i have to do in order that the Cheese recognize my camera. I have a Sony DCR-TRV256E a Digital 8 cam with ieee 1394 facility.

---

### Post by FakeOutdoorsman on 2013-02-01
I've never used Cheese, but have you tried dvgrab?
```
dvgrab -rewind -size 0 output.dv
```

---

### Post by sudodus on 2013-02-01
Another alternative is Kino, but I have to admit that it is tricky to get it running (to manage the connection via firewire).

---

### Post by Johnny Buffalkill on 2013-02-01
I think Cheese is a webcam application.  I wouldn't expect it to be suitable for video capture.  

I've used Kino for firewire capture.  dvgrab looks to be  good as well , though I haven't tried that one.   Regardless of what software you use, to use firewire in Ubuntu, apparently you have to run your capture program as root.  This thread is where I got all my firewire information

                                  [http://forums.linuxmint.com/viewtopic.php?f=49&t=42348](http://forums.linuxmint.com/viewtopic.php?f=49&t=42348)
  
To run kino as root, use:

```
sudo kino
```Since you'll be running as root, the files you generate will be owned by root, so you'll have to change the permissions.  Or, you can get around this if you save them to an NTSF partition, which alot of people who dual boot do.

I like Kino for capture.  It gives you the option of adding the timestamp to the filename.  Its kind of nice to be able to check the dates of video I captured years ago.

---

### Post by DonyRaz on 2013-02-03
Hello,

I installed Kino and when I run ii as a root and try to capture, I get the message on the kino interface
***No AV/C compliant cam connected or not switched on***

and on the Terminal from which I started as root it is appear the message:
[I][B]rom1394_0 warning read failed 0x0000fffff0000414.

[/B][/I]What can I ust to do in this case?

---

### Post by DonyRaz on 2013-02-03
the message to the command:
dvgrab -rewind -size 0 output.dv 
is
Error: No camera exist.
with camera on in play mode and with or without sudo mode.

---

### Post by DonyRaz on 2013-02-09
Hello Guys, What I have done wrong?
I install kino from terminal. with all the dependencies mentioned in the Kino web site and I run Kino as root.
It is impossible to capture movies from my camera. through fire-wire
I did with success on windows.
Can somebody give me an answer?

Thanks a lot for your kind help.

---

