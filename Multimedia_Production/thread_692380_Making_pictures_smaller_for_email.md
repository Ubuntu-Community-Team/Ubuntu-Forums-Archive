---
title: "Making pictures smaller for email"
date: 2008-02-09
forum: Multimedia Production
---

### Post by Charles2008 on 2008-02-09
I recently purchased a digital camera and was having trouble making the pictures smaller than 1.6 MB in Ubuntu 7.1.  Any suggestions so I don't have to use windows to email out pictures?



Thanks in advance,

---

### Post by zero-9376 on 2008-02-09
install the package nautilus image converter which will give you a right click option to resize the selected images so they are more suitable for email.

---

### Post by Charles2008 on 2008-02-10
I installed the nautilus package but when I right click I dont get that option.  Am I doing something wrong?


Thanks,


Charles

---

### Post by xarquid on 2008-02-10
> **Charles2008 said:**
> I installed the nautilus package but when I right click I dont get that option.  Am I doing something wrong?


Thanks,


Charles

Greetings Charles,

On your command line of your favorite terminal simply type:

> sudo apt-get install nautilus-image-converter

This will install the nautilus converter.

Then on the command line run the command:

> nautilus -q

To restart nautilus in your x/gnome session.

You should now have the image conversion option when you right click.

Cheers,

Craig Huffstetler / xq / xarquid
Ubuntu Team SC Leader
#ubuntu-us-sc on Freenode
"On Carolinian at a Time..."

---

### Post by Charles2008 on 2008-02-10
Thanks,

works wonderfully now.


Charles

---

### Post by xarquid on 2008-02-10
Glad to help :)

---

