---
title: "OpenGL support?"
date: 2005-10-22
forum: Multimedia &amp; Video
---

### Post by rozojc on 2005-10-22
Hi every1

I have been using Breezy on my laptop since release candiate 10, and I am very happy with it. I can do (almost) everything I used windows for, and I now am 99% windows free.

I do have one issue... I have recently tried playing different openGL games and it seems that my video card is not configured for openGL. My laptop is an Acer 3003LCi, and it has a  SiS M760GX that takes its memory of the system's RAM (up to 128). Is there any way I can enable this card to work with opengl?

When I type glxinfo the first lines read:
name of display: :0.0
display: :0  screen: 0
direct rendering: No

That doesn't sound very promising...

Any help would be greatly appreciated!

---

### Post by ranf on 2005-10-22
[QUOTE=rozojc]
I do have one issue... I have recently tried playing different openGL games and it seems that my video card is not configured for openGL. My laptop is an Acer 3003LCi, and it has a  SiS M760GX that takes its memory of the system's RAM (up to 128). [/QUOTE]

The one and only resource for SIS is [http://www.winischhofer.net/]("http://www.winischhofer.net/")

---

### Post by rozojc on 2005-10-22
Well, I had actually instaled the drivers found on that page without any luck. Unfortunately, I just read on that page that hardware acceleration openGL is not available for my chipset... So apparently there's no way I can have openGL with my laptop...

Does anybody know any workaround?

---

### Post by ubuntu_123 on 2005-10-23
Yes, me too.

I have the same problem, same laptop.

Or can we install another video card? I guess it is not, it is built-in? or can it be recalled? or is that possible sis will release some support for this type of card in the near future?

Or even worse anybody want to buy an aspire 3003wlci? I have it just for one month.

Thanks.
yasir.

---

### Post by prokher on 2005-11-28
try run
export=GLLIB_DEBUG=verbose
glxinfo
if you get message "SiS DRI driver expected DDX version 0-0.8 but got version 0.7.0" may be my thread with the same name could help....(or may be you can help me :) )

---

### Post by brallan on 2006-04-10
Has anybody tried buying the [www.winischhofer.net](www.winischhofer.net) premium sis XVGA driver? He says it provides 3D acceleration as well as a bunch of other features no available for the sis XVGA driver... It might be the way to go...

I myself am trying to get the SiS760 in my ASUS 9200U laptop to work. The FAQ for stellarium explains that very slow rendering, very low framerates happen when: "...hardware rendering is disabled. If you have a 3D video card, make sure that your OpenGL drivers are installed and up to date. "

well, I'm pretty sure the problem is the lack of 3D support...

---

### Post by rozojc on 2006-04-10
[QUOTE=brallan]Has anybody tried buying the [www.winischhofer.net](www.winischhofer.net) premium sis XVGA driver? He says it provides 3D acceleration as well as a bunch of other features no available for the sis XVGA driver... It might be the way to go...

I myself am trying to get the SiS760 in my ASUS 9200U laptop to work. The FAQ for stellarium explains that very slow rendering, very low framerates happen when: "...hardware rendering is disabled. If you have a 3D video card, make sure that your OpenGL drivers are installed and up to date. "

well, I'm pretty sure the problem is the lack of 3D support...[/QUOTE]
I have not tried them myself. Until now I have just been working with my laptop "as is", and I had given up in trying to make openGL work. So, if you do try these drivers please post back with your results to know if it is worth doing it or not...

---

### Post by FloSynergy on 2006-04-12
hi folks,

i've been wrestling with the same issue.
apparently, winishofer has updated the sis driver to allow dri for sis 650/740.

i've tried to change the settings in xorg.conf manually, to allow dri, but without any success.

perhaps we do have to wait....sis sux.

good luck all,

flo

---

### Post by chaoschannel on 2006-06-08
Unfortunately SiS support is very limited at the moment. Thanks to [www.winischhofer.net](www.winischhofer.net) we have some support, but for opengl support we are out of luck. Note that this isn't an issue with the sis driver but with the dri support for SiS's 330 chips (eg. 760gx, and others). Until someone provides the dri support we have to make do with software accelleration. :(

---

### Post by TiLK on 2007-04-08
I fight with the same problem. Has anything changed since the last post here?

---

### Post by Jjohn on 2007-04-09
Hi TiLK,
             I do not think there is any improvement but I am not the sharpest knife in the drawer either.
Some stuff I was told was the sys card is also known as a "ATI Mirage" However i did a lot of searching and found nothing that I could understand.
            When I first installed ubuntu the system for some reason installed Nvidea drivers and my 3d was totally dead. I changed the drivers to Xorg-driver for ati cards. I now have "some" 3d but no direct rendering so any game or sim runs at a miserable14-16 FPS .
           If you find an answer i would love to hear from you.
All the best  John

---

