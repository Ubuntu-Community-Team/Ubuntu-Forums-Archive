---
title: "Install latest NVIDIA driver Ubuntu 10.04 amd64"
date: 2010-10-15
forum: Multimedia Software
---

### Post by Dragonbreath on 2010-10-15
I am using Ultimate-Edition 2.7-x64. I'm unable to install the latest NVIDIA driver (NVIDIA-Linux-x86_64-256.53.run) that I downloaded from NVIDIA website.
I tried the following:-
[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

---

### Post by cchhrriiss121212 on 2010-10-16
Could you explain more about what the problem is? Did you get an error message? etc.

---

### Post by Dragonbreath on 2010-10-16
> **cchhrriiss121212 said:**
> Could you explain more about what the problem is? Did you get an error message? etc.
 
First I got the error message that X.org server was running. I stopped it using the command
```
sudo /etc/init.d/gdm stop
```
After that, it gave the error that nouveau was interfering. I uninstalled it using Ubuntu Software Centre. Then, it gave the error that nouveau was still running.:(
When I checked, libdrm-nouveau1 package wasn't removed. When I tried removing it, my system gave an error message that it will remove a critical package "plymouth" and so cannot be removed.:mad:
I don't know what to do now.:confused:

---

### Post by cchhrriiss121212 on 2010-10-16
You can leave any lib packages there as they won't interfere. What you need to do is remove any other packages labeled nvidia.

---

### Post by Dragonbreath on 2010-10-17
> **cchhrriiss121212 said:**
> You can leave any lib packages there as they won't interfere. What you need to do is remove any other packages labeled nvidia.

I removed all packages labeled nvidia using the command
```
sudo apt-get remove nvidia-*
```

Can you be more specific about leaving lib packages?

---

### Post by cchhrriiss121212 on 2010-10-17
Open up synaptic package manager and search for nvidia, then remove anything you see. If you see that some lib packages are needed by something else then leave them.
I think you may need to reboot after removing nouveau. Then do these steps:
Press ctrl+alt+f1
Login
sudo service gdm stop
sudo sh ./yournvdiadriver.run
sudo service gdm start

---

### Post by Dragonbreath on 2010-10-18
> **cchhrriiss121212 said:**
> Open up synaptic package manager and search for nvidia, then remove anything you see. If you see that some lib packages are needed by something else then leave them.
I think you may need to reboot after removing nouveau. Then do these steps:
Press ctrl+alt+f1
Login
sudo service gdm stop
sudo sh ./yournvdiadriver.run
sudo service gdm start

I tried it. It didn't work. It gives an error saying that nouveau is still running.

---

