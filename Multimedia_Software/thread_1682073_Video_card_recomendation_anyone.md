---
title: "Video card recomendation anyone?"
date: 2011-02-05
forum: Multimedia Software
---

### Post by JoeFriday49 on 2011-02-05
I came up with an "extra" PC and thought...  Hey!  I'll tie this into my big TV and make it my media machine!...  I can stream TV straight from the net and catch up on them old shows I missed!...  Well, it worked pretty good in my head anyway...

The PC is 32 bit running 10.4 Ubuntu with its 2 ghz processor.  I have 2 gig of ram in there, but it uses onboard video and I think that's my problem.  I've installed the Nvida drivers for the card and it outputs 1440 X 1050 video to the TV, (1080P) but the video is just a tad on the jerky side.  It's motherboard has only PCI slots available so if I have to go to another card this will restrict me there.

Is there a magic trick to force the card to use more than 64 meg of shared memory or does anyone have a recommendation for a better card that is Linux frendly and doesn't cost as much as a new PC?

---

### Post by gradinaruvasile on 2011-02-05
Are you sure you have an onboard nvidia card (because the nvidia driver works only with nvidia hardware)?
What are your hardware specs?
Launch a terminal and write 

lspci

then press enter then post here the output of that command.

---

### Post by JoeFriday49 on 2011-02-05
Now this is fun...  Trying to navigate around without a real keyboard...

Here goes.  Looks like it's nvidia all throughout..

joefriday49@JoeFriday-Ubuntu:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

---

### Post by gradinaruvasile on 2011-02-06
Yes, it is nvidia. The problem is that it is old. I dont know if it can handle 1080p playback smoothly.
Try vlc and smplayer to see if any of those has some improvements in playback.

---

### Post by cascade9 on 2011-02-06
> **JoeFriday49 said:**
>  I've installed the Nvida drivers for the card and it outputs 1440 X 1050 video to the TV, (1080P) but the video is just a tad on the jerky side.  It's motherboard has only PCI slots available so if I have to go to another card this will restrict me there.


1080p is 1920 x 1080. 

[http://en.wikipedia.org/wiki/1080p](http://en.wikipedia.org/wiki/1080p)

The old GF4MX will have virtually no hardware acceleration for video, so all the work will be done by the CPU. Athlon XPs havent quite got the power to decode 1080p smoothly in my expereince. Mind you, I''ve never tried with a 2GHz model (XP 2600+, XP 2900+, or XP-M 2600+)

Downscalling the video from 1080p to....er......whatever resolution you are running will just be using more power as well (there is no 1440 x 1050 AFAIK, you probably mean 1440 x 900 or 1680 x 1050). If you can find a 720p (1280 x 720) steam it might work. 

Steaming from the net could also be sucking CPU power, depending on what sort of stream you are getting.

---

### Post by gradinaruvasile on 2011-02-06
Forget about streaming HD content from the net if it is via flash on that computer.

There is one card that will fit in your computer - the nvidia 8400GS has a PCI version, but it is hard to find and i dont know how well it works with HD.
Best is to consider upgrading.

---

### Post by JoeFriday49 on 2011-02-06
> **gradinaruvasile said:**
> Yes, it is nvidia. The problem is that it is old. I dont know if it can handle 1080p playback smoothly.
Try vlc and smplayer to see if any of those has some improvements in playback.

I don't think it will either, that's why I was lookin' for a drop in replacement that is Linux friendly, fast enough for video and will run on the PCI buss...  I have MPlayer on there with a different front end, but I'm not familiar with Vic...  I guess it's in the multimedia repository (I don't have that installed on this laptop)

---

### Post by cascade9 on 2011-02-06
VLC, not Vic. Its in the standard repos- 

[http://packages.ubuntu.com/lucid/vlc](http://packages.ubuntu.com/lucid/vlc)

I dont think it will help copmpared to mplayer, but its worth a try.

---

### Post by gradinaruvasile on 2011-02-06
If you used mplayer (or smplayer/gmplayer), vlc will not help much (woth a try though, you never know).

Do not use the default "Movie player"  in this case (that is totem) because that has the worse performance.

---

### Post by JoeFriday49 on 2011-02-06
> **cascade9 said:**
> 1080p is 1920 x 1080. 

[http://en.wikipedia.org/wiki/1080p](http://en.wikipedia.org/wiki/1080p)

never tried with a 2GHz model 


This one is a 2800 XP and really fast just doin' the regular stuff I use a pc for.  But this task seems to be a bit much...

---

### Post by JoeFriday49 on 2011-02-06
> **gradinaruvasile said:**
> Forget about streaming HD content from the net if it is via flash on that computer.

There is one card that will fit in your computer - the nvidia 8400GS has a PCI version, but it is hard to find and i dont know how well it works with HD.
Best is to consider upgrading.

Yep, like you say, the PCI version of that card is hard to find, but thanks to Google and PayPal I got a 512mb one on the way for 14.99...  

I'll let you know how it turns out...

---

### Post by JoeFriday49 on 2011-02-06
> **cascade9 said:**
> VLC, not Vic. Its in the standard repos- 

[http://packages.ubuntu.com/lucid/vlc](http://packages.ubuntu.com/lucid/vlc)

I dont think it will help copmpared to mplayer, but its worth a try.

So that's why I couldn't find a VIC player...  LOL

Sure won't cost much to try...  I'll give it a shot...  Thanks

---

### Post by cascade9 on 2011-02-08
> **JoeFriday49 said:**
> This one is a 2800 XP and really fast just doin' the regular stuff I use a pc for.  But this task seems to be a bit much...

2800+ runs a touch faster than 2GHz (2241MHz, 2133MHz or 2083MHz depending on the model), not that it makes a huge difference. 

With a 8400GS you might be able to play 1080p smoothy with VDPAU (nvidia hardware video decdoing). Though if its a flash stream you still wont be able to.

---

### Post by JoeFriday49 on 2011-03-25
Well after lots of experimenting I've decided this setup isn't good enough...  The Nvivia card did help, and made the system usable without too many computer generated glitches, about on par with a WII game system...  Guess I was expecting too much...

---

