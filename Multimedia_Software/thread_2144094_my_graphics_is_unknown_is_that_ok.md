---
title: "my graphics is unknown is that ok?"
date: 2013-05-11
forum: Multimedia Software
---

### Post by nsync on 2013-05-11
My graphics are unknown is that okay to ignore? if not? where can i download a free graphic driver for Ubuntu? im currently using ubuntu 12.04 LT

---

### Post by coldraven on 2013-05-11
If your card is an AMD/ATI then this is probably the answer. I had the same problem and it worked for me, it does not change anything but just correctly identifies your card.
You can see all your hardware with the lshw command like this, you need to type your password but you won't see it displayed.
```
sudo lshw
```


And this solves the problem
```
sudo apt-get install mesa-utils
```

---

### Post by nsync on 2013-05-11
should i also enter 

sudo lshw

even if my card is intel ? thanks by the way :D

---

### Post by QIII on 2013-05-11
*Moved to  **Multimedia & Video***


Hello!

If you are sure your graphics controller is and intel unit, there is no need to bother any further.

The Intel graphics driver is already contained in the kernel and you are using it now.  That is why you are not discovering an additional driver.

But just to be sure, run lshw and look for a line something like this

```
VGA compatible controller
```

Just below that you should fine some information that will describe your controller.  If it's Intel, you're good.  If you see more than one, and one of the others is not Intel, you may have a hybrid system that could be problematic.

Best wishes!

---

### Post by coldraven on 2013-05-11
> **nsync said:**
> should i also enter 

sudo lshw

even if my card is intel ? thanks by the way :D


The lshw command just lists your hardware on any computer.
It's quite a long list so make the terminal screen big and then you can scroll up.

Another way is to send the results into a text file so that you can always refer to it. Also scrolling in a text editor is easy and you can use "Find" to go to the bit that you're interested in.

This creates a text file called hardware.txt in your home folder. You can of course name it anything you like.
```
sudo lshw > hardware.txt
```

Then find the file and just double click it.

If your card is Intel then ignore the mesa-utils part of my first post.

---

### Post by Yellow Pasque on 2013-05-12
> **coldraven said:**
> If your card is Intel then ignore the mesa-utils part of my first post.

Intel cards will also be listed as 'Unknown' until user installs mesa-utils: [https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)

---

