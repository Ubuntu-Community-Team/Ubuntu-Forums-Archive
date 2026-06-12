---
title: "VNC - unable to do anything... just view"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by zurih on 2009-05-10
Hi,
I just configured a VNC server on my Ubuntu 9.04 64bit, and it "seems" to be working.
When I connect to it from a VNC viewer, I'm able to see the desktop and all of the items, but when I click with the mouse/keyboard on anywhere, it doesn't seem to do anything.
The strangest thing is that when I'm it does the change, but I'm unable to see it in the VNC viewer.
If I'm near my desktop I see all of the actions I remotely in the local machine, but I don't see it from the VNC viewer.

Any idea what the problem is and how can I resolve it?

Thanks in advance.

---

### Post by p388l3s on 2009-05-10
It's a known issue with 9.04

Turn off compiz and it'll update correctly.

Here's a script someone else wrote that works to change this on the fly:

```

#!/bin/bash
#Metacompiz
compiz=`pidof compiz.real`
metacity=`pidof metacity`
metacity_composide=`gconftool -g /apps/metacity/general/compositing_manager`
 
if [ -z $compiz ]; then
    echo "Debug: Compiz is deactivated"
else
    gdialog --yesno "Current Window-Manager: Compiz\n\nStopping Compiz and starting Metacity."
    if [ $? = 0 ]; then 
       metacity --replace
##If you want to use Metacity Composite, uncomment the next line
#       gconftool-2 -s  --type bool  /apps/metacity/general/compositing_manager  true    
    fi
fi
if [ -z $metacity ]; then
    echo "Debug: Metacity is deactivated"
else
    gdialog --yesno "Current Window-Manager: Metacity\n\nStopping Metacity and starting Compiz."
    if [ $? = 0 ]; then 
	if [ "$metacity_composide" = "true" ]; then
      	 gconftool-2 -s  --type bool  /apps/metacity/general/compositing_manager  false
	 compiz --replace
	else
	 compiz --replace
	fi
    fi
fi
 
exit 0

```

Hope this helps.

Pebbles

---

### Post by zurih on 2009-05-10
Can I make compiz to be automatically disabled when VNC connection is made?

Thanks

---

### Post by arbcat on 2009-05-15
It's more of a permanent solution, but try: 
```

metacity --replace

```

---

### Post by migueletorres on 2009-05-18
I´ve done the proposed (disable compiz) and it worked for a while, but now I have restarted my machine and the it is happening again (compiz is disabled) and I'm connecting from a Ultra VNC windows machine.

Any ideas?

---

### Post by Greydog56 on 2009-06-22
I ran the script on my Ubuntu 9.04 64 bit server that was running compiz and I now have screen control.  I was pleased that compiz automatically restarts when I log out and back on. Thank you for this advice.

---

### Post by roland86 on 2009-07-14
I think it's something with the graphics driver. Try to disable your driver and see if it works. This helps for me. 
I haven't found a solution for this.
_Update:_ Net yet tested, but try to disable the visual effects

---

### Post by NiRaise on 2009-07-24
This is exactly what I have been looking for. I am a little new to linux, so I just have one question where would I actually put that script. Any information would be gladly appreciated. Thanks

---

