---
title: "External audio interface setup"
date: 2013-08-25
forum: Multimedia Software
---

### Post by Warlon on 2013-08-25
I recently bought Presonus Firebox external audio interface to use with Ardour in ubuntu 13.04 but I have so far failed to get a single bleep out of it. I've been fighting with this for two days now, so can someone please help me. I'm a newbie when it comes to jack and audio in linux in general.

I've installed jack and ffado, and if I select firewire as my driver the light on my presonus turns blue from red, so my box is probably recognized correctly. Still, no sound comes out when I play something with ardour. I've tried different interface -settings in QjackCtl, but nothing seems to work. I'm guessing the interface setting should be /dev/fw0 or /dev/fw1, but it makes no difference whatever I choose.

---

### Post by Warlon on 2013-08-25
Ok, I got some sound. I had to add a link from /dev/raw1394 to /dev/fw0 and give them sufficient permissions:

sudo chmod 0777 /dev/fw0 
sudo ln /dev/fw0 /dev/raw1394
sudo chmod 0777 /dev/raw1394

But now I have to do this after every reboot. How can I make this change permanent? Or is there some reason why I'm missing /dev/raw1394?

---

### Post by Dart56 on 2013-10-13
I have a firebox and this seems to work. make sure the box is on and connected to the computer before you power it up. Then open Terminal and type this "jackd -r -dfirewire then minimize Terminal. If you close the Terminal it will turn off the firebox. The blue light should come on. I had to try this a couple of times to get it going. Ardour will work right away when it is done. Also you must install Qjackctl.  [http://markmims.com/howtos/2011/08/17/presonus-firebox.html](http://markmims.com/howtos/2011/08/17/presonus-firebox.html) will give you more info and other steps to take if this does not work

---

