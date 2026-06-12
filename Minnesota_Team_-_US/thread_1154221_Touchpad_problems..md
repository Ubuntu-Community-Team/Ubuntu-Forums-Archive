---
title: "Touchpad problems."
date: 2009-05-09
forum: Minnesota Team - US
---

### Post by ppjdd on 2009-05-09
I just recently installed Ubuntu JJ on my computer. I was a hateful windows user before and I just had enough of there crap. So here I am. I have a Gateway Laptop MX3414, and the touchpad works half way decent with Ubuntu, but I was wondering if there is a fix to the weird stuff it does.

I have a scroll section to my touchpad and if i use it then switch to the regular part, everything still scrolls. Any way of fixing that?


Thanx in advance.

---

### Post by geraldm on 2009-05-10
The problem sounds similar to a "feature" that is also available with mouse in a scrollbar.  If the mouse is clicked in the scrollbar, but released outside of the scrollbar, then the scrolling continues.  The solution is to click the mouse outside of the scrollbar window, and then it should be back to normal.
When you have the scrolling problem, try one click in the regular part to see if that stops the scroll.

regards,
Gerald

---

### Post by ppjdd on 2009-05-11
Ok I will try that. Just not used to it doing that. Everything else about Ubuntu is better than Windows. I guess I can live with one minor problem.

---

### Post by VCSkier on 2009-05-12
This is actually a settings problem.  Ubuntu is setting the vertical scroll area much wider than it should be (double, in my case).  With releases of Ubuntu prior to 8.10, this could be fixed but adding something like this to the synaptics touchpad section of the xorg.conf:

```
Option “RightEdge” “5970”
```

There are also some other tweaks I'd like to apply, like making the touchpad ignore broader strokes, like with the palm.

With more current releases, these changes must be made with .fdi files in /etc/hal/fdi/policy, but I can't figure out how to get this to work.

If anyone could provide some help, it would be greatly appreciated.  I can't figure out the proper syntax for applying the changes.

---

### Post by VCSkier on 2009-05-12
I seem to have sorted it out.

First I created 11-x11-synaptics.fdi within the /etc/hal/fdi/policy/ directory:
```
gksudo gedit /etc/hal/fdi/policy/11-x11-synaptics.fdi
```
In this file, I entered:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
   <match key="info.capabilities" contains="input.touchpad">
       <merge key="input.x11_driver" type="string">synaptics</merge>
       <merge key="input.x11_options.SHMConfig" type="string">On</merge>
       <merge key="input.x11_options.RightEdge" type="string">5970</merge>
       <merge key="input.x11_options.PalmDetect" type="string">1</merge>
   </match>
 </device>
</deviceinfo>

```
After a reboot, things seem to be working fine.  Keep in mind, that the integer for the "RightEdge" option may be different for you, depending on your touchpad.

The sources that helped me piece all this together were...
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)
[http://blog.eddiemonge.com/2008/08/03/scrolling-area-adjustment-for-touchpads-using-ubuntu/](http://blog.eddiemonge.com/2008/08/03/scrolling-area-adjustment-for-touchpads-using-ubuntu/)
and "man synaptics"

Hope this helps someone else.

---

