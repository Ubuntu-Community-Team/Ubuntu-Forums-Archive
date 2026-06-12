---
title: "set-up question: No Live-TV on 8.10"
date: 2009-04-04
forum: Mythbuntu
---

### Post by Gerard08 on 2009-04-04
Greetings,

A friend installed mythtv on my dedicated Ubuntu 8.10 system. After he left, I tried to watch TV by clicking on the Watch LiveTV button. The button darkened a bit but nothing happened.

I have a ATI HDTV-Wonder card. I am receiving over the air DBV. I have a NVidia 7600 video card. A home-built AMD 64x2 4000. My reception is fair here in the Northeast U.S. I use a powered indoor antenna.

You can seem my logs here: [http://pastebin.com/m4cd31502]("http://pastebin.com/m4cd31502")

I can receive a few channels for short periods of time using MPlayer

Any help would be appreciated.

---

### Post by Zeedok on 2009-04-05
Have you tuned your turner cards?

I recently installed a Mythbuntu system as well and came across the same problem.  It is a fairly elaborate process and you can find more detailed instructions [here]("http://www.ozmyth.com/wiki/configuring+mythtv+for+australian+digital+tv").  

Briefly, go into Setup -> Mythbuntu -> MythTV setup

Select "Capture Cards" and then "New Capture Card".  Follow the prompts.

Go back one menu and select "Video sources" and "New video source".  Follow the prompts

Then go back to the main MythTV setup menu and select "Input Connections", scan for channels for each of the cards you have and you should get some channels going.

Good luck

---

### Post by Gerard08 on 2009-04-07
Thank You for the suggestions. I started over, making sure that I only used the digital set-up--the software recognizes both analog and dtv tuners as separate capture cards! I also had trouble deleting configurations using the d key. I  had to use my arrow keys to make a selection--the mouse did not work. I now receive an error message "can't connect to backend" so there is progress right?

---

