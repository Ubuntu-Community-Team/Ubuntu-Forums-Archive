---
title: "Ipevo free 1 usb: Ubuntu fiesty"
date: 2007-10-09
forum: Multimedia &amp; Video
---

### Post by Matty2006 on 2007-10-09
The device has drivers for the Mac.. I am thinking that there must be a way to enable it in linux, namely ubuntu.

If anyone might point me in the right direction.. its would be nice to get this phone going with skype. 

Thanks,

-Matt

---

### Post by c0nph1g on 2007-10-09
I had it working in Fedora 5 except for the microphone. I think that was an ALSA/OSS bug from Skype 1.3 beta. I am not getting much joy with Feisty. I installed some universal driver that I forget but doesn't recognise any device. 

There seems to be a long (development) way round to get a fully working handset
[http://www.spinics.net/lists/linux-usb-devel/msg03](http://www.spinics.net/lists/linux-usb-devel/msg03)

Or some maddening toggling to activate the mike and earphone
[http://www.google.com/search?&q=%22usb-audio%22+deb](http://www.google.com/search?&q=%22usb-audio%22+deb)

or whatever you can find out

Cph

---

### Post by c0nph1g on 2007-10-09
OK I plugged in the phone and rebooted then ran usbview

The Free 1 USB Phone (Ipevo VP170) showed up and I made the following changes in Skype 1.4

Options > Sound devices 

Sound In         Free-1 USB Phone (hw:Phone,0)    
Sound Out         Free-1 USB Phone (plughw:Phone,0)    
Ringing         [Default - I can't get the ringer to sound]


The phone works fine now (just mike and earphone, no buttons)

I am not sure what I had done to my underlying config but I remember adding some usb package through synaptic package manager and maybe a driver

---

### Post by etereo on 2007-10-25
c0nph1g do you remember which "universal driver" you installed?

Or maybe some where you may have gotten it from...

Thnx

---

### Post by etereo on 2007-10-25
I just got it working on Gutsy with a free.2 ipevo.

The handset was detected automatically apparently, although it didn't show in usbview it did show in System-Preferences-Hardware Information.

So all I needed to do was go into skype and set the sound configs as you wrote.  The ringer does work but all the volumes were  super low by default.  You have to go into the ubuntu volume settings, then change the device to free.2 (or whatever model) and adjust them there.

The cool ipevo buttons aren't working yet.

ps: didn't install any new drivers, just a fresh gutsy

---

### Post by ChamPro on 2008-02-11
The microphone and speaker work fine for me in Gutsy. Very loud and adjusting the volume isn't possible since it makes the volume control freak out.

Unfortunately none of the buttons work and the phone doesn't ring. You have to rely on your PC speakers.

---

### Post by c0nph1g on 2008-02-11
If the PC speaker is handling the output then you might need to take another look at Options > Sound devices again

Sound Out 
Free-1 USB Phone (plughw:Phone,0)
To pass that to the handset speaker. 

These settings still allow the PC speaker etc to work if the USB phone is  not plugged in

Cph

---

### Post by jon_gunnar on 2008-02-24
> **c0nph1g said:**
> OK I plugged in the phone and rebooted then ran usbview

The Free 1 USB Phone (Ipevo VP170) showed up and I made the following changes in Skype 1.4

Options > Sound devices 

Sound In         Free-1 USB Phone (hw:Phone,0)    
Sound Out         Free-1 USB Phone (plughw:Phone,0)    
Ringing         [Default - I can't get the ringer to sound]


The phone works fine now (just mike and earphone, no buttons)

I am not sure what I had done to my underlying config but I remember adding some usb package through synaptic package manager and maybe a driver

Thank's for the info.works nicely.No big deal to make the call from skype,even it it had been nice if the buttons on the phone had worked.
But crystal clear sound.

---

