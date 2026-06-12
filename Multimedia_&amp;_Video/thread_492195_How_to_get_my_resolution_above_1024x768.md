---
title: "How to get my resolution above 1024x768"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by underfunded on 2007-07-04
Hello All,

I have a Westinghouse W4207 LCD with a nvidia 8600 GTS GPU.  The max res on the should be 1366x768, but after installing the nvidia drivers, I can't seem to get my beyond 1024x768.   I ran "xresprobe", but all I got was the following.
id: 
res: 
freq: 
disptype: 

At this point I'm out of ideas.  If anyone can help that would be great.  Below is my xorg.conf output.


Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nv"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by SGI on 2007-07-04
check to see if you have a Nvidia Settings under Applications -> System Tools, if not try opening a terminal and type nvidia-settings. 


-=SGI=-

---

### Post by Beamvr6 on 2007-07-04
I'm away from my Linux box atm where I have a link how to mod xorg.conf for higher resolutions. I'm sure if you use the search function you'll find what you're looking for. Try searching for xorg.conf to begin with.

---

### Post by Wiebelhaus on 2007-07-04
> sudo dpkg-reconfigure xserver-xorg -p high

choose the resolution you want with the spacebar then save.

---

### Post by underfunded on 2007-07-04
Thanks sx, I was able to get the 1280c768, but for some reason the TV won't recognize the change in res..

Beamvr, 

I think you've got a point, my buddy at work told me about the modelines, and how they need to be changed.  I can do a search on them, but if you get a moment can you post the info on how to change them. 

Thanks,

---

### Post by H-Radical on 2007-07-04
I feel funny saying this since more experienced people than myselft haven't pointed this out yet, but am I missing something here or are you not even using your nvidia drivers? Looks to me like you should change ```
 Driver "nv" 
``` in the Device Section to ```
Driver "nvidia"
``` and then see if that helps things or not. In my personal experience, the nvidia drivers drastically improve the graphics on you computer but getting them to work is a whole other story.

---

### Post by ajpug on 2007-07-04
The way I got it to work was to edit xorg.conf.
In particular, you need to change two things. The first is add the resolution you want for the correct color depth, then you need to change the horizontal and vertical frequencies to the ones that you monitor supports.
After doing this everything should work.
Usually you can find vertical and horizontal refresh rates for you monitor on google.

Hope this helps,
ajpug

---

