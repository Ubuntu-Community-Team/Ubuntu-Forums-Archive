---
title: "Analog cable TV/Radio PCI card for Ubuntu?"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by johann_p on 2007-02-05
Which PCI or PCIE cards that can receive analog cable TV and FM radio are known to work with Ubuntu?

---

### Post by barney_1 on 2007-02-05
You are going to need to use IVTV to control an analog tuner or encoder.  Check out the supported hardware for IVTV:

[http://ivtvdriver.org/index.php/Supported_hardware](http://ivtvdriver.org/index.php/Supported_hardware)

I'm using a Hauppauge PVR250 and it works great!

---

### Post by johann_p on 2007-02-05
> **barney_1 said:**
> You are going to need to use IVTV to control an analog tuner or encoder.  Check out the supported hardware for IVTV:

[http://ivtvdriver.org/index.php/Supported_hardware](http://ivtvdriver.org/index.php/Supported_hardware)

I'm using a Hauppauge PVR250 and it works great!

Looks scary ... doesn't Ubuntu automatically recognize the hardware when I put it into the computer?

Under OpenSuse I just selected the TV option in yast and configured the card on my last computer.

I have installed the Hauppage card from my old PC into the Ubuntu PC and nothing happened, nothing shows up in the configuration. When I try to run kdetv or zapping, nothing works, no video device is found :(

Is there anything I need to manually install with synaptic or what else is needed to make the card work, once it is in the system?

---

### Post by fenian on 2007-02-05
The hauppauge wintv go cards are are recognized by ubuntu.They work fine with tvtime but aren't as good at recording live tv,you need to make sure you get the one with fm tuner for radio.This is a better link for setting up ivtv on ubuntu(you don't need ivtv with the wintv go cards).

[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

---

### Post by barney_1 on 2007-02-05
Fenian's howto link is the same one I used.  It installed my card without a hiccup.

@johann_p
It's really not scary, it is just something you haven't done before.  Using the module assistant to compile drivers is fairly painless. This wouldn't be any fun if everything just worked.

I'm assuming that you already know about MythTV, but just in case:

[www.mythtv.org](www.mythtv.org)

It's the only way to go when it comes to TV on PC.

---

### Post by johann_p on 2007-02-05
Did not work. 
When I did "sudo m-a a-i ivtv" I got an error and the log shows
> 
/usr/src/modules/ivtv/driver/ivtv-driver.c: In function ‘ivtv_probe’:      &#9618; 
 &#9474; /usr/src/modules/ivtv/driver/ivtv-driver.c:1291: warning: passing          &#9618; 
 &#9474; argument 2 of ‘request_irq’ from incompatible pointer type                 &#9618; 
 &#9474; /usr/src/modules/ivtv/driver/ivtv-driver.c: In function ‘ivtv_remove’:     &#9618; 
 &#9474; /usr/src/modules/ivtv/driver/ivtv-driver.c:1404: warning: passing          &#9618; 
 &#9474; argument 1 of ‘cancel_delayed_work’ from incompatible pointer type         &#9618; 
 &#9474; make[4]: *** [/usr/src/modules/ivtv/driver/ivtv-driver.o] Error 1          &#9618; 
 &#9474; make[3]: *** [_module_/usr/src/modules/ivtv/driver] Error 2                &#9618; 
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-5-generic'       &#9618; 
 &#9474; make[2]: *** [all] Error 2                                                 &#9618; 
 &#9474; make[2]: Leaving directory `/usr/src/modules/ivtv/driver'                  &#9618; 
 &#9474; make[1]: *** [binary-modules] Error 2                                      &#9618; 
 &#9474; make[1]: Leaving directory `/usr/src/modules/ivtv'                         &#9646; 
 &#9474; make: *** [kdist_build] Error 2  


Maybe it is because I am running Feisty, which in turn was necessary because Edgy would not even install on my computer.

Same situation as before :(

---

### Post by johann_p on 2007-02-05
Hm, I think I am getting closer -- for some reason, I was able to use KDETV and got a TV picture, but only under root. Under my own user KDETV complains that there is no device.

I found out that there must be some permission problem.
I did "chmod o+rw /dev/vbi0" and the same for "/dev/video0" and now I also get a picture. 

Unfortunately, no sound. I have connected the line out of the TV card with the line in of the sound card but it seems the Intel onboard audio does not work properly ... I hear a sound when eg playing an mp3, but not from line it or the mic.

---

