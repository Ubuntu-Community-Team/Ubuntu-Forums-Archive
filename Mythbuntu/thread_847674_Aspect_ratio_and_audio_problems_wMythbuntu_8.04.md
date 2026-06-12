---
title: "Aspect ratio and audio problems w/Mythbuntu 8.04"
date: 2008-07-02
forum: Mythbuntu
---

### Post by the kaz on 2008-07-02
Hello all, 
I'm having quite a few problems with a Mythbuntu 8.04 installation of which I just can't get rid no matter what I try. I'm looking for pointers what to try next, where to look or how to change the configuration so that I at least get additional debug output. So far I have no idea whatsoever what causes the problems.

The system is a AMD A64-X2 5200+ running on a ASUS M2N-VM HDMI microATX board. The board features a nForce 630a chipset with integrated graphics and a Realtek ALC883 audio chip, among other things.

I installed the system connected via DVI to a 1280x1024 4:3 ratio TFT and using logitec boxes connected to analog line out which worked flawlessly. After everything was set up, the computer moved to the living room where there're two displays
[LIST=1]
[*]a 800x600 4:3 beamer
[*]plus a 1360x768 16:9 Flatpanel TV
[/LIST]
Both are connected via VGA as they don't have any usable DVI or HDMI inputs. The audio is connected to a Dolby/DTS receiver via optical cable. 

Now, I have two main problems: 
[LIST=1]
[*]The system defaults to the beamer resolution, which is fine - but somehow the Internal Player of MythTV, as well as xine and VLC, all seem to think this is a 800x600 16:9 display when playing DVDs. This results in all 4:3 material being shown with black bars left and right (und thus squished together), while widescreen material is displayed without any bars (which again results in all people looking like the coneheads). The options in the context menu of MythTV don't help, regardless of what I select there, the aspect ratio of DVDs is always wrong.
[*]The mplayer shows all DVD material correctly, however I can't hear anything. In fact, I don't hear a thing via digital out unless I play the material via the MythTV interface. Everything I play via mythTV sounds fine, everything I play by manually starting mplayer, xine or vlc remains silent.
[/LIST]

Both errors combines mean I can't play DVDs at all, as I only have the option of choosing between wrong aspect ratio (MythTV internal, xine, vlc) and no sound (xine, vlc, mplayer), both of which is unacceptable.

Can anyone shed any light onto the matter? Any help will be appreciated, as I'm at a loss where to look at all. I have no idea where to find/set aspect ratio settings for x.org or something, and I don't know what mplayer, vlc et al. do wrong so that no sound is being played. Where can I find out what is going wrong?

Thanks in advance for any help you can provide. 

Greetings,
          the kaz.

---

### Post by bedge on 2008-08-24
For the mplayer audio issue, it may be that it's assuming /dev/dsp whereas you system is presenting /dev/dsp1 (mine was).
I ran xine from the cmdline to what it had picked, then made a symlink to /dev/dsp and viola` that was it.

---

