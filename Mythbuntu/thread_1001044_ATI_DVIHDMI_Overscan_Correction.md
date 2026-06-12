---
title: "ATI DVI/HDMI Overscan Correction?"
date: 2008-12-03
forum: Mythbuntu
---

### Post by anand on 2008-12-03
I'm thinking about upgrading my HTPC and trying to decide what kind of video card to go with - Nvidia or ATI.  My system now has an Nvidia card and the major frustration I've had with it is that there doesn't seem to be any way to compensate for overscan using the DVI output (via a DVI->HDMI cable) in the driver and trying to mess with modelines in the X config file always lead to a garbled screen.  Aside from that, I haven't had any problems with the Nvidia driver.

Does anyone know if the current ATI drivers have any easy to use way to compensate for overscan on their DVI outputs?  If they can, that might swing me over to the ATI side.  I don't have any particular allegiance to either side otherwise.  

Unfortunately I don't currently own an ATI card right now so I can't try anything out myself.  Was hoping to get an answer before I start spending money :)

---

### Post by SiHa on 2008-12-04
If you use the system for anything other than Mythtv - ie you want to be able to see the whole desktop, then for DVI / HDMI, the only way to do this AFAIK is from the TV end. Many digital TV's have a menu option to turn off overscan, Sometimes this is available from the standard manus otherwise it may be hidden in a service menu.

If you only use Mythtv, have you tried reducing the size of the Mythtv output: TV Settings -> Screen Setup Wizard. This will allow you to reduce the Myth window to the visible portion of the screen.

Beware: If you use standard Mythbuntu with the xfce desktop, any change to the Myth screen size will result in the top panel displaying over Myth - this is a known bug. My favoured workaround it to make this panel auto-hide, so that when it's hidden, the thin line that remains is lost in the overscan. Thn you can still move the mouse up to the top and bring it back if you need to.

As far as ATI is concerned, my experience was not a good one, For what it's worth.

---

