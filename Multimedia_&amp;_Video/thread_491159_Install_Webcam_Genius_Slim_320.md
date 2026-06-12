---
title: "Install Webcam Genius Slim 320"
date: 2007-07-03
forum: Multimedia &amp; Video
---

### Post by acadavid on 2007-07-03
Hi. I have this webcam Genis Slim 320 and i've been trying to make it work on Ubuntu Feisty but i can't get it work.

lsusb:
```

Bus 002 Device 003: ID 0458:702f KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

I tryed.

```
sudo apt-get install gspca-source
cd /usr/src/
unp gspca-source.tar.bz2 (This just uncompress it)
cd gspca
make clean
sudo make
sudo make install
modprobe gspca

```

lsmod give me this:
```

Module                  Size  Used by
gspca                 616272  0 
```

If i run gqcam i get this:
```

acadavid@SystematicChaos:/usr/src/modules/gspca$ gqcam
/dev/video: No such file or directory
```

Well.. can somebody help me? Any other info just tell me.

Thank you.

---

### Post by kamsnay on 2008-01-23
I have Genius Slim 320 too. And it doesn't work on Gutsy.
If someone can help me & other owners of this webcam, it will be great!
my webcam is only thing in my computer, which doesn't work at linux :(

---

