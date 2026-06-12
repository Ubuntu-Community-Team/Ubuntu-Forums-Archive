---
title: "Video output to TV"
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by cortexed on 2008-01-30
Hello
I am fairly new to Ubuntu and Linux.  I am trying to get my laptop to display on my tv.  I have a ATI Mobility Radeon 7500.  I have an S-Video output and a VGA output.  I have tried straight S-Video to the TV and I have also tried using a converter from VGA to S-Video and RCA, an nothing happens (no output or anything)?  Any ideas anyone?
Thanks

---

### Post by steefjeqv on 2008-01-31
[http://www.joshgerdes.com/blog/2007/10/29/s-video-tv-out-with-ubuntu-710-on-dell-xps-m140-laptop/]("http://www.joshgerdes.com/blog/2007/10/29/s-video-tv-out-with-ubuntu-710-on-dell-xps-m140-laptop/")

Hi,

Maybe this link will help you.

Greetings,
Steven

---

### Post by cortexed on 2008-02-01
Thank you I will give that a try.

---

### Post by cortexed on 2008-02-01
That didn't work...
It tried to put something on on the TV but is was garbled.  Like it was scrambled.  Anything else I can try?
Thanks

---

### Post by steefjeqv on 2008-02-02
Hi,

You can try the following (perhaps you already did).

Open up your terminal and type :

sudo xrandr –addmode S-video 800×600

sudo xrandr –output S-video –mode 800×600

Connect the s-video cable to your tv before entering these commands.

Greetings,
Steven

---

### Post by hardyn on 2008-02-02
as taken from another post... make sure you PAL vs. NTSC are correct

---

### Post by cortexed on 2008-02-02
I am pretty sure that I already tried those commands.  I did however try a lot of xrandr commands so I will try those commands you just typed out for me just in case.  How do I check the PAL and NTSC settings?
Thank you both for you replies.

---

### Post by cortexed on 2008-02-03
Yes I did try those commands but all I get is the help options.

=================================================
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --off
      --crtc <crtc>
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
==================================================
What am I doing wrong or what else can I do?
Thanks

---

### Post by ullix on 2008-02-12
Please note that the output port names are different for Intel and AMD; adjust your commands accordingly:

 Output port names

Intel driver

    * VGA - Analog VGA output
    * LVDS - Laptop panel
    * TV - Integrated TV output
    * TMDS-1 - First DVI SDVO output
    * TMDS-2 - Second DVI SDVO output 

The SDVO and DVO TV outputs are not supported by the driver at this time.

radeon driver

    * VGA-0 - Analog VGA output
    * LVDS - Laptop panel
    * S-video - Integrated TV output
    * DVI-0 - DVI output 
(taken from here: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2"))

---

### Post by steefjeqv on 2008-02-12
> **steefjeqv said:**
> Hi,

You can try the following (perhaps you already did).

Open up your terminal and type :

sudo xrandr –addmode S-video 800×600

sudo xrandr –output S-video –mode 800×600

Connect the s-video cable to your tv before entering these commands.

Greetings,
Steven

Hi,

Try changing the above mentioned command lines to :

sudo xrandr --addmode S-video 800×600

sudo xrandr --output S-video --mode 800×600

Greetings,
Steven

---

### Post by cortexed on 2008-02-17
Thanks for your reply.  However still will not work

---

