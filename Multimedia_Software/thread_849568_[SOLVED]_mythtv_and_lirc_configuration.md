---
title: "[SOLVED] mythtv and lirc configuration"
date: 2008-07-04
forum: Multimedia Software
---

### Post by pipenew on 2008-07-04
Hi, 

I'm new to Ubuntu but I've managed to get mythtv and lirc working. I say lirc is working becuase when I use the irw command, I can see all the buttons on the remote working properly. Also mythtv is working becuase, oh well, because it's working ... too bad they don't work together yet, the remote and mythtv at the same time. 

By following some other threads, I've discovered that I don't see the IR device when I look at the devices file:

cat /proc/bus/input/devices

[HTML]I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0003 Vendor=045e Product=007d Version=0100
N: Name="Microsoft Microsoft 3-Button Mouse with IntelliEye?"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input5
U: Uniq=
H: Handlers=mouse1 event5 
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10
[/HTML]

Also interesting is that lirc-start fails but lirc-restart doesn't:

[HTML]sudo /etc/init.d/lirc start
 * Loading LIRC modules                        [ OK ] 
 * Starting remote control daemon(s) : LIRC    [fail][/HTML]
[HTML]sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC     [ OK ] 
 * Loading LIRC modules                        [ OK ] 
 * Starting remote control daemon(s) : LIRC    [ OK ][/HTML]

Other information about my system:
Ubuntu 8.04
Kernel 2.6.24-19-generic
Hauppauge WinTV-PVR-500
MCE remote [(model 1069 from the wiki)]("http://www.mythtv.org/wiki/index.php/MCE_Remote")
I've followed [THIS LINK]("http://www.gexperts.com/blog/archives/2008/06/entry_347.html") to install lirc
Also I've been trying [THIS LINK ]("http://parker1.co.uk/mythtv_ubuntu2.php") to make it work in mythtv

Any ideas for the experts out there??
I can post hardware.conf and lircd.conf if needed.

Thanks in advance

---

### Post by funkydan2 on 2008-07-06
Mythbuntu comes with some scripts that automatically setup some remote controls, and I think the MCE one is included.  Have you tried installing some of the mythbuntu packages (particularly the control panel, but you could install the whole mythbuntu-desktop package) and see if they're any help?

---

### Post by pipenew on 2008-07-06
I'm actually not using mythbuntu distribution. I just mythtv in Ubuntu. I don't know if there's a lot of differences but I can see that my system starts as ubuntu instead of mythbuntu. Can you please explain to me how can I install these control panel options? I can give it a try
Thanks

---

### Post by funkydan2 on 2008-07-06
Yep, if you're a fan of the command line:
'sudo apt-get install mythbuntu-control-centre mythbuntu-lirc-generator'
or else search for 'mythbuntu' in synaptic and install mythbuntu-control-centre and mythbuntu-lirc-generator.

If your machine is primarily a mythtv machine, you may prefer to install the mythbuntu-desktop package which will automatically install a whole lot of things for mythtv, but I think the control-centre is the most useful part.

---

### Post by pipenew on 2008-07-07
It didn't work right after but just played a little with the setting and followed some more the links in the initial post and everything works great! (specially after telling the mythtv how to interpret the lirc events).

```
cp lircrc ~/.lircrc
cd ~/.mythtv
ln -s ../.lircrc lircrc

``` 

I'm definitely staying with Ubuntu, I gotta say I had my doubts for some time, not that is perfect .. I still need my graphic driver to recognize DVI full resolution, play videos in youtube better (not as choppy) and start to find out how to sync my ipod and life without Windows is possible.

Thanks funkydan2 !

---

