---
title: "Pinnacle pctv dvbt stick ultimate"
date: 2008-06-13
forum: Multimedia Software
---

### Post by ibhnielsen on 2008-06-13
I bought the usb tvtuner, as I imagined I could make it work in ubuntu 804, but in vain.
Is there anybody who can help me.
I searched the internet, and found a lot of sites, but I didnt understand a word.
I have to have tv on my laptop, and I know it works fine with xp, but now that I am microsoft free, it would be a bummer to have to install that again.

---

### Post by xc3RnbFO8P on 2008-06-13
First do this in Terminal:
> **lsusb**  
(just copy/paste into Terminal)
<return>
Show the output.

---

### Post by ibhnielsen on 2008-06-13
it says 
bus 006 Device 002: ID 2304:0236 Pinnacle Systems, Inc. [hex]

---

### Post by xc3RnbFO8P on 2008-06-16
Here is Howto:
[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_72e]("http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_72e")

---

### Post by 41115891 on 2008-06-16
You should install kaffeine(sudo apt-get install kaffeine) , then when kaffeine work, it can detect your dvb-t turner. 

It work very well in my ubuntu, so i think i can work in yours.

---

### Post by ibhnielsen on 2008-06-17
jeg har installeret kaffeine, men jeg kan ingen steder i programmet se tv?

---

### Post by ibhnielsen on 2008-06-17
så fandt jeg tv-et, men der sker intet.
der står en ip-adresse som udsendelsesadresse, er de det, der er fejlen, og burde det henvise til den usb port, tuneren sidder i?

---

### Post by ibhnielsen on 2008-06-17
Sorry I wrote in Danish.
I try gagain
i found the settings in  kaffeine but the adress was an ip-adress, should it be the usb-port I am using.

Kaffeine dvb is completely dead.

---

### Post by Erlander on 2008-06-17
In terminal enter dmesg and post the output re your tuner here.  We don't need the whole of dmesg just the part relevant to the tuner.

Rob

---

### Post by ibhnielsen on 2008-06-17
how can I see what is relevant, I cant find the word pinnacle, and dont understand a thing

---

### Post by Erlander on 2008-06-17
Well post the lot then and I'll see if I can help.

Rob

---

### Post by ibhnielsen on 2008-06-17
It wont work, it complaines that I have incluted 12 images, but its only a cope from terminal?????

---

### Post by xc3RnbFO8P on 2008-06-17
In Terminal:
> hg clone [http://linuxtv.org/hg/~pb/v4l-dvb/](http://linuxtv.org/hg/~pb/v4l-dvb/)
<return>
(just copy/paste into Terminal)

---

### Post by ibhnielsen on 2008-06-17
i think im going in cirkle:

root@ibzepto:/home/ib# hg clone [http://linuxtv.org/hg/~pb/v4l-dvb/](http://linuxtv.org/hg/~pb/v4l-dvb/)
The program 'hg' is currently not installed.  You can install it by typing:
apt-get install mercurial
bash: hg: command not found
root@ibzepto:/home/ib# apt -get instaLL MERCURIAL
The program 'apt' can be found in the following packages:
 * openjdk-6-jdk
 * sun-java5-jdk
 * sun-java6-jdk
Try: apt-get install <selected package>
bash: apt: command not found
root@ibzepto:/home/ib# apt -get instaLL mercurial

---

### Post by ibhnielsen on 2008-06-17
i found a package hg-xxxxx, and repieted the command.
it worked, but i dont know what it did???

---

### Post by xc3RnbFO8P on 2008-06-17
Do this:
> sudo apt-get install openjdk-6-jdk sun-java5-jdk sun-java6-jdk

> sudo apt-get install mercurial

> sudo hg clone [http://linuxtv.org/hg/~pb/v4l-dvb/](http://linuxtv.org/hg/~pb/v4l-dvb/)

---

### Post by ibhnielsen on 2008-06-17
I did get the command:
sudo hg clone [http://linuxtv.org/hg/~pb/v4l-dvb/](http://linuxtv.org/hg/~pb/v4l-dvb/)
to work. but I dont know what it did:

I tried it again:
root@ibzepto:/home/ib# hg clone [http://linuxtv.org/hg/~pb/v4l-dvb/](http://linuxtv.org/hg/~pb/v4l-dvb/)
destination directory: v4l-dvb
abort: destination 'v4l-dvb' already exists

it seams to have installed v4l-dvb

---

### Post by xc3RnbFO8P on 2008-06-17
Now in Terminal:
> cd /home/your folder/v4l-dvb

---

### Post by xc3RnbFO8P on 2008-06-17
If you are in the /home/your folder/v4l-dvb then:
./configure   <return>

if it shows errors, show the output.

---

### Post by ibhnielsen on 2008-06-17
I GET THIS:

root@ibzepto:/home/ib/v4l-dvb# ./configure
bash: ./configure: No such file or directory 

in the directory there are several files  makefile, install etc
perhaps there is something i have not done?

---

### Post by xc3RnbFO8P on 2008-06-17
sorry!
> make all

And then:
> make install

---

### Post by ibhnielsen on 2008-06-17
i used the command make all in the directory, and it ran a lot.
but the command ./configure gav the same result

---

### Post by ibhnielsen on 2008-06-17
ok i did make install and no errors
what shall i do now

---

### Post by xc3RnbFO8P on 2008-06-17
you dont use ./configure (it has been a long time since I installed dvb)
just **make all**
then **make install**

---

### Post by xc3RnbFO8P on 2008-06-17
Restart the computer 
and run dmesg
see if **dvb-usb-dib0700-1.10.fw** is loaded.
If it is, start Kaffeine.

---

### Post by ibhnielsen on 2008-06-17
i ran me tv,
AND IT WORKED
you are a genius

i have not found out how do i reward you?

---

### Post by xc3RnbFO8P on 2008-06-17
Just try to help someone :)

---

### Post by meadro on 2008-11-05
Sorry to latch onto this thread but I did everything that was suggested so far, and I do not see dvb-usb-dib0700-1.10.fw when I run dmesg.

FYI: I am on Ubuntu 8.10 (Intrepid) with Kernel 2.6.27-7

Any help you can provide will be very much appreciated. Thanks.

---

