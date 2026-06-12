---
title: "dell xps m1330 media remote control"
date: 2009-02-23
forum: Multimedia Software
---

### Post by vrv123 on 2009-02-23
Hi experts,

I have a dell xps m1330 with Ubuntu 8.10 installed.
issues with media controls(images attached):
1) the remote control is not working with ubuntu 8.10.
2) only the volume buttons on the keyboard are working, the rest eject, play/pause etc are not working.

as the system was preinstalled with vista, the media center remote control used to work fine with it, but does not work with Ubuntu 8.10.

how do i get these to work, is there an alternative media control existing for Ubuntu 8.10 ?

please help me....

Thanks in advance.

---

### Post by vrv123 on 2009-02-23
pls reply....

---

### Post by FirstByté on 2009-03-18
I use a Dell Studio 14 and share similar problem as well. All controls work on Windows Vista [I dual boot] and so does the romote in vista.

when I tried:

 ~$xev

It it captures all [media] events except the 'Eject' button.
It also doesn't capture any remote button.

I ran Ubuntu 8.10 on my previous hp with a remote and everything worked OFB.

However, nautilus can eject CD directly. On the other hand, you would have to first unmount the CD before you can use the eject button to eject the CD. This leads me to guess it's a 'sudo' related problem or just that it's a hardware event [which would need to be mapped]. Since it works on nautilus but require direct UNMOUNTing outside nautilus.

I'm not an authority in Linux, I'll gladly appreciate any help on how to get my Ubuntu Intrepid to recieve events from my remote too.


Above all, Ubuntu is a great work, and evolves!! Thumbs up guys!!

---

### Post by diensthunds on 2009-05-01
The remote is the blue tooth remote isn't it? Have you checked to make sure that the blue tooth service is installed and up and running? If so does it work with other devices? Can you pair the laptop with a headset, etc.
Start there as a beginning, I'm looking into this system as a new laptop and would like to have the remote as an option.

---

### Post by kapad on 2009-09-20
even i face the same problem with my dell studio 15. everything works on vista...
the media controls on the panel work but sadly the remote doesn't work...
the remote is infrared and not bluetooth...
also i have noticed that the infrared receiver port is not installed in ubuntu, i.e. their are no working drivers for it.
in vista the remote uses the ITE CIR driver.
any help would be great

---

