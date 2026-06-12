---
title: "Ubuntu Studio: Please post screenshots of working Qjackctl settings"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by Drophere on 2007-05-14
Hi all,

I have the following audio devices connected to my system:

[LIST]
[*]RME Digi 96/8 PRO
[*]Novation Speedio USB
[*]Onboard Via Chipset
[/LIST]

Ubuntu Studio sees all 3 (under Hardware Devices). The RME and Via chipset work under ALSA, but none work under JACK/Qjackctl (xruns and various other errors).

Since I can't find any documentation on how to setup Qjackctl, I thought I might be able to work out what's going wrong if I saw what settings are working for other people.

Could people who have Ubuntu Studio working with Qjackctl please post some screenshots of their settings?

Thanks,

Malcolm.

---

### Post by WestCoastSuccess on 2007-08-28
Try working with the suggested settings for the purposes of setup in brackets - you'll want to adjust some of these later to better your latency but you want a bigger latency to get the connection established:

-frames/period (512)
-sample rate (48,000)
-periods/buffer (3)
-input channels (2)
-output channels (2)
-interface (hw:0)
-latency (should show 32 ms with these settings)

The formula for latency is frames per period X periods per buffer divided by sample rate. 

See also my posts here for more info - the question was specific to the M-audio Firewire Solo, however the general principles apply:

[http://ubuntuforums.org/showthread.php?t=509312&page=2](http://ubuntuforums.org/showthread.php?t=509312&page=2)

---

