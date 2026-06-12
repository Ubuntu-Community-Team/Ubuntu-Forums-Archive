---
title: "Sound Not Working But Modules are Loaded"
date: 2006-07-15
forum: Multimedia &amp; Video
---

### Post by webbca01 on 2006-07-15
Hello Everyone!

So Here's the Deal:
My sound will not play in Ubuntu (or any distro of linux, for that matter). All the channels are unmuted, and also I've been told all the modules have been loaded correctly. I've been doing some research, and I have determined that this is not an ALSA issue. I also recieved the suggestion of doing "Irqpoll" boot, but that hasn't worked. (Refer to this suse article :
[http://www.linuxforums.org/forum/suse-linux-help/61338-sound-card-errors-2.html]("http://www.linuxforums.org/forum/suse-linux-help/61338-sound-card-errors-2.html")

Here's What I'm going for:

I added irqpoll at the end of  default=quiet splash in menu.lst? (I can't remember what it is called) and that didn't work. Is there any other ideas about irq (because it looks like there may be a conflict in irq 5 and 11?)

And also, any other ideas as to figure this solution out.

Other info :
lspci | grep -i audio

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

Thanks Much!

---

### Post by webbca01 on 2006-07-15
I also followed the sound problem sticky forum as well.. and still nothing.

---

