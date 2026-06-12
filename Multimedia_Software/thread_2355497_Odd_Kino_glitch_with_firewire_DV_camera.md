---
title: "Odd Kino glitch with firewire DV camera"
date: 2017-03-13
forum: Multimedia Software
---

### Post by Bucky Ball on 2017-03-13
Hi all,

Xubuntu-core 16.04.2 LTS, Kino 1.3.4, old Panasonic NV-DS60 DV camera connected via firewire. 

When I switch the camera off, dmesg gives me this when I switch it back on:

```
[ 2164.226240] firewire_core 0000:03:01.0: rediscovered device fw0
```

All good. In /dev there is /dev/fw0 so that's all good. Open Kino and go to 'Capture' and get this message along the bottom of the screen:

[quote=Kino error]WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394![/quote]

Looking in /dev, there is not /raw1394. I got as far as working out this has been deprecated and it is now /dev/fw0(?). I got as far as trying this, [from this page]("http://sharpeespace.blogspot.com.au/2012/06/capturing-firewire-1394-camcorder.html"):

```
sudo ln /dev/fw0 /dev/raw1394
```

... which I presume creates the symlink of the real camera device called /raw1394. Then I opened Kino as root as advised on the same link using:

```
gksu kino
```

Changes the error, but that's it. Now I get:

[QUOTE=Kino error]No AV/C compliant cam connected or not switched on? [/QUOTE]

I was looking at the /dev folder in Thunar (staring blankly at 'fw0') while I had the camera on, Kino on with an error. Up popped another entry in the /dev folder: fw1! What the ... I checked Kino and the capture controls were available, no error. :-k Just as I was getting excited, error came up, controls greyed, fw1 gone from /dev folder. It popped up again, no error and controls, then disappeared again, popped up, but this time, error remained in Kino and no controls.

I only got this all up and running a couple of nights ago. Then, the camera was recognised by Kino and everything was working. No diddling or fiddling required. To begin with. Capture controls were available. Then things became dodgy. Controls occasionally disappeared, Kino crashed (locked up) once or twice. Tonight, Kino locked up and locked up the whole machine. Only option was the restart button.

After years I finally have some time to digitise the meat from fourteen nearly 15 year-old DV tapes while they'll still play and I still have the functional technology to play them. Goes without saying, but I wouldn't be going to all this bother if the stuff on the tapes wasn't priceless. Family stuff and has been on the bucket list for years. :)

Any thoughts, tips, ideas, suggestions, solutions much appreciated. 

PS: The weird thing is that I did have a look at this when I was first into Ubuntu some nine years ago and got the camera working, no idea how. Still got test captures from then. Thought it would be plug and play currently, but hey, ancient camera. The camera might be the issue. Or the camera power supply.

---

### Post by Bucky Ball on 2017-03-16
Le Boomp.

---

### Post by walterav on 2017-03-18
On both ubuntu 16.04 amd64/i686 kernel 4.4.x I'm able to get all ancient DV FireWire camcorders working (sony/canon/jvc) and even pioneer CABLE-PVR, (H)DV-in and DV-out. I haven't tested ubuntu 16.04.2 which may run with a newer kernel and firewire stack changes (which may be broken). 
However I did got "kino" running with DV-out by correcting symlinks and access rights to /dev/raw1394... but it also needs some pulseaudio related fixes otherwise playbackspeed is 100x realtime and strange stutter performance. For now I can only guide you through terminal based step by step commands to let you capture your tapes. 
 
So first try these terminal steps and please post the output from the following commands.

Which kernel do you use?
```

uname -a

```

Which firewire pci/pci-e adapter chipset are you using?
```

lspci | egrep "IEEE|Ieee|ieee|1394|Fire|FIRE|fire|OHCI|Ohci|ohci"

```

Which FW kernel modules are loaded?
```

lsmod | egrep "IEEE|Ieee|ieee|1394|Fire|FIRE|fire|OHCI|Ohci|ohci|RAW|Raw|raw"

```

What IRQ does your PCI(e) FW card uses?
```

cat /proc/interrupts | egrep "firewire|ohci"

```


What FW GUID number does your PCI/PCIE adapter and DV camcorder (if detected) have?
```

dmesg | grep GUID #s400 are probably the pci(-e) chipsets itself, dv/hdv devices are probably s100

```

Both FireWire adapters pci(e) and (H)DV camcorders/vtr use their own "/dev/fwX" number.
```

ls -la /dev/fw*

```

Since you reported you only saw "/dev/fw0" this means the camcorder isn't detected but the FW adapter is re-initialising while you turn-on/off reinsert your camcorder.  This can also be because of BAD/broken FireWire cables!

Please try "dvgrab" (h)dv CLI capture tool, if your camera is detected.
```

sudo apt-get install dvgrab
dvgrab -f raw -s 0 ~/Destkop/tape1-shot.dv #captures dv from tape from 1st camcorder in VCR mode , -s 0 means unlimited filesize
dvgrab -noavc -f raw ~/Desktop/testcapturecamerastream.dv #captures dv fron camcorder in CAMERA mode, files usable by dvswitch/dvpause Final Cut X/Pro/Express

```

If you would like to use FireWire based services without root sudo permissions, all (H)DV camcorders will have to be detected as FW video device by udev. This works for almost all camcorders, but sadly for some ancient Sony VX2000 cameras this is not the case. But by patching udev ourself we can make it detect the camera as a video device with the correct user / permissions and we can use it without sudo or root permissions.  

```

ls -la /dev/fw*
getfacl /dev/fw*
cat /sys/bus/firewire/devices/fw1/* #shows more firewire info like ATTR

#do you see 
#wrong group root/video, no rw rights, missing +attribute, ATTR different!

#patch udev with correct ATTR to fix this
#quick&dirty autopatch for sony vx2000
sudo sed -i 's/0x010001/0x01000/g' /lib/udev/rules.d/50-udev-default.rules
sudo sed -i 's/0x010001/0x01000/g' /lib/udev/rules.d/70-uaccess.rules

```

Remember good firewire cables really make a difference, especially when you run multiple brands of camcorders, lengths of cables during live mixing streaming of video. For more info: [https://github.com/walterav1984/dvswitch](https://github.com/walterav1984/dvswitch)

EDIT
I missread your post about only finding /dev/fw0, but you also mentioned /dev/fw1 so I think you have a bad cable. Please just try dvgrab for ease to capture all your tapes, it can do scene detection file splitting as well.

---

### Post by Bucky Ball on 2017-03-18
Thanks for your input, walterav. Spent yesterday wrestling with a printer in XP and virtualbox and am bit busy with other things for the next day or two, but will get to this shortly and report back.

Thanks again.

---

### Post by Bucky Ball on 2017-03-19
Sooner than I thought. Firstly, dvgrab works fine. Got it going by accident when I was first doing this and captured some footage from the camera by accident, so 'tick' there. First things first though, I'm going to grab a new firewire cable. This one's old, took me a long time to find it, and I should have known better. ;) Just playing around with this again and from the slightly odd behaviour I'm seeing from dmesg when I plug it in, looks like a cable issue. 

For instance, I switched it on, checked dmesg, nothing. No sign of firewire device coming to life. Switch it off. Sees it.

... and then 'bingo'! I pulled the firewire cable out of the camera while it was on, plugged it back in, the system creates fw1 and dmesg spits me this:

```
[ 3829.554501] firewire_ohci 0000:03:01.0: isochronous cycle inconsistent
[ 3830.050879] firewire_core 0000:03:01.0: giving up on node ffc1: reading config rom failed: bus reset
[ 3830.247909] firewire_core 0000:03:01.0: phy config: new root=ffc1, gap_count=5
[ 3830.962287] firewire_core 0000:03:01.0: created device fw1: GUID 00804580b112cb7e, S100
```
 
Controls are working faultlessly. I have no idea what happened, I could have a guess, but certainly not expecting it to be reliable after what's gone on. Firewire cable here I come. Thanks again and I will update later.

* And final update for the night: it's the cable. All was working great. Left the room for twenty minutes, came back to get to it, bumped the cable and that was the end. No device, no controls, no mouse, machine locked. Didn't expect stability. 

Possiblity it might just work exactly as expected with a reliable cable. Let's find out.

---

### Post by walterav on 2017-03-19
Good to hear you are progressing, however for the hard lockups check IRQ usage (sharing/conflicts) and maybe try to put pci(e) FW adapterin other slot. I don't recall real hard lockups running 4 camcorders at the same time only fw stack crashing.

---

### Post by Bucky Ball on 2017-03-20
And the beat goes on. Wasn't that simple. Brand new firewire cable. Computer off, camera plugged in and off. Switch computer on, open terminal, switch on camera, run dmesg, now I get this:

```
[   22.470423] firewire_ohci 0000:03:01.0: isochronous cycle inconsistent
[   25.007093] firewire_core 0000:03:01.0: giving up on node ffc1: reading config rom failed: bus reset
[   25.506823] firewire_core 0000:03:01.0: rediscovered device fw0
[   25.953292] firewire_core 0000:03:01.0: phy config: new root=ffc1, gap_count=5
[   26.007587] firewire_ohci 0000:03:01.0: node ID not valid, new bus reset in progress
[   26.450725] firewire_core 0000:03:01.0: giving up on node ffc0: reading config rom failed: bus reset
[   26.506832] firewire_core 0000:03:01.0: giving up on node ffc0: reading config rom failed: bus reset
[   26.506842] firewire_core 0000:03:01.0: rediscovered device fw0
[   28.007174] firewire_core 0000:03:01.0: giving up on node ffc1: reading config rom failed: bus reset
[   28.506819] firewire_core 0000:03:01.0: rediscovered device fw0
[   28.950774] firewire_core 0000:03:01.0: phy config: new root=ffc1, gap_count=5
[   29.010063] firewire_ohci 0000:03:01.0: isochronous cycle too long
[   29.450642] firewire_core 0000:03:01.0: giving up on node ffc0: reading config rom failed: bus reset
```

The following appears to be a clue, although to what I do not know. Hopefully you will. :) When I switch the camera *_off_* and run dmesg, it has rediscovered fw0:

```
[  611.133085] firewire_core 0000:03:01.0: rediscovered device fw0
```

The firewire card in the computer has two large (6 pin?) sockets and a smaller one (4 pin?). I am using the small plug of the cable in the camera and the larger plug into the computer. Have tried both larger sockets on the firewire card and no different. Same dmesg. I'll continue to dig through these messages and re-read your longer post and see what I can find. If you have any ideas or would like any further info relating to these new messages, let me know. Cheers. ;)

PS: The firewire card:

```
03:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
```

Kernel: 4.4.0-67-generic, the latest 16.04.2 LTS kernel I guess. One thing is for certain: when the card worked last night it was using fw1. That is nowhere to be seen today. Truly a mystery, at least to me. I'm starting to think perhaps camera socket, although I really don't want to! That is 'worst possible case scenario'.

---

### Post by Bucky Ball on 2017-03-20
Ok. Just spotted something. Ran your commands for the info and found an anomaly. Comparing the output of these two commands ...

```
dmesg | grep GUID
[  312.405543] firewire_core 0000:03:01.0: created device fw1: GUID 00804580b112cb7e, S100
[  412.507913] firewire_core 0000:03:01.0: created device fw1: GUID 00804580b112cb7e, S100
[  606.814295] firewire_core 0000:03:01.0: created device fw1: GUID 00804580b112cb7e, S100

ls -la /dev/fw*
crw------- 1 root root 247, 0 Mar 20 16:05 /dev/fw0
```

... the fw GUID is fw1 and the camera is using fw0. Wonder how it magically flipped to fw1 and worked last night, which is making me wonder whether this is a hardware issue. Can we force the camera to use fw1 and that may work?

Incidentally, after the other two commands you gave at the beginning of the section on udev, I get this from the third:

```
cat /sys/bus/firewire/devices/fw1/*
cat: '/sys/bus/firewire/devices/fw1/*': No such file or directory
```

I preceded no further as I'd prefer not to get too 'ad hoc' and also because it says

```
#quick&dirty autopatch for sony vx2000
```

I have a Panasonic, although it may or may not work on that.

* Update: with further reading, think I'm understanding. fw0 is the firewire interface and fw1 is the firewire device? Yes? Then I'm getting the interface and not the device, because:

```
ls /dev/fw*
/dev/fw0
```

---

### Post by walterav on 2017-03-20
The one and only really usefull first debug step you already doing is run "dmesg" after turning on your camera and look for "/dev/fw1" since /dev/fw0 is the via firewire adapter, all the other steps I wrote do not have effect on whether your system detects fw1 or not. Getting /dev/fw1 with a valid GUID code is top priority. Changing cables / FW adapter (cheap on aliexpress) or even reboot your whole PC if you run into the isochronous/rom errors before the firewirestack would behave normally again will set you further.

```

[   22.470423] firewire_ohci 0000:03:01.0: isochronous cycle inconsistent
[   25.007093] firewire_core 0000:03:01.0: giving up on node ffc1: reading config rom failed: bus reset
[   25.506823] firewire_core 0000:03:01.0: rediscovered device fw0
[   25.953292] firewire_core 0000:03:01.0: phy config: new root=ffc1, gap_count=5
[   26.007587] firewire_ohci 0000:03:01.0: node ID not valid, new bus reset in progress
[   26.450725] firewire_core 0000:03:01.0: giving up on node ffc0: reading config rom failed: bus reset
[   26.506832] firewire_core 0000:03:01.0: giving up on node ffc0: reading config rom failed: bus reset
[   26.506842] firewire_core 0000:03:01.0: rediscovered device fw0
[   28.007174] firewire_core 0000:03:01.0: giving up on node ffc1: reading config rom failed: bus reset
[   28.506819] firewire_core 0000:03:01.0: rediscovered device fw0
[   28.950774] firewire_core 0000:03:01.0: phy config: new root=ffc1, gap_count=5
[   29.010063] firewire_ohci 0000:03:01.0: isochronous cycle too long
[   29.450642] firewire_core 0000:03:01.0: giving up on node ffc0: reading config rom failed: bus reset

```

Although having a new FW cable, these "dmesg" isochronous/rom errors are typical debug messages for a GOOD new FW cable being INCOMPATIBLE with a certain FW camera. Trust me debugging FW is hair pulling. Using a longer cable which may have other shielding quality may solve this issues although this cable would work fine on a other brand FW camera... but not yours. I'm mainly using 6>4 pin cables 4.5meters from FW adapter to FW camera. Some camera's refuse to work with 1.5meter high quality shielded cable but run fine on 4.5 meters... 

As far as physical/visual cable differences look inside the 4 pin header of the FW cable and look how far the 4 copper pins reach OUT to the edge of the connector, you may find that some cables have almost 2 millimeter shorter pins to contact the pins inside the camcorder.

---

### Post by Bucky Ball on 2017-03-20
> **walterav said:**
> Getting /dev/fw1 with a valid GUID code is top priority.

+1. Where my understanding of it has arrived.

> **walterav said:**
> Changing cables / FW adapter (cheap on aliexpress) or even reboot your whole PC if you run into the isochronous/rom errors before the firewirestack would behave normally again will set you further.

+1. I was planning on buying a new card tomorrow. I thought I may have damage this one installing it. Last resort.

> **walterav said:**
> Although having a new FW cable, these "dmesg" isochronous/rom errors are typical debug messages for a GOOD new FW cable being INCOMPATIBLE with a certain FW camera. Trust me debugging FW is hair pulling.

That had crossed my mind because of some of the things I'd been seeing in the outputs and some of the hints at it online. And yes, I don't need to take your word for it. When I first tried this in Ubuntu years ago I ended up with less hair (but it also ended up working perfectly). This one has been a bit painful also. 

> **walterav said:**
> Some camera's refuse to work with 1.5meter high quality shielded cable but run fine on 4.5 meters.

I think the new one is the former. I'm finding firewire cables hard to find where I am. One store down, one to go so will check if they have longer. 

As it worked perfectly for a magic half hour last night, I am fairly confident that with compatible hardware, this is going to be a matter of 'plug and play'. The messages have been erratic and unstable. And hey, I might need to spend a bit on another card, and perhaps even another cable, but it's cheaper than finding and buying another old DV camera!

Thanks for your further help. :)

PS: Yea, now I think of it ... this did work perfectly years ago, but the firewire card has changed. I have the same camera and was using the same cable last night when the camera worked, but now have a different card. 

With this in mind, that the camera and the cable work together (as proven by past experience), would it perhaps not be wise to be looking to buy a compatible firewire card? Any way of knowing which? Seems the card and cable need to be compatible with the camera, not the other way around, so I have the camera and cable. :-k

---

### Post by Bucky Ball on 2017-03-20
Looks like we might have a winner. Took a punt and went for the 4pin to 4pin cable. Plugged it up, switched the computer on, switched the camera on, received the following:

```
dmesg | grep firewire
[    0.773785] firewire_ohci 0000:03:01.0: enabling device (0080 -> 0083)
[    0.830544] firewire_ohci 0000:03:01.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x11
[    1.330335] firewire_core 0000:03:01.0: created device fw0: GUID 0011223333666688, S400
[   34.169745] firewire_ohci 0000:03:01.0: **isochronous cycle inconsistent**
[   34.869372] firewire_core 0000:03:01.0: created device fw1: GUID 00804580b112cb7e, S100
[   34.869375] firewire_core 0000:03:01.0: phy config: new root=ffc1, gap_count=5
[   34.869465] firewire_core 0000:03:01.0:** IRM is not 1394a compliant, making local node (ffc0) root**
[   34.869466] firewire_core 0000:03:01.0: phy config: new root=ffc0, gap_count=5
```

Few errors and oddities, but there was fw0 AND fw1. Launch Kino, hit 'Capture', works faultlessly. Controls are available and work and no problem. 

The 4 to 4 pin seems to have solved the issue. No idea about those errors in the terminal output (in bold), but if it's working, not going to question them. Maybe it's the cable that has made this work, maybe the larger sockets on the card are damaged but the 4 pin's fine, who knows. What I do know is same length (short) cable with 4 to 4 pin being the only diff. :-k

I will have a good session with the camera later when I have some time. If it all hangs together, will mark this as solved. Thanks again for all your help. :)

---

