---
title: "fireglcontrol error message on ati"
date: 2007-02-02
forum: Multimedia &amp; Video
---

### Post by tsapi on 2007-02-02
Hallo!

I am new to ubuntu. I have just installed 6.10 on my computer. My computer is an athlon dual core on an nforce4 motherboard with an ati radeon X1600 card on pci express. The installation of ubuntu was flawless.

I then followed the instructions here [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html) in order to install xgl and beryl. Everything went fine and now I have an impressive 3D desktop! :) 

Then I wanted to configure ati, in order to use the second output of the card (the card is dual head) and the tv out. As a matter of fact, I have the second output of the card physically connected to the projector of my home cinema and the tv out is connected to my TV. I tried to run fireglcontrol and fireglcontrolpanel but received the message: "Driver does not provide the FireGL X11 extensions! Panel components will operate only partially". The panel didn't appear at all.

I googled around about this error message but didn't find anything helpful. :confused: 

What can I do in order to have all the bells and whistles of xgl and beryl and at the same time be able to use both outputs of my ati and the tv out? How can I run the ati control panel?

Thanx a lot in advance for any help you can provide..

---

### Post by tsapi on 2007-02-03
By the way, fglrxinfo gives following result

fglrxinfo 
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

There is no solution to my problem or is it so obvious and easy that it slipped my attention? :(

---

### Post by tsapi on 2007-02-03
Further info:

When I run driconf, I get following messages
```

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Screen "0" is not direct rendering capable.
```

Then comes following message:

```
Could not detect any configurable direct-rendering capable devices. DRIconf will be started in expert mode.

```

That "expert mode" is more than useless to me as I am very far away from being an expert.. :lolflag: 

Nevertheless, I am stuck..

Do I need DRI? In my xorg.conf there is none module like that described..

Any help will be appreciated.. :)

---

