---
title: "MLB TV seek crashes"
date: 2007-05-16
forum: Multimedia &amp; Video
---

### Post by Hell_Rok on 2007-05-16
Hello, i am trying to get MLB TV to run on my debian box.

I use the "media player connectivity" plugin to enable the embedded stream to be able to be played with vlc (i have tried the mplayer plugin to no avail), but when i seek it will sometimes die and vlc will return to its initial state.

I have been ripping my hair out over this =(

I have also been able to replicate this exactly on my ubuntu machine so i thought i should post it here as if you can fix it on ubuntu but not debian i can just install ubuntu on the media pc.

Thanks in advance for your help.

---

### Post by Hell_Rok on 2007-05-17
am bumping for help, still unable to get this to work.

---

### Post by synonymous on 2007-05-17
Haven't noticed this. 
Using VLC watching an old archived game 700k now seeking anywhere.

---

### Post by Hell_Rok on 2007-05-18
I have been able to get an error by running firefox (or iceweasel if you will) from a terminal.

```
[00000293] access_mms access error: error: HTTP/1.0 401 Unauthorized
[00000293] access_mms access error: invalid chunk FATAL (0x6553)
[00000293] access_mms access error: invalid chunk FATAL (0x7261)
[00000290] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 36.5% failed
[00000293] access_mms access error: error: HTTP/1.0 401 Unauthorized
[00000293] access_mms access error: invalid chunk FATAL (0x6553)
[00000293] access_mms access error: invalid chunk FATAL (0x7261)
[00000290] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 37.1% failed
[00000293] access_mms access error: error: HTTP/1.0 401 Unauthorized
[00000293] access_mms access error: invalid chunk FATAL (0x6553)
[00000293] access_mms access error: invalid chunk FATAL (0x7261)
[00000290] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 44.1% failed
[00000293] access_mms access error: error: HTTP/1.0 401 Unauthorized
[00000293] access_mms access error: invalid chunk FATAL (0x6553)
[00000293] access_mms access error: invalid chunk FATAL (0x7261)
[00000290] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 46.3% failed
[00000293] access_mms access error: error: HTTP/1.0 401 Unauthorized
[00000293] access_mms access error: invalid chunk FATAL (0x6553)
[00000293] access_mms access error: invalid chunk FATAL (0x7261)
[00000290] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 61.3% failed
[00000293] access_mms access error: error: HTTP/1.0 401 Unauthorized
[00000293] access_mms access error: invalid chunk FATAL (0x6553)
[00000293] access_mms access error: invalid chunk FATAL (0x7261)
[00000290] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 62.9% failed
[00000279] main playlist: nothing to play

```

---

