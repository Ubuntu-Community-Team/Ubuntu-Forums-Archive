---
title: "configuration of Nvidia RIVA TNT2 64mb AGP video card"
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by wpshooter on 2008-03-24
What method is correct for getting the maximum/highest resolution possible when installing Gutsy on a system which is using an Nvidia RIVA TNT2 64mb AGP video card.

Here's my experience so far.

Installed Gutsy from scratch and afterwards had 1280 x 1024 resolution.

Decided to try the restricted driver and and I restarted after installing & had only 2 lower resolutions available, the highest being 800 x 600.  Performanance FPS was a good bit higher than on the scratch Gutsy install, but I want resolution higher than 800 x 600.

So I unchecked the restricted driver box, restarted and went back to Gutsy scratch setting.

Then decided to let ENVY have a try at it but after going thru ALL of that stuff that it does, and after restarting wound up again with highest available resolution of 800 x 600.

What is the correct procedure to get a good reasonable resolution rate with this card at it's best FPS performance ?

Thanks.

---

### Post by CaTeGoRe on 2008-03-25
Bump.. I'm having the same issue on a Compaq Evo D510

---

### Post by wpshooter on 2008-03-25
> **CaTeGoRe said:**
> Bump.. I'm having the same issue on a Compaq Evo D510

I had a suggestion from elsewhere, that I try going to the Nvidia site and download and install the driver from there.

But when I go to their site and do the download, there is supposedly a link shown for a README but when I click on it all I get is "file not found".

Is the card that you are having problems with the very same video card that I am trying ?

Thanks.

---

### Post by cirorodrigues on 2008-04-23
I faced this problem, and I fixed it editing directly the X configuration file (/etc/X11/xorg.conf), adding 1024x768 resolution in the "monitor" section. The problem is not directly linked to nvidia drivers, but to the config file. Higher resolutions were not added to it and I did it manually. 
Furthermore, I needed to edit also a file linked to GDM, as my desktop went to 1024x768, but the login screen was kept on 800x600. Editing GDM config files solved also this.
There's specific syntaxes and you'll need to know the vertical and horizontal sync frequencies for your monitor (see its manual).
Sorry I can't reproduce here what I did, as I upgraded to Hardy from scratch. You can find many howto around explaining how to edit X configuration files.

---

### Post by dwlegg on 2008-05-17
You can get a higher resolution by reducing the number of colours from 24 bits to 16 bits in the xorg.conf file.

TNT2 is a pretty feeble graphic card though.
A GeForce2 would be much better and nto cost v. much.

---

