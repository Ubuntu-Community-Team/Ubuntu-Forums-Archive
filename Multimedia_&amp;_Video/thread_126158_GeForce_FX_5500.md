---
title: "GeForce FX 5500"
date: 2006-02-05
forum: Multimedia &amp; Video
---

### Post by Sape on 2006-02-05
I am a complete and utter newb, i know nothing about Ubuntu...(one too many "blue screens of death" from windows)

I have everything working, except my video card. I have a GeForce FX 5500 PCI

I have the driver from Nvidia installed, but my resolution will not go above 1024 x 768, but i know that both my monitor and video card support 1280 x 1024 (the resolution i was aiming for)

I looked up my video card in the device manager and it says everything but the vendor is unknown.

I'm sorry that i don't know what information i need to put up for help, but if you ask and tell me how i can tell you :confused: 

Thanks to everyone in advance

---

### Post by grimmson on 2006-02-05
When you set up xorg.conf did you "*" 1280-1024
you might try to paste this in applications>system tools>terminal
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak 
to backup xorg
sudo dpkg-reconfigure xserver-xorg
This command lin configurator will ask what resolutions you want. "*" whatever you may want in the future and leave blank whatever you don't want to show.
Research xorg.config first. you may be able to 
sudo gedit /etc/X11/xorg.conf
and paste over Section "Screen"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
to add 1280x1024. I've never tried this method but I assume it will work. Please look it up first. I 1280x1024 is in the Section "Screen" ov xorg then I can't help. good luck.

---

### Post by veritas366 on 2006-02-05
I asked a similar question in the wrong forum and I think it (rightfully) got deleted.  I'm going to change video cards from a 64 mb nvidia geforce 4 to the FX 5500...they are on sale at circuit city for 40 bucks...and it's a big upgrade for me.

If I swap out cards, will the driver pick up the new one since it is also nvidia?  If not, what needs to be done BEFORE I switch...and what should wait till after.  I'm hoping to get the latest driver and not just the one in the repos because I tweaked my desktop as suggested in the "stealing KDE's eyecandy" thread and I think this needs the latest drivers.

What I am trying to avoid is failure to start x in the first place.  I'm still insecure with command only.  I'll do it with step by step directions but I can't even edit text in terminal mode.  

I think my xorg file should be okay as nothing specific to the model of nvidia card seems to reside there.  But are there things I should worry about?  Problems with this specific card?

---

### Post by Sape on 2006-02-05
thank you very much grimmson, it is working properly and playing nice..
i know nothing about about ubuntu, so i couldn't answer your question...someone else could probably, but if it were windows you wouldnt have to do anything >.>

---

