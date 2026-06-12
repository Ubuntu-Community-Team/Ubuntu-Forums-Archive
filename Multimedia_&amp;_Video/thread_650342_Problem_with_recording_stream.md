---
title: "Problem with recording stream"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by Pavcio on 2007-12-26
So my problem is:
I want to record a TV Stream from Tvuplayer (127.0.0.1:8901) and I use the command:
> mplayer -noframedrop -dumpstream [http://127.0.0.1:8901](http://127.0.0.1:8901)

Here is the answer:
> 
pawel@Jamnik:~$ mplayer -noframedrop -dumpstream [http://127.0.0.1:8901](http://127.0.0.1:8901)
mplayer: /home/pawel/mono-1.2.6/lib/libpng12.so.0: no version information available (required by mplayer)
mplayer: /home/pawel/mono-1.2.6/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) XP 2200+ (Family: 6, Model: 8, Stepping: 1)
CPUflags: MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Skompilowane z wykrywaniem procesora przy starcie.
Nie mog&#281; otworzy&#263; d&#378;ojstika /dev/input/js0: No such file or directory
Nie mog&#281; zainicjowa&#263; d&#380;ojstika
mplayer: could not connect to socket
mplayer: No such file or directory
Nie uda&#322;o si&#281; uruchomi&#263; obs&#322;ugi LIRC. Nie b&#281;dziesz mog&#322; u&#380;ywa&#263; swojego pilota.

Odtwarzam [http://127.0.0.1:8901](http://127.0.0.1:8901).
Zamieniam 127.0.0.1 na AF_INET6...
Nie mog&#322;em zamieni&#263; nazwy dla AF_INET6: 127.0.0.1
&#321;&#261;cz&#281; z serwerem 127.0.0.1[127.0.0.1]: 8901...
Rozmiar pami&#281;ci podr&#281;cznej (cache) ustawiono na 320 Kbajtów
Stream not seekable!
nop_streaming_read error : Resource temporarily unavailable
Zrzut pami&#281;ci

Wychodz&#281;... (Koniec pliku)
[End of the file]


And the problem is that. Everything to Stream not seekable is ok but then after 2-3 minutes of recording it just stops. I think it's temporary lack of signal but not visible on video. How to do that he will not stop recording till I tell him to do it even it's temporary lack of stream [less than 1s]

---

### Post by mirak63 on 2008-04-19
if you find a way tell me, I have the same issue with soap cast

though kaffeine records well but not from command line

---

