---
title: "logitech quick cam chat"
date: 2007-02-18
forum: Multimedia &amp; Video
---

### Post by dreww on 2007-02-18
I am linux beginner. having trouble getting Logitech" quick cam, chat" to work on my "ubuntu"
platform.:confused:[FONT="Arial Black"][/FONT]

---

### Post by qb4ever on 2007-02-19
Type ¨lsusb¨ in the terminal and post the result so we can find out what exact chip you have.

---

### Post by dreww on 2007-02-19
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

Somehow this does not seem right, help!

---

### Post by dreww on 2007-02-19
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:092e Logitech, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

That's better. excuse me but, I am very new to forums and
computers.

Thank You

---

### Post by truck87bp on 2007-02-19
I'm have similar problems, Ubuntu see it but it doesn't work. I'm a noob to. here is my list.
Bus 005 Device 002: ID 0781:8889 SanDisk Corp. SDDR-88 Imagemate 8-in-1 Reader
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:ca03 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000

I have camorama but can't get an image.

Thanx for any help.  You people are great!

---

### Post by qb4ever on 2007-02-19
It looks like the gspca driver might work: [http://mxhaard.free.fr/spca50x/Download/gspcav1-20070110.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20070110.tar.gz)

make sure the kernel headers are installed for your kernel version which can be found with this: "uname -r"
then make sure build-essential is installed

download the file to a folder

then run: tar -xvf gspcav1-20070110.tar.gz

cd gspcav1-20070110

make
sudo make install
sudo modprobe gspca


camorama or xawtv should pick it up on /dev/video0 IF it's compatible and installed properly

---

### Post by dreww on 2007-02-21
This is all new to me and I realize you are trying to help me.
But, I have not used this system before. If you have the time could you be a lttle more explicit?

Thank You,
Drew

---

### Post by mthaddon on 2007-03-08
Did you ever get this working? I followed the instructions and it worked fine for me. Let me know if you need a hand at all.

Cheers, Tom

---

### Post by dreww on 2007-03-09
hello,

I am really a beginner at this. Not even sure how to navigate forums.
But if you give me some step by step instructions. I could get it done.
Thanks for your help and patience. I have got the gspca driver. not sure how to unzip it.

dreww:guitar:

---

### Post by htmlland on 2007-03-29
Thanks qb4ever that has saved me hours of pulling out my hair!!

---

### Post by nightskywind83 on 2007-05-05
Drew,

you need to open the Terminal program (or Konsole if you're using Kubuntu) to enter the commands above (tar -xvf *filename.tar.gz*) etc

Meanwhile, my logitech quickcam worked automatically with camorama, but my image is tinted blue.  no adjustments i make from within camorama seem to resolve this.  (perhaps camorama should have RGB controls?)

Incidentally I also tried xawtv, which works great as far as color is concerned, but the entire bottom half of the picture is fuzzied out.

Easycam and Easycam2 attempts proved fruitless.  Easycam claims it doesnt support my camera, and Easycam2 fails to install, reporting errors with the command "Make install"

Hope this helps, questions and comments welcome...

---

### Post by dreww on 2007-05-11
Thanks for all the replies I was out for a while . But, will get back to this.
I'll reply with more info soon. Thanks for the help.

Drew:KS

---

### Post by lesan_sk on 2007-06-05
I tried to install the driver but when i run make i get the following error...

make -C /lib/modules/`uname -r`/build SUBDIRS=/home/geo/linux/gspcav1-20070508 CC=cc modules
make: *** /lib/modules/2.6.15-28-386/build: No such file or directory.  Stop.
make: *** [default] Error 2

I'm pretty sure that I upgraded the kernel (2.6.15-28-386) but not the kernel headers. In case u think it may have something in common with my problem could u point me to a tutorial?!

cheers

---

### Post by lysalf on 2007-06-30
thanks qb4ever..

Saved my day there.!

---

