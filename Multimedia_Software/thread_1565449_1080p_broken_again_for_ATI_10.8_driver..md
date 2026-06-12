---
title: "1080p broken again for ATI 10.8 driver."
date: 2010-08-31
forum: Multimedia Software
---

### Post by rmjohnson144 on 2010-08-31
I installed 100.8 drivers yesterday and now my monitor has the infamous black border around my desktop.

!0.7 fixed it and scaling was added, but the new one will scale, but it won't save properly, and the black border comes back at reboot.  I even tried the Catalyst (administrator) and no love.

Anyone else have this issue, or found a resolution. (other than going back to 10.7)?

-=Mark=-

---

### Post by SeePU on 2010-09-01
I am just curious... if you wouldn't mind provding info... whether the open source radeon drivers work with your card.

The radeon drivers should be available out of the box.  Do they work?  What can you do with your card if you use it?  Can you play video okay?  What happens if you try xv output?  I read that OpenGL output works but I am wondering what the status is for xv with the radeon driver and Evergreen cards.

For your situation, if it was me with that card and that Ubuntu install, I would go to the AMD website and do a fresh install of the 10.8 driver.  I believe the latest update is Aug. 25/'10.  

I would find the most 'up to date' installer 'how-to' for the Catalyst 10.8 driver for Ubuntu 10.04 and install it exactly that way.  If I had problems still, I'd go check the Phoronix website.

The reason I suggest that is there's a number of posts there about ATI driver installs in Linux including Ubuntu.  There are sometimes ATI/AMD devs there that visit although I think most deal with the radeon drivers.  But, they might recognize your issue or have suggestions.  I wouldn't use the default Ubuntu 10.04 'Restricted Drivers' option or whatever it is.  It's best to try the most up to date driver on the AMD site because, hopefully, they fixed some bugs.  Also, the AMD site will have links to the recommended driver install process.  If it doesn't, google the latest websites with 'Catalyst 10.8 driver install + Ubuntu 10.04' or something like that.  That's what I would try first.

---

### Post by Yellow Pasque on 2010-09-01
So Catalyst Control Center isn't saving your settings between each reboot?

---

### Post by rmjohnson144 on 2010-09-01
To be more clearer.

I downloaded the 10.8 drivers from AMD.COM.  It installs just fine and works without errors.

My only issue is the black border on 1080p monitors.  it has been an ongoing issue now for several months.  It happens in windows as well.  There is a scaling option that is suppose to fix the issue, but now when I exit it doesn't save the setting properly.  it sometimes even locks up on reboot from, i asssume, not saving the settings properly.

I reboot and the black border is back, but when I go into CCC to change the scaling, it says it is configured properly, but it still has the black border.

As soon as I move the scaling slider, it quickly readjusts itself and properly scales to get rid of the black border, but it comes back on reboot.

so yes, it isn't saving it properly, but is saving it as the CCC reports my changes are in affect, they just don't seem to apply.

This has been an ongoing issue of working one month, then not working the next.  It has been close to a year now and ubuntu had it working last month for the first time ever.

On research, it seems the monitor as firmware that talks to the PC, called an EDID, that doesn't play well with the ATI cards.  It seems the 1080P is a TV resolution and is the problem.  All the PC Monitor resolutions work fine.  Just the HDTV resolutions don't.

also, it is HDMI related as well.  not sure of DVI works properly, but VGA port works great as there are no HDTV options, (nor 1080p resolutions)

Hope that clears it up a bit.  Hopefully others have got theirs working if they dared to try 10.8.  I guess I'll be going back to 10.7 if noone has any clues what's going on this time around.

-=Mark=-

---

