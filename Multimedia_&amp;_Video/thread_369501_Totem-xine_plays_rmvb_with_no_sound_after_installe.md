---
title: "Totem-xine plays rmvb with no sound after installed win32codecs"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by zhumingvictor on 2007-02-24
Hi,
I install ubuntu 7.04, and then installed totem-xine and those stream* things. Then I am able to play rmvb files with sound. But not avi files. Then I found the xine-extracodecs then I installed it. After this I can get avi play well. But no sound while I play rmvb anymore. Then I tried to install the regular totem, now I can play rmvb with sound by no video. I tried to rmove win32codes. Nothing changes any more.
Can anybody help me?

---

### Post by asenci on 2007-02-27
Same thing here... 
Was using edgy and updated to feisty.
Totem-xine doesn't output audio for .rmvb files. MPEG and DIVX files are ok.
Mplayer works using the same plugins (w32codecs)...

Also, Totem's bright an contrast doesn't seen to ever get good enought compared to mplayer, (either too bright or too dark). Don't know if it's realy a bug... :(

---

### Post by kellsens on 2007-02-27
Hi,

   I'm having the same problem. So I'm using RealPlayer to play rmvb files.

---

### Post by ryurhrt on 2007-04-20
there is one solution, tat is delete one of the xine library

/usr/lib/xine/plugins/1.1.4/xineplug_decode_ff.so 

after delete it, rmvb bcome no problem, but.... cant play Avi format, got to use totem-gstreamer to play it.

---

### Post by teckfatt on 2007-04-20
ya me too, .rm and some .mpg no sound

---

### Post by hanzomon4 on 2007-04-20
It's a bug with xine-lib. I had this problem on sabayon so I downgraded my lib-xine to the same version number as the xine-lib used in edgy and all my videos worked again. Not sure how to do the same in Feisty

---

### Post by hanzomon4 on 2007-04-20
I found the fix on the Dropline Gnome forums> I found a solution to this problem. 

It seems, editing the file ~/.xine/catalog.cache and change the &#8220;decoder_priority=5&#8243; to &#8220;decoder_priority=10&#8243; for the configuration option of &#8220;xineplug_decode_real_audio.so&#8221; will solve this problem. 

This is found from here: 

[http://ubuntuforums.org/showthread.php?p=2185827](http://ubuntuforums.org/showthread.php?p=2185827)

---

### Post by in_flu_ence on 2007-04-21
> **hanzomon4 said:**
> I found the fix on the Dropline Gnome forums

it works for me too.

---

### Post by vyruss on 2007-06-18
many thanks, your tip worked!!

---

### Post by pingpongboss on 2007-06-18
sweet, that worked for me also.

---

### Post by takayuki on 2007-06-19
fixed it for me too.  thanks.

---

### Post by kolslorr on 2007-06-24
wow, thanks.... this really works... who the heck would know how to fix it themselves...

---

### Post by sosy on 2007-07-05
hey,
have you seen this post: [http://ubuntuforums.org/showthread.php?t=366252]("http://ubuntuforums.org/showthread.php?t=366252")
I think its a better solution.

---

### Post by sosy on 2007-07-05
hey,
have you seen this: [http://ubuntuforums.org/showthread.php?t=366252]("http://ubuntuforums.org/showthread.php?t=366252")
I think its a better solution.

---

### Post by pingpongboss on 2007-07-08
> **sosy said:**
> hey,
have you seen this: [http://ubuntuforums.org/showthread.php?t=366252]("http://ubuntuforums.org/showthread.php?t=366252")
I think its a better solution.

I looked through that thread... and isn't the solution exactly the same? =T

---

### Post by hikaricore on 2007-08-03
Many thanks for the info. ^_^

Now I wonder if I can adapt this trick for better play of mkv files.  >.<

---

