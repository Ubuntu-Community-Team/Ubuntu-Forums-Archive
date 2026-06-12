---
title: "Unable to run Feisty X800"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by k5cqb on 2007-04-12
I followed the instructions listed here to the T;

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) 

I have included the log in a text file, it was way too long to post.  It does recognize that the card is there and it is in the PCI-E slot.  I do have the restricted drivers manager activated.  Any ideas?

Thanks,
Jim

---

### Post by k5cqb on 2007-04-12
Oooops, too many cups of Ubuntu today!  Sorry I forgot to attach the log.  Here it is.  I had to zip it, it is 45kb and I was only allowed 19 for a text file.

---

### Post by k5cqb on 2007-04-17
OK, mark this one as resolved.  I restarted with just command lines.  I ran 

sudo dpkg -reconfigure xserver-xorg -phigh

I chose the ati driver and left the settings as they were and ran "starx".  It came up just fine.

---

