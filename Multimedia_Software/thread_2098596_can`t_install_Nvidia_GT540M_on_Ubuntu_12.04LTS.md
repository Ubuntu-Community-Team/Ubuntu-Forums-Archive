---
title: "can`t install Nvidia GT540M on Ubuntu 12.04LTS"
date: 2012-12-27
forum: Multimedia Software
---

### Post by Mortu911 on 2012-12-27
Hi,

I have a Nvidia GT540M graphic card and i just can`t install it on my ubuntu 12.04LTS (32-bit)
If i enter in Additional Drivers i have nothing there, it just says NO proprietary Drivers are in use. 
Although I have managed to install Nvidia X-servers but when i try to run it it says

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

Up now i have tried as it said using:

sudo nvidia-xconfig
sudo service lightdm restart

but still nothing

Can you help me please?

---

### Post by Mortu911 on 2012-12-27
I managed to install nvidia-current from ppa:ubuntu-x-swat/x-updates and now i have at aditional drivers more to chose from.
It says that this driver, nvidia-current is active but not in USE

print:

[IMG]http://img801.imageshack.us/img801/474/screenshotfrom201212271.png[/IMG]

---

### Post by Yellow Pasque on 2012-12-27
What does this command return?
```
lspci | grep -i vga
```
If it returns both an intel and nvidia adapter, then you have a hybrid/Optimus graphics setup. In that case, you would need to purge the nvidia driver, and follow the instructions here: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by Mortu911 on 2012-12-27
yes, 2 of them
i will install bumblebee

thx, very helpful!

---

