---
title: "USB ir receiver not loading with pc turn-on/restart"
date: 2011-01-30
forum: Multimedia Software
---

### Post by tim_m99 on 2011-01-30
Hi,
I'm a linux newbie so I'm struggling to problem solve this issue.

I have recently obtained a HTPC which has Mythbuntu pre-installed and already working with a remote it came with.
I have another remote that I have changed over to (including the ir receiver) as it had easier button layout. Setup seems to have gone fine, but when the pc is restarted (turned of and on) then the ir receiver is not reloaded in the usb port. This was not a problem with the old remote.
If once the pc is on I unplug and re-plug the ir receiver then it loads and works fine.

Running a lsusb in terminal shows that it is definitely not loaded on restart but is when re-plugged in.

Any thoughts.
Tim

---

### Post by tim_m99 on 2011-02-01
Bump

---

### Post by vidtek on 2011-02-01
> **tim_m99 said:**
> Hi,
I'm a linux newbie so I'm struggling to problem solve this issue.

I have recently obtained a HTPC which has Mythbuntu pre-installed and already working with a remote it came with.
I have another remote that I have changed over to (including the ir receiver) as it had easier button layout. Setup seems to have gone fine, but when the pc is restarted (turned of and on) then the ir receiver is not reloaded in the usb port. This was not a problem with the old remote.
If once the pc is on I unplug and re-plug the ir receiver then it loads and works fine.

Running a lsusb in terminal shows that it is definitely not loaded on restart but is when re-plugged in.

Any thoughts.
Tim

Try another usb port for receiver, plug direct rather than through a hub or extension.  I have found Linux in general (many distros) to have some weird USB effects not found on Windows.

Having said that my HTPC is in the garage and I'm using USB extensions with powered hubs to get the 20 mtrs or so to my theatre where my Topseed usb ir reciever is!

Tony.

---

### Post by tim_m99 on 2011-02-06
> **vidtek said:**
> Try another usb port for receiver, plug direct rather than through a hub or extension. I have found Linux in general (many distros) to have some weird USB effects not found on Windows.
 
Having said that my HTPC is in the garage and I'm using USB extensions with powered hubs to get the 20 mtrs or so to my theatre where my Topseed usb ir reciever is!
 
Tony.
 
Solved the problem adding a USB hub which obviously gets the USB port to activate on boot, although this is not ideal as it is using more power and extra ugly stuff hanging out the back.
Would still love a solution without the hub but will have to do for the time being.
Wonder whether there will be issues with wakeup/shutdown function I'm about to tackle.
 
Tim

---

