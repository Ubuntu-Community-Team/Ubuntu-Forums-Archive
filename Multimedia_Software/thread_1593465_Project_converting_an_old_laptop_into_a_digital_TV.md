---
title: "Project: converting an old laptop into a digital TV recorder / decoder"
date: 2010-10-11
forum: Multimedia Software
---

### Post by Roger Norton on 2010-10-11
I thought I would post my experiences of this project for beginners like myself who might be interested in a similar project (in ubuntu 10.04).

Start point:

laptop: Dell Inspiron 4150
processor: Pentium 4m, 1.7GHz
RAM: 256Mb
video controller: ATI mobility Radeon 7500C
relevant ports: USB 1.0, PCMCIA, S-video, audio out (headphone)
initial OS: Windows XP home with service package 3

tv format: PAL
tv input: SCART socket

cable and adapter: 4-pin S-video cable, audio cable (headphone plug to 2 plugs), S-video and 2-plug audio to SCART adapter


Hardware purchased: DVB-T USB stick: Hauppage NOVA-T WinTV stick (inexpensive plug-in digital tv receiver and decoder suitable for almost all the laptop's specs), PCMCIA to USB 2.0 card (USB 2.0 required to run Hauppage NOVA-T WinTV stick)


Ubuntu installation:

ubuntu version: 10.04 (download from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) and follow instructions on that page)
software: MeTV and Media Player (from ubuntu software downloads in the applications menu).  You can remove all non-essential software (such as Open Office).
drivers: proprietary driver for DVB-T stick (click on System, then Administration, then Hardware Drivers) 

Adaptations:

the display was initially black and white.  This was solved by: 
1. connecting the holes for pins 3 and 4 of the S-video socket (see [http://pinouts.ru/VideoCables/svhs_scart_pinout.shtml](http://pinouts.ru/VideoCables/svhs_scart_pinout.shtml) for pin numbers) with a small wire (an alternative is to connect pins 15 and 20 of the SCART adapter, as described at [http://camp0s.altervista.org/sVideo/sVideo.htm);](http://camp0s.altervista.org/sVideo/sVideo.htm);) and
2. using the xrandr command as follows:
  - open the terminal (in the applications menu, accessories option) and enter: gksudo gedit
  - cut the boxed section under the "Now automate it on login" heading in [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Using_xrandr_to_do_useful_things](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Using_xrandr_to_do_useful_things) , and paste it into the gedit window
  - add the line: xrandr --output S-video --set "tv standard" pal 
just above the line: xrandr |grep $EXTERNAL_OUTPUT | grep " connected "
  - change the external output from "VGA" to "S-VIDEO" in the EXTERNAL_OUTPUT="VGA" line
  - save as: 45custom_xrandr-settings in the /etc/X11/Xsession.d/ folder (you can do this by clicking on "save as" in the file menu, then "file system", then /etc and so on, and then typing in the file name and saving).
This will cause the computer to output in colour to the tv each time it is switched on (providing the cables and adapter are plugged in, and the TV is on and in AV mode).  The picture is shifted a little down and to the right on the TV though, and is in 16:9 format (and cartoons appear in a box in the middle of the screen).  I had to fiddle with the TV's colour, brightness and sharpness settings as the picture was over-coloured.

to play dvds, Media Player requires a plug-in which can be downloaded from: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats).

to play mpeg files (such as those created by recording programs with MeTV), Media Player requires a Gstreamer plug-in (from ubuntu software downloads in the applications menu).

to view programme information in MeTV: this was slow to load for me - just keep clicking on the channel names, and it comes eventually (in batches of channels, so you have to click on several different channels to get it all loaded - one from each of the frequency bands MeTV used while scanning, I think).

MeTV works quicker when there are fewer hours of programme information available (can be changed in the view menu, with preferences).


Things that didn't work:

- Digital TV in Windows XP (with SP3): the Hauppage stick came with proprietary WinTV software, but windows was too slow, even when WinTV priority was set to real time.
- Mythbuntu, MythTV: difficult to set up for beginners, and over-specified for my purposes (watching and recording digital TV from an aerial, and playing DVDs and recorded TV).  Mythbuntu froze my keyboard once I'd downloaded the latest updates.
- Kubuntu, KDE: I tried this as it comes with a DVB-tv programme which also plays DVDs, called Klear.  Found Kubuntu slow and unfriendly (no rubbish bin, for a start!), ditto KDE (the Kubuntu equivalent of gnome, which is ubuntu's desktop programme) when loaded in ubuntu (used the ubuntu desktop, so did have a rubbish bin)
- changing the xorg.conf file: makes no difference
- installing proprietary drivers for the ATI video controller: the open source driver that comes with ubuntu is as good if not better.

---

### Post by Roger Norton on 2013-03-20
update to the above:

the [http://www.thinkwiki.org/wiki/Xorg_R..._useful_things]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Using_xrandr_to_do_useful_things") link no longer gives the 45custom_xrandr-settings file in a readily cut-and-pasteable form, so here's the 45custom_xrandr-settings file text I use (a modification of [http://epiguru.com/2012/06/how-to-automate-xrandr-configuration-on-login/):](http://epiguru.com/2012/06/how-to-automate-xrandr-configuration-on-login/):)

# If an external monitor is connected, place it with xrandr
 
# External output may be "S-VIDEO" or "VGA" or "VGA1" or "VGA-0" or "DVI-0" or "TMDS-1"
EXTERNAL_OUTPUT="S-VIDEO"
INTERNAL_OUTPUT="LVDS1"
# EXTERNAL_LOCATION may be one of: left, right, above, or below
EXTERNAL_LOCATION="left"
 
case "$EXTERNAL_LOCATION" in
       left|LEFT)
               EXTERNAL_LOCATION="--left-of $INTERNAL_OUTPUT"
               ;;
       right|RIGHT)
               EXTERNAL_LOCATION="--right-of $INTERNAL_OUTPUT"
               ;;
       top|TOP|above|ABOVE)
               EXTERNAL_LOCATION="--above $INTERNAL_OUTPUT"
               ;;
       bottom|BOTTOM|below|BELOW)
               EXTERNAL_LOCATION="--below $INTERNAL_OUTPUT"
               ;;
       *)
               EXTERNAL_LOCATION="--left-of $INTERNAL_OUTPUT"
               ;;
esac
 
xrandr --output S-video --set "tv standard" pal 
xrandr |grep $EXTERNAL_OUTPUT | grep " connected "
if [ $? -eq 0 ]; then
    xrandr --output $INTERNAL_OUTPUT --auto --output $EXTERNAL_OUTPUT --auto $EXTERNAL_LOCATION
    # Alternative command in case of trouble:
    # (sleep 2; xrandr --output $INTERNAL_OUTPUT --auto --output $EXTERNAL_OUTPUT --auto $EXTERNAL_LOCATION) &
else
    xrandr --output $INTERNAL_OUTPUT --auto --output $EXTERNAL_OUTPUT --off
fi

---

