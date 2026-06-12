---
title: "Nvidia-driver doesn't work after correct installation"
date: 2006-11-16
forum: Multimedia &amp; Video
---

### Post by Ledah on 2006-11-16
Hi,

after a new installation of Dapper, I installed the nvidia-driver out of the reository. The driver worked fine and still worked after a restart of the X-Server and a reboot of my computer. The next day, I started my computer, but after the splashscreen, the X-Server did not start. The monitor showed a black screen and after 20 - 30 seconds it showed a white screen. I can't change to a text console or do anything.
I tried other drivers, reinstalled the driver, but nothing helped. The X-Server does not start with the nvidia-driver a second time.
I had the same Problem with Edgy. It was new installed and the installation of the driver and the restart of the X-Server with 3D-Acceleration worked fine, but when I bootet the computer the next day, the X-Server did not start a second time with the nvidia-driver.

I have a Geforce4 Ti 4200 8x. The mainboard is an ASUS K8V-X SE with the Via K8T800 Chipset.

Have anyone an idea, what is the problem?

---

### Post by tseliot on 2006-11-16
boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "nv" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vesa" instead of "nv" and try again.


[B]
THEN, if you want, we can try to diagnose the error:[/B]

Boot with the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
```
sudo /etc/init.d/gdm restart (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm restart (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by Ledah on 2006-11-16
After ```
startx -- -verbose 5 -logverbose 5
```the X-Server tries to start and I get a black screen again. The input of Ctrl + Alt F1 or Ctrl + C effects nothing.
I think the Xorg.0.log is overwritten after a reboot in recovery mode, isn't it?

---

### Post by Ledah on 2006-11-17
If I set the Option "NvAGP" "0", the driver works, but the Desktop is extremely slow and the 3D-Acceleration is worse.

---

### Post by Ledah on 2006-11-18
Any new ideas?

---

### Post by tseliot on 2006-11-18
> **Ledah said:**
> If I set the Option "NvAGP" "0", the driver works, but the Desktop is extremely slow and the 3D-Acceleration is worse.

That's because AGP is disabled.

you can try with:
```
Option "NvAGP" "1"
```

---

### Post by Ledah on 2006-11-19
The result of this option is unfortunately the black screen.

I tried to boot Windows before I boot Kubuntu with the nvidia driver and the driver worked fine. This is the same situation, which  I had with my Ati Card before (I had to boot Windows, then Kubuntu and then I got 3D-Accelaration).

Weird ...

---

