---
title: "Why does Vista look and sound better?"
date: 2009-02-14
forum: Multimedia Software
---

### Post by Ian0426 on 2009-02-14
I write a blog about singing and sometimes post pictures and youtube clips to my site. I do all my (modest) media editing with Linux programs like Gimp, Audacious, Cinelerra, and with the on-site editors for the blog.

What is interesting me right now, is that the exact same material will sometimes look or sound better on Windows Vista than in Ubuntu. For example, there is a picture that I shrank with the on-site editor and when I look at the blog in Ubuntu, the picture looks like it was shrunk with all the accompanying distortion. On Vista, it looks perfect.  I posted a youtube clip that I edited in Linux that had a ton of background noise and after its conversion in youtube, also had those awful compression noises. I heard those noises clearly in Linux but not in Vista. In Vista, it wasn't perfect, but it was much better.

Why is this the case? I use a dual boot Intrepid/Vista on a Dell Inspiron 1525 with a Sigmatel sound card and Intel GM965 Graphics card.

This is hardly a deal breaker as I have big issues with Vista most of the time, but I do wonder. Could this be incompatibilities between the blog site and Linux? Or Flash and Linux?

---

### Post by cariboo on 2009-02-14
It almost sounds like you are using Microsofts default drivers on your laptotp. I installed Win7 which is really only a Vista update and found that graphics and sound quality was quite a bit better after I installed the proper drivers for my graphics and audio adapters.

Jim

---

### Post by Ian0426 on 2009-02-14
Thanks for the reply, but to reiterate; Vista sometimes displays images and plays sounds from the internet at a much higher quality than in Ubuntu Intrepid using the exact same hardware. I am wondering how and if it is possible to make Ubuntu look and sound as good.

---

### Post by Melcar on 2009-02-14
As far as the sound, in Windows drivers usually come accompanied by software that will add equalizing and other post processing effects (like noise reduction).  There is really no such thing in Linux, except for individual applications that offer similar effects.  The same thing can apply to video.  
Another thing to consider is that things like flash and java behave very differently under Windows and Linux.  Flash rarely works like it should and java is a big pain.  Even Firefox is a bit better under Windows (specially when it comes to flash).

---

### Post by Ian0426 on 2009-02-14
Ah, I've figured out part of it. Firefox for Linux, for some reason, does not have smooth image scaling like it does in Windows. I could see the difference when I run Firefox 3 in Wine. 

Hmm. Now I need to look for a solution to that.

---

### Post by Melcar on 2009-02-14
The most recent rant in Linux Hater's blog is about Firefox 3 and how it runs better even under Wine.

---

### Post by Ian0426 on 2009-02-15
I found the source of the problem. There is in Intrepid a bug affecting some users of Firefox based off of whatever video card they are using. 

The bug is listed here: [https://bugs.launchpad.net/ubuntu/+bug/217908](https://bugs.launchpad.net/ubuntu/+bug/217908)

---

