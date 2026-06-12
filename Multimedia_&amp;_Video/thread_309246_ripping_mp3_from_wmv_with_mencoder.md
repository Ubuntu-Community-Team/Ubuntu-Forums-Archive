---
title: "ripping mp3 from wmv with mencoder?"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by linuxNewb on 2006-11-29
I've been searching through mplayer and mencoder docs for over an hour now, and it just is not happenin'

I want to take the audio from a wmv file and put it into an mp3.

I have all the codecs, I just can't find the (command or commands) to do it.

It keeps wanting to make an avi. Can't you just take audio?

Thanks in advance.

---

### Post by whatever on 2006-11-29
mencoder will always(*) create .avi files. however, you can use "mplayer -dumpaudio" afterwards to get the plain audio file out of the avi.


(*) there is experimental support for other containers via lavf

---

### Post by linuxNewb on 2006-11-29
Thank you, yes this worked. For anyone else wanting to do this...

```

 $ mplayer <path_to_wmv_file> -ao pcm
 $ lame -h audiodump.wav <path_to_output_mp3_file>

```

---

