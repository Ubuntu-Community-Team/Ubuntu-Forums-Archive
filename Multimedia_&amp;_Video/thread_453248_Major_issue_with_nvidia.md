---
title: "Major issue with nvidia"
date: 2007-05-24
forum: Multimedia &amp; Video
---

### Post by Ben James on 2007-05-24
Using umbuntu i installed a nividia driver accellerator, now my system has gone realy mucked up, it sais that the x server failed to start (your graphical interface),  

i view the x server detials output and i noticed that it sais failed to load nvidia kernal module, so it must be something to do with the driver i installed as everything was woking fine untill that time.

i now only have access to the shell! is there anyone that could help me get my system back the way it was 30mins ago without restarting.

help would be appretiated.

Thanks

Ben

---

### Post by EndPerform on 2007-05-24
My first question would be:

How did you install the driver?  Did you use something in the repository, or did you download it from Nvidia?

If nothing else, try:

```
sudo modprobe nvidia
```

which should load the nvidia module for the kernel if it's been built correctly.  If it gives you an error, then something is up.  Additionally, you could go into your /etc/X11/xorg.conf and change the driver from 'nvidia' to 'nv' and see if X comes back up that way.

---

### Post by Ben James on 2007-05-24
I installed the driver from some thing in the administrative section in ubumtu (i guess soemthing inb the repository) 

i tried that command and i got the error "fatal: error running install command for nvidia"

---

### Post by scrooge_74 on 2007-05-24
Check this site [http://albertomilone.com/latestrepo.html](http://albertomilone.com/latestrepo.html)

For the time beeing reconfigure your xserver so it uses the open source nvidia driver.

You can do it manually as EndPerform says.

Also you can type sudo dpkg-reconfigure xserver-xorg and use the nv driver

---

### Post by EndPerform on 2007-05-24
Hmmm...  do you remember which package specifically you installed?  Something doesn't make sense.

---

### Post by Ben James on 2007-05-24
how do i reset my installation to use the open source nivida do dar? i no how to get to specific directorys with the cd command, but i do not no how to edit files.

Thanks

Ben

---

### Post by Ben James on 2007-05-24
dont worry about telling me how to edit files as i found help on google, but just tell me what i need to do, thx

---

### Post by Ben James on 2007-05-24
Ha i changed the driver yipeeeeeee it works, thanks a bundle!!


luv u guys


Ben

---

