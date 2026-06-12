---
title: "Resolution problem (black borders)"
date: 2009-05-28
forum: Mythbuntu
---

### Post by mesc on 2009-05-28
I record in 720x576 (PAL Switzerland, analog Cablecom), but the image is not filling the whole area:
[IMG]http://lh5.ggpht.com/_dWrqQY1IE10/Sh5Sy2Xv57I/AAAAAAAAAHg/E-TXeRbEp7A/s640/uvs090528-003.jpg[/IMG]
as you can see the TV fills only about 700x428...
Does someone know why?

---

### Post by SiHa on 2009-05-28
Can't see your picture for some reason.

What interface are you using to the TV? (S-Video, Composite, DVI, etc.)

---

### Post by mesc on 2009-05-28
does that work:
[http://picasaweb.google.ch/lh/photo/Uu_ppY6K7Q8xHxBU5eAQvA?feat=directlink]("http://picasaweb.google.ch/lh/photo/Uu_ppY6K7Q8xHxBU5eAQvA?feat=directlink")
I am using a PVR-150 an connected is direct the analog cable from my cable tv provider ([www.cablecom.ch](www.cablecom.ch))
I tried via S-Video and Composite from my old VHS player and it was even worse...

---

### Post by SiHa on 2009-05-28
huh, the picture displays fine now!

I'm still not sure - how are you connecting the PC to the TV? in other words, is it via a digital (DVI / HDMI) method or analogue (S-Vid, Composite). Is the graphics chipset nVidia? Anyway, the question is less relevant now that I can see the pictture.

Looking at your screenshot (I pasted it into 'Paint') the aspect ratio of the screen is 4:3 (1.25), but the picture is approximately 1.6, which is closer to widescreen. 

So that could account for the top & bottom black bars, if Myth is trying to display the whole picture.

There's a couple of options in the frontend setup you could play with, they will be in one of the 'TV Settings' screens, not sure which at the moment, I'm not at home.

There's an option to force output to a certain ratio (4:3, 16:9 etc). 
I *think* there's an option that tells it how to display widescreen on a 4:3 display (Letterbox / Crop / Stretch).

Not sure if any of this will help, but I found that I have to force 16:9, otherwise I get some strange, almost square, pictures on certain US shows (like Diagnosis Murder:oops:)

---

### Post by nickrout on 2009-05-28
Its hard to tell but the picture looks as though its in the right aspect ratio. 

If you have a 4:3 screen but your boadcaster is sending a 16:9 picture (and most tv shows are shot in 16:9 these days) then you are going to end up with one of three scenarios:

1. Whole picture shown in correct aspect ratio, but with black bars at top and bottom; or

2. whole picture fills whole screen, in which case the picture will be vertically stretched, ie people will be tall and skinny; or

3. Picture cropped to 4:3 ratio and blown up to fill the screen, aspect ratio will be OK but you'll lose the edges of the picture.

Looks like you have scenario 1, although I am not sure why you have black borders on the sides too. Maybe the TV company inserts black borders to allow for overscan? 

Play the file non fullscreened in mplayer and see if the borders are in the original file.

---

### Post by ian dobson on 2009-05-28
Hi,

Are the menus in Mythtv OK (no black bars)?

You can set the fill mode so that the pictue is scaled to fit your TV resolution. On my system I had to set the scaling so that the vertical height was correct and a small amount of the picture is cut off left and right.

What TV do you have? It looks as if the program is 4:3 and your TV is something else (16:9 / 16:10).

Greetings from Birsfelden (No crap Cablecom and their settop boxes here for digital TV:p)

Edit: Try setting your capture resolution to 768x576, that's what I'm using on my PVR-500.

Ian Dobson

---

### Post by mesc on 2009-05-29
To SiHa:
now I understand, sorry, I am using the MSI Media Live (Nvidia graphics)
[IMG]http://www.msi-computer.de/uploads/prod_e1473207cded43be634d75112875c553.jpg[/IMG]
with a SCART connection to an old 4:3 TV.
The mythtv menu looks right to me...
I am going to try the 768x576 resolution recording mode.
>
>
>
10 minutes later

I tried but out of some reason the recorded file is empty?!? Changed back to 720x576.
>
>
>
okay, that is now another problem... I am going to do some tests after the long weekend.

---

