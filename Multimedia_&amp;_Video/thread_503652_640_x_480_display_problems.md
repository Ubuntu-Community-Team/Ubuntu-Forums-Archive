---
title: "640 x 480 display problems"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by Zuhaira on 2007-07-18
Hello everybody :KS

some people have some problems to the 640x480 display even they installing the driver and all OpenGL 3d working

I fixed my problem yesterday and I will give you some tricks that may help 

the problems sometimes because of the Horizontal and Vertical sync that over the range

```
$ sudo gedit /etc/X11/xorg.conf
```

 Monitor section
```
Section "Monitor"
    Identifier     "Generic Monitor"
    Option         "DPMS"
    HorizSync 30-70
    VertRefresh 50-160
EndSection
```

add these lines before endsection
```

    HorizSync 30-70
    VertRefresh 50-160
```

make sure you know the proper FH and VH in your monitors manual

---

