---
title: "Ubuntu 8.04 and ATI 3870X2"
date: 2008-05-14
forum: Multimedia Software
---

### Post by Maks1983 on 2008-05-14
Did anyone could make this graphic card (ATI 3879) work in ubuntu 8.04? if yes please tell me how.

Thanks

---

### Post by markbuntu on 2008-05-14
Is this a new card on an old install?

---

### Post by Maks1983 on 2008-05-15
> **markbuntu said:**
> Is this a new card on an old install?

no, its a new card on a new install. my whole computer is new. :)

---

### Post by Maks1983 on 2008-05-16
anyone? please.... i would like to start working/learning on linux... 3870x2??? :confused::confused:

---

### Post by Ren Höek on 2008-05-17
> **Maks1983 said:**
> Did anyone could make this graphic card (ATI 3879) work in ubuntu 8.04? if yes please tell me how.

Thanks

As for the release notes
[http://www2.ati.com/drivers/linux/catalyst_84_linux.html](http://www2.ati.com/drivers/linux/catalyst_84_linux.html)
fglrx should support ATI Radeon&#8482; HD 3800 series.

Have you tried already the standard ways of installation? This one is a good guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
If so, do you get any errors? Can you boot? Can you log in?
What results do you get with
```

$ cat /var/log/Xorg.0.log | grep "(WW)\|(FF)"

```
and
```

$ LIBGL_DEBUG=verbose fglrxinfo

```
?

---

### Post by Maks1983 on 2008-05-17
> **Ren Höek said:**
> As for the release notes
[http://www2.ati.com/drivers/linux/catalyst_84_linux.html](http://www2.ati.com/drivers/linux/catalyst_84_linux.html)
fglrx should support ATI Radeon&#8482; HD 3800 series.

Have you tried already the standard ways of installation? This one is a good guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
If so, do you get any errors? Can you boot? Can you log in?
What results do you get with
```

$ cat /var/log/Xorg.0.log | grep "(WW)\|(FF)"

```
and
```

$ LIBGL_DEBUG=verbose fglrxinfo

```
?

In the first link you can see that the 3870X2 is not supported by ATI. ill try the other link you gave me, and then ill post the results. btw im using the 64 bit version.

---

### Post by Ren Höek on 2008-05-18
> **Maks1983 said:**
> In the first link you can see that the 3870X2 is not supported by ATI. ill try the other link you gave me, and then ill post the results. btw im using the 64 bit version.

Sorry, you are right. I just have seen, that HD 3800 series is supported and not the exception HD 3870x2...

I found some threads suggesting, that fglrx will only use one core and it will be detected as a HD 3870. Have you tried it yet?

---

### Post by Maks1983 on 2008-05-18
> **Ren Höek said:**
> Sorry, you are right. I just have seen, that HD 3800 series is supported and not the exception HD 3870x2...

I found some threads suggesting, that fglrx will only use one core and it will be detected as a HD 3870. Have you tried it yet?

im sorry, havent tried yet... lack of time... :(:(
but when i get the time i'll and ill post here.
thx

---

### Post by Barina on 2008-07-11
hi im new here and i have the exact problem 
also im new to linux at all.. so i don't yet familiar with it...

please tell me how to set linux to "think" that my 3870x2 is a one core 3870 ?

i already try the EnvyNG and its all messed up..
please help..... 

thanks
roy

---

### Post by Melcar on 2008-07-11
No support for the X2 yet.  The driver won't even install correctly.  Only real choice is to use radeonHD, but that lacks acceleration (I think the latest build has 2D already) and only recognizes one core.  Crossfire is coming soon (I would guess by 8.8) but it's anyones guess how it will end up working.

---

### Post by Barina on 2008-07-11
i can get 3d acceleration with one core in that option? 
tell me how can i do that..? its a temporary solution....

---

### Post by Melcar on 2008-07-11
RadeonHD does not have 3D acceleration yet, so if that's what you're after then that driver is useless for you.  As I said, fglrx won't even recognize the card.  Here is a guide to install the latest radeonHD build:

[http://www.phoronix.com/forums/showthread.php?t=9951]("http://www.phoronix.com/forums/showthread.php?t=9951")

---

### Post by markbuntu on 2008-07-11
ATI is promising big things in a few months and that should include support for the 3870x2 card. What is weird is that they included linux support for the even newer 4000 cards in the 8.6 driver and included the linux driver in the cd. And put tux on the box!!

---

### Post by Barina on 2008-07-12
oh ok.. i understend
thanks
im gonna wait a while...

---

### Post by JohnC86 on 2009-05-30
old thread I know but I thought i'd bump it.

I got this working with fglrx, however i'm getting the horrible unsupported hardware watermark, annoying. Compiz and everything else is working great though and it's really stable.

It's only recognising one of the cards (cores) though! only a minor issue tbh. Just trying to get it all sorted now, but it seems progress has been made since this thread was made.

---

### Post by asyed94 on 2009-08-14
I'm sure progress has been made, but I still cannot get my card to work with fglrx. Whenever I install the proprietary driver, the most Ubuntu gets to is a scrambled login screen which then proceeds to ignore all keyboard input except the restart combination. I've combed the web looking for a solution, and this was the newest post I could find regarding this issue. How did you get this card to work? Any help would be greatly appreciated.

---

### Post by markbuntu on 2009-08-14
The release notes still say this:

Note: The ATI RadeonTM HD 3870 X2 series of product is currently
not supported by the ATI CatalystTM Linux software suite.


The 4870x2 is supported. You could try

sudo aticonfig --adapters=all --initial -f

which is what is neeeded to use both gpus with the 4870x2 card.

---

