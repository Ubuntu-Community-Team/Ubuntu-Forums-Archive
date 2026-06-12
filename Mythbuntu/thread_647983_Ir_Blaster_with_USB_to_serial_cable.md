---
title: "Ir Blaster with USB to serial cable??"
date: 2007-12-23
forum: Mythbuntu
---

### Post by tegwilym on 2007-12-23
Ok, I'm getting closer to a fix, but now just a bit stuck again.

I set up a Mythbuntu box and got most of it working but can't change channels.  See this thread ([http://ubuntuforums.org/showthread.php?t=644452](http://ubuntuforums.org/showthread.php?t=644452))
After a lot of messing around, I finally discovered that the serial port refused to work at all.  I mad a loop back connector with a 9 pin connector and used CuteCom to see the text coming back like it should.  Worked fine on my main computer, but my prototype MythTV box seems to probably have a dead serial port since nothing worked.

So.....I plugged in my USB to serial cable and it seems to be recognized just fine.  I connect to /dev/ttyUSB0 using CuteCom and the loopback and confirm that trick works just fine.  So I do have a good serial port now (through the USB) so how do I get this working with my irblaster cable?  
I've been reading that maybe you don't have to use Lirc with this method?  If so, what do I need to do to get control of my DirecTV box?

My plan is to do a setup like this --  Comptuer --> USB --> Serial --> IR Blaster --> Directv 
I'm pretty sure I have the D770 remote, so I have been using the configuration for that one in the lirc.conf file.  

Any tips on how to configure Mythtv to send a signal through a USB to Serial and get my channels changing?
With the dwindling amount of computers with good old RS232 ports, I'm sure there is an easy fix, but I'm making it too hard.

Thanks in advance, these forums have been a total lifesaver and I'm learning a lot these days!  :)


Tom

---

### Post by tegwilym on 2007-12-23
Anyone have a good link, thread or other site that shows how to do this?  
I'm soooo close now!

Tom

---

### Post by superm1 on 2007-12-24
> **tegwilym said:**
> Ok, I'm getting closer to a fix, but now just a bit stuck again.

I set up a Mythbuntu box and got most of it working but can't change channels.  See this thread ([http://ubuntuforums.org/showthread.php?t=644452](http://ubuntuforums.org/showthread.php?t=644452))
After a lot of messing around, I finally discovered that the serial port refused to work at all.  I mad a loop back connector with a 9 pin connector and used CuteCom to see the text coming back like it should.  Worked fine on my main computer, but my prototype MythTV box seems to probably have a dead serial port since nothing worked.

So.....I plugged in my USB to serial cable and it seems to be recognized just fine.  I connect to /dev/ttyUSB0 using CuteCom and the loopback and confirm that trick works just fine.  So I do have a good serial port now (through the USB) so how do I get this working with my irblaster cable?  
I've been reading that maybe you don't have to use Lirc with this method?  If so, what do I need to do to get control of my DirecTV box?

My plan is to do a setup like this --  Comptuer --> USB --> Serial --> IR Blaster --> Directv 
I'm pretty sure I have the D770 remote, so I have been using the configuration for that one in the lirc.conf file.  

Any tips on how to configure Mythtv to send a signal through a USB to Serial and get my channels changing?
With the dwindling amount of computers with good old RS232 ports, I'm sure there is an easy fix, but I'm making it too hard.

Thanks in advance, these forums have been a total lifesaver and I'm learning a lot these days!  :)


Tom
Tom,

The usb->serial ports can't be used for transmitting.  The serial port is used in a non traditional fashion when transmitting unfortunately.

---

### Post by tegwilym on 2007-12-24
> **superm1 said:**
> Tom,

The usb->serial ports can't be used for transmitting.  The serial port is used in a non traditional fashion when transmitting unfortunately.

Thanks for the reply.  
So since many computers now don't have serial ports, what is the best way to control the DirecTV with an ir and a USB port?

Something like this?
[http://www.usbgear.com/USB-Infrared.html](http://www.usbgear.com/USB-Infrared.html)

or this?
[http://www.usbuirt.com/](http://www.usbuirt.com/)

Seems that the serial port on my MythTV "prototype" box is dead.  I'm researching hardware for a small Shuttle or other cube-type of media box that I want to build.  

Tom

---

### Post by superm1 on 2007-12-24
> **tegwilym said:**
> Thanks for the reply.  
So since many computers now don't have serial ports, what is the best way to control the DirecTV with an ir and a USB port?

Something like this?
[http://www.usbgear.com/USB-Infrared.html](http://www.usbgear.com/USB-Infrared.html)

or this?
[http://www.usbuirt.com/](http://www.usbuirt.com/)

Seems that the serial port on my MythTV "prototype" box is dead.  I'm researching hardware for a small Shuttle or other cube-type of media box that I want to build.  

Tom

Yeah solutions like that should be the way to go.  I don't want to recommend a particular option since I personally don't have experience with them: however i've heard that the USB solutions work in cases such as yours.

---

### Post by tegwilym on 2007-12-24
> **superm1 said:**
> Yeah solutions like that should be the way to go.  I don't want to recommend a particular option since I personally don't have experience with them: however i've heard that the USB solutions work in cases such as yours.

From what I have read, it seems that the USB would be easier since you don't need to run lirc and since it's not a serial port, you don't have to deactivate that part in the kernel.  Does that sound about right?

Tom

---

### Post by superm1 on 2007-12-24
> **tegwilym said:**
> From what I have read, it seems that the USB would be easier since you don't need to run lirc and since it's not a serial port, you don't have to deactivate that part in the kernel.  Does that sound about right?

Tom

Well you didn't have to "deactivate" anything in the kernel going serial either.  If you were recompiling your kernel, that was a total waste of time.  You could have just been using the 'setserial' utility to turn off the UART for that port.

Depending on which USB device you go with, you may still need lirc however.

---

### Post by tegwilym on 2007-12-24
I didn't get as far as recompiling my kernel, that's just too much work.  I just did this to get the port working, (at least supposed to work, but nothing came out).
```

sudo apt-get install setserial
sudo setserial /dev/ttyS0 uart none
sudo modprobe lirc-serial

```

I'd have to modify something in the* modprobe.d* folder to  make it stick though from what I understand, but didn't get that far yet. 
I'm probably a high level newbie and in the low intermediate stages of knowledge in this stuff.  Without these forums, I'd still be booting Windows!

Tom
-Windows free for about a year now!:)

---

