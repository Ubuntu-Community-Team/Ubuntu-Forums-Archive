---
title: "HELP!!!!How to Configurate minicom to communicate with serial port §§"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by halas86 on 2010-02-09
i have the suzaku-v board and i need to do the first boot.so it's necessary to install the minicom which need a configuration to recognize the serial port and begin the communication.
i install the minicom and i connect the serial port to my evaluation  board suzaku-v after i short the jumper to boot normally but i don't receive any thing in the window of minicom.
any help is appreciate.
thx

---

### Post by halas86 on 2010-02-09
Plz help.:sad::-(:-(:-(:-(

---

### Post by puppywhacker on 2010-02-09
did you configure which serial port minicom should use
```
minicom -s
```

---

### Post by halas86 on 2010-02-10
and after that???

---

### Post by Rhubarb on 2010-02-10
Consider using **gtkterm** instead.
It's a nice GUI app that works for me when I need to connect via usb to serial for a few devices I have.
Once installed you'll find it in Applications --> Accessories --> Serial port terminal.
From there you can configure the serial port and the baud rate from Configuration --> Port

I have no experience with minicom so I can't help you much there.
Try reading minicom's manual page which may help:
```
man minicom
```

---

### Post by alexfish on 2010-02-10
hi

hope this is of some help

[http://www.cyberciti.biz/tips/connect-soekris-single-board-computer-using-minicom.html](http://www.cyberciti.biz/tips/connect-soekris-single-board-computer-using-minicom.html)

---

