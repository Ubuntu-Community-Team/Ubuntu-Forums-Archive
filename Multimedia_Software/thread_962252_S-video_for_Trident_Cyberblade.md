---
title: "S-video for Trident Cyberblade"
date: 2008-10-29
forum: Multimedia Software
---

### Post by somersetsimon on 2008-10-29
Hi,
I want to connect my laptop output to my TV using S-video. I have a Trident Cyberblade video card. How do I go about setting this up? I know the cable and TV are ok as I tested my Vista laptop with the setup last night. In Windows I just selected the secondary screen, clicked 'Attached' and it seemed to just work without any other settings. What is the equivalent in Ubuntu?
Thanks
Simon

---

### Post by overdrank on 2008-10-29
> **somersetsimon said:**
> Hi,
I want to connect my laptop output to my TV using S-video. I have a Trident Cyberblade video card. How do I go about setting this up? I know the cable and TV are ok as I tested my Vista laptop with the setup last night. In Windows I just selected the secondary screen, clicked 'Attached' and it seemed to just work without any other settings. What is the equivalent in Ubuntu?
Thanks
Simon

Hi and I do not have any experience with that model but you may try and use the alt, F2 keys and enter this command ```
gksu displayconfig-gtk
```
and setup the extra monitor there.

---

### Post by somersetsimon on 2008-10-29
> **overdrank said:**
> Hi and I do not have any experience with that model but you may try and use the alt, F2 keys and enter this command ```
gksu displayconfig-gtk
```
and setup the extra monitor there.

Thanks for the help, but I couldn't find anything there that related to TV out, just various monitor types.

---

### Post by overdrank on 2008-10-30
> **somersetsimon said:**
> Thanks for the help, but I couldn't find anything there that related to TV out, just various monitor types.

Does it detect the extra monitor?

---

### Post by somersetsimon on 2008-10-30
> **overdrank said:**
> Does it detect the extra monitor?

How can I tell if it has detected anything plugged into the s-video port? Even without anything else plugged in, you can select settings for a secondary display.

Is there somewhere I can check specifically for TV-out settings rather than general monitor settings?

Thanks

Simon

---

### Post by somersetsimon on 2008-11-04
> **somersetsimon said:**
> How can I tell if it has detected anything plugged into the s-video port? Even without anything else plugged in, you can select settings for a secondary display.

Is there somewhere I can check specifically for TV-out settings rather than general monitor settings?

Thanks

Simon

I still can't figure out how to get S-video working with a Trident Cyberblade video card. Can anyone help? It seems like you can use xrandr to set up S-video, but it only works for ATI or nVidia cards.

---

### Post by somersetsimon on 2008-11-07
I still can't figure out how to get S-video working with a Trident Cyberblade video card. Can anyone help? It seems like you can use xrandr to set up S-video, but it only works for ATI or nVidia cards.


Bump

---

### Post by somersetsimon on 2008-11-17
> **somersetsimon said:**
> I still can't figure out how to get S-video working with a Trident Cyberblade video card. Can anyone help? It seems like you can use xrandr to set up S-video, but it only works for ATI or nVidia cards.


Bump

Having to resort to another bump. I can't find any information on getting s-video output to work for non nVidia or ATI card. At least if someone told me I'm attempting the impossible, I would know to give up

---

