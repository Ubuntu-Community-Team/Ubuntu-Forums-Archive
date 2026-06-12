---
title: "File manager set default view to Details?"
date: 2011-02-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by candtalan on 2011-02-27
Is it possible for me to configure the file manager so that the default display is always Details rather than Icons?

I am running a live dvd of natty daily build of todays date
tia

---

### Post by t1497f35 on 2011-02-27
For Nautilus: Edit - preferences - Views tab - "view **new** folders using" - "List View".

---

### Post by candtalan on 2011-02-28
Using the live session, I click onto the file manager icon, a window appears, presumably nautilus, however I can not see any method of invoking a 'preferences' menu. Where is is obtained please?

---

### Post by mdurham on 2011-02-28
> **candtalan said:**
> Using the live session, I click onto the file manager icon, a window appears, presumably nautilus, however I can not see any method of invoking a 'preferences' menu. Where is is obtained please?

As t1497f35 said, it's in the 'edit' menu.

---

### Post by brallan on 2011-02-28
...so that the default display is ALWAYS Details?

hmm, I may be restating the obvious, but I think you CAN'T get that to work for more than one session on a liveDVD, simply because DVD is a read-only medium. To make changes that last for more than one session, you could try:

1) making a liveUSB:
from system>administration>startup disk creator
Include some extra space for documents and settings.

2) Install (including the bootloader) on a USB stick. 
To do this, just choose to install from the DVD as you would normally, then when it gets to partitions, be careful to choose your USB disk, and make sure it gives you the option to install the bootloader to the USBstick as well. this gives you a "live" (moveable) install, which has the advantage that you can configure it as you like. However, it may not work with as wide a variety of hardware as the liveUSB, and it will be ext4, not a FAT32 drive like the liveUSB, nor will it have the ubuntu installer.

---

### Post by candtalan on 2011-02-28
> **mdurham said:**
> As t1497f35 said, it's in the 'edit' menu.
Thank you, however I suppose my point now is, there is no 'Edit' menu shown.

Note I am using a live session from yesterday's daily build.

---

### Post by candtalan on 2011-02-28
>  I think you CAN'T get that to work for more than one session on a liveDVD, simply because DVD is a read-only medium 

Thank you . A misunderstanding. I do not want  subsequent sessions to retain the change I understand  that a true live session with no persistence is truly  live, no problem.

The problem I am attempting to draw attentioj to is thta  unlike all live CDs f or ubuntu versions up to and including 10.10, it is possible to do what has been suggested, that is, use the Edit>Preferences menu to choose  - for that live session - either Details or Icons.

This does not seem to be possible with the live DVD I am currently trying simply because, (although I am very unfamiliar with the Unity interface), there is simply NO edit menu!

If I have not yet found it, then somebody please tell me how?
tia

---

### Post by t1497f35 on 2011-02-28
If you wanna spare your and other's time just send a screenshot (of the whole desktop) and someone will hopefully point to the "edit" with a big red arrow. We can't read your mind and see your desktop to diagnose _why_ you can't find "edit".

---

### Post by candtalan on 2011-02-28
> **t1497f35 said:**
> If you wanna spare your and other's time just send a screenshot (of the whole desktop) and someone will hopefully point to the "edit" with a big red arrow
A little red arrow would have done ok
>  We can't read your mind and see your desktop

I do know that, and that is the reason why I have tried to explain in words. However, with little success.
>  to diagnose _why_ you can't find "edit".

Ah! Have just discovered how! 
The location is at the top panel of the display screen, as an auto hide/reveal facility.

I was using only the File Manager window, and within this window, including its top bar, there is no menu system (like there was with non-unity). I had done a lot of searching around with the cursor but had failed to find it. 

However, I have just now discovered it.

It is amazing how helpless one feels when a new gui is used. And presumably how frustrating it is to try to explain an apparently obvious answer without being shown the problem.
Thank you for your patience.

For the record the relevant screenshots (before and after discovery) are attached

---

