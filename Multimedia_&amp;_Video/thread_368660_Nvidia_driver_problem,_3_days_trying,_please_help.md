---
title: "Nvidia driver problem, 3 days trying, please help"
date: 2007-02-23
forum: Multimedia &amp; Video
---

### Post by MgNate on 2007-02-23
I've been trying to install the nvidia driver for the past 3 day now and I havent had any luck.

Envy doesn't work and easyubuntu doesn't work and automatix doesn't work. I even tryed the binary install of course.

I've heard there's a way to change the "nv" to "nvidia" in the source code i guess?

Can someone tell me how to do this please?

I really don't want to go back to wondows but i'm getting pretty close to going for it.

---

### Post by mr_mop on 2007-02-23
[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

---

### Post by r4ik on 2007-02-23
Try,

sudo gedit /etc/X11/xorg.conf

Change "nv" to "nvidia" (without the ")

Save the file.

---

### Post by MgNate on 2007-02-23
Well i changed it and yet again, no luck. I'm getting really frustrated...

Did the method work for you R4?

Anyone else have any idea? Please, anything I'm begging...

Also, i have edgy...

---

### Post by MgNate on 2007-02-23
Also, i was thinking and if i reinstalled linux to dapper and then upgraded after i installed the driver would iit help?

---

### Post by r4ik on 2007-02-23
> **MgNate said:**
> Well i changed it and yet again, no luck. I'm getting really frustrated...

Did the method work for you R4?

Anyone else have any idea? Please, anything I'm begging...

Also, i have edgy...

Please try,

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

Don't forget to enable extra repo's

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

Good luck !

---

### Post by tommcd on 2007-02-23
Are you on Dapper or Edgy? What nvidia card do you have? Unless it is a very new model you can probably do just fine with the nvidia-glx driver from the synaptic repositories. Just follow "method1" for dapper:
[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)
or edgy:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Make sure the driver from nvidia's website is completely removed first. DO NOT have both drivers installed together. Instructions for removing the nvidia driver are on the links I gave (under method2). To install the driver from the repos:
Do <uname -r> to get your kernel version.
If kernel is linux-generic do <sudo apt-get install linux-generic> (or linux-386 if on 386 kernel)
Then <sudo apt-get install nvidia-glx> to install
Then <sudo nvidia-xconfig> to set it up.
Then <gksudo gedit /etc/X11/xorg.conf> To edit the file, comment out (put a # in front of) "load dri" and "load GLcore" if present and change driver name from "nv" to "nvidia".
Hope this helps.
EDITED to fix mistake.

---

### Post by MgNate on 2007-02-23
Well i deleted my edgy and i reinstalled dapper and it worked! 

Now I'm just wondering if i upgrade will it still work or no?

---

### Post by r4ik on 2007-02-23
> **MgNate said:**
> Well i deleted my edgy and i reinstalled dapper and it worked! 

Now I'm just wondering if i upgrade will it still work or no?

Would not bet my life on it.
If there is nothing in edgy you absolutely want i would leave it as is.
But it would not be the first time i was wrong....

---

### Post by MgNate on 2007-02-24
Well i upgraded to edgy and it stopped working! 

What a pain!

I guess I'll jusr reinstall Dapper... 

Is there anything special in Edgy?

What bothers me is what's so different about my computer that makes it not work?

By the way, thanks for all of your help R4ik!

---

### Post by r4ik on 2007-02-24
My pleasure.

---

