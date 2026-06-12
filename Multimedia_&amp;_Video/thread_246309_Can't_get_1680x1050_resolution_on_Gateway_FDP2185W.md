---
title: "Can't get 1680x1050 resolution on Gateway FDP2185W"
date: 2006-08-29
forum: Multimedia &amp; Video
---

### Post by pandasonic on 2006-08-29
Hello.

I've been trying to get my monitor's native resolution (1680x1050) to work for the past two nights and to no avail.

My setup basically consits of:
HP Pavilion a818n
 - Intel Integrated Graphics Media Accelator 950
 and/or
 - PNY Verto (NVIDIA) FX5500 PCI
Gateway FPD2185W

I would ultimately like to get it to work with the NVIDIA card but after all this frustration at least the Intel chip would make me happy.

When I installed Ubuntu using the Intel 950 it would recognize the monitor (it's listed in xorg.config) and its available resolutions but it doesn't display at these resolutions nor does it list it under Preferences>Screen Resolution on GNOME. The same thing happens with the FX5500 but instead of giving at least some choices it only gives me a 640x480 resolution.

I'm a newbie and have no idea. I've been looking around the forums and googling around for info but had no luck with anything so far.

Has anyone had the same problem? Anyone has any suggestions?

I'd greatly appreciate the help. Thanks in advance.

---

### Post by tseliot on 2006-08-29
Try this guide to get your Nvidia card up and running:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

**Then**, if you have problems with the resolution:

Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

