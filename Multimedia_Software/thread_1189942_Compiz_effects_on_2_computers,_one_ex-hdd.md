---
title: "Compiz effects on 2 computers, one ex-hdd"
date: 2009-06-17
forum: Multimedia Software
---

### Post by Jarige on 2009-06-17
Hey guys,

There's a thing that has bugged me for a while now. I installed Ubuntu on my external harddrive on an HP laptop with an NVIDIA 8400GS M. I installed proprietary drivers from NVIDIA, working flawlessly on my HP. But since its installed on an external hdd, I boot it at school (yes I'm a scholar :P ). It boots well, but after a while it says 'Ubuntu is running in low graphics mode'. Then it will restart the display or something and blabla, which sometimes takes a long time. Sometimes I even need to reset my video configs by using tty1 and some command I forgot now. 
Because Ubuntu runs in low graphics mode there's no Compiz effects, which I really want to show to my friends :P
Ok since school has the same gpu on every computer, it could be very simple to just install Intel drivers, but when I click System->Administration->Hardware Drivers there's no drivers there.
This is the exact name of the gpu:
Intel Corporation 82Q963/Q965 Integrated Graphics Controller 

Now I want to have compiz effects on both school computers and at home on my laptop. How do I do that?

(At home I installed NVIDIA drivers, version 1.80)
(Ubuntu 9.04, GNOME, not afraid to use the terminal :P)

---

### Post by Jarige on 2009-06-17
bump

---

### Post by overdrank on 2009-06-17
Hi and please be patient. One bump a 24 hr period is accepted. If you are trying to use to different graphics set up you may have to save you nvidia xorg, then when you run the setup on the intel graphics change to that xorg. Now with then intel graphics you may look at the link in my signature for the issue with Jaunty.

---

### Post by Jarige on 2009-06-17
Oh, sorry, didn't know about that rule :P
Can you guide me around? Cause I've heard about xorg, and I know its some configuration file, but where the heck is it?
Do I need to manually put the nvidia xorg backup file back and forth every time I boot? That would be very annoying... Is there an easy way of doing this?

---

### Post by Jarige on 2009-06-18
bump

---

### Post by Jarige on 2009-06-22
bump again

---

### Post by overdrank on 2009-06-22
> **Jarige said:**
> Oh, sorry, didn't know about that rule :P
Can you guide me around? Cause I've heard about xorg, and I know its some configuration file, but where the heck is it?
Do I need to manually put the nvidia xorg backup file back and forth every time I boot? That would be very annoying... Is there an easy way of doing this?

Hi and if you have installed the nvidia driver then you xorg is located
```
gksu gedit /etc/X11/xorg.conf
``` is how you edit it. 
As for the intel graphics you may look at the link in my signature about intel graphics in Jaunty 9.04.
If you are using a external drive then it may be easier to have two installs of Ubuntu. One for the nvidia driver and one for the intel.
Sorry I can not help more.

---

### Post by Jarige on 2009-06-22
I'd rather know what to edit :S

---

### Post by overdrank on 2009-06-22
> **Jarige said:**
> I'd rather know what to edit :S

As I stated you would have to have to xorg's. One for the nvidia drivers and one for the intel.
It would be really difficult as I stated with the intel graphics because of the issues with Jaunty 9.04. If I understand the fix correctly you would have to revert to a older xorg and this would conflict with the nvidia drivers install for sure.
This is why I suggested the two partition for Ubuntu. Other than that I can not help.

---

### Post by Jarige on 2009-06-22
Then I'll just wait for someone else who might know what to do... I don't want 2 installations, I'll probably need to configure everything again (every customisation I did on one install, must be done again on the other blabla)

---

