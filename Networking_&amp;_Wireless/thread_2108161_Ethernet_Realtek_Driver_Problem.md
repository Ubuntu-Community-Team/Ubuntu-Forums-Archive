---
title: "Ethernet Realtek Driver Problem"
date: 2013-01-23
forum: Networking &amp; Wireless
---

### Post by dharr118 on 2013-01-23
Hi all, 

I'm having a problem where my computer won't connect to the internet 90% of the time I boot it up.  It always works from the Windows side. Anyway,  I have a Asrock z68 motherboard and found out that I need a Realtek ethernet driver which I found[COLOR=Black][ **here**]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false")
And also, I found this[/COLOR][COLOR=Blue][COLOR=Black][ **tutorial **]("http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/")[/COLOR]
[/COLOR]
When I do

     ```
sudo make modules
```It gives me back this error:

    ```
make -C src/ modules
    make[1]: Entering directory `/home/me/r8168-8.035.00/src'
    make -C /lib/modules/3.5.0-22-generic/build SUBDIRS=/home/me/r8168-8.035.00/src modules
    make: Entering an unkown directory
    make: *** /lib/modules/3.5.0-22-generic/build: No such file or directory. Stop.
    make: Leaving an unknown directory
    make[1]: *** [modules] Error 2
    make[1]: Leaving directory `/home/me/r8168-8.035.00/src'
    make: *** [modules] Error 2
```So does that mean I am missing the build directry? I tried searching for it I couldn't find anything. 

Thanks for the help!

---

### Post by Yellow Pasque on 2013-01-24
Make sure you have build-essential and linux-headers installed
```
sudo apt-get install linux-headers-generic build-essential
```

---

