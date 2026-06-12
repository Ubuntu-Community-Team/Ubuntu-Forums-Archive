---
title: "Ubuntu sound problem"
date: 2011-06-30
forum: Multimedia Software
---

### Post by vgartzolos on 2011-06-30
Good evening to you all. 
As most people i got bored with Windows 7, thus i decided to install Ubuntu 11.04 on my system. Everything works great, except the fact that i hear no sound to all applications or browsers i have tried. I have searched it to other forums, i have installed the latest editions of "restricted extras" and " alsa driver modules" but i didn't find any solution. I have also noticed that ubuntu does not recognize the correct sound card which is installed on my computer. I have "realtek 5.1" integrated with my motherboard (MSI) but i have the following options for sound cards:

Analog Stereo Input
Digital Stereo Duplex (IEC958)
Digital Stereo (IEC958) Output + Analog Stereo Input
Analog Stereo Output
Analog Stereo Duplex

No matter what i choose o hear no sound....
Any suggestions???

Thanks...

---

### Post by lidex on 2011-06-30
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

