---
title: "cannot detect camcorder!"
date: 2010-02-21
forum: Multimedia Software
---

### Post by raniaman on 2010-02-21
hello.
I've got a Panasonic NV-GS17 mini DV camcorder which I have connected onto my computer with firewire. I am running Ubuntu v.9.10 and via Kino I am trying to import the raw video from my camcorder onto my computer. However, the problem is that Ubuntu does not detect my camcorder and Kino gives the error "WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394"

I have already attempted to type in the code: sudo***[SIZE=1][COLOR=Black] [/COLOR][/SIZE]***[SIZE=1][COLOR=Black][SIZE=1]chmod o+rw/dev/raw1394 and generaly I have followed the advice from the following site: [http://iamnotageek.blogspot.com/2009/05/getting-firewire-camcorder-working-in.html](http://iamnotageek.blogspot.com/2009/05/getting-firewire-camcorder-working-in.html)

nevertheless the attempt is unsuccesful and Ubuntu still does not recognise my camcorder and instead receive the error: "chmod: cannot access `/dev/raw1394': No such file or directory."

Can you help?

As I am novice with Linux, I would appreciate to receive as much detailed response as possible. 

Thank you in advance.
[/SIZE][/COLOR][/SIZE][B][I][SIZE=1][COLOR=Black] [/COLOR][/SIZE]
[/I][/B]

---

### Post by Algenon on 2010-02-21
ranaiman,

I have a similar problem with firewire.  I added raw1394, dv1394 and video1394 to my /etc/modules file, but I get the message:"Error :No Camera Exists" when using dvgrag /dev/raw1394 or dvgrab /dev/video1394 or dvgrab /dev/dv1394.

---

### Post by Algenon on 2010-02-22
Got this working after a lot of fiddling.  Not quite sure what made it work but I did this:

1. commented out firewire-ohci (using #) in /etc/modprobe.d/blacklist-firewire.conf

and also

2. re-compiled dvgrab using:
apt-get build-dep dvgrab.

dvgrab now works!

Regards,

algenon.

---

