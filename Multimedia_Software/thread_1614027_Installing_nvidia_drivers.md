---
title: "Installing nvidia drivers"
date: 2010-11-05
forum: Multimedia Software
---

### Post by ltwinner on 2010-11-05
I go to Hardware Drivers and it searches for drivers and it finds NVIDIA accelerated graphics driver (version current) [Recommended].

However when I click Activate I get the following message -

SystemError: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-current_195.36.15-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-current_195.36.15-0ubuntu3_i386.deb) 404  Not Found [IP: 91.189.92.172 80]

I went to the dir it specified - [http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers/](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers/) - and I can see there is no /nvidia-current_195.36.15-0ubuntu3_i386.deb there, but there is a [nvidia-current_195.36.15-0ubuntu2_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-current_195.36.15-0ubuntu2_i386.deb")....so whats the deal here, are the repositories out of date or something?

---

### Post by drpjkurian on 2010-11-05
Hi
I think you can give a try for that package...

---

### Post by sikander3786 on 2010-11-05
Can you please post the output of

```
sudo apt-get update
```

from terminal.

Applications > Accessories > Terminal.


Edit: It is not only a problem with that nvidia package but with whole apt-get. This output will help us diagnose it better.

---

