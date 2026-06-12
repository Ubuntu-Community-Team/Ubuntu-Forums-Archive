---
title: "remote desktop problem"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by liwei2000 on 2009-05-09
I set up remote desktop using following guide:

[http://www.ubuntugeek.com/share-your...e-desktop.html](http://www.ubuntugeek.com/share-your...e-desktop.html)

I want to access my ubuntu desktop using laptop running windows XP with vnc viewer.

I can log in and see ubuntu desktop remotely, but I can't click on anything. Actually, my mouse action is displayed on ubuntu desktop only, but not broadcast to my laptop vnc viewer screen.

Can anyone help me out ?

Thanks!

Wei

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

### Post by jmap82 on 2009-06-09
I wrote a short script to turn compiz off when I'm remotely viewing and back on again when I leave.  I'm no wiz at this stuff, so it may not be the best script ever, but you're welcome to use it if you want.

You can copy and paste from my wiki, [_here_]("http://script.jmap82.com/doku.php?id=jmap82sscripts:monitor").

Hope it helps :)

---

