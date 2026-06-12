---
title: "Video playback choppy on Totem and VLC."
date: 2018-09-17
forum: Multimedia Software
---

### Post by rocco.martinello on 2018-09-17
Hito all!


I am experiencing choppy video when using either Totem and VLC on Ubuntu(watching video from my hard drive).
I tried to install Nvidia drivers for my graphics card (GeForce GT 740), but no luck.
I experience the problem only with Totem and VLC (with video on my hard drive) and not with Chrome watching video online (not downloaded on my hard drive).
Watching.mp4 videos the problem is only video and not audio: every some seconds the video freezes for less than a second.
Watching .mts videos (transport stream MPEG-2 (video/mp2t)) with VLC freezes happens for less than a second randomly (whitout audio problems) and pausing videos sometimes results in a still with horizontal lines.
Furthermore opening .mts videos with VLC cause an audio skip at the very beginning of the video.
How can I get rid of these problems?
Thank you in advance for your answers!!!

P.S.: I installed "Ubuntu restricted extras".

---

### Post by Autodave on 2018-09-17
I have the same video card (4 gig) and have no problems at all.  I didn't have any problems with that card on my previous machine either.  Did you actually install the Nvidia driver for it? If so, what one and where did you get it from.  I am running the 390.48 driver.  If you have NOT installed a driver, go to setting -> Additional drivers and get it.

Can you give us the specs on your machine? Also, what version of Linux are you running?  Are you sure that your internet speed is OK?  Are you hooked up wirelessly or by wire?

---

### Post by rocco.martinello on 2018-09-17
Hi Autodave,

thank you for your answer!!!
I installed Nvidia drivers from terminal (version 390.87) and I am rumming Ubuntu 18.04.1 LTS.
My Internet speed in fine and I'm hooked un via ethernet, BUT in you read carefully my message you will see that the problem happens only with videos on my hard drive and therefore the problem cannot be caused by Internet speed.
My specs:
[COLOR=#000000][FONT=Verdana]Processor: AMD FX-6300 six-core processor, processor speed 3,5 GHz with TurboCore up to 4,1 Ghz - Vishera 32nm Technology[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]RAM: 8,00GB Dual-Channel DDR3 @ 802MHz (11-11-11-28) (two sticks of 4 GB each)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Motherboard: ASUSTeK COMPUTER INC. M5A97 R2.0 (Socket 942)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Graphic card: MSI NVIDIA GeForce GT 740 - 2GB - GDDR5 &#8211; processor speed 1006 GHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Hard drive: Seagate ST2000DM001-1ER164 &#8211; 2000 GB &#8211; SATA-III &#8211; 7200 RPM[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Optical drive: LG DVD Writer HL-DT-ST DVDRAM GH24NSB0[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I have no audio card, I use jack on my motherboard ( Speccy says: NVIDIA High Definition Audio)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Operating system: Windows 10 Home Edition (64 bit)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]PSU: Antec VPF550 - 550W - 80 PLUS® BRONZE certified with Over Current Protection (OCP), Over Voltage Protection (OVP), Under Voltage Protection (UVP), Short Circuit Protection (SCP), Over Power Protection (OPP), No Load Operation (NLO), Brown-Out Protection (BOP), Over Temperature Protection (OTP) Surge & Inrush Protecion (SIP), Heavy-duty Caps - High-performance capacitors ensure tightest DC stability and regulation. - Active PFC.[/FONT][/COLOR]

---

### Post by Autodave on 2018-09-17
Do you have the extra power cable for the graphics card connected?

The specs on your machine are way better than my last machine that had that card in it.  You might try installing *psensor *and activating everything to see what might be maxing out.  You can also look inside the Nvidia settings and make sure that you have *Prefer maximum performance *ticked.

---

### Post by rocco.martinello on 2018-09-18
[IMG]http://www.roccomartinello.it/psensorscreenshot.png[/IMG]
Hi Autodave!
Thank you very much for your answer!
Here there is psensor screenshot of my system.
"temp1" is referred to GPU, while "temp2" is referred to CPU.
"cpu_fan" value is 0, but I think this is a software error.
I think my graphics card doesn't have [COLOR=#000000]extra power cable.
I selected "[/COLOR]*Prefer maximum performance*[COLOR=#000000]", but no luck.
I don't think this issue is due to an hardware problem because watching videos on Chrome (videos not downloaded on my hard drive) there are no problems.
How can I get rid of this problem?
Thank you in advance for your answers![/COLOR]

---

### Post by Autodave on 2018-09-18
Was that snapshot taken while a movie was playing?  If not, get a movie plating and while it is lagging, take the sanpshot.

---

### Post by rocco.martinello on 2018-09-18
[IMG]http://www.roccomartinello.it/psensorscreenshotwhilevideoischoppy.png[/IMG]
Hi Autodave and thank you for your help!
This is the screenshot taken while playing a choppy video as you requested!

---

### Post by Autodave on 2018-09-18
Interesting.  Nothing is maxed out or even close.  HD failing?  Could be.  When you get a chance, copy one of your movies to a USB stick and try playing it from the stick and see what happens.

---

### Post by rocco.martinello on 2018-09-19
Hi Autodave and thank you very much for your help!!!
I tried to copy a video on a USB stick and the problem is still present even playing the video from USB!
What can I do?

---

### Post by rocco.martinello on 2018-09-19
[IMG]http://www.roccomartinello.it/smartmontoolsscreenshot1.png[/IMG]

[IMG]http://www.roccomartinello.it/smartmontoolsscreenshot2.png[/IMG]

These are smartmontools' screenshots.

---

### Post by Autodave on 2018-09-20
I am running out of ideas here.  Have you gone into the Nvidia settings and then into Open GL Settings and tried moving the slider all the way to the Performance end?  Also, while you are in there, go into Power Mizer and set more max performance.

These movies aren't 4K resolution, are they?

---

