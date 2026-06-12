---
title: "HDMI flicker on nVidia 8600M"
date: 2009-12-06
forum: Multimedia Software
---

### Post by jakslev on 2009-12-06
Dear all, 

I have set up my old HP dv9000 series laptop with nVidia Geforce 8600M GS as a media center. I am connecting the laptop to a new Sony LCD HD screen via HDMI. I tested this setup with Windows and all worked perfectly (apart from it being Windows). 

My problem is that now the screen flickers now and again. It seems it is mainly in the beginning when the system is cold. Also it doesn't seem to flicker at all when watching movies streaming...

The flickering is also visible when I plug in via VNC.

My media center is running Ubuntu 9.10 Karmic Koala 64bit. The nVidia version is 185.18.36. I had problems with the sound but managed to fix that with Alsamixer (I use Realtek ALC268 and configured sound to be "auto" configured in the config file).

Anyone else with HDMI flickering?

Thanks, 

jakslev

---

### Post by elderly_punk on 2010-01-19
Yeah I have the same sort of problem.  I'm using a ASUS M3N78-VM motherboard with integrated graphics, and the nVidia version 185 drivers.  The graphics are apparently GeForce 8200 based, and I'm using the HDMI out.    When I first installed the 64-bit 9.10 version of Ubuntu I had wicked black flashes and the screen would frequently black out.  I couldn't even get to any of the TTY terminals to try and kill X from there.  Once I changed the resolution to 1368x768 the flickering got much much better, I assume that this is because that's my TV's native resolution.   I still get black flickers from time to time however, and every once in a while the signal totally blacks out and I have to kill the power manually and reboot.  If I am downloading something while I sleep, it seems there's about a 50/50 shot of coming back in 8 hours, turning the TV on and having it still be OK.   
I've seen quite a few messages out there with people having this sort of problem, but it doesn't seem like anyone's really got much in the way of ideas.  I think it's an nVidia issue, but short of waiting for another driver update I am pretty baffled.   Have you had any luck?

Mark

---

### Post by daveshep on 2010-01-19
yeah i'm having issues too. i've got an Asus M4N78 Pro mobo (nVidia 8300 with the 185 version driver), using HDMI out (to my Samsung full HD TV) and running mythbuntu (9.10). watching live TV seems to be ok, but watching anything else the screen flickers quite badly - every few frames it flashes a frame or two with a big offset, so it almost appears as ghosting. it happens even if i exit mythtv and run VLC from the mythbuntu desktop. if i watch a video, without viewing it in full screen, i get the flicker and it affects the WHOLE desktop, not just the video "screen" inside VLC...

so I'm keen to see if you guys have any luck fixing your probs ;)

---

### Post by lewiscypher on 2010-02-16
I am running an Asus M4n78 Pro Mobo and have the same issue.  I actually ran into the same issue with Windows once I added a new HDMI receiver to my setup.  The issue appears to involve Active desktops and video.  If you disable active desktop, the flicker will stop except when you try to access something with motion.  

The only fix I have found is to set my resolution to 1080I/50 (1080, Interlaced, @ 50 Hz)  My receiver does video upscaling so my end result is still 1080P.  This is not ideal, but it works and still looks fantastic.

The only issue I am running into with Ubuntu now is to get the HDMI audio working.. already checked for volume mute.  Any suggestions would be greatly appreciated.


Hope my tidbit helps!

---

### Post by Azazelus on 2010-07-09
I am Asus M4n78 Pro owner and I am also struggling with flickering picture when playing movies over HDMI. 

My system is kubuntu 10.04 x64, nVidia 195.36.24 driver. 

When entering fullscreen mode screen goes black once in a while which ruins all the joy of watching HD movies. Same thing happens when dragging windows quickly. Sometimes there are short horizontal lines appearing when picture is distorted.

Did you get any luck finding solution to this issue? I hope there is some switch I am not aware of which could be enabled in xorg configuration solving all the problems...

---

### Post by Azazelus on 2010-07-13
Anyone?

I am wondering is this a result of system hardware inefficiency (failure?) or is it just nvidia driver related issue? 

Does anyone have this mobo working via the HDMI port properly?

---

### Post by Azazelus on 2011-05-05
I have just tried kubuntu 11.04 live cd with nouveau driver enabled by default: no flickering occurred when hooking-up monitor using HDMI port.

So this is definitely driver problem, hardware seems to be working fine.

Today I found similar problem described here:

[http://www.ubuntusolutions.org/2009/02/screen-flickering-with-nvidia-on-ubuntu.html]("http://www.ubuntusolutions.org/2009/02/screen-flickering-with-nvidia-on-ubuntu.html")

will try this solution and post results when succeeded.

---

