---
title: "[SOLVED] Asus MK241H webcam problem..."
date: 2008-08-06
forum: Multimedia Software
---

### Post by 2m4Y on 2008-08-06
...as it is said in the title, I can't get it to work, or maybe I don't know! lsusb didn't gave me nothing exept my USB MX510 mouse!
When Ubuntu starts, the cam is started for a second or two, & then again shuted down, I noticed that becouse little blue LED that is turned on & then again off, does something prevents it from work?
Everything else works fine!

My specs:
AMD Athlon 64 4000+ X2
nForce 500
2x 1GB DDRII 800MHz
GeForce 8800GTS 320MB
2x 320GB SATAII HDD
DVD, CD-RW & DVD-RW all PATA
SB Live 5.1 Digital

Software: I have triple boot: WinXP Pro SP3, Mac OS X 10.5.2 (leo4all v3) & Ubuntu 8.04 64bit, exept Ubuntu, XP & Mac OS X see cam no problem, & works fine, without drivers!

Cheers...

---

### Post by cszikszoy on 2008-08-06
How have you tried to get it to work?

Right when your computer starts up, and the camera light blinks, can you type "dmesg" in a terminal and post the output?

---

### Post by 2m4Y on 2008-08-06
...here it is!

Cheers...

---

### Post by cszikszoy on 2008-08-06
These lines in your dmesg output lead me to believe that everything is working fine:

```
[   42.509409] uvcvideo: Found UVC 1.00 device ASUS USB2.0 Webcam (0458:705a)
[   42.678010] usbcore: registered new interface driver snd-usb-audio
[   42.678146] usbcore: registered new interface driver uvcvideo
[   42.678149] USB Video Class driver (v0.1.0)
```

Can you post the output of 'sudo lsusb'?

This time, just include it in the message.  Don't zip and attach please! :)

---

### Post by 2m4Y on 2008-08-06
Here it is:

```
mir@bezimenko:~$ sudo lsusb
[sudo] password for mir: 
Bus 002 Device 003: ID 0458:705a KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0d8c:0201 C-Media Electronics, Inc. 
Bus 001 Device 002: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 001 Device 001: ID 0000:0000  
mir@bezimenko:~$
```

...so? I don't see here any cam!

Cheers...

---

### Post by cszikszoy on 2008-08-06
It's there, it just doesn't say "Webcam".

Look at this line in dmesg:

```
[   42.509409] uvcvideo: Found UVC 1.00 device ASUS USB2.0 Webcam (0458:705a)
```The last bit, 0458:705a is the USB device identifier.

Now look at this line in your lsusb:

```
Bus 002 Device 003: ID 0458:705a KYE Systems Corp. (Mouse Systems)
```

Notice how the ID is the same as  the one shown in dmesg?

That's your webcam :)

What program are you using to test your webcam?

Everything looks green from here and your webcam should "just work".

Try downloading a program called cheese (sudo apt-get install cheese, I think).

Webcam support in linux is anything but unified.  Some programs that claim to support webcams dont.  I've had great success with cheese and skype 2.xx or higher.  Webcams seem to work reliably with those two programs.

Try installing cheese and see if it recognizes your camera.

---

### Post by 2m4Y on 2008-08-06
...jeap, now I see it, & it works, tnx m8!

Cheers...

---

### Post by cszikszoy on 2008-08-06
no problem, don't forget to mark this thread as solved.

---

