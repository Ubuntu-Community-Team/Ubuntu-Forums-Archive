---
title: "Airlive Wl 1600 usb wireless problem"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by beatt on 2010-03-06
Hi

I have problem to connect Airlive Wl 1600 usb (wireless) on Ubuntu Studio.
I tryed on Ubuntu 8.10 , but there is a problem too.


Please to help me about installing and connecting to internet.

Thanks
B

---

### Post by markodelafuego on 2011-11-11
my answer comes a little bit late for you I guess but not for someone else:

If you want to install your AirLive 1600 usb on your ubuntu system you should first try the following. I am sure that there are so many different ways but for me this one was the only one that worked :)
there are also things like the linux driver for the AirLive on their homepage. there they tell you in the readme-file to "make" and "compile" and so on and so on...
after some time I find out the easiest way on the "wireless troubleshooting" page of ubuntu :D
as I said, that worked out for me but if it doesnt for you feel free to contact me..

the installation:

got to that link and follow the instructions there:
[https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)

if you have to manually install the ndiswrapper you have to download three packages. you find them here:
1) [http://packages.ubuntu.com/hardy/all/ndiswrapper-common/download](http://packages.ubuntu.com/hardy/all/ndiswrapper-common/download)
2) [http://packages.ubuntu.com/hardy/i386/ndiswrapper-utils-1.9/download](http://packages.ubuntu.com/hardy/i386/ndiswrapper-utils-1.9/download)
3) [http://packages.ubuntu.com/hardy/i386/ndisgtk/download](http://packages.ubuntu.com/hardy/i386/ndisgtk/download)
install them in that order, too.

afterwards you are searching for the windows driver of the AirLive via ndiswrapper in the location where you have saved it (I used that one for WindowsXP btw)
search for the file "net8187b.inf" and click "install".

Thats it!
Now, you should be able to connect to your wireless network.

Hope it helps..

---

