---
title: "How to manually install 3D driver from Nvidia"
date: 2009-04-02
forum: Multimedia Software
---

### Post by Firidan on 2009-04-02
After a fresh Kubuntu x64 installation I tried to install Nvidia driver. I went to Nvidia homepage and downloaded the driver. Then I ran the following command: sudo sh NVIDIA-Linux-x86_64-180.44-pkg2.run. But the driver started to complain about something (I think about a compiler). How do I install Nvidia driver?

P.S. I couldn't install the driver on Fedora 10 KDE and Mandriva 2009 KDE(Why can't KDE automaticlly download the driver like in Ubuntu(gnome)).

---

### Post by cariboo on 2009-04-02
Have you tried installing Synaptic and then just installing the drivers from there? Just open synaptic and seach for:

```
nvidia-glx-180
```

If you do it through synaptic, you get all the dependencies install automatically. If you install the Nvidia driver you have to install the dependencies seperately. Here is a quick howto:

[list=1]
[*] Install build-essentials:

```
sudo apt-get install build-essential
```

[*] Go to a console:

```
Ctrl-Alt-F1
```

[*] Stop gdm

```
sudo /etc/init.d/gdm stop
```

[*]Make the file executeable:

```
sudo chmod +x /path/to/NVIDIA-Linux-x86_64-180.44-pkg2.run
```

[*] Run the file:

```
sudo /path/to/NVIDIA-Linux-x86_64-180.44-pkg2.run
```

if you are in the same directory as the file:

```
sudo ./*run
```

this assume you don't have any other file with a .run extension in the directory.

[*] Answer yes to all the questions

[*]Restart gdm:

```
sudo /etc/init.d/gdm start
```

After starting gdm you shouild boot to your desktop if you have done everything right

[/list]

Jim

---

### Post by inobe on 2009-04-02
jim wouldn't a kernel update bork the nvidia install using that method ? :)

i would suggest checking hardware drivers to see if they are not already there.

if not

you can get the source added to adept to get the latest nvidia drivers.

[http://www.avenard.org/files/ubuntu-repos/](http://www.avenard.org/files/ubuntu-repos/)

the site

[http://www.avenard.org/media/Home.html](http://www.avenard.org/media/Home.html)

going into adept searching nvidia and adding the 180 modealias should do it, simply reboot and look in hardware drivers, you should then see 180 driver, activate it.

encase they decide to patch the linux kernel you wont need to purge the driver and reinstall.

i am also running kubuntu x64bit

[IMG]http://www.itsyourpc.org/duane/files/nvidia_180_44.jpg[/IMG]

---

### Post by inobe on 2009-04-02
heres a more definitive way [http://ubuntuforums.org/showpost.php?p=6978054&postcount=3](http://ubuntuforums.org/showpost.php?p=6978054&postcount=3)

---

