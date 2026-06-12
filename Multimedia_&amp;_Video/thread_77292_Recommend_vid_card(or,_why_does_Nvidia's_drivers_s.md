---
title: "Recommend vid card?(or, why does Nvidia's drivers suck.)"
date: 2005-10-16
forum: Multimedia &amp; Video
---

### Post by Zentropic on 2005-10-16
Greetings to all,

First post, although I've been using Ubuntu since last May ( moved from gentoo. was fun, but too much care and feeding ).

I recently switched to a new display a few weeks back ( went from a 24 inch Sony GDM-W900 CRT I had for 5 years to a 24 inch Dell 2405FPW LCD ) and it's been a rather disappointing problem with getting a decent resolution. First, I'll describe my specific situaiton and experience and if you're still with me, I'll ask your experience and suggestions to augment my current idea about what to do.

Although hardware support and auto-configuration has made astounding gains in Linux, some things continue to be at best, a minor hassle, and at worst, a deal breaker. Getting a proper working display certainly ranks up there. Ok...

I always managed to get my CRT working at 1900x1200( after the requisite modeline tweak/restart X/tweak/restart X games ) and that was, of course, a good thing. However, the sheer bulk of that beast was always a problem ( took three square feet of space and weighed 93 pounds, or 42.27Kg for the rest of the free world ), and I wanted to replace it with an LCD. I was wary due to all the bullshit with DVI and TDMS, etc. and held off. That is, until Dell broke the $1000 barrier with a quality display. I could not resist any longer :D 

Now, the problems began.... I had a Ti4600 for a couple years and one day the fan  crapped out and something popped on the card. I decided to go for a cheaper card with no fan because I don't game much anymore and got a FX5200 /w 128MB. 

Running Hoary I was able( after a HUGE amount of modeline roulette ) to get 1600x1200 which is not the native 1900x1200 the LCD should be. I had read that the Nvidia drivers have problems getting high resolution and this would be fixed with the next series( which apparently isn't coming anytime soon.... *sigh* ), I had also read the FX5---- series itself could reach high resolution( it could for my CRT/analog.. maybe DVI? ). Lots of vague and not useful information.

Too make things worse, I read reports of people claiming to have achieved 1900x1200 with this LCD on a variety of cards, drivers, and linux flavors. Lucky them.

Now, I have done a fresh install/upgrade to Breezy and hoped that *just maybe* I might see an improvement in getting the optimal resolution. At worst, I could live with 1600x1200 for a while longer until the fabled next series of drivers arrives from nvidia. Well, it has degraded! Yes, I can now only get 1280x1024 which on a 24 inch display looks terrible. My old xorg.conf does not work, I tried every modeline and setting I could find via google and no success. Further suckage, I thought I'd switch from DVI to the analog VGA in the hopes that at least there I'd achieve the desired resolution. It does not work at all. Nothing. Not even 800x600. 

So, this brings me to my first question( not to YOU, just musing really.. ). Why do Nvidia's linux drivers suck so bad? This is really unacceptable, but what can you do? Nvidia is becoming the Microsoft of video cards, and is pretty much catering to their role model as does every other hardware/software maker.

My next question: Is there anybody out there with a Dell 2405FPW, running Ubuntu( or any linux distro ), with a video card/driver that works? At 1900x1200? If so, please tell me!

I've been using Linux for two years as my main desktop system(I've got two others running as servers with Fedora, for my job...) and would like to continue doing so.  This is a serious deal breaker for me and if I must, I'll bite the bullet and install XP. I vastly prefer Ubuntu to XP ( and other distros ) but I can't work with a resolution that is unusable.

Thanks for reading this far, and I appreciate any input, however small.

---

### Post by Zentropic on 2005-10-16
Well, I guess salvation is possibly at hand. The 1.0-8XXX drivers are supposed to be released by the end of the month. Here's hoping that a) they are released very soon, b) they fix the damn pixel clock bug that is my problem, and c) it shows up in synaptic soon after.

*crosses fingers*

---

### Post by Somatik on 2005-10-18
I also have a nvidia gfx card (fx5200) and can't get my 1600*1200 tft to work in the right resolution using DVI. After a reboot and with a vga cable no problems. Rebooting and switching back to dvi gives me crappy 1024*786.

I'm using the default resolution tool in ubuntu, changing anything in the xorg.conf does not seem to get me more choice.

In windows there is no problem at all...

I also have a dell 24" but i can't get it to work properly in ubuntu, not even with vga. That's about the only thing keeping me from using linux in that box (geforce fx 5900xt)

Hoping for a fix soon, i'd realy like to switch!

---

### Post by Somatik on 2005-10-25
seems the FX5200 has a max resolution of 1600*1200 for dvi

> Able to drive the industry's largest and highest resolution flat-panel displays with up to 1600x1200 resolution. 

> Support for dual-link DVI for compatibility with next-generation flat panel displays with resolutions greater than 1600x1200 without the need for reduced blanking

> The common denominator is that even the Dell 2405FPW, with its 1920 x 1200 native resolution, only requires a single link DVI connector to handle the bandwidth required by its high resolution. However, once you start getting much higher than 1920 x 1200, you start running into the bandwidth limitations of a single link DVI connection. 

hmm, think it depends on the manufacturer, my fx5200 won't go higher than 1600*1200 (dvi), even in windows :-s

---

### Post by Watter on 2005-10-26
I'm in the same boat: FX5200 trying to run a 2405fpw. I had a little more luck than you. I used the exact settings described [here](http://www.ubuntuforums.org/showthread.php?t=73032) and that somehow set my resolution to 1400x1050. Not what I was looking for, but better than 1024x768. I'm off to the store in about an hour to pick up a different video card. We'll see what happens. I'll probably stick with Nvidia because as bad as they may seem, they have the best linux support, period.

I want to try a 6200 but I'm a little worried that my Antec 350 may not be up to the power requirements. I may give it a shot anyway. I'll let you know if I get anything to work. 

It's ridiculous that it has to be this hard, though... Frankly, this is going to be a deal-breaker for me. I've been using Linux on my primary development station for three years now, but if I can't get my new LCD to use its native resolution, I may have to head back to Windows/Cygwin. I'm just so tired of spending days and days screwing with stuff that should be a no-brainer.

---

### Post by Watter on 2005-10-26
Bada bing, bada boom, and there it is. After some research at [nvnews.net](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14), I saw lots of folks who had their 2405fpw working and lots who didn't. The common denominator between those who didn't was a FX 5xxx series video card. All the way from 5200's to 5700's, to 5900XT's. So, before I headed to the store, i decided to plop in an old ti4600 card I had laying around and bam! It worked first try! I believe that the combination of a high resolution, the nvidia linux drivers and the 5200's DVI port are somehow not cooperating. Change one factor in that combo and things work. 

Anyway, I'm now going to start paring down my xorg.conf to elimante all of the probably needless extra things I added trying to get this to work on my FX5200. When I get a minimal xorg.conf that works, I'll post it here. 

Fantatstic! I'm finally going to be able to take advantage of my beautiful new monitor!

---

### Post by Watter on 2005-10-26
Here's the pared down xorg.conf that works for me on a Nvidia ti4600"
```

Section "Device"
        Identifier      "Nvidia ti4600"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Dell 2405fpw"
        Option          "DPMS"
        DisplaySize     518.4 324
        HorizSync       30-81
        VertRefresh     56-76
        Modeline "1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235 +HSync -VSync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Nvidia ti4600"
        Monitor         "Dell 2405fpw"
        DefaultDepth    24
        SubSection "Display"
                Depth           8
                Modes           "1920x1200" "1600x1200" "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1920x1200" "1600x1200" "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1920x1200" "1600x1200" "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1200" "1600x1200" "1280x1024" "1024x768"
        EndSubSection
EndSection

```

I have only one little nitpick left. The resulting DPI using these settings is 94x94 (found with "xdpyinfo | grep resolution"). I'd like to get it to 96x96, which is a pretty standard DPI, if I could. Anyone know how to do this?

---

### Post by John Nilsson on 2005-12-09
1920/(518.4/25.4) = 94.1
1200/(324/25.4)= 94.1
25.4*1920/96 = 508
25.4*1200/96 = 317.5

So no you can't have a standard DPI ;-), if numbers are important to you, you coud lie to X and say that your screen was 508 by 317.5...

---

### Post by Zentropic on 2005-12-11
[QUOTE=Watter]Bada bing, bada boom, and there it is. After some research at [nvnews.net](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14), I saw lots of folks who had their 2405fpw working and lots who didn't. The common denominator between those who didn't was a FX 5xxx series video card. All the way from 5200's to 5700's, to 5900XT's. So, before I headed to the store, i decided to plop in an old ti4600 card I had laying around and bam! It worked first try! I believe that the combination of a high resolution, the nvidia linux drivers and the 5200's DVI port are somehow not cooperating. Change one factor in that combo and things work. 

Anyway, I'm now going to start paring down my xorg.conf to elimante all of the probably needless extra things I added trying to get this to work on my FX5200. When I get a minimal xorg.conf that works, I'll post it here. 

Fantatstic! I'm finally going to be able to take advantage of my beautiful new monitor![/QUOTE]

Thanks for the info Watter.

Gawd, I've been getting my ass handed to me at work the last 6 weeks, so I apologize for the tardy reply to all those who responded.

Yeah, so it seems the 5000 series has a crap TDMS chip in it, because I borrowed an old ti4600 after reading your reply, popped it in, and got 1600x1200 right off! Not the native 1900x1200 sweetness I so dearly crave, but it says that the 5000 series is, ah, of lesser quality :mad:

Given that nvidia is pretty much the only decent choice( if you consider subpar TDMS chips and drivers with dot clock bugs decent ), I'll likely suck it up and get a 6600 or something. Also, the new driver rev. is finally released so between those and the new card, I pray I'll have this monitor operating as it should! I've almost been getting used to it as it is. Getting the full experience will be like having it new all over again!

---

