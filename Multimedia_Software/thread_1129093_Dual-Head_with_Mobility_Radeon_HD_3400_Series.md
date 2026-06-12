---
title: "Dual-Head with Mobility Radeon HD 3400 Series"
date: 2009-04-18
forum: Multimedia Software
---

### Post by schlatter on 2009-04-18
Hi everybody

I have recently bought a Lenovo Thinkpad T400 and have installed Ubuntu (Intrepid Ibex) on it along with Win XP in dual-boot config. For use at home I also have a docking station that provides me with a DVI port. The laptop features Mobility Radeon HD 3400 Series graphics.

My problem is that I can not get dual-head with my Iiyama ProLite E481S to work reliably. Here's what I have tried so far and the results:

1. Attached ProLite on analog VGA port (not the DVI I mentioned above) using the open source driver. This actually works but the analog output of the laptop seems to be pretty poor: The output is unacceptably blurry.
I tried the same under Win XP (with ATI drivers): Same result.

2. I bought a DVI cable and attached the screen to the DVI port, still using the open source driver. I could easily configure dual-head config using the Gnome monitor resolution settings. So far so good. But as soon as I reboot, Ubuntu can't handle the external display anymore and goes into low graphics mode. The problem can be solved by disconnecting the external display during boot up. But then I end up with a single monitor, even if I reconnect it later.

3. I tried the commercial driver: Works with single-head. Gnome display resolution tool can't recognise the ext. monitor anymore. I used the ATI gui CCC but the ext. monitor remains dark. I configured dual-head on the command line using "aticonfig". Still, the ext. monitor remains dark, the laptop display works but I get only the desktop background, no icons, no taskbar.

4. I tried to get the display to work on Win XP using the digital port: Doesn't work. The ATI tool recognises the ext. monitor correctly and I can configure dual-head and everything but the screen remains dark.

5. I had a quick look into xorg.conf. However, this file does not really seem to be a config file anymore. It just contains some general stuff but no info on drivers, mode lines, etc.

Can anybody give me hint on how to get this to work? I know the hardware is ok as I can actually get dual-head to work. It just does not survive a reboot. What really confuses me is that it works not at all under windows. While I do not care too much about that, it could have been helpful for debugging.

Any help is very much appreciated,
Adrian

---

### Post by schlatter on 2009-05-01
Good news. It works after upgrading to Jaunty Jackalope using the open source drivers.

EDIT: I still can't get it to work with the ATI drivers. At least not using Catalyst Control Center.

---

