---
title: "Nvidia 8500gt video on ubuntu 8.04"
date: 2008-09-03
forum: Multimedia Software
---

### Post by emco83 on 2008-09-03
i have this graphic card.i've tried with restricted drivers,but i've noticed that when i play some movie,the quality is not so good and there is tearing.i have settings on nvidia and i set the highest quality but without great result.i saw that restricted drivers are quite old.169.now there is 173 version but i dont know how to install from official site NVIDIA.then i tried with envy and the same problem. tearing is still there.
On windows i don't have this problem.the video is very smooth there.pls someone help
i'm a big fan of ubuntu,i like it so much.it has a lot off better things that windows

---

### Post by falcon61102 on 2008-09-03
You could either try installing the drivers from the website, following their directions or you could use Emvyng which, if I remember correctly, is using 171 or 172.  While they are not the newest available they are considered a very stable version of the drivers.  You can install Envy either through Synaptic or by running the following in your termina:
```
sudo apt-get install envyng-gtk
```

Then run it by typing:
```
gksudo envyng-gtk
```

---

### Post by Bucky Ball on 2008-09-03
How about:

**sudo apt-get install nvidia-new-glx**

or

**sudo apt-get update nvidia-new-glx**

in the terminal. Falcon61102 might be able to advise on the validity and effectiveness of this, but it worked for me when I was having a few probs.

The other thing I did to update the drivers last time was, in System->Administration->Hardware Drivers, I found the nvidia driver was installed and ticked but not in use. I unticked it, closed, opened and ticked it again and it downloaded the *new* driver and set it in use for me.  :)

---

### Post by falcon61102 on 2008-09-03
Yeah, those are supposed to be very reliable as well.  Try one and if it doesn't work, uninstall them and try the others.  If both don't work then it may not be the drivers causing you the issue but something else instead.

---

### Post by emco83 on 2008-09-03
thanks very much.i'll try tonight and i'll let you know:)

---

### Post by emco83 on 2008-09-03
i've tested and its better now.thank you guys.god bless you

---

### Post by falcon61102 on 2008-09-03
No problem.  Glad it worked.

---

### Post by Bucky Ball on 2008-09-04
Cool, glad to be of help. :)

---

### Post by dorame on 2008-09-04
Thank.I think i'd better do so.

---

### Post by Ux64 on 2008-12-08
> **emco83 said:**
> i've tested and its better now.thank you guys.god bless you

Better? I'm curious if you completely got rid of tearing, or is it just better.

Because I suffer from same problem. Picture is very nice, but there is still some tearing. It's not too annoying when you'll get used to it.

I haven't been able to get rid of it even I have been working hard to fix it. I don't know anyone who would say that 8500gt works without tearing. (When using linux and VLC)

---

