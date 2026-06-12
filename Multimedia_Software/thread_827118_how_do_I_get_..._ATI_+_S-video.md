---
title: "how do I get ... ATI + S-video"
date: 2008-06-12
forum: Multimedia Software
---

### Post by cyclingman on 2008-06-12
I have laptop with an S-video output and (working) cable which i wish to connect up to a television. I am using the open source ATI drivers that were originally installed (no fglgx - i don't think I can) and an (old) ATI Radeon Mobility M6 LY graphics card.

I must have tried over a million different methods (all to which have failed), I don't care how, I just want the easiest method of an S-video output. Can anyone give some suggestions on how to do this, from the top, as if I haven't tried anything.

Thank you!

Oh yeh, and in terms of Ubuntu knowledge, I'd call myself an intermediate beginner.

---

### Post by cyclingman on 2008-06-14
anyone?

---

### Post by overdrank on 2008-06-14
> **cyclingman said:**
> I have laptop with an S-video output and (working) cable which i wish to connect up to a television. I am using the open source ATI drivers that were originally installed (no fglgx - i don't think I can) and an (old) ATI Radeon Mobility M6 LY graphics card.

I must have tried over a million different methods (all to which have failed), I don't care how, I just want the easiest method of an S-video output. Can anyone give some suggestions on how to do this, from the top, as if I haven't tried anything.

Thank you!

Oh yeh, and in terms of Ubuntu knowledge, I'd call myself an intermediate beginner.

HI and I do not have a ati card running at the moment but have you tried 
```
gksu displayconfig-gtk
```

---

### Post by ag65151 on 2008-06-14
Have you tried xrandr?

---

### Post by soxs on 2008-06-14
> **overdrank said:**
> HI and I do not have a ati card running at the moment but have you tried 
```
gksu displayconfig-gtk
```
DO NOT use that tool, NO WAY! It is like playing russian roulette. It will mix/mess up your xorg.conf and leave you behind with vesa rendering and 800x600 or 640x480 resolution!! DO NOT use that crazy tool!
You will have to learn, how to configure xorg.conf by hand (the only secure way without shooting your gdm/kdm whatever)

---

### Post by cyclingman on 2008-06-15
Thanks for all the replies. Yes I have tried the gksu displayconfig-gtk program, and yes it did mess everything up, but luckily I had a backup of xorg.

Can you explain more about xrandr and its capability with my graphics card?
Can you explain how I go about editing my xorg? and if I did, would I need to edit it again each time i connected the S-video cable?

Thanks again!

---

### Post by soxs on 2008-06-15
A good refernce as always is man xorg.conf. It includes a lot info (especially for old cards, new ones only use a limited number of the listed options).
I am an ati user from the beginning, but I never tried attaching multiple displays to my gpu device.
Googled a little.. here are 2 links that seemed usefull: 
[http://hobbylobby.wordpress.com/2007/09/08/dual-monitors-in-ubuntu-xorgconf-driver-ati-card/](http://hobbylobby.wordpress.com/2007/09/08/dual-monitors-in-ubuntu-xorgconf-driver-ati-card/)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by cyclingman on 2008-06-15
Thanks for the info, I'll have a look/give it a try, then post back.

---

### Post by cyclingman on 2008-06-21
OK, after looking around and trying several things, I think my problem is that the S-video out isn't being recognized. This is after using xrandr, i get the following message:
> S-video disconnected (normal left inverted right x axis y axis)

Similarly, if I use the ATITVOUT program, that I found on this post, which seems to have worked for others ([http://ubuntuforums.org/showthread.php?t=382333&highlight=igp+340](http://ubuntuforums.org/showthread.php?t=382333&highlight=igp+340)   -   3rd post down) I get this reply when trying to detect displays with "sudo atitvout -r detect"
> Forcing Radeon/Rage 128 mode
CRT is attached.


The cable is fine (it works on a separate laptop running windows) and I have the cable plugged in when I reboot.

Does anyone have any suggestions as to why it is not being recognized, or am I on the wrong track?

Thanks again.

---

### Post by rubberglove on 2008-07-03
I don't know how much help I can be, but here is how I got s-video working on my desktop (radeon 9250). I'd take it with some grain of salt, as it's been a while since I wrestled with this issue.

First, you need to add a line to xorg.conf, if it isn't there already. In the "Display" subsection of the "Screen" section, you need to add a 'virtual' screen resolution, which is big enough to contain your two screens.

Here, my monitor is 1680x1050 and my s-video screen runs at 800x600, so I need a virtual screen size of 2480x1050 (2480= 1680+800)

```
Section "Screen"
    Identifier  "Default Screen"
    Device      "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
    Monitor     "MV220D"
    DefaultDepth    24
    SubSection "Display"
        Virtual 2480 1050
        Modes       "1680x1050" "1440x900" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```

After that (and restarting X), I am able to run the following two commands to turn on the S-Video display:

```
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600 --left-of DVI-0
```

'left-of' can be replaced by 'right-of', and DVI-0 will probably need to be replaced by something else, depending on your video card. (if you run xrandr without any arguments, it will list the outputs on your card. On my laptop, I get 'LVDS')

There is one other 'gotcha', that drove me up the wall for a while. If you are using compiz, the 'Virtual Resolution' that you need to contain both screens might very well exceed the maximum size that your card can support with 3D acceleration. 

I don't remember what my card's limit is, but it is definitely less than 2480 px wide. The best solution (that I'm aware of) is to disable compiz when you want to use the S-Video. 

At one point, I wrote a script to do it (nobody laugh at my pathetic bash scripting abilities, please):

```
#!/bin/bash
if [ -n "$1" ]
then
#/usr/bin/metacity --replace &
/usr/bin/kwin --replace &
xrandr --addmode S-video 800x600;
xrandr --output S-video --mode 800x600 --left-of DVI-0;
echo "done";
else
xrandr --output S-video --off;
/usr/bin/compiz --replace &
echo "done";
fi
```

If you save it as tv-out.sh, then running 'tv-out.sh on' will turn off compiz and enable your s-video, and running 'tv-out.sh' without any arguments will turn it off. 

If you are running gnome instead of KDE, switch  

```
#/usr/bin/metacity --replace &
/usr/bin/kwin --replace &
```

to 

```
/usr/bin/metacity --replace &
#/usr/bin/kwin --replace &
```

And.. if you aren't running compiz at all, just comment out or delete all the lines starting with /usr/bin/

I ran with that script attached to some hotkeys for a while, and eventually got sick of switching between compiz/kwin (as well as general compiz instability), so stopped using compiz altogether. I still turn off the S-Video when I'm not using it, though, since I don't like windows opening up on the TV screen across the room from me. 

Hope that helps someone. Getting the video output to work on my box was one of the most annoying Linux tasks that I've faced.

---

### Post by gigahz on 2009-05-13
> **rubberglove said:**
> 
After that (and restarting X), I am able to run the following two commands to turn on the S-Video display:

```
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600 --left-of DVI-0
```


This worked so incredibly well for me! I have an ATI Technologies Inc RV280 [Radeon 9200 PRO] { 1002:5940 (rev 01)}

Funny thing right after installing Januty 3d accel worked, desktop effects and all. So I had to try to get TV-out working.
Installed 
1) atidriver with catalyst and all that. X crashed. Reverted to default driver.
2) Tried atitvout and saw the TV blink when checking for connected displays, but aside that there were no graphics
3) found this post and BANG it worked!

So I made a small script and put a button on my gnome panel to activate it. The script tries to be smart and switch back and forth between VGA only and TV only. works for me anyway. You can probably create other behaviours by editing the script.

```
#!/bin/bash
#
#
# TV/VGA-out-switcher on Radeon 9200 
# by Arno Teigseth
#
# Thanks to http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=827118
# and possibly others
#

function turnontv() {
# turn on tv
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
}

function turnofftv() {
# turn off tv
xrandr --output S-video --off
}

function turnonvga() {
# turn on vga 
xrandr --output VGA-0 --auto
}

function turnoffvga() {
# turn off vga (to scale desktop to tv, primary display tv etc)
xrandr --output VGA-0 --off
}


# The actual logic

if [ -e ~/TVOUT ]; then
	# TVOUT active, switch to VGA only
	rm ~/TVOUT
	touch ~/VGAOUT
	turnonvga
	turnofftv
	exit
fi

if [ -e ~/VGAOUT ]; then
	# VGAOUT active, switch to TV only
	rm ~/VGAOUT
	touch ~/TVOUT
	turnontv
	turnoffvga
fi

```


Please make this thread sticky for Jaunty+radeon9200, anyone!!

---

