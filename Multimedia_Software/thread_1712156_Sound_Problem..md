---
title: "Sound Problem."
date: 2011-03-22
forum: Multimedia Software
---

### Post by ankur.trapasiya on 2011-03-22
Hello..!! I am using ubuntu 10.10 and today my audio suddenly stopped playing properly. It is playing at a very low volume and when i try to open sound preferences then i am introduced to a dialog box which shows the message as follows "Waiting for sound system to respond.". After this the dialog box closes without showing any preferences options. Now how can i make my sound drivers as they were before ? .. 

What i have to do ? 
Thanks in advance for help.

---

### Post by lidex on 2011-03-22
Try powering down; leave it off for five minutes. Startup and use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by ankur.trapasiya on 2011-03-23
[http://www.alsa-project.org/db/?f=d329ce6e5c58f51f1c1d0a7b8bced158988e909f](http://www.alsa-project.org/db/?f=d329ce6e5c58f51f1c1d0a7b8bced158988e909f)

---

### Post by lidex on 2011-03-23
Did you disable pulse audio? It is not running.
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**

---

### Post by ankur.trapasiya on 2011-03-24
i have not disabled pulse audio...

when i run the commands you told.. i get something like this

root@ubuntu:~# rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
rm: cannot remove `/root/.asound*': No such file or directory
root@ubuntu:~# rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
rm: cannot remove `/root/.pulse': No such file or directory
rm: cannot remove `/root/.asound*': No such file or directory
rm: cannot remove `/root/.pulse-cookie': No such file or directory
root@ubuntu:~# sudo rm /etc/asound.conf
rm: cannot remove `/etc/asound.conf': No such file or directory
root@ubuntu:~# rm /etc/asound.conf
rm: cannot remove `/etc/asound.conf': No such file or directory

---

### Post by lidex on 2011-03-24
You're running as root. Do you always do that or do you have a user account?

---

