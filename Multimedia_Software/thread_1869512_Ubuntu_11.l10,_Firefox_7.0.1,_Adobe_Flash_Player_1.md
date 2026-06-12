---
title: "Ubuntu 11.l10, Firefox 7.0.1, Adobe Flash Player 11,0,1,152"
date: 2011-10-25
forum: Multimedia Software
---

### Post by grigglestone on 2011-10-25
Any thoughts on why I can't seem to play the following: [http://www.boston.com/sports/baseball/redsox/video/?bctid=1238950021001](http://www.boston.com/sports/baseball/redsox/video/?bctid=1238950021001)

Yup .. sorry a RS fan       :redface:

Anyways .. the little waiting grid shows, but I never get to the actual video.

I happen to have VirtualBox with an XP guest on the same Ubuntu host and running the same version of Firefox and Flash have no problem in viewing the video.

thx for looking!

---

### Post by lovinglinux on 2011-10-25
Get [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and run its wizard.

---

### Post by grigglestone on 2011-10-26
> **lovinglinux said:**
> Get [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") and run its wizard.

Ran it with wizard and recommendations and still cannot load the video.

I tried the 32bit plugin with no success either.

I have attached a flash aid report after applying the original defaults provided by the wizard.

thanks, David

---

### Post by grigglestone on 2011-10-26
.. also just tried Chrome on 11.10 and it has no issues .. grrrr

Could someone else try the original link and let me know if they also have an issue with firefox on 11.10?

Maybe its a setting in my firefox profile inherited from earlier installs thats causing an issue?

---

### Post by Bobhuber on 2011-10-26
> **grigglestone said:**
> .. also just tried Chrome on 11.10 and it has no issues .. grrrr

Could someone else try the original link and let me know if they also have an issue with firefox on 11.10?

Maybe its a setting in my firefox profile inherited from earlier installs thats causing an issue?
What video card and driver ?

---

### Post by grigglestone on 2011-10-26
> **Bobhuber said:**
> What video card and driver ?

$ sudo lshw -C video
[sudo] password for davidg: 
  *-display               
       description: VGA compatible controller
       product: G98M [Quadro NVS 160M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f5000000-f5ffffff memory:e0000000-efffffff memory:f2000000-f3ffffff ioport:df00(size=128) memory:f4000000-f401ffff

Video driver:

NVIDIA Driver Version: 280.13

---

### Post by HowardChau on 2011-10-26
> **grigglestone said:**
> .. also just tried Chrome on 11.10 and it has no issues .. grrrr

Could someone else try the original link and let me know if they also have an issue with firefox on 11.10?

Maybe its a setting in my firefox profile inherited from earlier installs thats causing an issue?


I just tried the link and it plays OK for me. I'm running Firefox 7.0.1 on 11.10, 64 Bit OS

I also just checked on [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) and saw that my Flash version is 11,0,1,152.

---

### Post by lovinglinux on 2011-10-27
> **grigglestone said:**
> Ran it with wizard and recommendations and still cannot load the video.

I tried the 32bit plugin with no success either.

I have attached a flash aid report after applying the original defaults provided by the wizard.

thanks, David

You still have two versions of Flash installed.  I need to update Flash-Aid, since they added *flashplugin-downloader* package on oneiric, which isn't present on older Ubuntu versions.

Remove it using:

```
sudo apt-get remove flashplugin-downloader
```

Then use only Flash-Aid wizard to install the version you want.

Report back if still doesn't work. Please test on YouTue but also on another site like Vimeo, because sometimes is an YouTube only problem.

---

### Post by grigglestone on 2011-10-27
It appears as though the issue is due to an Adblock Plus filter that was enabled. I have no idea why I got a difference in behavior between Ubuntu/Firefox releases .. I can't even see a reference to the filtered site on the offending page.

The offending filter was "||brightcove.com^".

Thanks for everyones input .. especially the Flash-Aid advice!

---

