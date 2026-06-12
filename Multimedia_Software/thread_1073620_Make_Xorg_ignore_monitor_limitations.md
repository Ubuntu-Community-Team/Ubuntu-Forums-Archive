---
title: "Make Xorg ignore monitor limitations?"
date: 2009-02-18
forum: Multimedia Software
---

### Post by lykwydchykyn on 2009-02-18
Here's the situation:  I'm tinkering around with some old surplus laptops which I use as thin clients.  The graphics chip will do at least 1024x768, but the onboard LCD panel will only do 800x600.  

Even when I plug in an external monitor, I can't get Ubuntu to do more than 800x600.  I thought it just wasn't going to work, but then I booted up a DSL disc and it happily defaulted to 1024x768, switching off the onboard monitor.

How can I get Ubuntu to do the same?  I tried manually specifying refresh rates in the xorg.conf file, but it didn't work.  Xorg.0.log says 
```

(II)MACH64(0): Not using driver mode "1024x768" (exceeds panel size)

```

EDIT: ok, I found that if I use the function keys on the laptop to switch off the onboard monitor, then restart X, it will default to 1280 x 1024.  Nice, but I am not sure how to get it to boot this way.  There's no BIOS option to turn off the onboard.

---

