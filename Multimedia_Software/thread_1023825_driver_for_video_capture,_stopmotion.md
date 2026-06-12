---
title: "driver for video capture, stopmotion"
date: 2008-12-28
forum: Multimedia Software
---

### Post by FOffMicrosoft on 2008-12-28
Hey all, I'm fairly new to linux and enjoying it so far, mostly have been able to resolve my own issues by searching the net, but I've been stumped on this for a couple days.  I am running Ubuntu Hardy 2.6.24-22 and put in a PixelView XCapture PCI card.  I'm just looking to use it for stopmotion, not really video or audio at this point.  Here is the lspci command output, truncated:


 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)


And when I try to run stopmotion I get:


Forking for daemon mode
Error 22 occured while unmapping map


At first I was trying to test the camera with xawtv, which gave the output:


This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-22-generic)
xinerama 0: 800x600+0+0
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_REQBUFS(count=2;type=VIDEO_CAPTURE;memory=MMAP): Success


And here is the dmesg output, truncated to what looks relevant:


cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   50.910802] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 19
[   50.910902] cx88[0]: Your board has no valid PCI Subsystem ID and thus can't
[   50.910905] cx88[0]: be autodetected.  Please pass card=<n> insmod option to
[   50.910906] cx88[0]: workaround that.  Redirect complaints to the vendor of
[   50.910908] cx88[0]: the TV card.  Best regards,
[   50.910909] cx88[0]:         -- tux
[   50.910912] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:

etc.  It looks like the card number should be =3, but I can't figure out how to change it.

Can anyone tell me where to go from here?  I know I should do something with the driver but when I try to figure it out I end up running in giant circles all over the forums and the internet.  Any advice would be greatly appreciated.  Thanks.

---

### Post by cariboo on 2008-12-28
To set the card number create a file like this:

```
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=17
```

substitute what ever driver your capture device uses for saa7134, then save the file as something that makes sense to you, I named the file saa7134. THe next step is to copy the file to /etc/modprobe.d

```
sudo cp <filename> /etc/modprobe.d/
```

The final ste is to reload the driver, using modprobe or just reboot.

To find what driver your capture device is using, in a terminal type:

```
sudo lshw -C multimedia
```

and look for the driver in the output for example:

```
sudo lshw -C multimedia
[sudo] password for jim: 
  *-multimedia            
       description: Multimedia controller
       product: SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 7
       bus info: pci@0000:04:07.0
       version: d0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: **driver=saa7134** latency=64 maxlatency=40 mingnt=16 module=saa7134
```

The above is the output of the command on my computer, I haved bolded the driver section.

Jim

---

### Post by FOffMicrosoft on 2008-12-28
hey thanks jim, i just have a couple follow-up questions:

here's my driver output from the command sudo lshw -C multimedia:

  *-multimedia:0          
       description: Multimedia video controller
       product: CX23880/1/2/3 PCI Video and Audio Decoder
       vendor: Conexant
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: vpd pm bus_master cap_list
       configuration: driver=cx8800 latency=64 maxlatency=55 mingnt=20 module=cx8800


so i made a file called 8800 which is on the desktop, the file should just be a text editor file, right?

and the content of the file is:

alias char-major-81 videodev
alias char-major-81-0 cx8800
options cx8800 card=3

so i entered at the terminal:

sudo cp 8800 /etc/modprobe.d/

and the output was:

cp: cannot stat `8800': No such file or directory


so did i make the wrong kind of file, or should I have put it somewhere else to copy from?  I'm assuming I leave out the < > from the filename command above?  Obviously I'm a complete noob.  Again, appreciate the help.

---

### Post by cariboo on 2008-12-28
If the file is on your desktop, the command should be:

```
cp ~/Desktop/8800 /etc/modprobe.d/
```

If you are in a terminal you have to enter the full path to the file the tilde character is shorthand for /home/<user> where <user> is your username.

To test that the command will work in a terminal type:

```
sudo rmmod cx8800
```

there may be another module that depends on the cx8800, if there is it will print out what it is when you try to remove the module. After you remove the module in the same terminal type:

```
sudo modprobe cx8800 card=3
```

Then check to see if your capture card is working. with the file you created you won't have to manually insert the module every time you want to use your capture card, it will be done automatically on boot up.

Jim

---

### Post by FOffMicrosoft on 2008-12-29
hey thanks again jim, i got the file copied into modprobe.d when i figured out i had to put sudo in front of the copy command.  i rebooted afterwards.

then, the output for sudo rmmod cx8800 was: 

ERROR: Module cx8800 does not exist in /proc/modules


And if i start stopmotion and click on the camera button, i get the message 'No video device selected in the preferences menu', which i find strange because stopmotion doesn't have a preferences menu.  does this refer a preferences menu somewhere else then?

sudo lshw -C multimedia command output is now:

 *-multimedia:0 UNCLAIMED
       description: Multimedia video controller
       product: CX23880/1/2/3 PCI Video and Audio Decoder
       vendor: Conexant
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: vpd pm bus_master cap_list
       configuration: latency=64 maxlatency=55 mingnt=20

i don't see the driver info listed in configuration anymore, no idea what that means?

also i did a dmesg and the last 2 lines are:

[  777.635938] cx8800: Unknown parameter `card'
[ 2205.016483] cx8800: Unknown parameter `card'

and i tried xawtv just to see what it would say, here is output:

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-22-generic)
xinerama 0: 800x600+0+0
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available


so i think i got a little farther maybe?, once again i really appreciate the advice, it's hard to believe how patient you guys are with us who constantly need our hand held.

---

### Post by semjaza on 2009-07-27
Well the "Error 22 occured while unmapping map" message seems to be related to the vgrabbj settings.  If you add a "-G" in the preferences it works (at least on my machines)

I made this youtube howto video to show how to do it.

[http://bit.ly/dJj8N](http://bit.ly/dJj8N)

---

### Post by Paul D on 2009-12-01
This thread is 4 months old, but it is the closest thing I could find relating to the subject of my capture card. Perhaps others are attempting this with different brand cards.
I am trying to figure out about installing and using a capture card in Ubuntu 9.10. First, here is my understanding of the process; Power off, install card, turn power on.

Ubuntu appears to see My CTX Model MD001 PCI capture card as it is in the 4th PCI slot in my motherboard. In a terminal; lspci    reveals (short version)->  Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05).

 In the terminal; sudo lshw -C multimedia    reveals (short version)-> 
       -multimedia:1
       description: Multimedia video controller
       product: CX23880/1/2/3 PCI Video and Audio Decoder
       vendor: Conexant Systems, Inc.
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: vpd pm bus_master cap_list
       configuration: driver=cx8800 latency=32 maxlatency=55 mingnt=20
       resources: irq:19 memory:fa000000-faffffff

I guess from this that a driver has been found (driver=cx8800). However, 
in the terminal; dmesg    reveals (short version)->
[    8.676437] Linux video capture interface: v2.00
[    8.955362] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[    8.955407] cx8800 0000:00:0a.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    8.955867] cx88[0]: Your board has no valid PCI Subsystem ID and thus can't
[    8.955869] cx88[0]: be autodetected.  Please pass card=<n> insmod option to
[    8.955870] cx88[0]: workaround that.  Redirect complaints to the vendor of
[    8.955872] cx88[0]: the TV card.  Best regards,
[    8.955873] cx88[0]:         -- tux
[    8.955877] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[    8.955880] cx88[0]:    card=0 -> UNKNOWN/GENERIC
Then a bunch of card numbers are listed

Basically, here I think that this message is saying that the hardware is not completely set up yet. Here is the first issue for me.... The big list of brands and models of cards does not list exactly, the model of my card as listed in dmesg. I could try a few and see what happens?

To do that, I looked up the insmod command. It suggests to instead use modprobe.

Caraboo907 elsewhere in this thread talks about adding a script and doing stuff with the /etc/modprobe.d something or other. First off, modprobe.d is a folder containing some *.conf files. What will copying that file into that folder do? Does everything in that folder get run at bootup? What is the relationship between the folder and the command?
I also don't understand what the commands...
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=17
are for. What is char-major-81? What is the significance of the alias of videodev to that name? Or what the -0 is about?

I think that I am real close to getting this, but might as well be miles away.
Suggestions anyone? Caraboo907?

---

### Post by Paul D on 2009-12-04
Is there anybody out there?

---

### Post by 4ebees on 2010-01-01
> **Paul D said:**
> Is there anybody out there?

The likely response would be (to paraphrase): "Just nod if you can hear me. Is there anyone home?" However, this makes no  sense unless you are a Floyd fan :)

Sorry I can't help. There seems to be a bit of discussion in relation to the issues you've raised - just on different posts on this site and others.

I'm experiencing a related problem with a Logitech Quickcam 4000 which worked in Hardy 8.04 with Stopmotion, but doesn't now I've installed Karmic 9.10 :((

I'd suggest reading around a bit more - which appears to be what I'm going to need to do as well.

---

