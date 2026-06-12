---
title: "Usb microscope led lights."
date: 2010-06-30
forum: Multimedia Software
---

### Post by techno-mole on 2010-06-30
Hello.

I have recently purchased a usb microscope from Maplins, and although it does work with ubuntu 10.4 (and linux mint 9) I cant for the life of me get the led lights to work, the lights are kind of needed when viewing things close up.

[Usb microscope link]("http://www.maplin.co.uk/Module.aspx?ModuleNo=286566")

The output from running lsusb gives the following - 
```
Bus 002 Device 005: ID 0c45:6270 Microdia PC Camera (SN9C201 + MI0360/MT9V011 or MI0360SOC/MT9V111) U-CAM PC Camera NE878, Whitcom WHC017, ...
```

Like I said it works, tried it with cheese, and I can get close up to stuff, but because the led's don't work it's difficult to get a clear picture with out a torch.

Any help is appreciated, we intend to us the microscope to help with our kids education.

I know I could just run it under windows (we dual boot) but that kind of defeats the object, I don't think that it's a hard thing to figure out.

---

### Post by techno-mole on 2010-06-30
I should point out that I'm usng linux mint 9 (64bit) but I have also tried the microscope no my daughters pc, she is running karmic, and although I can get pictures the led's don't light up.

One other thing is that when I first plug the microscope in the led's do flash momentarily, but that's all I get.

The microscope does work, I have installed it on xp 64bit and it works as it should.

cheers.

---

### Post by techno-mole on 2010-06-30
I have been playing around and still not managed to get the led's to work, I have tried un-plugging every usb device I have (apart from my trackball) and the lights still don't work, I tried this because I thought the usb bus maybe over stretched, I seem to have a lot of usb devices.

I have also found that if the led's aren't going to work, although I can't find anything that says they won't, it may be possible to hack the microscope to at least use the led's, although I won't be able to control them as I can under windows, well not with out a very small switch and some tape and some solder :-)

The camera works well using cheese, this is the only one I have managed to get to work with the device, although I may have errors on my system due to messing around with compiling drivers, this is one of those little things that would put off a windows user, luckily I am a little more persistent :-)

---

### Post by CJ_Hudson on 2010-06-30
Hi techno mole,
My Dad has a malpins USB microscope he was hoping to examine his nails with for playing the guitar better.
It seems somewhat limted in scope though we did get some results with it on my Dads laptop running Vista.
He's asleep now but I will try it with my Ubuntu desktop tomorrow and let you know if the light works.

---

### Post by CJ_Hudson on 2010-06-30
What I can suggest is plugging the USB from the microscope into 2 (two) USB sockets at once. You can get power supply adapters for USB that plug into two sockets, i.e. 2 male USB plugs into one female, I have one for the external CD ROM drive for my Eee PC (it also plugs helpfully into a PS2 connector for a mouse or keyboard.) Because it probably uses the whole of the 5 volts supply the computer shuts down the non-essential functions i.e. the lights and keeps the essential one i.e. the camera going.
I hope that helps.

---

### Post by techno-mole on 2010-07-01
> **MogBug said:**
> What I can suggest is plugging the USB from the microscope into 2 (two) USB sockets at once. You can get power supply adapters for USB that plug into two sockets, i.e. 2 male USB plugs into one female, I have one for the external CD ROM drive for my Eee PC (it also plugs helpfully into a PS2 connector for a mouse or keyboard.) Because it probably uses the whole of the 5 volts supply the computer shuts down the non-essential functions i.e. the lights and keeps the essential one i.e. the camera going.
I hope that helps.

Well, I tried what you suggested, it hasn't worked, using 2 usb ports confuses the system and the microscope doesn't run.
I wondered about giving the microscope some extra power, so I made a lead that would allow me to run the microscope of one usb port, and also allow me to pull power from another port, this also didn't work.

I'm not sure that power is the issue, I think it's more that the driver doesn't switch the led's on in the first place, the windows software allows you to control the led's from the gui you get when you install the software.

The microscope we have is also from Maplins by the way, it's and igadget at least that's what it's branded as, it still uses a microdia chip though, the same as the Veho usb microscopes.

Here's the idea I had - From looking at the circuits in the microscope it would seem that bridging the connection straight from the main usb lead would bypass any switches etc on the circuit board and in theory feed the led lights, the only downside is they would be on constantly, but a small switch could solve this.

It's not an ideal solution by any means, but I think it would work, that's if I can't figure out why the led's don't light, whether it's down to the driver or something else, I've attached a picture, which kind of shows what I mean.

---

### Post by potat on 2010-07-01
If you want to find out what the Windoze driver is doing, try this program.
[http://sourceforge.net/projects/usbsnoop/]("http://sourceforge.net/projects/usbsnoop/")
Got the link from [here]("http://jespersaur.com/drupal/book/export/html/21")

---

### Post by puppywhacker on 2010-07-01
or use wireshark to snoop the USB messages.

The point is that your device can turn on the leds by usb-command sent by the windows drivers. For linux it is only recognized as a webcam. I don't think there are proper drivers that can turn on the led as well. However in windows you can catch the signals while turning the leds on and of, and you can replay these usb-commands in linux

It wouldn't hurt to also look at the device capabilities 
```
lsusb -v -s 0c45:6270
```

---

### Post by techno-mole on 2010-07-01
I figure the driver wasn't turning the led's on, I have tried my little hack, and it does work.

I will have a go at seeing what commands windows is using to turn the led's on and off and see if I can pass those commands on linux.

I tried the code given, but it doesn't output anything ?

```
lsusb -v -s 0c45:6270
``` doesn't give me any out put.

cheers

---

### Post by puppywhacker on 2010-07-02
"-s 0c45:6270" filters on your device, it could not be found, hence the output was empty. use "lsusb -v" without the filter instead.

good luck finding the correct usb message

---

### Post by CJ_Hudson on 2010-07-07
Although this is all getting a bit technical for me I tried the microscope in Ubuntu, and the LED lights come straight on without even installing any software- although I can't get the program to run that makes the micorscope bit function, as it's beyond me!

---

### Post by techno-mole on 2010-07-08
have you tried cheese ? it's in the repo's I tried a variety of apps, and the only one that actually enabled me to see anything was cheese.

I still can't get the led's to work on ubuntu or mint for that matter, still I live in hope of a driver surfacing that does the job, my graphics tablet has one which works well, so you never know.

---

### Post by practic on 2010-07-12
I can't explain why your LED lights don't work, but I'm using a different brand of USB microscope with Ubuntu 10 and it works fine. lsusb gives:

```
Bus 001 Device 008: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera

```

It's from DealExtreme, the DigiMicro 200x. $35.51 with free shipping.

When I first got it only 3 of the 4 LED's would light, but after a while they all came on. We've had a lot of fun with this unit, and it works nicely with Cheese.

---

### Post by mashedbear on 2010-11-13
I am looking to buy a USB microscope for my son for his birthday. It would be great to get some advice on what models / makes will work on Ubuntu. My system is running Ubuntu 10.10 (2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux)

Thank for your help

---

### Post by 4ebees on 2010-12-04
> **techno-mole said:**
> Hello.

I have recently purchased a usb microscope from Maplins, and although it does work with ubuntu 10.4 (and linux mint 9) I cant for the life of me get the led lights to work, the lights are kind of needed when viewing things close up. 

Hi there,

Try here:

[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs)

Though the site states there is a driver in the newer kernels, these do not switch on the LEDs.

Use the 'git' instructions and then compile and install the driver per the instructions. 

Works like a charm.

If it doesn't, get back to me and we'll see what we can do (I'm not promising anything as I didn't create the driver :)))

The only problem is you have to go through the whole rigmarole each time you update the kernel!

<shakes head>

PS.

You will need to address the issue of the existing driver which is located here:

lib/modules/2.6.31-22-generic/kernel/drivers/media/video/gspca/gspca_sn9c20x.ko

of course the kernel number will depend on the kernel you are using :))


Change the name of the gspca driver to something like gspca_sn9c20x.ko.original (or something) rather than delete it (which I'm sure you wouldn't do but there are many who are new who may :))

then install the driver.

I've found that sometimes modprobing doesn't work (dunno why) and I've had to reboot (I use the microscope on a laptop so turning it off doesn't feel too unusual LOL)

---

