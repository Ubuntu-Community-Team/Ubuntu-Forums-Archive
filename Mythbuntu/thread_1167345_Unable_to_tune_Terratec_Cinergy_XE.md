---
title: "Unable to tune Terratec Cinergy XE"
date: 2009-05-22
forum: Mythbuntu
---

### Post by Triptol on 2009-05-22
I just bought a new Terratec Cinergy XE to replace my broken DVB-T usb-stick.

Somehow I just can't get it to work with Mythtv (using the fixes repos: deb [http://ppa.launchpad.net/mythbuntu/fixes-0.21/ubuntu](http://ppa.launchpad.net/mythbuntu/fixes-0.21/ubuntu) jaunty main).

Kaffeine and me-tv have no problem with the card, they find all the channels and I can tune them.

However as soon as I start mythtv-setup and tune the card, I get the following lines on the console:
```
2009-05-23 01:08:45.637 FE_GET_INFO ioctl failed (/dev/dvb/adapter0/frontend0).
2009-05-23 01:08:45.638 FE_GET_INFO ioctl failed (/dev/dvb/adapter0/frontend0).
```
The setup reports that it is not able to communicate with the card (I can't exactly tell the English error message since it is a German installation which says: "Konnte die Karte nicht ansprechen").

Google didn't give me the answer, neither have I been able to find anything on the forum. I tried changing the rights on everything in the /dev/dvb folder to 666, but that didn't do the trick.

Any suggestions would be highly appreciated.

Update: if I remove the modules and reinsert them (rmmod / modprobe) I can start the tuning with mythtv-setup, however it will not find any channels and after the tuning the situation is the same as the one described above.

---

### Post by Caysho on 2009-05-23
Kaffeine and mt-tv are both xine based, so I would hope they're consistent :)

What is the device ID ?
The linuxtv wiki shows three XE models.

Mythtv cannot open the device.  The mythtv log files might give a clue, and you can use fuser to check which process is locking the device.

Does mythtv-setup do anything if it's the first thing you run ?

---

### Post by Triptol on 2009-05-23
The device ID:
```
$ lsusb | grep -i terratec
Bus 001 Device 004: ID 0ccd:0069 TerraTec Electronic GmbH Cinergy T XE DVB-T Receiver
```
Based on the fact that xine :-) works, I would say the card is installed correctly.

When I start the mythtv-setup and navigate to the tuning part of DVB-T I issue the following fuser command.
```
fuser /dev/dvb/adapter0/frontend0
```
It gives nothing, so I guess that means nothing is using it (unless I don't understand that command, or I am specifying the wrong path.)

The logfiles are not giving any useful information. Which is what I would expect, since I have no channels setup yet, so there is no way the backend could tune to one of the channels. Mythtv-setup only gives the output stated in the first post.

My mythbox is configured in such a way that it always starts the backend, then mythwelcome which in turn starts mythfrontend. I would rather not change that configuration (it has been a lot of work setting it up). But I closed all programs and reinserted the card. Then I started mythtv-setup, but I still get the same results.

Any other ideas?

---

### Post by Caysho on 2009-05-23
Run kaffeine from a terminal and watch a tv snippet.
Post the result.  I suspect mythtv might be using the wrong device path.

---

### Post by Triptol on 2009-05-23
```
$ kaffeine 
/dev/dvb/adapter0/frontend0 : opened ( Afatech AF9013 DVB-T )
0 EPG plugins loaded for device 0:0.                         
Loaded epg data : 1376 events (36 msecs)                     
mythtv@shire:~$ Tuning to: WDR D&#65533;sseldorf / autocount: 0     
DvbCam::probe(): /dev/dvb/adapter0/ca0: : No such file or directory
Using DVB device 0:0 "Afatech AF9013 DVB-T"                        
tuning DVB-T to 674000000 Hz                                       
inv:2 bw:0 fecH:9 fecL:9 mod:6 tm:2 gi:4 hier:4                    
....... LOCKED.                                                    
NOUT: 1                                                            
dvbEvents 0:0 started                                              
Tuning delay: 965 ms                                               
pipe opened                                                        
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
xine pipe opened /home/mythtv/.kaxtv.ts 
```
Seems to me they are both using the same path :-(

---

### Post by Caysho on 2009-05-23
Go back to permissions then.
It's a USB device, so each at each boot or insertion, the permissions will be default again due to the udev rules.
I don't know the details on how to do this though.

---

### Post by Triptol on 2009-05-25
Nothing like that...

So I made a mistake and dropped the database :-(. Luckily I had a backup which already contained a pretuned DVB-T configuration from my old card.

I restored the backup and my new DVB-T works fine. I am still unable to tune it through mythtv-setup, so I guess I'm running in a bug. My situation is fixed (kinda).

Thanks for the help!

---

### Post by Triptol on 2009-05-29
Seems I am not alone: [http://ubuntu-virginia.ubuntuforums.org/search.php?searchid=59952644](http://ubuntu-virginia.ubuntuforums.org/search.php?searchid=59952644). No answer on that thread either.

---

