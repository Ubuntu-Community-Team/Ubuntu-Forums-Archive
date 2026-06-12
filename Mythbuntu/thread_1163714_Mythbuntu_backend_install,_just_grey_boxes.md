---
title: "Mythbuntu backend install, just grey boxes"
date: 2009-05-19
forum: Mythbuntu
---

### Post by mevans7 on 2009-05-19
I need some help with my Mythbuntu install on a Dell 8300, using the Hauppage 1600.

When I install the Mythbuntu CD and get to the backend install, I get a near black box about 1/3 the height of the screen with a faint outline.  After awhile, and pressing some keys, I get a grey box in the middle, and two lighter grey boxes below.  Pressing the up/down arrow keys moves the box up/down.  If I press "enter" with the bottom box highlighted, it seems to quit the backend install.

Obviously there is something wrong with how the myth backend install is displaying its configuration menus.  HELP!

I searched the net.  I found instructions for using the Hauppage 1600 card.  I don't know if that card can mess up the display of the backend install menus.  Can it?

I tried to follow these instructions:  [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

but when I get to:
sudo apt-get install mercurial linux-headers-$KERNEL_VERSION build-essential

[FONT=Verdana]I get the message:

E: Couldn't find package mercurial

(Last week I tried to install the CD on a 10 year old Dell and I successfully got the backend 
install menus just fine.

Bottom line: 1) why doesn't the backend install display correctly?  and 2) what must I do to use the Hauppage 1600?

Any help or recomendations would be welcome.
[/FONT]:frown:

---

### Post by klc5555 on 2009-05-19
> **mevans7 said:**
> I need some help with my Mythbuntu install on a Dell 8300, using the Hauppage 1600.

When I install the Mythbuntu CD and get to the backend install, I get a near black box about 1/3 the height of the screen with a faint outline.  After awhile, and pressing some keys, I get a grey box in the middle, and two lighter grey boxes below.  Pressing the up/down arrow keys moves the box up/down.  If I press "enter" with the bottom box highlighted, it seems to quit the backend install.

Obviously there is something wrong with how the myth backend install is displaying its configuration menus.  HELP!

I searched the net.  I found instructions for using the Hauppage 1600 card.  I don't know if that card can mess up the display of the backend install menus.  Can it?

I tried to follow these instructions:  [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

but when I get to:
sudo apt-get install mercurial linux-headers-$KERNEL_VERSION build-essential

[FONT=Verdana]I get the message:

E: Couldn't find package mercurial

(Last week I tried to install the CD on a 10 year old Dell and I successfully got the backend 
install menus just fine.

Bottom line: 1) why doesn't the backend install display correctly?  and 2) what must I do to use the Hauppage 1600?

Any help or recomendations would be welcome.
[/FONT]:frown:

Is your video card an ATI Radeon of some sort? If so, you've likely fallen victim to this bug here: [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898)

If your card is an ATI Radeon, the current best fix is to replace it with an NVidia Geforcecard.

If your card is not ATI Radeon, then the problem must be something else.

---

### Post by klc5555 on 2009-05-19
Upon further review, if your machine is bitten by the ATI Radeon bug, there exists a workaround which may get you running for the time being. In some cases the mythfrontend can be started from a command prompt by:

XLIB_SKIP_ARGB_VISUALS="1" mythfrontend

If this workaround does it for you, then David Dean shows how to automate it here:

[https://lists.ubuntu.com/archives/kubuntu-bugs/2009-May/074607.html](https://lists.ubuntu.com/archives/kubuntu-bugs/2009-May/074607.html)

---

### Post by mevans7 on 2009-05-19
Running the frontend like:

XLIB_SKIP_ARGB_VISUALS="1" mythfrontend

TOTALLY WORKED!!  Thanks!  Now to get the system configured...

---

