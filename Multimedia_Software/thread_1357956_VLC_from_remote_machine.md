---
title: "VLC from remote machine"
date: 2009-12-17
forum: Multimedia Software
---

### Post by korvirlol on 2009-12-17
Ive got my ubuntu desktop on a desk that is on the far side of the room from my TV. I have another linux desktop connected to that TV that i use to play videos when nothing is on TV. 

The machine that is connected to the TV uses vlc, and here is my problem:

After just eating a pizza, the last thing i want to move. I want to be able to queue video files for vlc to play on that tv from a remote machine. 

So, i tried to ssh into the other machine and launch a VLC video from the command line. I certainly wasnt expecting this to work, and respectively, it didnt. 

Is this even possible? I tried googling it, but i couldnt find any relevant information about it. 

Im not bent on using VLC, if a different media player supports this kind of functionality, thats fine to.

Thanks for any suggestions!

---

### Post by issih on 2009-12-17
vlc supports both an ncurses and a web interface, you can enable them from within vlc's preferences or indeed via the command line.

To get the web interface enabled, open vlc's preferences, select to view all, then navigate to interface->main interfaces and enable whatever you want.

Once that is done you can log onto the web interface at

[http://hostIPADDRESS:8080](http://hostIPADDRESS:8080)

I think thats the right port..

---

