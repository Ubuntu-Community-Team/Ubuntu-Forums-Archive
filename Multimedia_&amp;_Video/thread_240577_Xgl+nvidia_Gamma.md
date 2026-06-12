---
title: "Xgl+nvidia Gamma"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by nonex on 2006-08-21
How to increase Scale, with included xgl? In nvidia X server setting there are no adjustments! :evil:

---

### Post by mushr00m on 2006-08-23
This is my problem also.  I've got an aging monitor that needs gamma turned up to make video watchable.  I can see that it is using mesa instead of nvidia graphics, but how?

---

### Post by mushr00m on 2006-08-23
I fixed my problem in a fashion...

I used script from this thread: [http://www.ubuntuforums.org/showthread.php?t=176636&highlight=nonXgl]("http://www.ubuntuforums.org/showthread.php?t=176636&highlight=nonXgl")

I substituted DISPLAY=":93" with DISPLAY":0" , which I use to play accelerated games.

If I run my nvidia-setting through the nonXGL script it loads correctly... but without window dressing.

---

### Post by zetaz7680 on 2006-09-19
Thanks mushr00m.. that was something i hunted around for a while now. Good to have digital vibrance back while running XGL.
Do you know how to modify the old "nvidia-settings --load-config-only" session to accomodate with the nonXgl script? I tried adding that as a prefix to the session cmd, but no result.
Thx.

---

### Post by mushr00m on 2006-09-26
I took a look at the script again... after sorting through the conditionals it ends with a "exec $@" which, as I understand, passess all the arguments you gave the script.

I would say that your problem in using this script at session startup is that it requires something out of your sphere of rights... aka, needs sudo.

I think that you might be able to replace sudo with gksudo and use the script  at session start.... but I might also be sniffing glue. :confused: 

if that doesn't work. remove sudo totally and start the script in the session manager with: 

gksudo "nonXgl nvidia-settings --load-config-only"

in fact I might just go try that myself :) Good luck!

mushr00m

---

