---
title: "Can't convert FLAC files"
date: 2007-07-01
forum: Multimedia Production
---

### Post by fluoblack on 2007-07-01
Hello there!
I had to convert FLAC audio files recently, and all went right for most of the files. But for those coming from my own CD Collection (encoded with EAC at the time) I get error messages. I can read them, but not convert them. I Tried with soundconverter, soundKonverter and the flac -d itself, here is the error message I get:

```
$ flac -d /home/matt/Desktop/Rock.flac

flac 1.1.2, Copyright (C) 2000,2001,2002,2003,2004,2005  Josh Coalson
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

Rock.flac: *** Got error code 1:FLAC__STREAM_DECODER_ERROR_STATUS_BAD_HEADER
Rock.flac: *** Got error code 1:FLAC__STREAM_DECODER_ERROR_STATUS_BAD_HEADER
Rock.flac: *** Got error code 0:FLAC__STREAM_DECODER_ERROR_STATUS_LOST_SYNC
Rock.flac: *** Got error code 1:FLAC__STREAM_DECODER_ERROR_STATUS_BAD_HEADER
Rock.flac: *** Got error code 0:FLAC__STREAM_DECODER_ERROR_STATUS_LOST_SYNC
Rock.flac: *** Got error code 1:FLAC__STREAM_DECODER_ERROR_STATUS_BAD_HEADER
Rock.flac: *** Got error code 0:FLAC__STREAM_DECODER_ERROR_STATUS_LOST_SYNC
Rock.flac: *** Got error code 1:FLAC__STREAM_DECODER_ERROR_STATUS_BAD_HEADER
Rock.flac: *** Got error code 0:FLAC__STREAM_DECODER_ERROR_STATUS_LOST_SYNC
Rock.flac: *** Got error code 1:FLAC__STREAM_DECODER_ERROR_STATUS_BAD_HEADER
Rock.flac: *** Got error code 0:FLAC__STREAM_DECODER_ERROR_STATUS_LOST_SYNC


Rock.flac: ERROR while decoding data
           state = FLAC__STREAM_DECODER_READ_FRAME
```

Did I miss something? How can i resolve this?
Thanks for helping.

---

### Post by teledyn on 2008-03-01
Same problem in Gutsy, not all flac files, just a few and in the sets where it happens it is consistent across all the files in that set.  Rhythmbox can play these files no problem, I just can't decode them using flac -d, which means I can't create audio CDs or mp3s from the flac-entrusted files :(

Could this be a version conflict?  The Flac authors reported this error as due to ID3 tags following a final block of a certain size and had fixed the problem -- could be the Ubuntu flac package is in need of an update?

---

### Post by Creative2 on 2008-03-01
ffmpeg -i INPUT -acodec flac -ab 192k -y OUTPUT
or maybe better
ffmpeg -i INPUT  -ab 192k -y OUTPUT.flac

install ffmpeg after you turned on medibuntu repository

---

