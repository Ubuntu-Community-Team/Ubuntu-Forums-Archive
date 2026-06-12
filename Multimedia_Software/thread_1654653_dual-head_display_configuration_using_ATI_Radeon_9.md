---
title: "dual-head display configuration using ATI Radeon 9200 5961 (AGP)"
date: 2010-12-28
forum: Multimedia Software
---

### Post by maarten256 on 2010-12-28
For about a week now (altogether) I've been working to get my desktop set up with a shared desktop across two monitors.

After a lot of research and trawling through more-or-less relevant postings and other information available on the web, I seem to have hit the good spot and got it to work. I'm not an expert of any sort in this xserver business; the below is the result from ample hours of trial and error, and since it works I figured I'd best share as there might be somebody else out there who could use this information. Happy to hear if I could've done something different/better to achieve the same result.

Here then is the summary, for those out there trying something similar... This works for me - it might not for anybody else! ;)

I'm running Ubuntu 10.10 (Linux version 2.6.35-24-generic) 32 bit with an ATI Radeon 9200 Graphics Card.

As I found out, there are both the ATI version of the driver for the Radeon board (fglrx) and the open source driver (xserver-xorg-video-ati & xserver-xorg-video-radeon).

There are a lot of threads out there that talk about fxglr - I did not have much luck getting it to work (essentially after installing fxglr the ATI configuration application still wouldn't work) so I gave up on that and stuck with trying the open source drivers.

I have not had much luck getting my setup to work using the Monitors application (System->Preferences->Monitors) as generally using that tool would result in both displays showing complete garbage or mostly (~75%) garbage. I still have not figured out why this tool doesn't work for me.

However, after a lot of digging around I decided to try and put together my own xorg.conf file (located in /etc/X11) to "force" the xserver into the configuration I wanted. It is my understanding that the newer xserver does not need xorg.conf but will read it in if available - essentially it'll assume default setting for a whole lot of things unless the user specifies otherwise.

The xorg.conf I ended up with is:

Section "Device"
    Identifier "Card0"
    Driver "radeon"
    Option "Monitor-VGA-0" "Envision"
    Option "Monitor-DVI-0" "Acer"
EndSection

Section "Monitor"
    Identifier "Envision"
    Option "PreferredMode" "1440x900"
    Option "RightOf" "Acer"
EndSection

Section "Monitor"
    Identifier "Acer"
    Option "PreferredMode" "1440x900"
EndSection

Section "Screen"
    Identifier "Screen 0"
    SubSection "Display"
        Virtual 2880 900
    EndSubSection
EndSection

Note that I left a host of settings up to the xserver/OS to figure out for itself... For the graphics board I specified what driver to use (radeon) and what monitor definitions should be associated with the outputs available on the board (I'm using VGA and DVI, S-Video is not used).

Then, for each of the monitors I'm enforcing the resolution (1440x900), as well as the order (VGA output physically to the right of the DVI output).

Last I define the virtual display as 2800x900 (so both displays fit next to each other). I'm not sure if that section is really required or not, but it works so I'm not going to try and see what happens if I take it out!

Some other tweaks I implemented:

    Insert "modprobe radeon" into your /etc/init/gdm.conf just before the gdm-binary is executed    Add radeon.modeset=1 to the end of the line GRUB_CMDLINE_LINUX_DEFAULT= in grub


Both suggestions from this page: [https://wiki.kubuntu.org/X/KernelModeSetting](https://wiki.kubuntu.org/X/KernelModeSetting)


I added these before I wrote the above xorg.conf, so I'm not sure they have any effect at all (they sure did not help any before I added my xorg.conf) but again I got it to work now, so I'm not taking them out to see what happens.


Last but not least, /var/log/Xorg.0.log indicates that it reads the configuration and picks up the settings from it...

---

