---
title: "mplayer not working right"
date: 2008-12-29
forum: Multimedia Software
---

### Post by Silvernail on 2008-12-29
Mplayer sometimes doesn't work as illustrated in the howtos. Or instructions  from the manuel.

I have this line in the .mplayer > registry

```
	   &#65533;&#65533;&#65533;&#65533;   HKLM    &#65533;&#65533;&#65533;&#65533;   HKCU       /   HKCU\SOFTWARE\Microsoft\Scrunch\CPU Clock Speed         9   HKCU\SOFTWARE\Microsoft\Scrunch\Current Post Process Mode          1   HKCU\SOFTWARE\Microsoft\Scrunch\Post Process Mode       &#65533;&#65533;&#65533;&#65533;   HKCU\SOFTWARE\Microsoft\Scrunch   &#65533;&#65533;     7   HKCU\SOFTWARE\Microsoft\Scrunch\Force Post Process Mode   &#65533;&#65533;&#65533;&#65533;   0   HKCU\SOFTWARE\Microsoft\Scrunch\Video\Resolution    (#    -   HKCU\SOFTWARE\Microsoft\Scrunch\Video\BitRate   &#65533;  
``` 

With the word Microsoft showing up so much is it possible I have the wrong version?

Seems like I got some updates recently.

TIA
Dave

---

### Post by frenchn00b on 2008-12-29
> **Silvernail said:**
> Mplayer sometimes doesn't work as illustrated in the howtos. Or instructions  from the manuel.

I have this line in the .mplayer > registry

```
	   &#65533;&#65533;&#65533;&#65533;   HKLM    &#65533;&#65533;&#65533;&#65533;   HKCU       /   HKCU\SOFTWARE\Microsoft\Scrunch\CPU Clock Speed         9   HKCU\SOFTWARE\Microsoft\Scrunch\Current Post Process Mode          1   HKCU\SOFTWARE\Microsoft\Scrunch\Post Process Mode       &#65533;&#65533;&#65533;&#65533;   HKCU\SOFTWARE\Microsoft\Scrunch   &#65533;&#65533;     7   HKCU\SOFTWARE\Microsoft\Scrunch\Force Post Process Mode   &#65533;&#65533;&#65533;&#65533;   0   HKCU\SOFTWARE\Microsoft\Scrunch\Video\Resolution    (#    -   HKCU\SOFTWARE\Microsoft\Scrunch\Video\BitRate   &#65533;  
``` 

With the word Microsoft showing up so much is it possible I have the wrong version?

Seems like I got some updates recently.

TIA
Dave


~/.mplayer$ less registry
"registry" may be a binary file.  See it anyway?

I also have binary in mplayer, and it works great.

DO you have the codecs installed ?

---

### Post by Silvernail on 2008-12-29
Here it is with a 'hexedit':


```
00000000   09 00 00 00  E7 FF FF FF  04 00 00 00  48 4B 4C 4D  ............HKLM
00000010   00 00 00 00  E7 FF FF FF  04 00 00 00  48 4B 43 55  ............HKCU
00000020   00 00 00 00  04 00 00 00  2F 00 00 00  48 4B 43 55  ......../...HKCU
00000030   5C 53 4F 46  54 57 41 52  45 5C 4D 69  63 72 6F 73  \SOFTWARE\Micros
00000040   6F 66 74 5C  53 63 72 75  6E 63 68 5C  43 50 55 20  oft\Scrunch\CPU
00000050   43 6C 6F 63  6B 20 53 70  65 65 64 04  00 00 00 02  Clock Speed.....
00000060   00 00 00 04  00 00 00 39  00 00 00 48  4B 43 55 5C  .......9...HKCU\
00000070   53 4F 46 54  57 41 52 45  5C 4D 69 63  72 6F 73 6F  SOFTWARE\Microso
00000080   66 74 5C 53  63 72 75 6E  63 68 5C 43  75 72 72 65  ft\Scrunch\Curre
00000090   6E 74 20 50  6F 73 74 20  50 72 6F 63  65 73 73 20  nt Post Process
000000A0   4D 6F 64 65  04 00 00 00  00 00 00 00  04 00 00 00  Mode............
000000B0   31 00 00 00  48 4B 43 55  5C 53 4F 46  54 57 41 52  1...HKCU\SOFTWAR
000000C0   45 5C 4D 69  63 72 6F 73  6F 66 74 5C  53 63 72 75  E\Microsoft\Scru
000000D0   6E 63 68 5C  50 6F 73 74  20 50 72 6F  63 65 73 73  nch\Post Process
000000E0   20 4D 6F 64  65 04 00 00  00 00 00 00  00 E7 FF FF   Mode...........
000000F0   FF 1F 00 00  00 48 4B 43  55 5C 53 4F  46 54 57 41  .....HKCU\SOFTWA
00000100   52 45 5C 4D  69 63 72 6F  73 6F 66 74  5C 53 63 72  RE\Microsoft\Scr
00000110   75 6E 63 68  04 00 00 00  8C B2 00 00  04 00 00 00  unch............
00000120   37 00 00 00  48 4B 43 55  5C 53 4F 46  54 57 41 52  7...HKCU\SOFTWAR
00000130   45 5C 4D 69  63 72 6F 73  6F 66 74 5C  53 63 72 75  E\Microsoft\Scru
00000140   6E 63 68 5C  46 6F 72 63  65 20 50 6F  73 74 20 50  nch\Force Post P
00000150   72 6F 63 65  73 73 20 4D  6F 64 65 04  00 00 00 FF  rocess Mode.....
00000160   FF FF FF 04  00 00 00 30  00 00 00 48  4B 43 55 5C  .......0...HKCU\
---  registry       --0x0/0x1E0------------------------------------------------


```

I suppect that I do not have the entire set of codecs. I can convert from an .avi file to .wmv file. If I try the other way I get an error saying something to the effect that .avi is not supported. I can seperate an .avi into .jpg or .png frames.

Where would i look for the complete set of codecs, both video and audio?

Thanks
Dave

---

### Post by philetus on 2008-12-29
I have found this very helpful

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Silvernail on 2009-01-03
So did I. Thanks

---

