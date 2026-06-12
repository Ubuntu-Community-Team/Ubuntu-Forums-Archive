---
title: "resolution concern"
date: 2009-12-19
forum: Multimedia Software
---

### Post by windowsfree on 2009-12-19
I am using Ubuntu 9.10.  When PC is turned off and turned back on my resolution defaults to 800x600 instead of 1024x768.  See attached screenshot for error message when I change resolution and try to save the settings.  What can I do to correct this?
I would appreciate any guidance on this.  I tried googling and reading the forums.  I looked at my files-but not sure how to edit them correctly.
Thank you

---

### Post by Tricity on 2009-12-19
Hmmmm.... why do recent Ubuntu versions always cause problems with the video setup? All was fine while we still could hand-edit the xorg.conf file. 

Now, this is exactly your problem. The file /etc/X11/xorg.conf is missing. You can create one by using

$ sudo dpkg-reconfigure -phigh xserver-xorg

And just in case, I have attached a very generic xorg.conf file. It uses the "vesa" driver - this driver should work almost with every card, but does not use the capabilities, so you'll need to tweak it.

---

### Post by Tricity on 2009-12-19
OK, I was unable to upload the raw file - had to gzip it for the system to accept. HTH.

---

### Post by Woe_is_me on 2009-12-19
> **Tricity said:**
> OK, I was unable to upload the raw file - had to gzip it for the system to accept. HTH.


Hi im new to ubuntu, im not sure what to do with this file once its downloaded. I unzipped it and then just got baffled. 
Also then I try the above command nothing happens.

---

### Post by Tricity on 2009-12-19
> **Woe_is_me said:**
> Hi im new to ubuntu, im not sure what to do with this file once its downloaded. I unzipped it and then just got baffled. 
Also then I try the above command nothing happens.

OK, sorry :mrgreen:

The two options are (use a command-line shell to type, and don't include the $ symbol)

$ sudo dpkg-reconfigure -phigh xserver-xorg

Next, check if the file has been created:

$ ls /etc/X11

In the listing, there should be a file named xorg.conf. If not, use the one I provided. Assume you unzipped the file in your home directory, then type

$ cd
$ sudo cp -i xorg.conf /etc/X11/

Should an xorg.conf already exist (cp warns you, DON'T overwrite).

Then restart your X server.

---

### Post by windowsfree on 2009-12-20
thank you - I will attempt that resolution later today.  I appreciate your help

---

### Post by windowsfree on 2009-12-20
It blew out my X config altogether.  could only get a terminal login.
reloaded everything and guess what......no problems after fresh install!

---

### Post by windowsfree on 2009-12-21
So I do an update from update manager and now the same problem returns.  Software center says the correct nvidia driver is loaded.   What is the problem here?  The update had 175 updates to do, so I am not sure what screwed up the screen resolution.

---

