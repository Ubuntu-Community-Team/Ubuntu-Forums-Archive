---
title: "S-video output on NVIDIA 9600 hardy heron"
date: 2008-08-03
forum: Multimedia Software
---

### Post by johnnybg00de on 2008-08-03
I've seen a few threads on this topic but haven't been able to get S-video output working on my geforce 9600. 

I've tried using xranr but without any luck. 

I'm not worried about modifying xorg if I have to do it manually, but all of the changes I've made so far havent worked. I've added sections called 'Monitor' with settings for my TV, edited the 'Device' and 'Screen' sections, but with no luck.

I've gotten the nvidia driver installed and the card is working fine with a regular VGA monitor, but I can't get dual monitor support working. It's almost like ubuntu isn't detecting the s-video connection at all. When I click 'Detect Displays' in nvidia-settings gui, for example, nothing happens.

Any suggestions? I'm totally stuck here...

---

### Post by cariboo on 2008-08-04
Give **nvtv** a try it is available in the repositories, you can use Add/Remove Programs, Synaptic Package Manager or the command line to install it.

Jim

---

### Post by johnnybg00de on 2008-08-05
thanks for the advice, i hadn't heard of that tool before. however it seems not to support newer nvidia gpus, and i'm running a 9600 so when i run it i get this error:

```
Fatal: No supported video card found.
```

any other suggestions? anyone have any luck with a 9600 yet? tv out is pretty important to me as i'm trying to set this box up as a media server.

---

### Post by johnnybg00de on 2008-08-05
i was just doing some searching and found a [vga to rca/s-video adapter]("http://www.computercasesandcables.com/ccc/CV-25120.html"). anyone know if this might enable me to output to tv via my onboard card, an nvidia geforce 6150?

---

### Post by cariboo on 2008-08-05
Try this, down near the bottom there seems to be a solution:

[http://ubuntuforums.org/archive/index.php/t-195141.html](http://ubuntuforums.org/archive/index.php/t-195141.html)

Most of the cards are older, but they are getting the same error.

Jim

---

