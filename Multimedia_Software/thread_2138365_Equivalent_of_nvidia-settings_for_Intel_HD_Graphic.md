---
title: "Equivalent of nvidia-settings for Intel HD Graphics 4000"
date: 2013-04-23
forum: Multimedia Software
---

### Post by PeterTaps on 2013-04-23
Folks,

My existing HTPC runs on Ubuntu and has an nVidia video card. The HTPC has two video outputs. The HDMI output is connected to the projector and the VGA output is connected to a monitor. I run separate X Windows (not twinview) so that, while watching the movie via projector,  I can do something else on the monitor.

I am thinking of replacing this HTPC with a smaller form factor and am looking at the new breed of mini-ITX motherboards. The CPU I am looking at is Intel core i3 that has HD Graphics 4000 GPU.

One advantage of nVidia was that I could run nvidia-settings and configure separate X-Windows from its UI.

I am wondering if there is an equivalent UI available for Intel HD Graphics GPU. More importantly, will I be able to configure my new setup for two separate X-Windows?

Thank you in advance for your help.

Regards,
Peter

---

### Post by papibe on 2013-04-23
Hi PeterTaps.

AFAIK, there's no equivalent GUI tool.

You would need to use the command tool 'xrandr', and/or edit your Xorg config file manually.

Regards.

---

### Post by PeterTaps on 2013-04-23
Thank you for your help. So basically all nvidia-settings does is to either run xrandr in the background or modify Xorg config file programmatically.

It is good to know that there is some workaround. I was worried that two separate xwindows was not even a possibility.

Regards,
Peter

---

### Post by papu40000 on 2013-07-16
xrandr GUI

sudo apt-get install arandr

[http://christian.amsuess.com/tools/arandr/](http://christian.amsuess.com/tools/arandr/)

---

