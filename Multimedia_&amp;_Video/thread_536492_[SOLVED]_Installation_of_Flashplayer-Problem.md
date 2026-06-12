---
title: "[SOLVED] Installation of Flashplayer-Problem"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by Metaljaz on 2007-08-27
I was installing flashplugin- nonfree using the terminal and typing this command:

sudo apt-get install flashplugin-nonfree

During the download process it was somehow interrupted. Now when i try to continue the install i get the following error message:
dpkg was interrupted, you must manually run 'dpkg  --configure -a'  to correct the problem

I am not sure what i am suppose to type at this point.  I have even tried to install from adobe's website and it just searches for the download.

Help

---

### Post by hooplah on 2007-08-27
Hey, I don't know why you may be experiencing this issue, but I have a simple workaround. When you're in firefox, go to a site that has flash animations, flash games, etc. Example, is [http://www.newgrounds.com](http://www.newgrounds.com) , Now ... when you see the area where the animation SHOULD be, what you do, is click it [Puzzle Piece]. Firefox will find the missing plugins, and it will allow you to install. I'm not sure if you've tried this method or not, just trying to give another option.

Regards, 
Max

---

### Post by -SpaZ on 2007-08-27
> **hooplah said:**
> Hey, I don't know why you may be experiencing this issue, but I have a simple workaround. When you're in firefox, go to a site that has flash animations, flash games, etc. Example, is [http://www.newgrounds.com](http://www.newgrounds.com) , Now ... when you see the area where the animation SHOULD be, what you do, is click it [Puzzle Piece]. Firefox will find the missing plugins, and it will allow you to install. I'm not sure if you've tried this method or not, just trying to give another option.

Regards, 
Max

As far as I now, I think that works with Java and such also.  If you use Firefox as your browser this is probably the way to go.

I however use Opera as my browser, and I just used [EasyUbuntu]("http://easyubuntu.freecontrib.org/").

---

### Post by hooplah on 2007-08-27
Actually, Java doesn't work. Firefox cannot automatically install Java, only with flash and other various multimedia codecs.

---

### Post by -SpaZ on 2007-08-27
> **hooplah said:**
> Actually, Java doesn't work. Firefox cannot automatically install Java, only with flash and other various multimedia codecs.

Thanks for clarifying, I wasn't sure.  By the way, do you know if EasyUbuntu works with Firefox?  (I think so.)

---

### Post by hooplah on 2007-08-27
I really have no idea. I've never tried.

---

### Post by -SpaZ on 2007-08-27
> **hooplah said:**
> I really have no idea. I've never tried.

I think it does since it installs Java, Flash, and video for the whole system.

---

### Post by hooplah on 2007-08-27
Actually, I've never heard of the program you mentioned. 
Can you please link me to a download of some sort? Or can I obtain it through synaptic.

Regards,
Max

---

### Post by -SpaZ on 2007-08-27
> **hooplah said:**
> Actually, I've never heard of the program you mentioned. 
Can you please link me to a download of some sort? Or can I obtain it through synaptic.

Regards,
Max

Here you go: [EasyUbuntu download instructions]("http://easyubuntu.freecontrib.org/get.html").

---

### Post by hooplah on 2007-08-27
Thank you very much for the link, installing it right now.

---

### Post by Metaljaz on 2007-08-27
Thanks for the replies. I got it working again by typing this command:

sudo dpkg --configure -a

I forgot to put sudo in front of the command.

---

### Post by -SpaZ on 2007-08-27
> **hooplah said:**
> Thank you very much for the link, installing it right now.

You're welcome.  Feel free to tell me if you have any problems or questions.

---

