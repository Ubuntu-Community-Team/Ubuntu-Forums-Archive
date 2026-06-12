---
title: "Hauppauge Nova T USB2 Timeout issues upon scanning"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by Markieman234 on 2007-04-30
Hi guys,

I've run into a bit of a roadblock with configuring my Hauppauge WinTV Nova T USB2 external card with kubuntu Feisty 7.04.
The card is installed okay with the proper firmware and mapped to the relevant device location, however when attempting a "scan" command I get the following messages:

```
root@markslinuxbocks:/usr/share/doc/dvb-utils/examples/scan/dvb-t# scan uk-PontopPike -v -v -5 channels.conf
scanning uk-PontopPike
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 690000000 0 1 9 1 0 0 0
>>> tune to: 690000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_1_2:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
>>> tuning status == 0x1b
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
dumping lists (0 services)
Done.
root@markslinuxbocks:/usr/share/doc/dvb-utils/examples/scan/dvb-t#
```

I've followed all the relevant DVB howto's and thread in this and other forums but have come to no avail.
I've also install the xine-ffdshow codecs that are mentioned to decode PAL DVB.
The reception of the signal is definetly all fine, I get a good signal under Media Center in Windoze.
Tuning in Kaffeine dosn't work either, it displays a signal reception quality percentage and a green light to confrim its locked, but dosn't pick up any channels.

MythTV also spits out similar tuning timout errors when doing a channel scan.


Any thoughts on this guys? So far everything else worked magically out of the box which is somewhat of a miracle given my past headaches with other Linux distro's.

Any feedback or suggestions are much appreciated, many thanks.


Mark Fulton

---

### Post by dentaku65 on 2007-05-02
try

```
sudo gedit /etc/modprobe.d/options
Add: options dvb-usb-dib0700 force_lna_activation=1 
```
and reboot

Using the force_lna_activation=1 turn on the internal signal amplifier 

Moreover if u are under Feisty the Nova-T goes offline by a issue of USB2 module ("can't tune dvb" under Kaffeine), the workaround is:

```
modprobe -r ehci_hcd
modprobe ehci_hcd
```

---

### Post by Markieman234 on 2007-05-03
Many, many thanks for that :)
I'll check it when I get in from work and let you know how I get on.:guitar:

---

### Post by m47h3us on 2007-06-24
i have a problem with timing out, i tried that aboved that did not work. 
im using mythtv to scan for the channels and i just says onver and over.
```
Timeout Scanning offset 1 -- no signal
Timeout Scanning offset 2 -- no signal
Timeout Scanning  -- no signal

```
im not sure what to do? can anyone help

---

### Post by m47h3us on 2007-06-25
come on, some one help you cant tell me that the Wintv nova-t usb2 93000 is the only f^%&ing digital card that does not work on ubuntu, cos as you see this is really pissing me off. im thinking of going back to xp again if no ones gona help me.

---

### Post by rgiskard on 2008-02-29
El problema no está en el Nova-TD stick. Este es muy sensible al ruido y necesitas un atenuador de señal como este: [http://img466.imageshack.us/img466/8633/s1069zm.jpg](http://img466.imageshack.us/img466/8633/s1069zm.jpg)
Se que el Windows no hace falta pero en Linux si :(

Yo tengo este Nova-TD: [http://www.hauppauge.co.uk/pages/products/data_novatdstick.html](http://www.hauppauge.co.uk/pages/products/data_novatdstick.html)
# lsusb
Bus 004 Device 005:  ID 2040:9580 Hauppauge

Después de instalar el atenuador puedo ver todos los canales en mi zona geográfica (Islas Canarias - España).

**** TRANSLATE (more or less ;) ) **************************************

The problem not is Nova-TD stick. This is very sensitive to noise. You need a atenuator like this: [http://img466.imageshack.us/img466/8633/s1069zm.jpg](http://img466.imageshack.us/img466/8633/s1069zm.jpg)
I know that you don't need in Windows but in Linux you need it :(

I have this Nova-TD: [http://www.hauppauge.co.uk/pages/products/data_novatdstick.html](http://www.hauppauge.co.uk/pages/products/data_novatdstick.html)
# lsusb
Bus 004 Device 005:  ID 2040:9580 Hauppauge

After I installed the atenuator, I can see in Kaffeine all channels in my geographic zone (Canary Islands - Spain)

---

### Post by gorski on 2008-05-30
Hi!

I'm a novice to all this, so please, can anyone guide me to install this TV card on Ubuntu 8.04, and at booting it says something like a new version of kernel "....17", if memory serves?

I have:

Hauppauge WinTV Nova-T USB2 93000

I wouldn't know where to start, since on Wiki there are no drivers, as the guy from Hauppauge told me.

Check this out, please:

[http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices#Hauppauge_WinTV-NOVA-T_usb2](http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices#Hauppauge_WinTV-NOVA-T_usb2) - aparently this should work for us... 

But! One goes here only to find an empty page:

[http://linuxtv.org/wiki/index.php/DiB3000P](http://linuxtv.org/wiki/index.php/DiB3000P)

Where are all these, please:

- dib3000-common.ko
- dib3000mc.ko
- dvb-usb.ko
- dvb-usb-dibusb-common.ko
- dvb-usb-nova-t-usb2.ko

...and how to install all of them - for a novice, that is?

Thank you kindly!!!!

---

### Post by gorski on 2008-05-30
Forgot to subscribe to thread [will have to edit the options in the user cp, of course but no time now, so...;)]...

---

### Post by gorski on 2008-06-02
No takers?:confused::(

---

### Post by gorski on 2008-06-02
A copy of my post from Urban75 forum, where I got the necessary impetus to continue... :)

> Actually, moved by Jaed, I went into it all again! I can see that 2 new posts were written in the meantime! Thanx a bunch! But solved it in the meantime, and here's how...

Found one link I missed, in the Google link by Jaed! [http://www.tonymcm.co.uk/content/view/1/2/](http://www.tonymcm.co.uk/content/view/1/2/) - it's all there, after all!!!

And, as I stated earlier, provided I find the driver and instructions, I am not lazy or stupid. It worked!

The problem I face now is how to force some viewers away from my webcam and direct them to my DVB-T card. Some are not allowing me to change the source via a GUI... Me TV is OK, it saw the new driver and scaned it all via a CP transmitter...

Well, must learn a bit more...

[http://www.tonymcm.co.uk/files/uk-Divis](http://www.tonymcm.co.uk/files/uk-Divis)

[http://www.artificialworlds.net/blog/2007/05/10/digital-tv-on-dapper-with-my-hauppauge-wintv-nova-t-card/](http://www.artificialworlds.net/blog/2007/05/10/digital-tv-on-dapper-with-my-hauppauge-wintv-nova-t-card/)

Very cool! Ta, boys!!!!:popcorn:

[Yes!!!:guitar:]

---

### Post by gorski on 2008-06-02
I should add: MythTV I added to my previous installation, messed it all up - I had to re-install it all. It became Mythbuntu and wouldn't do anything at all. Couldn't go anywhere. So, won't be doing anything with that for a while... Must find other stuff.

I shall install Kaffeine now and try not to alter anything in the basic setup [Ubuntu to Kubuntu - I do not wish that, right now, not before I learn more about this, anyway]...:guitar:

---

### Post by gorski on 2008-06-03
OK, **Me TV** and **Kaffeine** are working and all is well!

**But: does anyone know how to change the input device for**

1) **Zapping TV viewer** - this is what is displayed when my webcam is on:

> VBI initialization failed.
Cannot open '/dev/vbi0': 2, No such file or directory.
This probably means that the required driver isn't loaded. Add to your /etc/modules.conf the line:
alias char-major-81-224 bttv (replace bttv by the name of your video driver)
and with mknod create /dev/vbi0 appropriately. If this doesn't work, you can disable VBI in Settings/Preferences/VBI options/Enable VBI decoding.

and this when it's not on:

> Couldn't open /dev/video0, try other devices?

and then is says 

> Sorry, but "/dev/video0" could not be opened:
The device cannot be attached to any controller

2) **Xine** - input plugin failed to open mrl: "Sorry, no valid channels .conf found", i.e. must find a proper scanning plugin, learn how exactly to install it or find and install into a proper spot that particular file for UK/Crystal Palace transmitter... 'Seen the info about that earlier, so that I can do...

3) **Xaw TV** - won't even start/appear, only when my webcam is on, it gets that and displays it properly but I can not change the input, as it doesn't see the DVB-T USB2 card

4) **TVtime Television Viewer** - as above: I go to Input Configuration -> Change video source and nothing happens, as it keeps saying "No video source", i.e. it's not giving me the DVB-T option

5) **Klear** - like 2) - no channels.conf

6) Somebody mentioned **MPlayer** - but mine doesn't even have the possibility of DVB... I have **SMPlayer** and **MPlayer Movie Player**

Thank you kindly!:)

---

### Post by toothy on 2008-06-06
You're probably missing the firmware, which you can find here [http://ubuntuforums.org/showpost.php?p=4570186&postcount=6](http://ubuntuforums.org/showpost.php?p=4570186&postcount=6), unzip the file and copy dvb-usb-nova-t-usb_0.2.fw to /lib/firmware/your_kernel_version/, (get the kernel version from 'umame -a')

Next step is to get w_scan from [http://www.edafe.org/vdr/wscan.html](http://www.edafe.org/vdr/wscan.html)
Unzip the file, the binary is supplied, so you can enter './w_scan -k > channels.dvb'. Copy channels.dvb to ~/.kde/share/apps/kaffeine/, then fire up Kaffine and hopefully all should be well

---

### Post by gorski on 2008-06-25
Sorry, I just saw this reply...

Kaffeine itself was not the problem, as it scanned no probs, so obviously it had the plugin...:popcorn:

The other progs listed, however, did...:(

Thanx anyway, m8!!!:guitar:

---

