---
title: "SIS741GX video onboard problems..."
date: 2006-02-03
forum: Multimedia &amp; Video
---

### Post by AzraelShade on 2006-02-03
Just installed Ubuntu 5.10 on a new PC with an ASRock 741GX MoBO and a Sempron 2800+. Seems Ubuntu is acting a little weird on my card: Here goes... 
Installed ubuntu it booted in 640x480. So first thing go to /etc/X11/xorg.conf > Section "Device"
        Identifier      "Silicon Integrated Systems (SiS) SiS Default Card"
        Driver          "sis"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "ADI VD-695B"
        Option          "DPMS"
EndSection

        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"

So I said it should work.. seems everything works fine. Still in the Preferences/Resolution Choose i get only 640x480 on 60 Hz.. Then go for a CTRl+backspace. Result: WOW, it works in 1280x1024 in 60hz

After install a few things with Automatix , reboot my PC.. Gone back to 640x480. xorg.conf is the same , but CTRL+backspace doesn't do the trick now

---

### Post by AzraelShade on 2006-02-03
Keep trying.. but not much of a result.. instead i came upon this [http://www.winischhofer.at]("http://www.winischhofer.at/linuxsispart4.shtml")
Tried the sis_drv.o for Xorg 6.8.2 and gcc version 3.x .. 
> X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8))


Still no good... Anyone managed to solve their SiS problem with that.. ?

~~~AzraelShade~~~

---

### Post by AzraelShade on 2006-02-03
LOL... I changed in xorg.config from Driver "sis" to Driver "vesa" .. and it worked.. or smth like this .. I can choose a rezolution from 1280*1024 , 1024*768, 800*600 and 640*480... But at the refresh rate selection i can only select... 0 Hz?!? Also when it worked the first time( see first post) i could choose from much more resolutions, even if the limit was still 1280*1024 - those were the intermediat resolutions. Will try further more till I get the Hz thing too...

P.S. Posting all these, maybe someone will need this too!

~~~AzraelShade~~~

---

### Post by Teroedni on 2006-02-03
You should go back to the sis driver. Vesa is bad

The reason  you get so low refresh rates is probably because your vert  and horinz are set too low

Can you paste your xorg.conf file here and i show you where you need to alter

---

### Post by AzraelShade on 2006-02-03
Section "Device"
        Identifier      "Silicon Integrated Systems (SiS) SiS Default Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"

EndSection

believe this is what you asked for... but changing to sis will go matters into worse.. only 640*480 option!no thanx.. although i know vesa isn't the way, that's what i got for now, yet I am in search for a new solution ( video files and vesa in fs - bad combination -> proc at 100% full time)
Btw.. don't know if you read the 2 other posts.. i explained the whole process i've gone trough.
~~~AzraelShade~~~

---

### Post by AzraelShade on 2006-02-04
LOL .. this is very funny.. after about 6 hours of researching around and a failed try of compiling the xorg server and get the driver from there.... The solution came from one of the ubuntuforums.org members
 ```
dpkg-reconfigure xserver-xorg
```

So ... many thanks to JASMUZ for this one! :)

~~~AzraelShade~~~

---

### Post by DanyAlejandro on 2007-01-18
Another SIS741GX video onboard user (newbie) here.

Used the command, put in some random info (sorry, I'm not hi tech like u ppl so I didn't understand anything they asked me in the utility), video works ok, scrolling, dragging windows as fast as it should be... maybe i got my 2d/3d/4d/wtever aceleration working.

Happy newbie here ^_^ thanks a lot, AzraelShade! U saved me from throwing linux to the trash for another 3 years...

---

