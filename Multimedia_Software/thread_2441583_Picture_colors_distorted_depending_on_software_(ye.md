---
title: "Picture colors distorted depending on software (yellowish in picture viewer)"
date: 2020-04-24
forum: Multimedia Software
---

### Post by whochismo on 2020-04-24
I am in the process of scanning a few picture albums. I want the color to be at least moderately accurate, so I bought a colorimeter and calibrated my screen. I use Xsane to scan my pictures, and Gimp to do some adjustments (cropping, color curves, etc.)

However, I noticed something. In Xsane I scanned a picture. Then I opened that picture using ubuntu's picture viewer. I noticed it looked warmer, more yellowish. Then I opened that same picture in Gimp: it looks exactly the same as in Xsane. 

I have tried converting the picture from png, to jpg, and I even used a .gif with a color palette I got from internet. In all cases, image viewer looked different from gimp.

So I decided to measure the colors using gpick (in case I was going mad and it was just a perceptive issue), and indeed, the colors were different in each application.

This the original image I am trying to compare:
[IMG]https://i.imgur.com/aYsCaAr.gif[/IMG]

I opened that file in several software and measured the colors using gpick: Gimp, Image viewer, Google Chrome, Mozilla Firefox, and Darktable. 

These were the results:
[IMG]https://i.imgur.com/Hf06E2p.png[/IMG]

So, Gimp, Xsane and Firefox display the true RGB colors in Ubuntu.

Image viewer and Darktable show the same colors, but with a warmer tone compared to the true RGB colors.

Google Chrome shows its own colors, also different from the true RGB colors.

So, my question: Why is that, and how can I make the image viewer show the true colors of a picture?

PS: you can only see this post correctly in Mozilla Firefox. :-?


EDIT: I managed to display the colors in Google Chrome identical to those in Gimp and Firefox, by going to [chrome://flags/]("chrome://flags/") and changing the Force color profile option to "sRGB". Now I have to find if there's a way to force image viewer to display colors in sRGB.

EDIT2: running this command: 
[FONT=Courier New]xprop -root -remove _ICC_PROFILE[/FONT] 
made that image viewer showed the correct colors, regardless of the colors profiles that you have set to your monitor. So, solved for now, although I don't know if those changes will survive a restart.

EDIT3: That command does not survive a restart. It must be run after each login. However, I have noticed that Shotwell picture viewer, that is already installed in Ubuntu, displays the colors correctly. So for now I will use that viewer instead of the default picture viewer (Eye of Gnome).

---

### Post by Claus7 on 2020-04-29
Hello,

"you painted then"! 

Just a minor comment to your step by step comprehensible guide (since it became a guide in the end), is to add the command in the startup applications if you want every time you reboot to use the eye of gnome instead of shotwell.

Regards!

---

