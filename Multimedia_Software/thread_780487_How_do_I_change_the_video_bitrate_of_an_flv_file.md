---
title: "How do I change the video bitrate of an flv file?"
date: 2008-05-03
forum: Multimedia Software
---

### Post by snoopgst on 2008-05-03
I have a bunch of flv videos encoded at 400-vbitrate  how do I convert them to 250-vbitrate?

I have already installed ffmpeg and mencoder.

---

### Post by disturbedite on 2008-05-03
you could just use avidemux.  no instructions really needed, as it is mostly self explanatory.

---

### Post by ron999 on 2008-05-03
> **disturbedite said:**
>  as it is mostly self explanatory.
Can you explain how to open an flv file with Avidemux?:confused:

---

### Post by snoopgst on 2008-05-03
I am doing this on a server.  It does not have a gui.

---

### Post by disturbedite on 2008-05-04
> **ron999 said:**
> Can you explain how to open an flv file with Avidemux?:confused:
you've got to be kidding!!!

File --> Open --> select your flv file.

---

### Post by snoopgst on 2008-05-04
What about from command line?

---

### Post by ron999 on 2008-05-05
[QUOTE=disturbedite;4882511]you've got to be kidding!!!

File --> Open --> select your flv 
I don't think so.
See attachment.

---

### Post by ron999 on 2008-05-05
> **snoopgst said:**
> What about from command line?
To change a flash video file to 250Kbps video bitrate you could try using ffmpeg like this:-

ffmpeg -i <yourfilename> -b 250 foo.flv

Then if it works OK maybe someone brighter than me will write a script to convert the bunch.

---

### Post by disturbedite on 2008-05-05
> **ron999 said:**
> 
I don't think so.
See attachment.
sorry bud, but you're wrong.  i strongly suspect you are using an outdated version.  please upgrade to the latest version.  it works perfectly fine for me with flv & has for as long as i can remember.

---

