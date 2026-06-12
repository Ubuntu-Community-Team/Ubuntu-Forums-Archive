---
title: "dual uk freeview system"
date: 2009-05-09
forum: Mythbuntu
---

### Post by wildbillkelso on 2009-05-09
Hello all.

My hard disk recorder is on its way out. I am new to Linux and am very impressed with Ubuntu,and I am interested in Mythbuntu very much. Ideally I would like a system that can record two uk free view programs simultaneously while I watch another on my television that has a built in freeview reciever. I would greatly apretiate any advice or thoughts on what hardware I would need to do this if it is at all possible, and what is recomended. Such as, Would I need a freeview tv card? Or do I need two? If so which ones are supported, or is it better to get a standard terrestrial card and use an external freeview decoder? It needs to perform quite well as my wife gives me grief when the recorder plays up and she misses a program. Sorry if these seem simple questions but I am new to all, this but it is rather interesting.

Thank you very much

---

### Post by Chris Musampa on 2009-05-09
Hi WildBill,
As far as the reciever is concerned, I bought a Hauppauge WinTV-Nova TD-500 last weekend.  Its a PCI dual freeview and works almost out of the box with Mythbuntu, I say almost as I had to install a new driver (extremely straightforward procedure) to get the remote to work.  I'm happy with the result.

No ideas for the rest of your hardware.

---

### Post by wildbillkelso on 2009-05-09
Many thanks for the advice Chris. I will have a look at this card. Every bit of help is apretiated.

---

### Post by gwagchunks on 2009-05-09
Hi,

how did you get the remote to work?! I have been trying for ages with a happauge nova td-500 and have had no luck, would love to find some simple instructions for how to do this!:)  P.S. Chris the new TD-500 does work out of the box with mythbuntu 8.10 and 9.04, video was choppy at first but I updated the nvidia driver and this seemed to help

---

### Post by Chris Musampa on 2009-05-09
> **gwagchunks said:**
> Hi,

how did you get the remote to work?! I have been trying for ages with a happauge nova td-500 and have had no luck, would love to find some simple instructions for how to do this!:)  P.S. Chris the new TD-500 does work out of the box with mythbuntu 8.10 and 9.04, video was choppy at first but I updated the nvidia driver and this seemed to help

Yeah TV reception works out of the box, the remote was why I had to update the drivers as follows (from memory):

[http://linuxtv.org/hg/v4l-dvb/tags](http://linuxtv.org/hg/v4l-dvb/tags)

Click on 'Tip' (I assume that means latest as I notice the number has changed since last weekend), 
Click bz2, saved to a new folder under my home folder.
Unpack the bz2 (I don't know the command so I did it from nautilus)
Opened a terminal and cd to the unpack directory (here you'll find  'install' and 'readme' files containing instructions, check them)
make all
Take the dog for a walk (optional step and probably won't affect the installation)
sudo make install
sudo reboot

You can then check if worked by ```
me@desktop:~$ dmesg | grep -i dvb
[    8.911216] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[    8.911223] usb 1-1: firmware: requesting dvb-usb-dib0700-1.20.fw
[    9.460934] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   10.164041] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[   10.164266] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   10.164862] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   10.385797] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   10.559870] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   10.560394] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   10.705050] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[   10.880477] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:0c.2/usb1/1-1/input/input6
[   10.884778] dvb-usb: schedule remote query interval to 50 msecs.
[   10.884789] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[   10.885071] usbcore: registered new interface driver dvb_usb_dib0700

```

The 'input: IR-receiver inside an USB DVB receiver...' line was not present before installing the new drivers.  After that I added the remote (Nova t-500) in myth control center and it worked.

HTH

---

### Post by gwagchunks on 2009-05-09
Thanks for the reply / info Chris. It'll be tomorrow evening before I get a chance to play again. I'll let you all know how I get on. Thanks again.

---

### Post by wildbillkelso on 2009-05-16
Hi Chris.

Ive got my system and a Nova-T 500 sorted but no remote working. If I follow the procedure you described, will that overwrite the firmware for the card? I am having problems with mythbuntu and if that is the case I do not want to do that.

Many thanks.

---

### Post by wildbillkelso on 2009-05-17
Remote sorted now. Thanks for previous posts. They have proved very usefull.

---

### Post by Chris Musampa on 2009-05-17
Glad its working for you WildBill :)

---

### Post by ffaker on 2009-10-04
Chris Musampa: I never said thanks for this -- thanks it finally got my remote working!

Unfortunately, today there was a kernel security patch pushed to my Jaunty box. I installed it (along with a bunch of other updates) and now my remote is not working. I have tried recompiling and resintalling these drivers. I have also tried downloading the newest version and compiling and installing that: all to no avail.

The weird thing is that the "input: IR-receiver inside an USB DVB receiver..." is still there when I run dmesg. But it seems somthing else is stopping the remote from working (no response when I run the irw command either).

I've checked the batteries and it's not that.

Another weird symtom, is that" when I run the MythTV frontend, my mouse is frozen. When I close the frontend, the mouse works again. Very odd, not sure if it's connected to the remote issue or not.

Any ideas?!?

---

### Post by Chris Musampa on 2009-10-04
> **ffaker said:**
> Chris Musampa: I never said thanks for this -- thanks it finally got my remote working!

Unfortunately, today there was a kernel security patch pushed to my Jaunty box. I installed it (along with a bunch of other updates) and now my remote is not working. I have tried recompiling and resintalling these drivers. I have also tried downloading the newest version and compiling and installing that: all to no avail.

The weird thing is that the "input: IR-receiver inside an USB DVB receiver..." is still there when I run dmesg. But it seems somthing else is stopping the remote from working (no response when I run the irw command either).

I've checked the batteries and it's not that.

Another weird symtom, is that" when I run the MythTV frontend, my mouse is frozen. When I close the frontend, the mouse works again. Very odd, not sure if it's connected to the remote issue or not.

Any ideas?!?

Sorry FF, I have no idea, would appreciate it if you let us know how you solve it though, I'll leave off updating for the moment as my myth box isn't exposed to the world anyway.

---

### Post by ffaker on 2009-10-05
OK thanks anyway. When (not if!) I fix it I'll update you.

p.s. note to self: once MythTV box is working: DO NOT TOUCH IT AND DO NOT INSTALL UPDATES!!!

---

### Post by ianhaycox on 2009-10-05
I've had similar problems after a kernel update.

You need to rebuild the drivers, but do a make distclean first to ensure it uses the updated kernel headers etc.

Ian.

---

### Post by ffaker on 2009-10-07
> **ianhaycox said:**
> I've had similar problems after a kernel update. You need to rebuild the drivers, but do a make distclean first to ensure it uses the updated kernel headers etc.

Ah thanks I will try that tonight.

In the past, I've had this problem after kernel security fixes, but it works again after I do a recompile and reinstall of the drivers (removing the folder that had originally been extracted from the TAR file first). This time, it's still not working after I reinstall the drivers.

Will ```
make distclean
``` do something that deleting the folder would not?

ALSO weird is that fact that the ```
input: IR-receiver inside an USB DVB receiver...
``` line is still showing up in the dmesg, yet the remote does not work and there is not output from button presses when I run irw.

argh.

---

### Post by ianhaycox on 2009-10-07
> 
Will

make distclean

do something that deleting the folder would not?


no, sadly not. It is the equivalent of deleting the folder and unpacking the source again.

Sorry, don't know about your remote.

---

### Post by easyasmc2 on 2009-11-02
I am having a similar issue, ir reciever seems to be there but irw gives no response. I did lsmod | grep lirc and found that I don't have any lirc modules listed. Not sure if I am supposed to or if so which ones. Maybe this is a clue. Would be good to get it working.
will post if I have any luck

---

### Post by kja999 on 2009-11-02
> **wildbillkelso said:**
> Hello all.

My hard disk recorder is on its way out. I am new to Linux and am very impressed with Ubuntu,and I am interested in Mythbuntu very much. Ideally I would like a system that can record two uk free view programs simultaneously while I watch another on my television that has a built in freeview reciever. I would greatly apretiate any advice or thoughts on what hardware I would need to do this if it is at all possible, and what is recomended. Such as, Would I need a freeview tv card? Or do I need two? If so which ones are supported, or is it better to get a standard terrestrial card and use an external freeview decoder? It needs to perform quite well as my wife gives me grief when the recorder plays up and she misses a program. Sorry if these seem simple questions but I am new to all, this but it is rather interesting.

Thank you very much


Hi, Regards hardware compatibility, the mythtv wiki has lots of info in the hardware section
[http://www.mythtv.org/wiki/Category:Hardware](http://www.mythtv.org/wiki/Category:Hardware)

---

### Post by ffaker on 2009-11-10
> **easyasmc2 said:**
> I am having a similar issue, ir reciever seems to be there but irw gives no response. I did lsmod | grep lirc and found that I don't have any lirc modules listed. Not sure if I am supposed to or if so which ones. Maybe this is a clue. Would be good to get it working.
will post if I have any luck

Hmmmm.... thanks for this clue. Any luck with your investigations? I will try something around this tonight...

---

