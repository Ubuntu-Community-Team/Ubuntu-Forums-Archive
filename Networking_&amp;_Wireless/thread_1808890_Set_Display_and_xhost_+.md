---
title: "Set Display and xhost +"
date: 2011-07-20
forum: Networking &amp; Wireless
---

### Post by OBI_Ron on 2011-07-20
Hello Everyone,

I have configured an instance in AWS EC2.  I am trying to set the display back so I can run x apps.

I login using ssh -xy -i...
export DISPLAY=XXX.XXX.X.XXX:0.0
echo $DISPLAY to verify
xhost +
xhost:  unable to open display "XXX.XXX.X.XXX:0.0"

I have commented out nolisten tcp as suggested [HERE]("http://davesource.com/Solutions/20070912.Ubuntu-xhost.html")

I have modified /etc/gdm/custom.conf as suggested [HERE]("http://tonymcneil.wordpress.com/2008/07/23/x-tunnelling-xhost-unable-to-open-display/")

Actually, the last suggested modifying /etc/gdm/gdm.conf, but that file didn't exist, so I added the line:
DisallowTCP=false
to /etc/gdm/custom.conf

I rebooted, and still I get:

xhost:  unable to open display "XXX.XXX.X.XXX:0.0"

So, what am I missing?

Thanks in advance!!

---

### Post by SeijiSensei on 2011-07-22
You run xhost on the local machine, not the remote host.  It grants the remote machine the privilege of writing to your screen. I don't recall needing that with ssh -X, but it's been a while since I've done this.

---

### Post by OBI_Ron on 2011-07-23
SeijiSensei,

Thank you - it has been a long while since I have done this as well, and completely forgot the order of things.  Actually, after more reading, it appears as though ssh -X is the better way, and when set up correctly doesn't require the DISPLAY variable to be set.

Thanks again!

---

