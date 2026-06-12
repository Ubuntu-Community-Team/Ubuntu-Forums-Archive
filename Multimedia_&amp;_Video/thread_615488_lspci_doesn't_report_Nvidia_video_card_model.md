---
title: "lspci doesn't report Nvidia video card model"
date: 2007-11-17
forum: Multimedia &amp; Video
---

### Post by GoJa on 2007-11-17
I found these instructions in one of the threads:

 > Originally Posted by carlinuxlearner  View Post
2.2
In a terminal window type "lspci | grep VGA" find the part that has these around it "[ ]", write down what it says then go here
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)
If the name of your graphics card is in the list (such as "Geforce 6800") then download this driver to your Desktop
[http://us.download.nvidia.com/XFree8...14.19-pkg1.run](http://us.download.nvidia.com/XFree8...14.19-pkg1.run)
(if that link is old go to this page to get driver)
[http://www.nvidia.com/object/linux_d...100.14.19.html](http://www.nvidia.com/object/linux_d...100.14.19.html)
(if that link is old, go here and select the driver that starts with "100")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html).


(EXAMPLE

"carl@carlubuntu1:~$ lspci | grep VGA
01:0b.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
carl@carlubuntu1:~$"

The "GeForce4 MX 420" is the name you are looking for. So "GeForce4 MX 420" is what I would look for on the list here.



But when I run the lspci command I get
> 01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0423 (rev a1)
It's a new machine sold as having a Nvidia GeForce 8300GS. Any idea why lspci doesn't report this?

Also I've looked in various lists for both the model (8300) and pci ID (0423) and haven't found it, any ideas?

---

### Post by Yellow Pasque on 2007-11-17
Try:
```
sudo update-pciids
```
..and then run your lspci command.

---

### Post by GoJa on 2007-11-17
The command below is the magic incantation.  Thanks for the help.  Now lspci properly reports my nVidia card.


> **Temüjin said:**
> Try:
```
sudo update-pciids
```
..and then run your lspci command.

---

