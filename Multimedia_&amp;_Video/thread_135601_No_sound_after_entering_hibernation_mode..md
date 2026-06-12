---
title: "No sound after entering hibernation mode."
date: 2006-02-24
forum: Multimedia &amp; Video
---

### Post by tc10b on 2006-02-24
Hi, me again. 
I have got Ubuntu to recognise all of my hardware and it works fine normally.

But as I have a laptop I like to use hibernation mode as often as possible to save my battery power. But everytime I use this mode I can never get the sound card to be recognised until I reboot.:confused: 

Why is this? Is there anyway I can get it to recognise the sound card again after hibernating? I don't have the same problem with Windows and I don't understand it.

Thanks a lot

T.

---

### Post by tc10b on 2006-02-27
Does anyone have any ideas on how I could fix this?

I asked my friend and he said it was something to do with the sound demon not reinitialising but I don't know how I could sort that and neither does he.

Any thoughts would be appreciated, thanks.

---

### Post by thirek on 2006-02-28
i have pretty much the same problem, i'm running ubuntu 5.10 on my thinkpad t23. all seems to work fine, when i come back from from hibernate mode i have no audio. reboot seems to fix everything.

---

### Post by tc10b on 2006-03-09
Any Ideas? I would appreciate any help as although it's not a major problem it's an inconvenience as I would like to be able to hibernate my computer more often and get sound.

Thanks a lot.

---

### Post by jhedeman on 2006-03-09
I'm having the same issue here on my desktop in Breezy.  I don't know how to fix it though...

James

---

### Post by Thorne on 2006-04-11
Hello

I've found a nice solution to this problem with the T23 model. It also happens to me that when coming back from the hibernation succesfully i have no sound. But after spending some hard time with google, i found the solution. 

When coming out of the hibernation, just reload alsa by force.
"sudo /etc/init.d/alsa force-reload"

Works for me, at least. :)

---

### Post by tc10b on 2006-04-27
Thanks a lot. I sort of thought I could do that but I had no idea how to so I was completely stuck.

Once again a belated Thank You.

---

