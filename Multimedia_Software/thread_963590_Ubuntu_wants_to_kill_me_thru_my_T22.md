---
title: "Ubuntu wants to kill me thru my T22"
date: 2008-10-30
forum: Multimedia Software
---

### Post by monitor35 on 2008-10-30
Help everybody, Ubuntu wants to see me dead, and is doing so by consistently refusing, release after release, to work on my T22. I can't seem to get video to work on that beast for the life of me.

During boot up, I see the progress bar, but when I should be presented with a login prompt, I'm met with a black screen. Nothing there, can't get out, can't do anything.

If I pop the HDD out and put it in my T23 - aces.

The T22 will run windows fine, but not ubuntu, or ubuntu Live.

help!

---

### Post by eternalnewbee on 2008-10-30
Please excuse my ignorance. What is T22?

---

### Post by monitor35 on 2008-10-30
IBM T22 and T23 laptops.

---

### Post by eternalnewbee on 2008-10-30
> Help everybody, Ubuntu wants to see me dead, and is doing so by consistently refusing, release after release, to work on my T22. I can't seem to get video to work on that beast for the life of me.
That implies that you managed to install Ubuntu.
> 
During boot up, I see the progress bar, but when I should be presented with a login prompt, I'm met with a black screen. Nothing there, can't get out, can't do anything.

That implies that you didn't.

---

### Post by emshains on 2008-10-30
I am sorry, but what was the release date of you're laptops ? And what kind of videocards do they have  ?

---

### Post by Kevbert on 2008-10-30
Welcome to Ubuntu.
How much ram does your T22 have ?  A standard install probably will fail, it looks like you may need to try the alternate (text based) install CD.

---

### Post by monitor35 on 2008-10-31
> **Kevbert said:**
> Welcome to Ubuntu.
How much ram does your T22 have ?  A standard install probably will fail, it looks like you may need to try the alternate (text based) install CD.

My T22 has the maximum RAM possible - 512Mb.

---

### Post by monitor35 on 2008-10-31
As for if I did or did not get it installed - I did. I have been able to boot into ubuntu maybe 5% of the time. When I get in there, I do every update and upgrade I can find in hopes of finding the problem fixed. So yes, it's i nstalled. If I put the HDD in my T23, slightly beefier, newer, it will work. So it seems a video card issue primarily with the T22, but I can't be certain. Even if I change the driver to vesa, which looks like crap, of course, I still can't be guaranteed to get the login screen.
:(

---

### Post by robaerus on 2008-11-13
Hello,
try to replace the device, monitor and screen sections of your xorg.conf file with this:

Section "Device"
        Identifier      "S3 Inc. 86C270-294 Savage/IX-MV"
        Driver          "savage"
        BusID           "PCI:1:0:0"
        Option          "BusType" "PCI"
        Option          "DmaMode" "None"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. 86C270-294 Savage/IX-MV"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

I did it and after I have rebooted Intrepid Ibex is smoothly running on my IBM T22 machine.
Hope this can help.

Cheers

---

### Post by PaulHeth on 2008-11-21
> **robaerus said:**
> Hello,
try to replace the device, monitor and screen sections of your xorg.conf file with this:

Section "Device"
        Identifier      "S3 Inc. 86C270-294 Savage/IX-MV"
        Driver          "savage"
        BusID           "PCI:1:0:0"
        Option          "BusType" "PCI"
        Option          "DmaMode" "None"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. 86C270-294 Savage/IX-MV"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

I did it and after I have rebooted Intrepid Ibex is smoothly running on my IBM T22 machine.
Hope this can help.

Cheers

Uber new user here.  Just giving Ubuntu and this whole Linux thing a try for the first time.  Have tried to run/install Unbuntu (8.04 and 8.10) and Xubuntu on my 800 MHZ, 256MB Ram thinkpad T22.  So far no luck.  Screen goes blank after almost finishing the progress bar.  Seems to be video.  Strangely Knoppix come up without  a hitch.  Even the sound works.

I would love to do as instructed above, but don'e know where to start.  How does Ubunto (or Xubuntu) load, where do I go to find this file? :confused:

Any help is much appreciated.  I would love to leave the MS world behind for all my home PC's.

---

### Post by Fabio K on 2008-11-21
If you can use the keyboard while the screen is blank, try pressing CTRL+ALT+F1.
If you got to the VT (Virtual Terminal), type in ```
sudo nano /etc/X11/xorg.conf
```
Then you'll be able to modify your xorg.conf. It's a text based editor, so I'm afraid you'll have to manually type in the code robaerus told you to.
In case you don't know, xorg.conf is in /etc/X11, it is the file that contains most of the configuration of your mice, keyboard, video card and monitor.

Fabio K

---

### Post by PaulHeth on 2008-11-22
> **Fabio K said:**
> If you can use the keyboard while the screen is blank, try pressing CTRL+ALT+F1.
If you got to the VT (Virtual Terminal), type in ```
sudo nano /etc/X11/xorg.conf
```
Then you'll be able to modify your xorg.conf. It's a text based editor, so I'm afraid you'll have to manually type in the code robaerus told you to.
In case you don't know, xorg.conf is in /etc/X11, it is the file that contains most of the configuration of your mice, keyboard, video card and monitor.

Fabio K

Thanks for the post.

Once it reached the blank screen the keyboard ant ctrl-alt-F1 produces no results.

I have tried the same cd on a T23 I have here and it comes up beautifully.

Any other suggestions?

Thanks.

---

### Post by Fabio K on 2008-11-22
I had some issues with my laptop using a VIA card, the X session wouldn't boot, instead it drew lines all over the screen and made the system lock up. I have managed to get through that by pressing CTRL+ALT+F1 while it is booting and keep repeatedly pressing it until it finished booting.
Then I killed gdm ```
sudo /etc/init.d/gdm stop
``` Changed the bits on xorg.conf```
sudo nano /etc/X11/xorg.conf
``` and started X```
startx
```
I was using feisty at the time. But these commands are still the same in hardy. Maybe for intrepid too.

I think that the alternative cd would work too, but I have no idea how it works.

Fabio K

---

