---
title: "DVB-T not lip-sync"
date: 2012-09-14
forum: Multimedia Software
---

### Post by groundnut on 2012-09-14
I am using a PCTV nanoStick Solo(73e SE)for DVB-T reception on both a Windows and an Ubuntu computer.
On the Windows computer sound and vision are synchronous.
This is not the case on my Ubuntu system.
I use Kaffeine as tuner software on Ubuntu.

Is there any solution to my problem?

---

### Post by Bucky Ball on 2012-09-14
You could try another app and see if you get the same result. MeTV has an auto-scan and is really easy to use. 

My main squeeze is Xine. Quick, easy and I don't need the bells and whistles. Gxine is fine, too. You need to create a channels.conf file for those two though using w_scan.

KDE apps can sometimes be problematic on anything other than KDE. Presuming Kaffeine is KDE app so could have something to do with it.

---

### Post by groundnut on 2012-09-14
Thanks Bucky Ball

Now I've MeTV up and running.
Sound and vision are now synchronous.
The static image quality is good.
However the dynamic image quality is not on par with Kaffeine due to appearing horizontal stripes.
Can this be solved?

---

### Post by Bucky Ball on 2012-09-14
I'm about 750Kms away from my MeTV setup right now so can't experiment, sorry. You could try tinkering with some of the vid settings ...

You have the correct drivers for your vid card? What have you got in 'Additional Drivers'?

---

### Post by groundnut on 2012-09-15
In the mean time Me TV stopped working for some reason.
At some time the image got distorted like a bad reception of the signal. Later there was no signal at all.
I get a message like: exceeding time during reading.

Now also Kaffeine stopped working.
It says no device found.

What can I do to solve this problem?

---

### Post by Bucky Ball on 2012-09-15
How much RAM have you got and what processor? If it's saying no device found that is strange.

Unplug the dongle, restart the machine. When back at a desktop, before doing anything else, plug the dongle in and run this in a terminal immediately after plugging in:

```
dmesg
```Do you see the dongle recognised when you plug it in, down near the bottom of the output of dmesg?

---

### Post by groundnut on 2012-09-16
My machine has 4GB RAM and a Core2Quad Q8200 processor.

You can see the bottom of the output of dmesg below.
Now MeTv works again.
Kaffeine still says no device found.

Back to the MeTV stripes problem.
Most programs show horizontal stripes when the image is dynamic.
However some programs do not have this problem.

I have the current Nvidia driver installed for my graphics card GeForce 9600 GT.
The problem with the stripes did not happen with Kaffeine.
Also viewing videos with a browser is no problem.



[   82.212701] dvb-usb: found a 'Pinnacle PCTV 73e SE' in cold state, will try to load a firmware 
[   82.212999] IR JVC protocol handler initialized 
[   82.214316] IR Sony protocol handler initialized 
[   82.215671] IR MCE Keyboard/mouse protocol handler initialized 
[   82.217213] lirc_dev: IR Remote Control driver registered, major 250 
[   82.217400] IR LIRC bridge handler initialized 
[   82.220292] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw' 
[   82.421836] dib0700: firmware started successfully. 
[   82.924106] dvb-usb: found a 'Pinnacle PCTV 73e SE' in warm state. 
[   82.924169] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer. 
[   82.924218] DVB: registering new adapter (Pinnacle PCTV 73e SE) 
[   83.127238] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)... 
[   83.338880] DiB0070: successfully identified 
[   83.364008] Registered IR keymap rc-dib0700-rc5 
[   83.364152] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4.4/rc/rc0/input11 
[   83.364222] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4.4/rc/rc0 
[   83.364365] dvb-usb: schedule remote query interval to 50 msecs. 
[   83.364368] dvb-usb: Pinnacle PCTV 73e SE successfully initialized and connected. 
[   83.364612] usbcore: registered new interface driver dvb_usb_dib0700

---

### Post by Bucky Ball on 2012-09-16
Well, that's getting picked up and installed okay by the looks of the dmesg. Not sure where I'd go from there, sorry. As I say, don't have that box around right now to experiment at this end.

---

### Post by groundnut on 2012-09-16
Thanks Bucky Ball.

For now I will settle with the current situation.

---

### Post by Bucky Ball on 2012-09-17
Just finally; have you figured out how to make a channels.conf file with w_scan? w_scan is part of the dvb-apps which you can find in Synaptics or SCentre. Once you created that file you can use any number of tv viewers. As I said, xine is my favourite. 

You create the channels.conf file (one might already exist for your area if you have a dig) and go to /home/your_user/.xine and put that channels.conf file in there. Boot xine and it should be able to find the channels. There are commands that will create the channels.conf file and write it straight to that folder in the process. Again, have a dig because all my info on this is not at hand. 

Good luck ...

---

### Post by groundnut on 2012-09-20
I am busy with Xine.

I have found the following site:
[http://linuxtv.org/wiki/index.php/Xine]("http://linuxtv.org/wiki/index.php/Xine")
I also have w_scan and dvb-apps and xine installed.
I don know why but xine has no menu.

from the link above I executed in two steps:

mkdir -p ~/.xine
scan /path_to/initial_tuning_file >~/.xine/channels.conf

However as you can see below the second step failed.

How can I solve this problem?


tony@xp:~$ sudo scan /path_to/initial_tuning_file >~/.xine/channels.conf
scanning /path_to/initial_tuning_file
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy

---

### Post by Bucky Ball on 2012-09-20
```
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy
```Can't remember exactly how to fix, change or check this so bear with me. You're possibly using /adapter1/frontend0 instead of /adapter0/frontend0. If you unplug and plug back in then check dmesg think will let you know what adapter it's picked up as. Could be wrong ...

I also don't remember how to do this but you sound like you're in the right place to find out; pretty sure you can add the relevant adapter details to your channel.conf code:

```
scan /path_to/initial_tuning_file >~/.xine/channels.conf
```Incidentally, if you have xine already install there is no need to mkdir; .xine should already be there in /home/user. To see hidden files/folders  (which is what the . before the folder name signifies) hit control+h. 

Secondly, make sure xine and all other apps that might be using the  device are  closed before attempting to scan and generate a channels.conf so you know the  device isn't busy ...


PS: Way to go with the learning curve on the DVB-T! I went through the same thing a couple of months ago; wish I was anywhere near that box so I could help you more. Making the channel.conf was the trickiest but sounds like you're almost there. Also, did you try the search for 'channels.conf your_location', whatever your location is? One might exist. That way you can just drop a copy in the /.xine folder, and any other apps /. folder that needs one, and launch xine.

 ;)

PPS: You would think MeTV would create a channels.conf during auto-scan but it doesn't appear to, at least I couldn't find one, and it's seems to be set-up  differently to the others .

---

### Post by groundnut on 2012-09-24
Do I need the Xine dvb input plugin in my case?

---

### Post by Bucky Ball on 2012-09-24
Don't know, sorry. Don't remember it. I'll be at that machine tomorrow night (in about thirty hours) so remind me then. I'll be able to check whatever you need. ;)

---

### Post by groundnut on 2012-09-26
reminder for Bucky Ball:

Do I need the **[COLOR="Red"]Xine dvb input plugin[/COLOR]** to solve the following problem?

main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy

---

### Post by Bucky Ball on 2012-09-26
Ha, sorry. ;( Home postponed for a day. Back in another twenty or so hours ...

Looking at this page doesn't give any clues:

[http://www.linuxtv.org/wiki/index.php/Xine](http://www.linuxtv.org/wiki/index.php/Xine)

Your dongle seems to be working fine though so don't think that's the problem.

---

### Post by groundnut on 2012-09-26
Thank you Bucky Ball,

I will ignore input plugin for now.

---

### Post by Bucky Ball on 2012-09-27
Yea, think that is part of something else, possibly dvb-apps. Home now so find attached a screenshot of Synaptics showing the results of a quick search for 'dvb t' and what I have installed in Xubuntu 12.04. Makes no difference; you should have the same in Ubuntu (maybe a few extras).

---

### Post by groundnut on 2012-09-27
I don't know why, but I just managed to get it right in Kaffeine (sound and vision synchronous) .
Maybe it worked now because I deleted the configuration files of Kaffeine.(~/.kde/share/apps/kaffeine)


many thanks for your help!

---

### Post by Bucky Ball on 2012-09-27
All good then. Have fun! ;)

---

