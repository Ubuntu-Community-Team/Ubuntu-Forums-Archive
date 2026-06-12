---
title: "VGA 2 S-Video Adapter"
date: 2011-06-27
forum: Multimedia Software
---

### Post by ModernDayCaesar on 2011-06-27
I have a standard definition television and I'm trying to connect my PC to my TV. I only have VGA, HDMI and some other weird monitor output on my computer. I recently purchased a VGA to S-Video Composite cable and hooked it up correctly from my PC to my TV.

All I'm experiencing is a black screen. When I disconnect and connect the VGA cable to and from the computer, I get a little flickering on the TV but never a picture. 

I was under the assumption that this was just a plug and play operation. Am I missing something?

Thanks

---

### Post by BicyclerBoy on 2011-06-27
It will not be plugNplay.
If you were using a video card with s-video or component output then it would be a lot easier..

The adapter only converts the RGB HV sync analogue video (VGA) to S-video format.
The adapter does not convert resolution or refresh rates (or interlace).
The adapter does not have EDID & is likely detected as a VGA monitor, default 1024x768.

Your adapter & TV will have limits on what they will accept.
What is the TV model ?
What is the video card (figure out the weird conn) ?

Your TV should accept 480i60 (NTSC) or 576i50 (PAL TV).
You can set the video modes to be a certain TV format for the VGA output but I only having any idea about nVidia.

Your TV may accept progressive scan
Try
480p or 576p

S-Video can not support higher than 576p (AFAIK).

---

### Post by ModernDayCaesar on 2011-06-27
Tv is an old Toshiba 36" incher I believe. 

This is my string of ports on the side of my PC.
[IMG]http://i52.tinypic.com/14ljxi8.jpg[/IMG]

I'm 90% sure it's an ATI Radeon card. From what I remember coming from Win7. I'm not even sure how to confirm it in the linux machine. Like I said I'm new and still getting used to this OS.

I've tried changing the res on my rig to 480 with no success.

---

### Post by BicyclerBoy on 2011-06-28
That weird connector must be some kind of digital video connector. Probably the expense type..

There must be some way of setting the video modes (on  the VGA port) to be a TV standard video mode. This will probably enable interlaced output (likely to be necessary for an old TV).
I have no experience of any AMD/ATI cards.

xrandr --props
xrandr -q
 xrandr --addmode VGA-0 640x480
xrandr --output VGA-0 --mode 640x480
xrandr --output VGA-0 --set "tv standard" ntsc   or diff syntax (older/newer)
xrandr --output VGA-0 --set TV_FORMAT NTSC

Problem here is we have not specified interlace.
It may be you must create a modeline to get an interlaced mode.
It may transpire that you can not make this card output low resolution interlaced on VGA.

---

### Post by ModernDayCaesar on 2011-06-28
So maybe I'd be better off with a converter box?

After further inspection of my "brand new" VGA to S-Video converter.. I've noticed that one of the pins on the male VGA plug is broken.

I've already contacted the seller and a new one will be in the mail tomorrow. Hopefully this is why I couldn't get the picture to show on my TV. Although I won't be able to do anymore troubleshooting until the replacement part comes in.

---

### Post by BicyclerBoy on 2011-06-28
Well spotted..could have saved yourself endless trouble.
Do you know which pin ?
There (could be) are tiny numbers inside the D shell on the plastic body.

Your TV doesn't have SCART or component video inputs ?
Because you could get a different adapter..
SCART can support RGB+Sync & your TV might ?

---

### Post by ModernDayCaesar on 2011-06-28
Unfortunately my TV is an older model.. Only has 2 sets of Composite inputs and 1 S-Video input.

My ultimate agenda is to get MythTV activated on this TV. I have 2 other HDTV's with DVR capabilities but I did not want to get an extra DVR box for this standard definition TV. Therefor I am looking into using my laptop for this purpose.

I do have a Popcorn Hour which I've been reading that people have been dabbling into setting it for use as a front-end for MythTV. But it seems like a lot of work and stability is not guaranteed. 

Here is the Male VGA plug I was talking about.
[IMG]http://i51.tinypic.com/157de9.jpg[/IMG]
The line where the pin is broke is labeled number 5

---

### Post by BicyclerBoy on 2011-06-28
That's pin 4 ..reserved fn..could have been snapped off intentionally..

The MythTV concept is one master backend & many frontends.
All the tuners/set-top-box capture live at the server.

A good concept to solve frontend HTPCs is to use DLNA & ethernet connectivity.
The latest generation TVs are finally able to playback usable video formats.
So you don't need a frontend just a backend DLNA server (MythTV etc) that has tuners etc.
Use some cheap device with browser to access MythWeb for scheduling etc.

This does not result in a good audio solution unless your TV outputs S/PDIF or better..
I don't know how MythTV DLNA works with LiveTV..but I never use LiveTV.

---

### Post by ModernDayCaesar on 2011-07-02
I received the new VGA 2 S-Video wires with all pins. Still made no difference. I suppose my video card doesn't support TV Out. So I purchased a VGA 2 S-Video converter box and it worked pretty much plug and play.

---

