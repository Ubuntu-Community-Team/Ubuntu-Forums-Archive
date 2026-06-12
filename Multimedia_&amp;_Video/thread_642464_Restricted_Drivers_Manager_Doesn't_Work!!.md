---
title: "Restricted Drivers Manager Doesn't Work!!"
date: 2007-12-16
forum: Multimedia &amp; Video
---

### Post by Lord DEA on 2007-12-16
Hello everyone,

I'm using Ubuntu Feisty and I haven't been able to enable my graphics card.
I use an Nvidia Geforce FX 5200.

Here's what I do every time I try:
- I go to System --> Administration --> Restricted Drivers Manager (It shows me the name of the driver under "Driver", an empty check box under "Enabled", and a red button and 'Not in use' under "Status").
- I click the check box and get a message that says "Enable the driver? \n NVIDIA Accelerated graphics driver \n This driver is required..... bla bla bla.
- When I click "Enable Driver" in this last message window, Ubuntu displays again the Restricted Drivers Manager window, but the check box for the driver is still un-checked.
- After that, nothing else happens, no matter how many times I try the same.
- Then I click "Close" and, effectively, the window closes, but nothing happens then.

Apparently the "Close" button is the only thing that works fine.

Please some one help me with this.

For now, I'm gonna try re-installing Ubuntu and try again.

Thanks.

Daniel.

---

### Post by eth on 2007-12-17
try to take a look into 
```
/etc/modprobe.d/
```
inside there must be a lot of file named
```
blacklist
```
and
```
blacklist-*something*
```
open these file as root
```
sudo vim blacklist(-*something*)
```
those are thext file that contains lists of driver that is better avoid using. But if needed, you have to comment the lines containing the drivers you need.
As an EXAMPLE (it is not your specific case, just an example!!)
when you type
```
sudo vim blacklist-framebuffer
```
you see a list like
```

blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist cyblafb
blacklist gx1fb
blacklist hgafb
blacklist i810fb
blacklist intelfb
blacklist kyrofb
...

```
and if you need to get working, for example, the Framebuffer for Radeon R200 cards and for the intel, comment the lines as follows
```

blacklist aty128fb
blacklist atyfb
#blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist cyblafb
blacklist gx1fb
blacklist hgafb
blacklist i810fb
#blacklist intelfb
blacklist kyrofb
...

```

---

