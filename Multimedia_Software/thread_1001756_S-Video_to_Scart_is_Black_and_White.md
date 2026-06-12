---
title: "S-Video to Scart is Black and White?"
date: 2008-12-04
forum: Multimedia Software
---

### Post by the lemming on 2008-12-04
Hello

I am trying to stream my movies from my Desktop computer, which is in one room, to my Telly.

At the moment I have had the bright idea of using my laptop as the media streamer.  The laptop, which is Ubuntu, can access my desktop , which is Vista and can play all my media files.

Seeing as my laptop has a s-video output I bought an s-video and scart adapter to plug into the telly.

So far I have managed to get an image of my laptop onto the TV but at the moment it is in black and white.  Also I have horizontal lines going accross the screen of the telly.

Does anybody know how to:

Get the images on my TV to become full colour?

Improve the resolution of the image on my TV to try and remove the horizontal lines that break up the displayed images?

Even though S-Video does not carry a sound signal when I connect the laptop to my Telly I can hear a very annoying high pitched squealing noise coming from the TV's speakers.

---

### Post by EasyRiderOnTheStorm on 2008-12-05
The black-and-white only picture might be caused by a mismatch of the TV-standards you are using, on more than one level. 

- First, it might be the S-video signal you use. The main point of S-video as opposed to Composite is that it carries luminance and chrominance (colour) information on two separate leads in the cable. 

Therefore, if either your laptop's TV-out is set to anything other than "S-video" output, or your cable/SCART adapter is missing the extra lead, or your TV just **doesn't do** S-video input (you wouldn't be the first...), black-and-white is what you would get.

If your TV isn't S-video capable, you could switch the TV-out signal to "Composite", which should get you colour or no picture at all. That probably involves locating the laptop's adapter cable for Composite-out (it had to have one, S-video socket to RCA socket), and a different extension cable, for RCA-Composite to SCART. 

- Second, unrelated to the first issue, there might be a mismatch in TV-norm between your TV-out and TV: I assume you have a PAL TV - if your laptop is set to output NTSC or SECAM or some outlandish version of PAL, you're also back to black-and-white. 

If your TV supports multiple systems, try browsing through them, and if you don't get colour back this way, this is not the cause. Either way, try to find the TV-norm setting on your laptop, and try setting it to PAL B/G or PAL D/K if it's not already.

Unfortunately I have no idea regarding the lines or the noise, unless it's related to one of the issues above or to the quality of your extension cable (I had a 10m store-bought cable once that totally wrecked the image - it was not shielded, would you believe it).

Good luck!

---

### Post by the lemming on 2008-12-05
Thany you for taking the time out to write that very informative reply.

And when I re-install Ubuntu, because I turned off the laptop monitor by mistake trying to deal with this, I will see if I can use your advice to good effect.

Cheers

---

### Post by iosifidis on 2009-03-25
Hello,

Don't know if you made it. I face the same problem as you (black and white) and I also cannot make the standard to PAL from NTSC (I guess).

Well, I solve the colour problem. A guy from the Greek forum did it. Don't see the language. Check the picture only at
[How to see color connecting S-video to your tv]("http://forum.ubuntu-gr.org/viewtopic.php?f=9&t=2402")

Hope it helps.

---

### Post by Sylslay on 2009-03-25
My s-video dosn,t work propley. Never checked at Ubutu, But form Windowz Xp, always had blck and white pcture, on my telly.
No matter with driver I usded. Maby laptop Siemens-Fujitsu wasn;t best choice for watching movies on TV.
Desktop graphic card-dual head manage its fine (2years older than my laptop.THX. Too many standards in Eu, PAl B/G , Pal/I NTSC, Secam,
BTW try command line:  gnome-display-properties  and have fun, if You use gnome.

---

### Post by Sylslay on 2009-03-25
That picture was awsome.................

---

### Post by Roger Norton on 2010-10-01
Similar alternatives to this solution include:

- connecting the sockets for pins 3 and 4 on the S-video socket with a small wire (see [http://pinouts.ru/VideoCables/svhs_scart_pinout.shtml](http://pinouts.ru/VideoCables/svhs_scart_pinout.shtml) for pin numbers)

- connect scart pin 15 to scart pin 20 (see [http://pinouts.ru/VideoCables/svhs_scart_pinout.shtml](http://pinouts.ru/VideoCables/svhs_scart_pinout.shtml) for pin numbers)

- use a s-video cable where the pin 4s at each end of the cable are not connected (use a multimeter to check resistance)

I found the first 2 solutions online, with pictures, but have lost the links.

These solutions work for me in Windows XP, but not ubuntu 10.04.

Specs as follows:

Dell Inspiron 4150 laptop
ATI Mobility radeon 7500c (M7) video adapter
S-video cable and scart adapter
PAL-I tv.

Regards,

Roger

> **iosifidis said:**
> Hello,

Don't know if you made it. I face the same problem as you (black and white) and I also cannot make the standard to PAL from NTSC (I guess).

Well, I solve the colour problem. A guy from the Greek forum did it. Don't see the language. Check the picture only at
[How to see color connecting S-video to your tv]("http://forum.ubuntu-gr.org/viewtopic.php?f=9&t=2402")

Hope it helps.

---

