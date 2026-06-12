---
title: "ATI+Video Playback = OMFG"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by rabanomen on 2007-11-24
I've just installed Gutsy . After install de codecs , the video playback its ok , the video seems great and the audio codec right . BUT when i install restricted driver controller ( Ati X1300 driver ) the video playback becomes tinted of  GREEN !!!. All the videos seems to be saturated , ugly colors in totem , and in the vlc the video doesnt play right ... it do " jumps" between frames

Mplayer haves problemas to open files , and when the video finish , i have a message of error " gnome_Screensaver_control() "

Before install the ati driver i dont have problems , i've tryed to install all codecs , i've reinstalled gutsy  four times to test the problem with a clean setup , and the problem is the ati driver 

Someone have the same problem ? Someone have an idea ?

***Sorry about my poor english , im spanish*

> 
**En español**
Acabo de instalar Gutsy.Tras instalar los codecks , se reproducen bien los videos , se ve bien y el codec de sonido funciona perfecto. PERO cuando instalo los drivers de ati restringidos , los videos reproducidos parecen estar titnados de VERDE. Todos los videos parecen estar saturados , con colores feos en totem y en VLC pega saltos desagradables ente frames

Mplayer me da problemas al abrir archivos y cuando el video termina me salta un error " gnome_Screensaver_control()"

Antes de isntalar los drivers de ati no tengo probloemas , he intentado instlar todos los codecs , he reinstalado gutsy 4 veces para probrar el problema con la instalacion limpia, y el problema son los drivers de ati

¿Alguna idea?¿Alguien tiene el mismo problema?

---

### Post by davec64 on 2007-11-24
I had a similar problem with viewing video clips emailed to me by a friend, I'd get a flash of the clip, then it would go to black whilst the sound was fine. This was while I had Compiz running. Have yo got Desktop Effects running?

To fix it I opened gstreamer-properties from the terminal, and on the video tab set the output to "X Windows System (No Xv)".

This did the trick for me! Might be worth a go!

Here's the page I got the info from:

(sorry here's the correct link:)

[http://arstechnica.com/reviews/os/ubuntu-gutsy-gibbon-review.ars/2]("http://arstechnica.com/reviews/os/ubuntu-gutsy-gibbon-review.ars/2")

(it about half way down)

Best of luck!

---

### Post by tiachopvutru on 2007-11-24
Well, I'm still a noob on Ubuntu so I'll just give some advices with no guarantee of it fixing the problem.

Try

```
sudo apt-get install xserver-xgl
```

Well, you mainly need XGL for Compiz-Fusion, but you probably need it for video playback as well.

If that happens to solve your problem (hopefully), a good video player is SMPlayer.

---

### Post by rabanomen on 2007-11-24
Oh ! thanks a lot  !!!!!!!!!!!!!!!!!!!!!!!!!!!!
I didn't know this properties ! My totem now its ok !
i havn't effects on my desktop , i prefer it without them

No more problems with totem !!But vlc .... uffff its horrible the playback. I'll post in the launchpad this error.

Well  thanks again !!

pd. The link that you posted , doesn't work


tiachopvutru :

"sudo apt-get install xserver-xgl"
im not sure .... i dont think that it will be a great idea but thanks !

---

### Post by tiachopvutru on 2007-11-24
> **rabanomen said:**
> 

tiachopvutru :

"sudo apt-get install xserver-xgl"
im not sure .... i dont think that it will be a great idea but thanks !

Well, XGL is used to support hardware acceleration since the ATI driver version in Restricted Drivers Manager doesn't support AIGLX. I can't give my guarantee but it may be the solution (I have the latest driver now with AIGLX support so I can't really test it). You can always uninstall it later, but in the end, it comes down to your choice.

Wikipedia entry on Xgl:
[http://en.wikipedia.org/wiki/Xgl](http://en.wikipedia.org/wiki/Xgl)

---

### Post by rabanomen on 2007-11-24
maybe works ...
i used to install drivers for fix problems with rendering and aceleration , not about video playback xD
later y try it  , i hope that works !!

But its strange , last month , video playback works fine , with sames restricted drivers and i dont have problems !!! .... i dont understand
well .. thanks !

---

### Post by tiachopvutru on 2007-11-24
> **rabanomen said:**
> maybe works ...
i used to install drivers for fix problems with rendering and aceleration , not about video playback xD
later y try it  , i hope that works !!

But its strange , last month , video playback works fine , with sames restricted drivers and i dont have problems !!! .... i dont understand
well .. thanks !

Well, you could have tried the latest driver, which is 7.11 Catalyst (8.43) ... The only thing is since AIGLX has only been implemented on ATI driver for a month so it doesn't work very well. I have trouble with Compiz, but since using it means I don't require an extra install of XGL, and my video playback happens is smoother than it used to be. (although enabling Compiz gets worse, lol)

Here's the link to the driver, click on "ATI Driver Installer" to download it:
[http://ati.amd.com/support/drivers/linux/linux-radeon.html]("http://ati.amd.com/support/drivers/linux/linux-radeon.html")

It's very simple to install this driver, after you download it, type this in the terminal:
```
sudo sh driver_name
```
Where driver_name is whatever the driver file name is. Alternatively, just drag the file into the terminal.

Wait a bit then a GUI installer will pop up. Follow whatever on screen and install. Then restart

It may work right away for you, but in case it doesn't, you may have to do a little configuration.
Instruction is here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Configure_the_Driver]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Configure_the_Driver")


Of course, if you don't feel like going through with the hassle or wanting to wait for a stable AIGLX, just stick with the current driver you already have.

---

### Post by rabanomen on 2007-11-25
I tried to install the last ati driver in mi computer , but  as you said , it doesnt work fine
I have a  ATI X1300 , seems that make work rendering and aceleration in this card is too harder

I hope in a few months, a new release of the drivers solve my problems with the ATI . If the new drivers doestn make my desktop better , i'll buy a nvidia . Im tired about ati issues and problems

Thanks about the information !! :)

---

