---
title: "Make Asus Webcam works"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by XioNoX on 2006-07-02
Hello,

I have an asus Z92T laptop, his webcam need the m560x driver to works.
It is aviable here : [http://m560x.x3ng.com/](http://m560x.x3ng.com/)
But I don't know what I can doo to make it working.

Thanks

---

### Post by christhemonkey on 2006-07-02
The driver seems to still be in very early development stage.

To use what they have currently see [this]("http://m560x.x3ng.com/wiki/CurrentState") page.

> 
How to test the current code? 

Get a copy from 0.1 version (source:m560x/tags/km_m560x-0.1):

cd ~
svn co [http://m560x.x3ng.com/svn/m560x/tags/km_m560x-0.1](http://m560x.x3ng.com/svn/m560x/tags/km_m560x-0.1) m560x
cd m560x

Then compile the m560x kernel module:

make

Let's install the new compiled module into our running kernel:

sudo make install

And finally, load the module (with debug mode activated):

sudo modprobe m560x debug=16

You should get some new info when running 'dmesg':

...
usb_m560x_init - M560x-based WebCam driver startup
m560x_probe - M560x-based WebCam connected
Ali M5602-based WebCam found.
m560x_probe - Ali_M560x WebCam driver is now controlling video device 0
usbcore: registered new driver m560x
0.1:Ali M560x Webcam Driver

So, a new video device is registered ('/dev/videoX') and it's accessible via 'sysfs':

ls /sys/class/video4linux/videoX

You can also run some specific V4L commands to communicate with the device (but at the current point we just started with the V4L API implementation, a lot of code is still missing):

v4l-info
v4l-conf
v4lctl list

Some debug messages are stored into your logs and show us what still need to be implemented... ;-) 


---

### Post by aki-andre on 2006-11-19
```
andre@aki:~/km_m560x$ make
make -C /lib/modules/2.6.15-27-amd64-generic/build SUBDIRS=/home/andre/km_m560x modules
make: *** /lib/modules/2.6.15-27-amd64-generic/build: Nie ma takiego pliku ani katalogu. Stop.
make: *** [all] B&#322;&#261;d 2
andre@aki:~/km_m560x$ 
```

What is wrong? I have ubuntu 6.06 , how to solve this problem?

---

