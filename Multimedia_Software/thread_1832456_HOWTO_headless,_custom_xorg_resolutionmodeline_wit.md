---
title: "HOWTO: headless, custom xorg resolution/modeline with vnc access to display 0 console"
date: 2011-08-24
forum: Multimedia Software
---

### Post by tigerstripedcat on 2011-08-24
(This HOWTO will cover different aspects you might not need all of this, but if you need a) a custom resolution b) setup headless access c) access to the console (display :0)remotely part of this may be useful to you.)

So this was going to be a question but it turned into a HOWTO after spending hours on this. 

PROBLEM #1: I needed remote access to the console (display :0) of a server from a laptop because I needed to access the audio hardware (though I'm sure there are different reasons one needs access to :0) so nx, tightvnc, xvnc were all out.   
PROBLEM #2: The server had no monitor attached
PROBLEM #3: I was connecting with a laptop that had a resolution of 1280x800 but of course windows (and other OSes) have a task bar, so the actually workable area is less than that.  I needed a resolution of 1224x685 (not your typical resolution).
PROBLEM #4: need the vnc server to start at boot to allow login from the server (no monitor).

1) Install x11vnc (this seems to be the only vnc server I found that allows console access, nomachine 4 (coming soon) and nomachine 3 have some form of 'physical screen' access, but I had a hard time with managing the audio hardware with that so I needed to use vnc.
```
sudo apt-get install x11vnc
```


2) To make x11vnc start at boot, create a password (instructions here: [http://www.karlrunge.com/x11vnc/faq.html#faq-passwd](http://www.karlrunge.com/x11vnc/faq.html#faq-passwd)) with the xserver place the following at the bottom of /etc/gdm/Init/Default

```

/usr/bin/x11vnc -forever -rfbport 5900 -rfbauth /etc/x11vnc.pass -auth guess -display :0 -bg -shared -noxdamage -xrandr

```

This will start your vnc server when your xserver starts.

3) Modify grub so that your kernel doesn't start a modeline module.  Edit /etc/defaults/grub and make sure your GRUB_CMDLINE_LINUX_DEFAULT variable includes a 'nomodeset' flag:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

(I'm not certain if that step is necessary, but I think so.)

4) Install the 'dummy' xorg driver.  This tells the xserver that there is no monitor:

```
sudo apt-get install xserver-xorg-video-dummy
```

5) Modify your /etc/X11/xorg.conf file.  The xserver tries to do everything it can to get settings form the monitor.  We need to disable all this and the 'dummy' driver might not be enough, hence the NoDDC AND IgnoreEDID.   Here is my xorg.conf:

```

Section "Monitor"
Identifier "Monitor0"
HorizSync 28.0-80.0
VertRefresh 48.0-75.0
#Modeline "1280x800"  83.46  1280 1344 1480 1680  800 801 804 828 -HSync +Vsync
# 1224x685 @ 60.00 Hz (GTF) hsync: 42.54 kHz; pclk: 67.72 MHz
Modeline "1224x685" 67.72 1224 1280 1408 1592 685 686 689 709 -HSync +Vsync
EndSection

Section "Device"
Identifier "Card0"
Option "NoDDC" "true"
Option "IgnoreEDID" "true"
Driver "dummy"
EndSection

Section "Screen"
DefaultDepth 24
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
    SubSection "Display"
    Depth 24
#    Virtual 1280 800
    Modes "1224x685"    
    EndSubSection
EndSection

```

6) Add a custom resolution.  You'll notice my custom resolution above (the two calls to "1224x685").  I used this calculator to generate the modeline (but there are many cli and online calculators):

[http://www.arachnoid.com/modelines/index.html](http://www.arachnoid.com/modelines/index.html)

If you need something else, use that calculator and replace the relevant parts.


7) Restart the computer and log into your sever with a vncclinet and enjoy your custom-resolution, headless, vnc.  

Note that vnc is not encrypted after login so if you need this procedure of important information you should run this though an SSH tunnel (see other howtos).  I may have forgot something here, so if you need help, I'm subscribed to this thread and I would be happy to help, or you can find me as 'aaas' on IRC.  

TSC

---

### Post by ajmssc on 2011-08-25
Thanks this was helpful to me

---

### Post by 13thfloor on 2012-01-20
Thanks.  This helped me setup my server at home.  We have a need for a couple of servers setup like this at work too.  Glad I finally found this page.

---

