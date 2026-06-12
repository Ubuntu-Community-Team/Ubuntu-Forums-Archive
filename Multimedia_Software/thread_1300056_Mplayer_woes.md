---
title: "Mplayer woes"
date: 2009-10-24
forum: Multimedia Software
---

### Post by H3l0 on 2009-10-24
Ok im finally going to do it.

This may be a solved issue already for some but I am having trouble finding a solution for this particular problem.  

I am currently running Ubuntu 8.04 and have installed Mplayer and the w32codecs from Medibuntu repositories.  Despite this the player decides to give me the message: "ERROR: Could not open required DirectShow codec wmvdmod.dll"  or someting of that nature.   The thing that is weird to me is that the video still plays (quite well I might add.)   My thought is that some configuration file is looking in the wrong place for that particular dll.  I have confirmed that the wmvdmod.dll file is in the codec folder under /usr/lib and have made a copy of it in the directory /usr/local/lib/codecs.  I can play it from the terminal and it will not give me that message.  Any Ideas???

---

### Post by vinutux on 2009-10-25
mplayer used some non-native libraries....

use native apps like vlc or gstreamer (totem)....etc

---

### Post by H3l0 on 2009-10-25
...............guess I will just deal with the error message.

---

### Post by andrew.46 on 2009-10-26
Hi H310,

> **H3l0 said:**
>  "ERROR: Could not open required DirectShow codec wmvdmod.dll"  or something of that nature. 

Can I ask for 2 extra pieces of information? Could you run your file from the commandline as follows, and post the full command and terminal output here:

```
mplayer -v **[COLOR="Red"]*my_troublesome_file.avi*[/COLOR]**
```

Obviously putting your own file in there :). Could you also show the results of the following:
```

sudo find /usr -iname 'wmvdmod.dll'
```

which will demonstrate the exact location of the missing codec on your system.

Andrew

---

### Post by H3l0 on 2009-10-26
Hey thanks for the reply!

I believe I stated in the original post that I have already run this from the terminal as a troubleshooting step and got no error message.  Did this again anyway just to confirm and got the same result, playback  with no error messages.

as for the other piece of code:

"colin@LinuxLappy:~/Videos$ sudo find /usr -iname 'wmvdmod.dll'
 [sudo] password for colin: 
 /usr/lib/codecs/wmvdmod.dll
 /usr/local/lib/codecs/wmvdmod.dll"

---

### Post by H3l0 on 2009-10-28
> **H3l0 said:**
> ...............guess I will just deal with the error message.



:???:

---

### Post by H3l0 on 2009-10-30
"Bump"

---

