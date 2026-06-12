---
title: "Watching Taxi 2 on Linux"
date: 2008-09-19
forum: Multimedia Software
---

### Post by spibou on 2008-09-19
A while ago I bought a region 2 DVD of [Taxi 2](http://www.imdb.com/title/tt0183869). I use ogle to watch DVDs which has a few bugs but generally does the job well enough. But I can't watch this one. ogle opens a window, plays for a few seconds and then stops. On the terminal I get
```

libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x000001be)!!
WARNING[ogle_mpeg_vs]: wrong start_code picture_start_code: 00000108
xscreensaver-command not found.
*** skipped blocks in I-picture
*** invalid macroblock type
*** invalid macroblock type
*** invalid macroblock type
*** skipped blocks in I-picture
WARNING[ogle_mpeg_vs]: ** temporal reference skipped
*** skipped blocks in I-picture
*** skipped blocks in I-picture
*** invalid macroblock type
*** skipped blocks in I-picture
*** invalid macroblock type
*** invalid macroblock type
*** skipped blocks in I-picture
(vlc) invalid huffman code 0xb in vlc_get_block_coeff()
*mai error
*** invalid macroblock type
*** skipped blocks in I-picture
*** skipped blocks in I-picture
*** skipped blocks in I-picture
*** invalid macroblock type
**** DP remove this when implemented
*** invalid frame motion type
*** invalid frame motion type
**** DP remove this when implemented
*** invalid macroblock type
**** DP remove this when implemented
*** invalid frame motion type
*** invalid frame motion type
**** DP remove this when implemented
*** invalid frame motion type
**** DP remove this when implemented
No accelerated IMDCT transform found
FATAL[ogle_audio]: failed opening the oss audio driver at /dev/dsp
WARNING[ogle_vout]: req_code: 140
WARNING[ogle_vout]: minor_code: 14
WARNING[ogle_vout]: error_code: 8
WARNING[ogle_vout]: XV_COLORKEY not available
ERROR[ogle_vout]: Couldn't get attribute: XV_COLORKEY
ctrl: ipc_rmid: Invalid argument

```
Which leads me to ask:

1) Any ideas on what the problem is? With every other DVD I've tried ogle can play it with occasional mildly annoying glitches. Do you think it's a problem with the programme itself or some library?
2) Has anyone watched a region 2 DVD of the movie on Linux?
3) Has anyone watched any region DVD of the movie on Linux?
4) What do you consider the best programme for watching (commercial) DVDs?

---

### Post by sayid on 2009-03-07
In reply to:
> **spibou said:**
> A while ago I bought a region 2 DVD of [Taxi 2](http://www.imdb.com/title/tt0183869). I use ogle to watch DVDs which has a few bugs but generally does the job well enough. But I can't watch this one. ogle opens a window, plays for a few seconds and then stops. On the terminal I get
```

libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x000001be)!!
WARNING[ogle_mpeg_vs]: wrong start_code picture_start_code: 00000108
xscreensaver-command not found.
*** skipped blocks in I-picture
*** invalid macroblock type
*** invalid macroblock type
*** invalid macroblock type
*** skipped blocks in I-picture
WARNING[ogle_mpeg_vs]: ** temporal reference skipped
*** skipped blocks in I-picture
*** skipped blocks in I-picture
*** invalid macroblock type
*** skipped blocks in I-picture
*** invalid macroblock type
*** invalid macroblock type
*** skipped blocks in I-picture
(vlc) invalid huffman code 0xb in vlc_get_block_coeff()
*mai error
*** invalid macroblock type
*** skipped blocks in I-picture
*** skipped blocks in I-picture
*** skipped blocks in I-picture
*** invalid macroblock type
**** DP remove this when implemented
*** invalid frame motion type
*** invalid frame motion type
**** DP remove this when implemented
*** invalid macroblock type
**** DP remove this when implemented
*** invalid frame motion type
*** invalid frame motion type
**** DP remove this when implemented
*** invalid frame motion type
**** DP remove this when implemented
No accelerated IMDCT transform found
FATAL[ogle_audio]: failed opening the oss audio driver at /dev/dsp
WARNING[ogle_vout]: req_code: 140
WARNING[ogle_vout]: minor_code: 14
WARNING[ogle_vout]: error_code: 8
WARNING[ogle_vout]: XV_COLORKEY not available
ERROR[ogle_vout]: Couldn't get attribute: XV_COLORKEY
ctrl: ipc_rmid: Invalid argument

```
Which leads me to ask:

1) Any ideas on what the problem is? With every other DVD I've tried ogle can play it with occasional mildly annoying glitches. Do you think it's a problem with the programme itself or some library?
2) Has anyone watched a region 2 DVD of the movie on Linux?
3) Has anyone watched any region DVD of the movie on Linux?
4) What do you consider the best programme for watching (commercial) DVDs?

I has viewed that your problem is related with sound, I'm not answering you "why you can't see Taxi 2 on Linux" only helping you configure Ogle correctly.

Look at your /etc/oglerc and put (as sudo) in your audio section what driver you 'll use. 
Change:
 <audio>
    <device>
      <driver>occ</driver>
      <path>/dev/dsp</path>
      <alsa>
        <name>default</name>
      </alsa>
    </device>
For:
 <audio>
    <device>
      <driver>PCM</driver>
      <path>/dev/dsp</path>
      <alsa>
        <name>default</name>
      </alsa>
    </device>
This is correct if your linux is using PCM, if you are using alsa put <driver>alsa</driver>.

I hope this helps you!
Regards
        Sayid...

---

