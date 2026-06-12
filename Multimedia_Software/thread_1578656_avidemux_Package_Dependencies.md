---
title: "avidemux Package Dependencies"
date: 2010-09-20
forum: Multimedia Software
---

### Post by JamieKitson on 2010-09-20
Hi,

it just took me quite a while to work out why sound wasn't working on avidemux, it turned out I had to install the avidemux-plugins-common package. Shouldn't this package, or at least the audio plugins be dependencies?

Cheers, Jamie

---

### Post by tommcd on 2010-09-20
> **JamieKitson said:**
> 
 Shouldn't this package, or at least the audio plugins be dependencies?

You would think so. The *avidemux-plugins-common* package is not even listed as a suggested dependency for avidemux:
[http://packages.ubuntu.com/lucid/avidemux](http://packages.ubuntu.com/lucid/avidemux)
The repository info for *avidemux-plugins-common* carries this advice:
> This package includes common files for plugins to extend the functionality of Avidemux and should not be installed directly.
[http://packages.ubuntu.com/lucid/avidemux-plugins-common](http://packages.ubuntu.com/lucid/avidemux-plugins-common)
I am not sure what they mean by that. 
The Ubuntu developers obviously decided to leave the *avidemux-plugins-common* package out as a dependency for avidemux, for whatever reason I do not know.

---

### Post by mc4man on 2010-09-20
> Shouldn't this package, or at least the audio plugins be dependencies?
They are - sorta.
In karmic I believe it was a dep., in lucid and now maverick it is a recommend.
The default now is treat recommends as dependencies, so normally it would be installed. (though you can turn that off, or it doesn't always work/apply.

Ex.
> sudo apt-get install avidemux
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  avidemux-common avidemux-plugins-common avidemux-plugins-gtk libavidemux0
  mjpegtools twolame
Suggested packages:
  mpeg2dec
........ ect.


---

### Post by JamieKitson on 2010-09-21
> **tommcd said:**
> You would think so. The *avidemux-plugins-common* package is not even listed as a suggested dependency for avidemux:

To be fair that does recommend the gtk package which has the plugins as a dependency.

> **mc4man said:**
> They are - sorta.
In karmic I believe it was a dep., in lucid and now maverick it is a recommend.
The default now is treat recommends as dependencies, so normally it would be installed. (though you can turn that off, or it doesn't always work/apply.

Yeah, it obviously didn't work in my case :-/

---

