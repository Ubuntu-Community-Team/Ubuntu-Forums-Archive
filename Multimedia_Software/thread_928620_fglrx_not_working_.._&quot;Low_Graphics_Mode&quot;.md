---
title: "fglrx not working .. &quot;Low Graphics Mode&quot; imminent"
date: 2008-09-24
forum: Multimedia Software
---

### Post by truebosko on 2008-09-24
Hi there,

I have been trying on and off for a few months to get Ubuntu working with my ATI Radeon X850XT Card using the fglrx drivers

Vesa works fine, but it keeps me on a low resolution (1024x768) and I'm running a wide screen monitor that supports about 1680x1050

My problems have varied, initially I was getting out of range errors with my monitor, but then after I had unplugged my second monitor from the card I am not getting an issue of "Low Graphics mode"

Basically what happens is Ubuntu begins booting up then it flickers a few times between a black screen and some text showing what it was loading

Then it says "Ubuntu is running in low graphics mode blah blah .. configure, shut down, continue"

Continuing loads up Ubuntu fine in a horrible resolution and that's as far as I've gotten.

I've followed the guides on page like this:
[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

And many more, and still no idea

The only issues that I think may be causing an issue:

- When I run fglrxinfo I still get Mesa drivers showing despite attempts to uninstall them. I followed the instruction here on how to remove them: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers)

- I have set my Modes of resolution in Xorg.conf and setup VertRefresh/HorizSync for my monitor but this seems to have no effect.

Any help would be GREATLY appreciated. This is literally the only thing keeping me from my Vista box which I am growing more and more tired of.

---

### Post by overdrank on 2008-09-24
Moved :)

---

### Post by truebosko on 2008-09-28
Bumping this in an effort to get any replies :/

---

### Post by Agron on 2009-04-17
Hey, did anyone ever get past this problem?

Is there a way to capture fglrx failures before "Low graphics mode" dialog shows up?

Thanks!

---

### Post by markbuntu on 2009-04-17
You will have better results with the open source ati or radeon driver.

---

