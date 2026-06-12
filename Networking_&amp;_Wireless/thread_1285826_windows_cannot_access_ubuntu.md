---
title: "windows cannot access ubuntu"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by enoughsaid05 on 2009-10-08
hi guys

I don't know if I should be writing this since there are plenty of posts with the same problem, but I can't just seem to be able to share files from my ubuntu machine using vista.

So basically what I have done is to follow what was stated in the youtube

[http://www.youtube.com/watch?v=89hjWOb8qmY](http://www.youtube.com/watch?v=89hjWOb8qmY)

i.e. click the folder, share options
enable sharing
download samba and install
change the /etc/samba/smb.conf file, just only WORKGROUP=WORKGROUP which is the one that my vista recognises.
restart the computer
then add some files to the folder that i want to share

but then on vista machine, it only recognises my ubuntu laptop, but it says "windows cannot access \\xxx " and asked me to check my network etc...

what should i do so that I can access files from ubuntu?

many thanks!~

---

### Post by kiridude on 2009-10-08
What format have you used for your "shared" folder?

---

### Post by enoughsaid05 on 2009-10-08
sorry but what do you mean by format?

---

### Post by kiridude on 2009-10-08
Sorry, wasn't paying attention that you were using Samba.

have a look at [this]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html#id2553786"). You should find the answers you need there.

This is another [page]("http://ubuntuforums.org/showthread.php?t=1169149") that should help you.

---

