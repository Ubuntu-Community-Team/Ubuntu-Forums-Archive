---
title: "Screen res"
date: 2006-06-21
forum: Multimedia &amp; Video
---

### Post by Coomkeen on 2006-06-21
Hi,
Please excuse a beginners questions but...
I've just tried to upgrade to 6.06, and it's limited to 1024 x 768 screen res.
I've gone back to 5 because it's got 1920 x 1200, my laptop screen size.
How come a new version has such limited screen resolutions over the old version?
Is there any way I can get 1920 x 1200 on Dapper?

Ron

---

### Post by Ptero-4 on 2006-06-21
copy your /etc/xorg.conf to your home folder while on breezy, then update to dapper and replace it's /etc/xorg.conf with the copy you have in your home folder. Also remember that if you use the non-free Nvidia/ATI drivers dapper probably reverts to vesa automatically and you'll need to reinstall the Nvidia/ATI drivers to get the full resolution/3D accel.

---

### Post by Coomkeen on 2006-06-21
[QUOTE=Ptero-4]copy your /etc/xorg.conf to your home folder while on breezy, then update to dapper and replace it's /etc/xorg.conf with the copy you have in your home folder. Also remember that if you use the non-free Nvidia/ATI drivers dapper probably reverts to vesa automatically and you'll need to reinstall the Nvidia/ATI drivers to get the full resolution/3D accel.[/QUOTE]

Many thanks for that.
I'll give it a go.

Ron

---

### Post by Coomkeen on 2006-06-22
Hi again.
Can't seem to find /etc/xorg.conf anywhere.
Is there a search facility in the file system?
Regards,
Ron

---

### Post by Valavien on 2006-06-22
To search:

Goto the Places menu on the panel up the top and then search for files

or goto the command line and

sudo gedit /etc/X11/xorg.conf

ok so as I type that up I realise why you can't find it.  it's in /etc/X11/xorg.conf

---

### Post by Coomkeen on 2006-06-22
Ah got it!
Thanks again.
Ron

---

### Post by Ptero-4 on 2006-06-23
[QUOTE=Coomkeen]Hi again.
Can't seem to find /etc/xorg.conf anywhere.
Is there a search facility in the file system?
Regards,
Ron[/QUOTE]

Oops, my wrong. I was on OSX at the moment and slipped up a bit, the path is /etc/X11/xorg.conf

---

