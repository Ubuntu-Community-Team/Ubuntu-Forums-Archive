---
title: "Multiple Monitors + input switching + ATI = ??? :("
date: 2009-10-07
forum: Multimedia Software
---

### Post by DuplexEmotions on 2009-10-07
Okie dokie, here's what's going down.

I just (as in, in the last couple hours) got a sweet new 24" monitor, an ACER H243H. It has built in speakers and HDMI input as well as DVI and VGA. The idea was simple; hook my xbox or digital cable box to the HDMI port and my computer to the DVI, with my old 20" NEC Multisync as a secondary monitor. That way I could slide my chat windows and the like onto my secondary monitor while watching TV or what not on my first. Thanks to ATI's configuration software (i'm using the ATI proprietary drivers and a Radeon 4870), I can easily set up my 24" as the primary and extend the desktop onto the 20". Everything was easy to set up and relatively painless.

The problem comes from when I switch inputs on the primary monitor to get to the xbutt or cable. Ubuntu loses the primary monitor and switches the secondary one to the primary, resulting in a big scrolling screen of approximately  the same size as both of the monitors filled with a large black space on monitor 2, and then clone mode at monitor 2's resolution when I change the input back.

Is there any way I can tell Ubuntu "hey, we're good with the video settings, just keep doing what you're doing" once the monitors are configured the way I like? I don't like having to open up the ATI program and swap everything around just because I wanted to see what's on the food network.

I'm using Jaunty, 9.04

Thanks!

John

---

### Post by Nathan.Flow on 2009-10-08
> **DuplexEmotions said:**
> Okie dokie, here's what's going down.

I just (as in, in the last couple hours) got a sweet new 24" monitor, an ACER H243H. It has built in speakers and HDMI input as well as DVI and VGA. The idea was simple; hook my xbox or digital cable box to the HDMI port and my computer to the DVI, with my old 20" NEC Multisync as a secondary monitor. That way I could slide my chat windows and the like onto my secondary monitor while watching TV or what not on my first. Thanks to ATI's configuration software (i'm using the ATI proprietary drivers and a Radeon 4870), I can easily set up my 24" as the primary and extend the desktop onto the 20". Everything was easy to set up and relatively painless.

The problem comes from when I switch inputs on the primary monitor to get to the xbutt or cable. Ubuntu loses the primary monitor and switches the secondary one to the primary, resulting in a big scrolling screen of approximately  the same size as both of the monitors filled with a large black space on monitor 2, and then clone mode at monitor 2's resolution when I change the input back.

Is there any way I can tell Ubuntu "hey, we're good with the video settings, just keep doing what you're doing" once the monitors are configured the way I like? I don't like having to open up the ATI program and swap everything around just because I wanted to see what's on the food network.

I'm using Jaunty, 9.04

Thanks!

John

Just an idea, don't know if it will work, but try disabling xrandr, and edit your xorg.conf (back it up first) to hard code your settings in.

Good luck

---

### Post by markbuntu on 2009-10-08
WHat you need to do is reconfigure your minitors before you switch. There is a WAY TO "Force your monitors with aticonfig but since you are using a big desktop you would need to reconfigure that before switching. Big desktop uses randr so do not disable it.

---

### Post by DuplexEmotions on 2009-10-18
Sorry it took me so long to respond, it's been super crazy over here. I'd rather not disable xrandr since, like mark said above, I'm using xrandr right now.

I guess I'll just switch to having to fiddle with the settings a bit before and after I play my xbox. Thanks anyway!

---

