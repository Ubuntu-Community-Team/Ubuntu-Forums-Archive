---
title: "Weird echo sound with dapper"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by hamsteri on 2006-06-05
Hello,
I did a fresh install with kubuntu and everything is great, except one thing:
I have a annoying echo sound when playing music. It's the same eventhough I use amarok, xine, kaffeine...

Sound worked great in breezy but this is really killing me now.

I have a abit al-8 motherboard with following:
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

Any one have any ideas ?

---

### Post by CarlFK on 2006-07-13
I have a similar problem - only I get 16 or so echos.  This should only play for about 2 seconds, but it loops:

carl@amd15:~$ play /usr/share/hwdb-client/sound.wav

Input Filename : /usr/share/hwdb-client/sound.wav
Sample Size    : 16-bits
Sample Encoding: signed (2's complement)
Channels       : 1
Sample Rate    : 8000

Time: 00:01.64 [00:00.00] of 00:01.64 ( 100.0%) Output Buffer:  13.16K

Done.

mplayer does it 'better' but still 16 echos.

---

### Post by CarlFK on 2006-07-13
This seems to play it about 35 times.  (turn your volume way down)

carl@amd15:~/dev/parse$ time dd if=/usr/share/hwdb-client/sound.wav of=/dev/dsp dd: writing to `/dev/dsp': Input/output error
33+0 records in
32+0 records out
16384 bytes (16 kB) copied, 40.0139 seconds, 0.4 kB/s

real    0m40.024s
user    0m0.004s
sys     0m0.004s


carl@amd15:~$ lspci|grep audio
0000:00:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 30)

---

### Post by CarlFK on 2006-07-13
I disabled the on board sound (VIA AC97) and now I have no echos.  

carl@amd15:~$ lspci|grep -i audio
0000:00:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)

---

