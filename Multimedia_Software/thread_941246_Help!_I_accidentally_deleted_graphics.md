---
title: "Help! I accidentally deleted graphics"
date: 2008-10-07
forum: Multimedia Software
---

### Post by Archanjil on 2008-10-07
Hello, I am running ubuntu 7.04 feisty and I attempted to update my nvidia package, and I ended up doing this. However, afterwards my beryl manager stopped working, so I decided to temporarily delete it and go back to what I had before

It turns out that I deleted the wrong nvidia package accidentally, and now my computer starts in a sort of ms-dos (or terminal mode) and I can't see graphics.

I typed in commands in this menu attempting to get my computer back to normal, however, then I get authentification errors. 

More specifically: sudo apt-get install nvidia-glx linux-restricted-modules-generic 

Then I would recieve an error message saying: WARNING: The following packages cannot be authenticated!

Afterwards I try to install without verification and it doesnt work.

Any help would be GREATLY appreciated. 

Thanks in advance!

---

### Post by minky311 on 2008-10-07
Try
```
startx
```

---

### Post by Nasaki on 2008-10-07
if startx doesn't work (which it should) you can always try 

"sudo apt-get --reinstall install nvidia-glx linux-restricted-modules-generic"

---

### Post by Archanjil on 2008-10-07
I tried startx with and without sudo. 

It said: Fatal server error: no screens found
XIO: fatal IO error 104 (connection reset by peer) on X server ":0:0" after 0 requests (0 known processed) with 0 events remaining.

---

### Post by Archanjil on 2008-10-07
> **Nasaki said:**
> if startx doesn't work (which it should) you can always try 

"sudo apt-get --reinstall install nvidia-glx linux-restricted-modules-generic"



I just typed that In and i got:

Warning: The following packages cannot be authenticated! 
nvidia-kernel-common linux restricted-modules-2.620-15-386
linux-restricted-modules-2.6.20-17-generic linux-restricted-modules-generic nvidia-glx

After I try to install them without verification, I get the message:

Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by Archanjil on 2008-10-08
Any other help would be greatly appreciated.

---

### Post by Archanjil on 2008-10-08
To be more specific, I deleted the packages in Synaptic. I think if I could get past authentication errors, for installing packages like nvidia-glx, etc it would be alright.

---

### Post by hessiess on 2008-10-08
if possable, can you post /etc/X11/xorg.conf

```
nano /etc/X11/xorg.conf
```

---

### Post by Archanjil on 2008-10-08
> **hessiess said:**
> if possable, can you post /etc/X11/xorg.conf

```
nano /etc/X11/xorg.conf
```

I can't post it because I am on another computer, unless there is a way I can copy paste and send in terminal? If you would like I could type out a section of it.

---

