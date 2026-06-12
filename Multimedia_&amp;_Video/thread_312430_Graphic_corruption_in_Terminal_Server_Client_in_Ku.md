---
title: "Graphic corruption in Terminal Server Client in Kubuntu Edgy Eft"
date: 2006-12-04
forum: Multimedia &amp; Video
---

### Post by bnortham on 2006-12-04
Hello, since my Kubuntu upgrade to 6.10 from Dapper, I've been having screen corruption issues when logged into a Windows machine using Terminal Server Client. Whenever I drag a window or scroll up (scrolling down doesn't seem to do it), the window graphics repeat and the screen image become garbled.

Here's a screenshot:
[IMG]http://www.brentnortham.com/images/Screenshot.png[/IMG]

I'm using an NVidia GeForce4 MX 440 with AGP8X with an nvidia driver (1.0-8776).  I don't think this changed when I upgraded to 6.10, but the Terminal Server Client problem did happen directly as a result of the upgrade, so it seemed.  Any ideas out there?  Any more information I can give?

Best,
Brent

---

### Post by mishranurag on 2006-12-04
I had same problem with Edgy Eft and that's why I downgraded to 6.06.

---

### Post by bnortham on 2006-12-06
Anyone have a suggestion other than downgrading?

---

### Post by yolfer on 2006-12-28
Did anyone ever figure this out?  I have the same problem.  Thanks.

---

### Post by speedman on 2006-12-28
Instead of using tsclient call rdesktop directly from a script like the following:

=====

#!/bin/bash

export XLIB_SKIP_ARGB_VISUALS=1

rdesktop -g 1280x1024 -n your_tscal_name 10.123.0.20

=====

The export line will fix your problem, which is related to the nvidia driver in edgy.

HTH


SM

---

### Post by yolfer on 2006-12-28
Yes, that worked.  Thank you speedman!

BTW, I updated the script slightly, here's what I used:

> rdesktop -g 1280x960 -a 16 -n your_tscal_name 10.123.0.20

That will use 16-bit color depth, and a display size of 1280x960

---

### Post by speedman on 2006-12-28
Cool - glad to hear it fixed your problem.

I have a 1920x1200 display on my laptop hence me using 1280x1024 for rdp.  And, we only have a Windows 2000 terminal server in the office, which will only do 256 colors over rdp unlike 2k3, which will work with your modified setting.  Unfortunately our erp app won't run on 2k3, so we are stuck with our old 2k terminal server.


SM

---

### Post by mishranurag on 2007-01-01
Is there a simpler, one click solution?

---

### Post by flickerfly on 2007-01-09
What would I lose by simply putting ```
export XLIB_SKIP_ARGB_VISUALS=1
``` in my ~/.bashrc file? That would render the same results wouldn't it?

---

### Post by flickerfly on 2007-01-09
I went ahead and created a bug for this if anyone wants to follow it . . .

[https://bugs.launchpad.net/ubuntu/+bug/78571](https://bugs.launchpad.net/ubuntu/+bug/78571)

---

### Post by changhua on 2007-02-20
Actually, you don't need to call the rdesktop client directly.

You can also write a script that first performs the export, then calls the client appropriate to your desktop.  For example, I use gnome so I put the following script in /usr/local/bin

export XLIB_SKIP_ARGB_VISUALS=1
tsclient

I then copied the menu item into a launcher on my panel, and changed the launcher to use that script.


Thanks to everyone above for finally making this problem go away for me.

---

### Post by mishranurag on 2007-02-20
Could you please give me a step by step instruction of how you did it?
Thanks

---

