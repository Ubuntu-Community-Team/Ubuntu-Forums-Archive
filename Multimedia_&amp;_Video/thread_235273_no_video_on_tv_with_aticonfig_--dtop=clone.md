---
title: "no video on tv with aticonfig --dtop=clone"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by hpb on 2006-08-12
Hello,

I' m trying to set my tv as a second monitor. I have a ATI RADEON X700 PRO (128 Mb) videocard and the latest ATI linux (propriety) display-driver installed (and Ubuntu 6.06 LTS DD).
When I config the driver: "aticonfig --dtop=mirror" I get a fine video image on my tv, but my pc-monitor doesn't work anymore (no signal) and when I try "aticonfig --dtop=clone", then both my tv and my pc-monitor are working and I can see my dektop on tv but no (moving) videoimages (output of mplayer for example is black on my tv while on my pc-monitor there is a normal image).

My xorg.conf (partly):

Section "Device"
Identifier "Generic Video Card"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "TVStandard" "VIDEO"
Option "DesktopSetup" "clone"
Option "ForceMonitors" "crt1,tv"
BusID "PCI:1:0:0"
EndSection

I also tried both the "--force-monitor" as "--enable-monitor" options, but with no succes.
Does anyone have an idea how I can both monitors get to work at the same time so that you can watch a video on the tv and do some other work on the pc?


hpb

---

### Post by mordi on 2006-08-12
the way I did it on an ati aiw 9800pro was

1 I followed this howto for the ati driver

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

2 and then I followed this howto for tv out, replacing nvidia with fglrx.

[http://gentoo-wiki.com/HOWTO_Separate_x-screens_on_Monitor_and_TV](http://gentoo-wiki.com/HOWTO_Separate_x-screens_on_Monitor_and_TV)

---

### Post by hpb on 2006-08-14
Thanks, but my first attempt didn't work out to well I'm affraid (no aticonfig -options in the howto!?) and resulted in a messed up X (not too bad though).
But I keep trying (rewriting my xorg.conf) and let you now if I succeed.

---

### Post by isharra on 2006-08-14
Clone mode only allows for one monitor to use the overlay at a time. I think you can select which one with the --overlay-on=* setting. For me 0 is crt, 1 is tv (I'm unsure what the port numbering is on the X700.) I know it worked with dtop=horizontal.

I took the lazy way out with 'aticonfig --initial=dual-head --screen-layout=right'. [note: I'm not at that machine, this laptop has a savage chipset so I can't verify the command.] This is a much shorter way of ending up with the same setup that mordi did.

The positive: both screens have video overlay, maximizing a window only takes up one screen. (I hate windows spanning when the tv is 2 feet from the crt.) I can put full screen video display on the tv and have a usable workspace on the crt. glxgears on both screens at once is slow but it works.

The negative: it takes more cpu, my frame rates are lower, and I can only log on using the crt. I can't run totem on both screens at once. I must pick one. :)

---

### Post by hpb on 2006-08-14
Yes... that's it. After reading (and acting on) the howto (thanks to mordi) and isharra's explanation (thank you too), I fiddled around with some settings and this is what works for me:

Section "Device"
        Identifier  "ATI RADEON X700 PRO"
        Driver      "fglrx"
#       Option      "VideoOverlay" "on"
        Option      "TVStandard" "VIDEO"
        BusID       "PCI:01:00:0"
EndSection

Section "Device"
   Driver          "fglrx"
   Identifier      "TVOUT"
   Screen 1
   Option          "TVOutFormat" "SVIDEO"
   Option          "VideoOverlay" "on"
   Option          "TVStandard" "PAL"
   Option          "ConnectedMonitor" "TV"
   BusID           "PCI:01:00:1"
EndSection

So it only works (for me) when I disable the "VideoOverlay "on"" option in the device-section of my pc-monitor. I guess I can't have video overlay on both monitors this way?

Anyhow, thanks to you both! (gonna watch a movie tonight).

;>} hpb

---

### Post by isharra on 2006-08-14
Here's a difference from what I have in my configs and Mordi's referenced howto.  (Note: this is with a 9800xt and a 9000) Using aticonfig I ended up with both ports using the same BusID. (it writes it that way and it's working) VideoOverlay is on for both. If you use separate BusID then you are limited to the one monitor.

Just something to try :)

---

### Post by mordi on 2006-08-15
> **isharra said:**
> 
Using aticonfig I ended up with both ports using the same BusID. 


from what I read that is the correct way. the bus id should be identical with the one you get with lspci, the first one.

---

### Post by hpb on 2006-08-16
You are right, I overlooked that part in the HowTo. 
So I tried setting both BusID's to "01:00:00" and VideoOverlay to "on". But I' m afraid that's not working for me: pc monitor = OK, but on my TV, only my Desktop is visible (no video, not even unfolded menu's show up, just the background image and the panels). 
After some Ctrl-Alt-Backspace's, the only thing that seem to work for me (bit weird huh?) is:
BusID "PCI:01:00:00" for my pc-monitor; BusID "PCI:01:00:01" for my TV and VideoOverlay off (#) in the device section of my pc-monitor; both monitors do exact the same thing this way, included full screen video. I can watch my Xvid movies on tv now (which is very nice).

Thanks to you both for helping me on this (hope I can help you out sometime).
;>)

---

### Post by isharra on 2006-08-17
It's a separate xwindows session. You should be able to configure the panels and launch apps there. (right click on the panels to add to them.) If I've misunderstood you and the panels are already configured, but unresponsive, that's a different issue.

At this point I don't know if it's the difference in video cards or configuration. I used aticonfig to set up everything but the video rates for the crt.  [NEC MultiSync 3FGe that refuses to die. Silly thing has been on barring power failures 24x7 since 1993. I've buried 3 monitors I bought to replace it on my primary system.]

But if it works, quit messing with it. You can go mad trying to get things "just right".  Even worse you could end up like me. :)

---

### Post by hpb on 2006-08-17
So you've learned things the hard way, did you? I guess I'm a bit in your footsteps now and besides that I'm afraid I'm a newbie still. Of course you're right, it's in a separate session (dumb, dumber ...). The screen (displayed on my tv) and where I previously said there was no video, where not even unfolded menu's showed up, only the background image and the panels: it turned out I can go there with my mouse (going right off the screen of my pc-monitor), load mplayer, play a video (with the correct xorg/aticonfig/howto settings and both having overlay-on now!).

So after all it did work and I'm sorry to say that I didn't discovered that earlier. Maybe partly because I was too busy configuring and forgot about the "Screen[1]" RightOf "Screen[0]" setting from the howto . So thanks again for pointing in the right direction.

"DISPLAY=:0.1 mplayer bla.avi" works great now! (except for bla o.c.).

Turned to Linux because I was bored with winXP. Can't say this distro disappointed me in that sense (So... now I can get back to cron (doesn't do anything) and vncserver (scrambled up X in TightVNC). But that's a different thread.

---

### Post by morikaweb on 2006-09-21
I just followed the advice in this thread, and in the howto mordi posted. I got my tv out working great but I have a few questions:

I. Is there anyway to tell the second session to use the settings of the first(primary) sesion? By settings I mean things like background, theme and such.

II. Who is the second session logged in as? It never asked for a password so is it root? Or is it just my account? If its my account then I refrer to question I and ask why it does not use my settings.

III. Is there any way to toggle tv out on and off (other than overwriting the xorg.conf with a new one and restarting x)? It seems like a wast of resources to have it on without using it.

IV. This all is ridiculously complicated compared to windows, is anyone working on a popper gui?

---

### Post by hpb on 2006-09-22
I. My desktop on the second display is the same as on the first, including background and theme. I even can't change them independently (I don't know if the "aticonfig --dtop=clone" has something to do with that).
:confused: 
:confused: 
IV. I'm using a GNOME Desktop and sometimes Enlightenment (and of course the X Window System, Version 7.0.0)

I hope Isharra or Mordi (or someone else) have more complete answers to your questions.

---

