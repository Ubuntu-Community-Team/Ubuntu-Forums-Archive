---
title: "Were ATI Radeon Xpress 200 problems ever solved?"
date: 2009-12-10
forum: Multimedia Software
---

### Post by tashirosgt on 2009-12-10
I have a system wth a MSI-RS480 motherboard whose integrated graphics are detected as an ATI Radeon Xpress 200G.  Using Ubuntu 8 (before and after an update done today) I cannot login to a regular GNOME session.  An attempt to login produces some blank screens and then returns to the login screen.  I can login with a GNOME failsafe login.

For the failed login. the /var/log/gdm/:0.log.1 file ends with the error:

SetClientVersion: 0 9
in RADEONProbeOutputModes
in RADEONProbeOutputModes
X: r300_emit.c:403: r300EmitArrays: Assertion `((inputs_bitset)[((_TNL_ATTRIB_COLOR0) / (sizeof (GLuint) * 8))] & (1 << ((_TNL_ATTRIB_COLOR0) % (sizeof (GLuint) * 8))))' failed.
~
(END) 

I've researched this problem and found similar bug reports about the Xpress 200.  But the only work-around that I found suggested uninstalling compiz.  Doing this didn't fix the problem on my system.

Was this problem ever solved?

---

### Post by pme 72 on 2009-12-10
I had a similar sounding problem with my Radeon Express 200G (RS480) and Hardy Heron 8.04. I ran into a forum discussion that mentioned logging into a failsafe mode and installing the restricted proprietary drivers. That seemed to solve the issues for me. 

Intrepid Ibex 8.10 with the same card did not have the same issue. The card worked from the start with the default open source driver. I never installed the proprietary driver. I could even play SuperTuxKart. 

I eventually bought a replacement graphics card but did try the integrated card with 9.04 and 9.10 and they both granted me access. The cube and wobbly windows even worked with the default open source drivers in 9.10 although SuperTuxKart would not work for me and suspend was iffy. I did not bother to explore any potential work arounds.

---

### Post by tashirosgt on 2009-12-10
Thank you for the idea about proprietary drivers.  From the desktop I used System->Administration->Hardware Drivers and checked the box for the ATI accelerated drivers. After it installed and after rebooting, I can now login to the normal GNOME session.  Things look worse.  I assume all the options were customized to look nice with the other driver.  I must figure out how to configure appearances.

---

### Post by pme 72 on 2009-12-10
Yes, that is what I did to be able to log in to the desktop. Not sure what you mean by "Things look worse". 

You should have the option to turn off Desktop effects, System/Preferences/Appearance/Visual Effects - set to "None", if they seem to be creating any issues. It is easy enough to re-enable them.

---

