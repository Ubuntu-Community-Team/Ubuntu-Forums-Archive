---
title: "Installing BT878 tuner from A to Z"
date: 2008-08-07
forum: Multimedia Software
---

### Post by emi23sgh on 2008-08-07
I'm very new to ubuntu so installing any new hardware is very tricky for me. So I found an old bt878 tvtuner and put it into my pc...i installed tvtime but i have a blue screen and nothing shows...as a windows user i think the driver is missing or the card is not recognized. Pls anyone can help with step by step configuration?

---

### Post by emi23sgh on 2008-08-07
ok i sort it out in the way that i found various info on internet and combine them...i put here how i did it maybe someone else will need this info:
1.Open a terminal window 
2.Type in the following to install gcc, mercurial and the kernel headers:

sudo apt-get install build-essential mercurial linux-headers-`uname -r`

3. Move to the /usr/src/ folder with:

cd /usr/src

4. Download the latest V4L drivers with:

sudo hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

5. Move into the newly created folder with

cd v4l-dvb

6. Now start the building process with:

sudo make

This will take a while.

7. And finally we install these drivers with:

sudo make install


I think in this first part it installs all updated drivers for any supported tv tuner.
And after this I used in terminal the following command:

sudo gedit /etc/modprobe.d/options

and here in the window that apears add at the end the following line:

options bttv card=78 tuner=5 radio=1

 

Save and close! Restart PC/Hope it will work you too!

---

### Post by mocha on 2008-08-07
I didn't have to compile v4l drivers for my old Hauppauge 401 with the Bt878.  It should just work.  Do a "dmesg | grep 878" to see if there are any messages

---

### Post by excursionist on 2008-10-06
Hi everybody

Command 
sudo apt-get install build-essential mercurial linux-headers 'uname-r'

gives me this:

Package linux-headers is a virtual package provided by:
  linux-headers-2.6.24-19-xen 2.6.24-19.41
  linux-headers-2.6.24-19-virtual 2.6.24-19.41
  linux-headers-2.6.24-19-server 2.6.24-19.41
  linux-headers-2.6.24-19-rt 2.6.24-19.41
  linux-headers-2.6.24-19-openvz 2.6.24-19.41
  linux-headers-2.6.24-19-generic 2.6.24-19.41
  linux-headers-2.6.24-19-386 2.6.24-19.41
  linux-headers-2.6.24-19 2.6.24-19.41
  linux-headers-2.6.24-18-xen 2.6.24-18.32
  linux-headers-2.6.24-18-virtual 2.6.24-18.32
  linux-headers-2.6.24-18-server 2.6.24-18.32
  linux-headers-2.6.24-18-rt 2.6.24-18.32
  linux-headers-2.6.24-18-openvz 2.6.24-18.32
  linux-headers-2.6.24-18-generic 2.6.24-18.32
  linux-headers-2.6.24-18-386 2.6.24-18.32
  linux-headers-2.6.24-18 2.6.24-18.32
  linux-headers-2.6.24-16-xen 2.6.24-16.30
  linux-headers-2.6.24-16-virtual 2.6.24-16.30
  linux-headers-2.6.24-16-server 2.6.24-16.30
  linux-headers-2.6.24-16-rt 2.6.24-16.30
  linux-headers-2.6.24-16-openvz 2.6.24-16.30
  linux-headers-2.6.24-16-generic 2.6.24-16.30
  linux-headers-2.6.24-16-386 2.6.24-16.30
  linux-headers-2.6.24-16 2.6.24-16.30
You should explicitly select one to install.
E: Package linux-headers has no installation candidate

I have Ubuntu 8.04 and I too am a novice in Linux.
Thanks for any help.

---

