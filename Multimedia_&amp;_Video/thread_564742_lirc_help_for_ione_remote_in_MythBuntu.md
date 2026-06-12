---
title: "lirc help for ione remote in MythBuntu"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by dragoster on 2007-10-01
I have mythbuntu installed on a EagleTech EC2 case that comes with a USB ir receiver and a black Ione remote that I believe is a MCE remote. 

[http://www.newegg.com/Product/ShowImage.aspx?Image=11-117-048-02.jpg%2c11-117-048-03.jpg%2c11-117-048-04.jpg%2c11-117-048-05.jpg%2c11-117-048-06.jpg%2c11-117-048-07.jpg%2c11-117-048-08.jpg%2c11-117-048-09.jpg%2c11-117-048-10.jpg&S7ImageFlag=0&Depa=0&Description=Eagle+Tech+CA-EC2+Black+Computer+Case](http://www.newegg.com/Product/ShowImage.aspx?Image=11-117-048-02.jpg%2c11-117-048-03.jpg%2c11-117-048-04.jpg%2c11-117-048-05.jpg%2c11-117-048-06.jpg%2c11-117-048-07.jpg%2c11-117-048-08.jpg%2c11-117-048-09.jpg%2c11-117-048-10.jpg&S7ImageFlag=0&Depa=0&Description=Eagle+Tech+CA-EC2+Black+Computer+Case)

If I try to set up the remote using the MythBuntu Centre as a mceusb or mceusb2 remote I can get a few buttons to work (arrows, Escape, OK, numbers) but not all of them. I found some lircd.conf for the ione remote ( I suppose the same as the one I have) I tried both, replacing the lircd.conf in the /etc/lirc/ folder, but no success so far.

I also went on the manual route. I tried compiling lirc with my kernel sources, following the ubuntu lirc howto. I was never able to get irw to record any remote signals. In fact, irw crashes lircd, if I run lircd -n in a separate window. After typing lirc and return, there is no hang in the prompt. However, the buttons that work in mythtv (up, down, ok, escape) work and perform those functions in my terminal window (move cursor, copy line, enter numbers). I checked in dev and there is only a lircd device, no lirc or lirc0. 

I am a quasi-noob to linux and this remote problem is driving me crazy. I love mythtv but not being able to pause or skip or access the menu from the comfort of the couch is not very nice. 

If anyone has gotten this ione remote to work with ubuntu gutsy (mythbuntu), your help would be highly appreciated. 

Thanks,
-D

---

### Post by superm1 on 2007-10-01
> **dragoster said:**
> I have mythbuntu installed on a EagleTech EC2 case that comes with a USB ir receiver and a black Ione remote that I believe is a MCE remote. 

[http://www.newegg.com/Product/ShowImage.aspx?Image=11-117-048-02.jpg%2c11-117-048-03.jpg%2c11-117-048-04.jpg%2c11-117-048-05.jpg%2c11-117-048-06.jpg%2c11-117-048-07.jpg%2c11-117-048-08.jpg%2c11-117-048-09.jpg%2c11-117-048-10.jpg&S7ImageFlag=0&Depa=0&Description=Eagle+Tech+CA-EC2+Black+Computer+Case](http://www.newegg.com/Product/ShowImage.aspx?Image=11-117-048-02.jpg%2c11-117-048-03.jpg%2c11-117-048-04.jpg%2c11-117-048-05.jpg%2c11-117-048-06.jpg%2c11-117-048-07.jpg%2c11-117-048-08.jpg%2c11-117-048-09.jpg%2c11-117-048-10.jpg&S7ImageFlag=0&Depa=0&Description=Eagle+Tech+CA-EC2+Black+Computer+Case)

If I try to set up the remote using the MythBuntu Centre as a mceusb or mceusb2 remote I can get a few buttons to work (arrows, Escape, OK, numbers) but not all of them. I found some lircd.conf for the ione remote ( I suppose the same as the one I have) I tried both, replacing the lircd.conf in the /etc/lirc/ folder, but no success so far.

I also went on the manual route. I tried compiling lirc with my kernel sources, following the ubuntu lirc howto. I was never able to get irw to record any remote signals. In fact, irw crashes lircd, if I run lircd -n in a separate window. After typing lirc and return, there is no hang in the prompt. However, the buttons that work in mythtv (up, down, ok, escape) work and perform those functions in my terminal window (move cursor, copy line, enter numbers). I checked in dev and there is only a lircd device, no lirc or lirc0. 

I am a quasi-noob to linux and this remote problem is driving me crazy. I love mythtv but not being able to pause or skip or access the menu from the comfort of the couch is not very nice. 

If anyone has gotten this ione remote to work with ubuntu gutsy (mythbuntu), your help would be highly appreciated. 

Thanks,
-D

Okay first off:  Don't go compiling items.  It won't solve anything in your case, but only make them worse.

Undo anything you compiled.  If you've got a lircd.conf that is different than the standard mceusb2 lircd.conf, you can drop it in /etc/lirc.  Open the control centre for mythbuntu and check the box to regenerate application specific buttons.  You'll get a new ~/.lircrc and ~/.mythtv/lircrc that then use that remote.

Lastly: file a bug on launchpad to add your remote config to the lirc package.  We still have time before gutsy is released to get it in.  

If the problem is with your ~/.lircrc and ~/.mythtv/lircrc not working with all the buttons (but your lircd.conf is good), file a bug against mythbuntu-lirc-generator.

Either way post the appropriate files (lircd.conf or lircrc) and what they should be, and we can try to get this resolved before release.

---

### Post by dragoster on 2007-10-01
Thanks for the fast reply. I'll post the lircd.conf and lircrc when I get home. 

I guess my confusion is how do I know if the lircd.conf is good? Both irw and irrecord crash lircd so I really don't know what the codes for the other buttons on my remote are. 

Thanks again,
-D

---

### Post by superm1 on 2007-10-01
Are you sure this receiver is supposed to be using mceusb or mceusb2?  It's typically one or the other.  If it ends up your receiver isn't supported by either of them in their current state, then we can possibly pull a patch from lirc cvs for newer support for one of them (if its fixed upstream)

---

### Post by dragoster on 2007-10-08
Sorry for the late follow up. Crazy times at work = no time for MythTV

Apparently the ione remote is seen by Ubuntu as an IR mouse and keyboard combo. To make it work with lirc I have to redirect the mouse output to a new device and use the lirc_i2c to read that. I haven't gotten it to work yet, but here's a recent post that shows how to do it. 

[http://www.gossamer-threads.com/lists/mythtv/users/293732?do=post_view_flat#293732](http://www.gossamer-threads.com/lists/mythtv/users/293732?do=post_view_flat#293732)

I wonder if there is any easier way to do this, and if the install it can be  incorporated in MythCentre. If I get it to work I'll post what I did step by step so others can benefit from this case. 

D

---

### Post by superm1 on 2007-10-08
It's way to late in the development cycle for something automatic like this.  Once you've got it working, please post a spec on the mythbuntu project on launchpad.  We can target it for hardy.

---

