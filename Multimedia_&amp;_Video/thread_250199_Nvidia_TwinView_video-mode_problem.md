---
title: "Nvidia TwinView video-mode problem"
date: 2006-09-03
forum: Multimedia &amp; Video
---

### Post by willgott on 2006-09-03
Hi everybody

I have a really tough problem that I would be really happy I someone could help me with.

I am trying to enable the twinview functionality on my Nvidia Geforce FX
5200 Go (driver ver 1.0-8762). The primary display is my laptop's
(Toshiba M200) DFP running at 1400x1050 while
the secondary is a CRT, Sun (Sony is the original manufacturer) GDM-20E20, (capable of 1600x1200). The server starts fine and according to its log (attached below)
it detects both displays and creates a
virtual area of 2800x2100.
However, the image on the CRT is distorted:
1) It tilts slitghtly to the right
2) It's very far from the left border of the display
3) The location of X's cursor (the famous X) is marked by a horizontal disruption/distortion that makes the cursor unidentifiable. Moving the mouse from the left to
the right side changes the distortion. It looks like the cursor "sucks" the border towards itself.
4) The display goes on and and off (I assume it cuts the picture whenever the signals goes outside the bounds).

I have tried, to no avail, with the following:
1) Change resolution in xorg.conf
2) Manually specify the CRT's horizontal and vertical sync (horizync and vertrefresh).

The result is very similar with the distortion only changing slightly and the CRT sometimes only turns on when I move the mouse-pointer into its area. A
friend of mine told me that the horizontal sync was whacked so I tried to adjust it with xvidtune, but that proved to be a fruitless attempt ("can't change
frequencies on this chip"). Furthermore I would like add that I've used this display successfully with X in the past and that it
works just fine with Windows XP.

I have spent well above 10 hours on this problem and my frustration is increasing. I appreciate all the help I can get.

Best regards,
Ville Jutvik

[X's startup log]("http://www.update.uu.se/~ville/nvidialog.log")
[My xorg.conf]("http://www.update.uu.se/~ville/xorg.conf")

---

### Post by wiseguy8575 on 2007-05-23
I really need help with this too guys.  I can't seem to get TwinView working.  I have the same exact laptop.

---

### Post by fenian on 2007-05-23
Use Envy to install newest drivers follow instructions [here.]("http://www.albertomilone.com/nvidia_scripts1.html")

After you have installed the new drivers open the nvidia-settings panel with...
> 
sudo nvidia-settings

this will bring up a gui window from where you can setup twinview (X Server Dispplay Configuration) be sure to click the Save to X Configuration button before you quit.

---

