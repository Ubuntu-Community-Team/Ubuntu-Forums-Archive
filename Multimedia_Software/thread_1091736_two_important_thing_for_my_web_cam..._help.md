---
title: "two important thing for my web cam... help"
date: 2009-03-09
forum: Multimedia Software
---

### Post by toblina63 on 2009-03-09
first i want to know that my web cam is work or no in ubuntu

is any code for this to know ?

second if my web cam was known in ubuntu how can i use the camera ?

any program for that ???

---

### Post by lindsay7 on 2009-03-09
Download "cheese" and you will know if you camera works. You can also try "Skype"

---

### Post by toblina63 on 2009-03-09
it doesn't work

what can i do to work it ??? :(

---

### Post by lindsay7 on 2009-03-09
From what I have read, web cams are tricky on Ubuntu. Research the forum for tips, someone may have your same cam that will respond to you.  I have a Microsoft cam that Will not work so I bought a BestBuy model Dynex DX-web1c for $39. It is not the best but it works out of the box.

FYI, my son can not get his MS webcam to work on Vista.. go figure. As a matter of fact, installing it really messed up this machine, blue screens of death, until he did a lot of fixing. So it is not just Ubuntu that has problems with webcams.

---

### Post by kyphi on 2009-03-09
Not all webcams will work in Ubuntu.

What brand is it?

If you want to know if your webcam will work, plug it in and then open a terminal and type:```
lsusb
```

This will produce a list of your USB devices giving the ID of your webcam.

Post this ID number here.

---

### Post by toblina63 on 2009-03-09
in my terminal

( Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0c45:613c Microdia PC Camera (SN9C120)


can this cam work in ubuntu ?

---

### Post by kyphi on 2009-03-09
Your camera is a Sonix PCcam168 and needs the gspcav1-20071224 driver.

You can download the driver from here: [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

A Readme file is included in the download and will tell you what to do.

---

### Post by toblina63 on 2009-03-10
i install it but i didn't understand how to install it

help me to knwow how to install this files

---

### Post by kyphi on 2009-03-10
When you download the file "gspcav1-20071224.tar.gz", where did you put it?  If it is on your Desktop then do the following line by line followed by pressing the Enter key: ```

cd Desktop
tar xvf gspcav1-20071224.tar.gz
sudo make [config|menuconfig|xconfig]; make dep
sudo ./gspca_build
```

After the driver is loaded, you will need a program for your webcam.  Try Camorama or Cheese.  Both are available from Applications, Add/Remove.

---

### Post by toblina63 on 2009-03-10
when i write

m@m:~/Desktop$ sudo make [config|menuconfig|xconfig]; make dep

it was show :

m@m:~/Desktop$ sudo make [config|menuconfig|xconfig]; make dep
[sudo] password for m: bash: menuconfig: command not found
bash: xconfig]: command not found


what i do then ????

---

### Post by kyphi on 2009-03-10
You can leave that line out.  I included it because the Readme file recommended it and I know nothing of your setup.

---

### Post by toblina63 on 2009-03-11
i still didn't know how to install

:(:(:(:

---

### Post by kyphi on 2009-03-11
If the downloaded file (gspcav1-20071224.tar.gz) is on your desktop follow this sequence in a terminal pressing Enter after each command:

cd Desktop
tar xvf gspcav1-20071224.tar.gz
cd gspcav1-20071224
sudo ./gspca_build

The last command will prompt you for your password.

---

