---
title: "error: Can't open default sound device!"
date: 2011-09-15
forum: Multimedia Software
---

### Post by simranjitsingh7 on 2011-09-15
Hi All, 

I am using ubuntu10.10. I want to play a mp3 file using mpg123. But when i try to run it, it fails with the following error:

% mpg123 ~/Public/song.mp3
[oss.c:172] error: Can't open default sound device!
[audio.c:627] error: failed to open audio device
[audio.c:180] error: Unable to find a working output module in this list: oss
[audio.c:529] error: Failed to open audio output module
[mpg123.c:869] error: Failed to initialize output, goodbye.

I tried to search for the solution but couldn't find one. Can anyone please help me with it?

Regards

---

### Post by fdrake on 2011-09-15
> **simranjitsingh7 said:**
> Hi All, 

I am using ubuntu10.10. I want to play a mp3 file using mpg123. But when i try to run it, it fails with the following error:

% mpg123 ~/Public/song.mp3
[oss.c:172] error: Can't open default sound device!
[audio.c:627] error: failed to open audio device
[audio.c:180] error: Unable to find a working output module in this list: oss
[audio.c:529] error: Failed to open audio output module
[mpg123.c:869] error: Failed to initialize output, goodbye.

I tried to search for the solution but couldn't find one. Can anyone please help me with it?

Regards
do you have sound in your pc or not. Is this problem relate to mpg123 only or to all media player(flash movies)?

---

### Post by simranjitsingh7 on 2011-09-16
I am running Ubuntu10.10 as virtual machine on windows7 as host OS. In windows, the audio is working fine and in Ubuntu also, the audio is working for flash movies. So I guess audio device is there with drivers.

Regards

---

