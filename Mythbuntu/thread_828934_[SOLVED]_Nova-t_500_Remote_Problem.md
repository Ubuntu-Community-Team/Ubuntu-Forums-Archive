---
title: "[SOLVED] Nova-t 500 Remote Problem"
date: 2008-06-14
forum: Mythbuntu
---

### Post by zymba on 2008-06-14
Hello,

I have a concrete problem with this remote that cant find how to solve.

I have Mythbuntu 8.04 and the card is working perfectly (once I disabled the EIT scanning, never had a problem with disconnects again).

The remote is working ok, but when the IR receptor catchs events from other remotes, my syslog is filled with:


Jun 14 14:30:03 mythtv kernel: [ 3508.760546] dib0700: Unknown remote controller key :  D 1F
Jun 14 14:30:03 mythtv kernel: [ 3508.912513] dib0700: Unknown remote controller key :  D 1F
Jun 14 14:30:03 mythtv kernel: [ 3509.064497] dib0700: Unknown remote controller key :  D 1F
Jun 14 14:30:03 mythtv kernel: [ 3509.216320] dib0700: Unknown remote controller key :  D 1F
Jun 14 14:30:03 mythtv kernel: [ 3509.368300] dib0700: Unknown remote controller key :  D 1F
Jun 14 14:30:03 mythtv kernel: [ 3509.520275] dib0700: Unknown remote controller key :  D 1F
Jun 14 14:30:03 mythtv kernel: [ 3509.672250] dib0700: Unknown remote controller key :  D 1F
Jun 14 14:30:04 mythtv kernel: [ 3509.824216] dib0700: Unknown remote controller key :  D 1F
Jun 14 14:30:04 mythtv kernel: [ 3509.976042] dib0700: Unknown remote controller key :  D 1F
Jun 14 14:30:04 mythtv kernel: [ 3510.128049] dib0700: Unknown remote controller key :  D 1F
Jun 14 14:30:04 mythtv kernel: [ 3510.279997] dib0700: Unknown remote controller key :  D 1F
Jun 14 14:30:04 mythtv kernel: [ 3510.436275] dib0700: Unknown remote controller key :  D 1F
Jun 14 14:30:04 mythtv kernel: [ 3510.587933] dib0700: Unknown remote controller key :  D 1F
Jun 14 14:30:04 mythtv kernel: [ 3510.739901] dib0700: Unknown remote controller key :  D 1F
Jun 14 14:30:05 mythtv kernel: [ 3510.891747] dib0700: Unknown remote controller key :  D 1F

As you can see, there are several per second.

I can stop it just by clicking a valid nova-t remote key, but thats not a practical solution :)

I really will be grateful with any help.

Regards,

zymba

---

### Post by tohc1 on 2008-06-14
This was a problem I had with 7.10 and I was hoping it would be fixed by now. I find the problem even worse as it seems to block my usb wlan stick will its doing it. 

The solution is to build a new version of the drivers which have been patched so that if the keypress is unknown it will flush the buffer and only show one error message. I found a patch for this somewhere and it fixed the problem on 7.10.

I had funnily enough just noticed the problem myself after installing 8.04 today, so I don't know precisely how this is going to go yet but I'll post instructions when i've got it working.

---

### Post by Beebock on 2008-06-14
Yup got the issue to. restarting the machine clears it, and i thnk (might eb wrong) thaat restarting LIRC clears it too.

Best thing is to ensure that you ahve all the buttons mapped :) There are some mappings avaialble on the mythTV wiki

---

### Post by tohc1 on 2008-06-14
Ok problem solved it was fairly straight forward using my instructions from 7.10:

--------------------------------------------
Upgrade drivers to solve key press problem
-------------------------------------------
1) Install packages required to build kernel modules 

possibly need these (I'd already installed these for wlan drivers but I though I'd put them here in case people had problems compiling)
>sudo apt-get install build-essential subversion module-assistant
>sudo module-assistant prepare

(needed these from my 7.10 instructions bare minimum required?)
> sudo apt-get install linux-headers-$(uname -r) build-essential 

2) Install Mercurial (cvs like program) 
> sudo apt-get install mercurial

3) Retrieve the v4l-dvb source tree 
> hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

4)Change into the v4l-dvb directory 
> cd v4l-dvb

5)Apply patch
> nano linux/drivers/media/dvb/dvb-usb/dib0700_devices.c

Change the code near line 523 from
```

err("Unknown remote controller key: %2X %2X %2X %2X", (int) key[3-2], (int) key[3-3], (int) key[3-1], (int) key[3]);
d->last_event = 0;
return 0;
```
to
```

err("Unknown remote controller key: %2X %2X %2X %2X", (int) key[3-2], (int) key[3-3], (int) key[3-1], (int) key[3]);
st->rc_toggle=key[3-1];
d->last_event = 0;
return 0;
```

6) Build the modules
> make

7) Install the modules 
> sudo make install

8)Load the module (not sure if this is needed)
> sudo modprobe dvb-usb-dib0700

9) Reboot and test.

Hope this helps. If anyone knows what the essential packages in step 1 feel free to correct me I tend to write everything I've done so that if I need to do it again I can.

---

### Post by JugeHuge on 2008-06-15
removed

---

### Post by zymba on 2008-06-19
> **tohc1 said:**
> Ok problem solved it was fairly straight forward using my instructions from 7.10:

--------------------------------------------
Upgrade drivers to solve key press problem
-------------------------------------------
1) Install packages required to build kernel modules 

...

Hope this helps. If anyone knows what the essential packages in step 1 feel free to correct me I tend to write everything I've done so that if I need to do it again I can.

Awesome, thank you very much for this very right answer. I recommend every owner of a Nova-T 500 aplying this patch.

-zymba-

---

### Post by JugeHuge on 2008-07-31
Seems to be working.. This should be included to v4l-dvb source by default.. Thank you..

---

### Post by curioussquid on 2009-01-21
That patch works great! I have been periodically trying to fix the problems with my remote for ages, now it all works smoothly with auto-repeat etc.

Good Job!

---

