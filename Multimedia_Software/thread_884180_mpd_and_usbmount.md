---
title: "mpd and usbmount"
date: 2008-08-08
forum: Multimedia Software
---

### Post by ve.ru on 2008-08-08
Hi,

I installed mpd and usbmount and both are working. I.E. mpd is playing music and when I plug in a USB stick it autmatically gets mounted in /media/usb0 (or /media/usb1 to 7) without any further interaction.

When I manually do mpc update after a USB stick is pluged in, the database is updated and I see the the music stored on that stick ncmpc. 

Now I'd like to get rid of the manual "mpc update", since mpd is running on a small home media server which normally should have no monitor attached.

How can I get mpd to update its database on plugging in a USB stick? Does usbmount provide a hook for a shell script? Is there anything better than usbmount?

---

