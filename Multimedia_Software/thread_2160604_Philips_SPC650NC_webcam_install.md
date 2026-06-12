---
title: "Philips SPC650NC webcam install"
date: 2013-07-07
forum: Multimedia Software
---

### Post by zirtik on 2013-07-07
Hello, I have a 6 year old Philips SPC650NC that I'd like to get it working under Linux. I have cheese and Skype installed and it did not work out of the box. I did some research and figured there are a few drivers I can use depending on my hardware. When I look at the kernel logs, here is what I see:

```

cat /var/log/kern.log.1  | grep Philips
Jul  1 22:21:30 apollo kernel: [ 6890.831100] usbcore: registered new interface driver Philips webcam
Jul  1 22:21:37 apollo kernel: [ 6897.208044] usbcore: deregistering interface driver Philips webcam
Jul  1 22:21:40 apollo kernel: [ 6900.517836] usbcore: registered new interface driver Philips webcam
Jul  1 22:47:34 apollo kernel: [ 8454.132070] usbcore: deregistering interface driver Philips webcam
Jul  1 22:47:38 apollo kernel: [ 8458.483855] usbcore: registered new interface driver Philips webcam

```

also, searching for uvcvideo results in this output in the kernel logs

```

cat /var/log/kern.log.1  | grep uvcvideo
Jul  1 22:33:15 apollo kernel: [ 7596.003808] usbcore: registered new interface driver uvcvideo

```

I assume my web cam is detected by the kernel and the uvcvideo module is loaded. However, dmesg doesn't show anything and I cannot see anything under /dev/vid*. 

Where should I look at and how can I resolve this? I searched the forums and couldn't really find anything useful. I apologize if I'm missing an obvious step.

Thanks.

---

### Post by sanderj on 2013-07-07
I don't know if it helps, but you could post and Google the lsusb id of the webcam ...

---

