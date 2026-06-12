---
title: "Flash player don't works."
date: 2013-07-02
forum: Multimedia Software
---

### Post by lampadron on 2013-07-02
Hi everyone.

I have a problem with my flash plugin. Seems like my browser(chromium) can't load it. I'm sure that flash player was installed correctly because I can see it in the list of plugins( the version is [COLOR=#000000][FONT=Ubuntu]11.2 ). Does somebody know what I should do?

Thanks for your future replies. [/FONT][/COLOR]

---

### Post by ajgreeny on 2013-07-02
What hardware, particularly the CPU and graphic card?

Some CPUs are not sse2 enabled so can not use the newest version of flash, 11.2 or later, including the 11.7 now used as pepperflash in Google-Chrome.

Run ```
cat /proc/cpuinfo | grep sse2
``` and see if you get any output from that.  If you see nothing you have a non-sse2 cpu and will need to either forget about flash or use a previous version.

See [Flash 11.1.102-63]("http://ubuntuforums.org/showthread.php?t=1953796") for info.

---

### Post by lampadron on 2013-07-02
I'm using:
processor  AMD sempron(tm) 2500+
g card       ATI Radeon 9550 

Where I can find the information about them? I mean can't find out if they support adobe flash player 11.

---

### Post by lampadron on 2013-07-02
It looks like my processor is too slow. Is there another way to run flash on my computer?

---

### Post by ajgreeny on 2013-07-02
See the link in my previous post which gives details of how to install the previous flash version which did work with your sempron CPU, which you will find is not sse2 compliant and will probably show no output from command ```
cat /proc/cpuinfo | grep sse2
```

---

### Post by lampadron on 2013-07-04
I don't see any output form the command 
[COLOR=#000000][FONT=Ubuntu Mono]```


```[/FONT][/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]cat /proc/cpuinfo | grep sse2
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

So I can't run flash 11.1, right? [/FONT][/COLOR]

---

### Post by lampadron on 2013-07-04
I don't see any output form the command 
[COLOR=#000000][FONT=Ubuntu Mono]```


```[/FONT][/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]cat /proc/cpuinfo | grep sse2
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

So I can't run flash 11.1, right? [/FONT][/COLOR]

---

### Post by ajgreeny on 2013-07-04
> **lampadron said:**
> I don't see any output form the command 
[COLOR=#000000][FONT=Ubuntu Mono]```


```[/FONT][/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]cat /proc/cpuinfo | grep sse2
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

So I can't run flash 11.1, right? [/FONT][/COLOR]

No that's not right.  You can use flash 11.1 from the link I gave, but you will not be able to run flash 11.2 or later versions if your cpu is not sse2 compliant, which yours isn't judging by the lack of output from that command.

Follow the instructions on the link I gave to download and install flash 11.1.  Be aware that some sites will not allow flash if using that version of flash, which they say is not secure, however, I am not aware of any way round that problem.  Also you will find that the FF add-on flashaid, mentioned in the post, is not available any more, so you will have to install manually by extracting the archive to your system and copying the** libflashplayer.so** file to you ~/.mozilla/plugins folder, which you will probably have to make first.

---

### Post by lampadron on 2013-07-05
> **awapal said:**
> Unistall your flash player and download it again

:) I've already tried it.

---

### Post by ajgreeny on 2013-07-05
As I have said a few times, there is no point trying to use the current most up-to-date flash because it **WILL NOT WORK** with your cpu; if it is imperative that you must use flash, your only way will be to get the flash 11.2.02-63 from the link I gave you, extract it and copy the .so file to ~/.mozilla/plugins folder which you may have to make first.

Sorry, my previous post gave you an incorrect pathway for that plugins folder.  Apologies for that glitch!

---

### Post by lampadron on 2013-07-06
Thanks :D!

---

### Post by lampadron on 2013-07-06
Thank you all for your replies, especially you [COLOR=#000000]**ajgreeny **[/COLOR]:D, now it's working !

---

