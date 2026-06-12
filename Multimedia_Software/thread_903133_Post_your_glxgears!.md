---
title: "Post your glxgears!"
date: 2008-08-28
forum: Multimedia Software
---

### Post by tuxxy on 2008-08-28
I got some interesting results running glxgears recently, wondered how everyone elses looked, below is an example of mine 

```
:~$ glxgears
46223 frames in 5.0 seconds = 9244.529 FPS
46938 frames in 5.0 seconds = 9387.399 FPS
46120 frames in 5.0 seconds = 9223.916 FPS
44482 frames in 5.0 seconds = 8896.369 FPS
45938 frames in 5.0 seconds = 9187.447 FPS
43560 frames in 5.0 seconds = 8711.875 FPS
```

---

### Post by Rhubarb on 2008-08-28
GeForce 7950, with over-clocked memory and GPU:
```
88454 frames in 5.0 seconds = 17690.668 FPS
89192 frames in 5.0 seconds = 17838.365 FPS
88834 frames in 5.0 seconds = 17766.725 FPS
88842 frames in 5.0 seconds = 17768.350 FPS
88786 frames in 5.0 seconds = 17757.074 FPS
88258 frames in 5.0 seconds = 17651.486 FPS
```

Edit, and if I overclock it some more, I can get it running stable:
```
92874 frames in 5.0 seconds = 18574.686 FPS
92824 frames in 5.0 seconds = 18564.607 FPS
92947 frames in 5.0 seconds = 18589.223 FPS
92437 frames in 5.0 seconds = 18487.289 FPS
92550 frames in 5.0 seconds = 18509.992 FPS
92776 frames in 5.0 seconds = 18555.129 FPS
```
:D

---

### Post by Melcar on 2008-08-28
Glxgears is not really a benchmark; it's more of a tool to see if you got working 3D or not.  Hell, my old x1950xt got higher numbers than my current HD3850.

---

### Post by Rhubarb on 2008-08-28
True Melcar, but it's fun to do sometimes.
In my case glxgears does reflect performance in games by comparing speeds in glxgears with how much I overclock my video card.

---

### Post by tuxxy on 2008-08-28
> **Rhubarb said:**
> GeForce 7950, with over-clocked memory and GPU:
```
88454 frames in 5.0 seconds = 17690.668 FPS
89192 frames in 5.0 seconds = 17838.365 FPS
88834 frames in 5.0 seconds = 17766.725 FPS
88842 frames in 5.0 seconds = 17768.350 FPS
88786 frames in 5.0 seconds = 17757.074 FPS
88258 frames in 5.0 seconds = 17651.486 FPS
```

Edit, and if I overclock it some more, I can get it running stable:
```
92874 frames in 5.0 seconds = 18574.686 FPS
92824 frames in 5.0 seconds = 18564.607 FPS
92947 frames in 5.0 seconds = 18589.223 FPS
92437 frames in 5.0 seconds = 18487.289 FPS
92550 frames in 5.0 seconds = 18509.992 FPS
92776 frames in 5.0 seconds = 18555.129 FPS
```
:D

hehe nice, mines not been touched settings wise.

---

### Post by Prefix100 on 2008-08-28
> **Rhubarb said:**
> GeForce 7950, with over-clocked memory and GPU:
```
88454 frames in 5.0 seconds = 17690.668 FPS
89192 frames in 5.0 seconds = 17838.365 FPS
88834 frames in 5.0 seconds = 17766.725 FPS
88842 frames in 5.0 seconds = 17768.350 FPS
88786 frames in 5.0 seconds = 17757.074 FPS
88258 frames in 5.0 seconds = 17651.486 FPS
```

Edit, and if I overclock it some more, I can get it running stable:
```
92874 frames in 5.0 seconds = 18574.686 FPS
92824 frames in 5.0 seconds = 18564.607 FPS
92947 frames in 5.0 seconds = 18589.223 FPS
92437 frames in 5.0 seconds = 18487.289 FPS
92550 frames in 5.0 seconds = 18509.992 FPS
92776 frames in 5.0 seconds = 18555.129 FPS
```
:D

Teach me to overclock my 8600GT :<

---

### Post by Jose Catre-Vandis on 2008-08-28
OK, so where am I going wrong
```
linux@hardy:~$ glxgears
4674 frames in 5.0 seconds = 934.600 FPS
4617 frames in 5.0 seconds = 923.227 FPS
4706 frames in 5.0 seconds = 941.058 FPS
4799 frames in 5.0 seconds = 959.698 FPS
4717 frames in 5.0 seconds = 943.329 FPS
4726 frames in 5.0 seconds = 945.056 FPS
4795 frames in 5.0 seconds = 958.876 FPS
4713 frames in 5.0 seconds = 942.247 FPS
XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 36 requests (36 known processed) with 0 events remaining.
```

This on Nvidia 6800

---

### Post by tuxxy on 2008-08-28
How do these equate though to FPS in games, im sure mine hits around 300 when in game.

---

### Post by djRobbieF on 2008-08-28
> **Jose Catre-Vandis said:**
> OK, so where am I going wrong
... This on Nvidia 6800

You answered your own question.  ;)  You'd want a bare minimum of a 7600.

Here's my 7950GT:
52518 frames in 5.0 seconds = 10503.583 FPS
51472 frames in 5.0 seconds = 10294.190 FPS
52083 frames in 5.0 seconds = 10416.598 FPS
50610 frames in 5.0 seconds = 10121.796 FPS
51446 frames in 5.0 seconds = 10289.181 FPS

---

### Post by Tom--d on 2008-08-28
I thought my card was quite fast.. but.. seeing those figures just put me down :(
I have a Intel 965 chipset.
```
4540 frames in 5.0 seconds = 906.681 FPS
4540 frames in 5.0 seconds = 904.130 FPS
4540 frames in 5.0 seconds = 905.267 FPS
4540 frames in 5.0 seconds = 904.274 FPS
4520 frames in 5.0 seconds = 901.158 FPS
4540 frames in 5.0 seconds = 906.863 FPS
4527 frames in 5.0 seconds = 903.838 FPS
4540 frames in 5.0 seconds = 905.135 FPS

```

---

### Post by djRobbieF on 2008-08-28
> **Tom--d said:**
> I thought my card was quite fast.. but.. seeing those figures just put me down :(
I have a Intel 965 chipset.


Integrated video will never perform as well as a half-decent nVidia card.  You won't believe the difference if you install one.

---

### Post by Tom--d on 2008-08-28
> **djRobbieF said:**
> Integrated video will never perform as well as a half-decent nVidia card.  You won't believe the difference if you install one.

Really? 
Its that big of a difference? Wow.

---

### Post by djRobbieF on 2008-08-28
> **Tom--d said:**
> Really? 
Its that big of a difference? Wow.

Absolutely.  *Especially* if you want to use the beautiful compiz-fusion effects; a PCIe video card, for example, will take the load of the 3D off your CPU and put it on the GPU on the card, resulting in faster performance all across the board.  Plus, your integrated video uses some of your RAM for its video RAM.  Again, a card will stop this from occurring (as long as you disable the on-board) and give you more RAM, which translates into better performance.

---

### Post by tuxxy on 2008-08-28
> **Tom--d said:**
> Really? 
Its that big of a difference? Wow.

It certainly is, I dont think ill ever build myself a system again that didnt have an nvidia card :lolflag:

---

### Post by djRobbieF on 2008-08-28
> **tuxxy said:**
> It certainly is, I dont think ill ever build myself a system again that didnt have an nvidia card :lolflag:

Just to expand on the "nVidia" thing a little further, IMO nVidia has the best support for OpenGL graphics.  This is why I choose nVidia over ATI or any other brand.  Linux relies heavily on OpenGL, where Windows uses DirectX, for the most part.  So while an ATI card would do fine on Windows (DirectX), I prefer the nVidia line in Linux (OpenGL).

Again; this is only my opinion.

---

### Post by tuxxy on 2008-08-28
I have been through hell with them ATI drivers, never again :lolflag:

---

### Post by Tom--d on 2008-08-28
Yeah.. i would love to replace it but.. its in a laptop.

I do have a ati card in a Desktop.
Its an ATI X1650 Pro and I could not get 3D support, at all. Tried everything.

---

### Post by tuxxy on 2008-08-28
Ye I got a that card and a x1250 onboard, the x1250 seems to work to an extent but with major flaws in compiz effects and 3D graphics.

---

### Post by Crafty Kisses on 2008-08-28
> **Melcar said:**
> Glxgears is not really a benchmark; it's more of a tool to see if you got working 3D or not.  Hell, my old x1950xt got higher numbers than my current HD3850.

Yeah I agree, plus on the computer I'm on right now, I would be embarrased to post them. (not my main one)

---

### Post by tuxxy on 2008-08-29
> **Codename said:**
> Yeah I agree, plus on the computer I'm on right now, I would be embarrased to post them. (not my main one)

heh go on, you cant not do now! :lolflag:

---

### Post by markbuntu on 2008-08-29
I can change my graphics settings so glxgears runs at 60, or runs at 15,000+. It is really a useless benchmark more dependent on cpu and graphics settings than raw gpu speed.

---

### Post by remicks916 on 2008-09-05
```
:~$ glxgears
43804 frames in 5.0 seconds = 8760.770 FPS
45899 frames in 5.0 seconds = 9179.711 FPS
46081 frames in 5.0 seconds = 9216.135 FPS
46342 frames in 5.0 seconds = 9268.336 FPS
46152 frames in 5.0 seconds = 9230.254 FPS

```

System specs in signature below :)

---

