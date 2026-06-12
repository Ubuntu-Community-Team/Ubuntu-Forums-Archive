---
title: "HOWTO: Generic USB Headset ringing in Skype"
date: 2009-05-24
forum: Multimedia Software
---

### Post by pakis on 2009-05-24
I just bought a cheap usb headset from ebay to use with Skype, Ekiga etc. The device is recognised as a Generic USB audio device. The headset works fine with Skype except for the keypad and it doesn't ring when someone is calling me. I found a workaround for making my headset ring when someone is calling me in skype so i'll just tell you how i did it and hopefully you can get yours to work as well.

[SIZE="3"][COLOR="Red"]System[/COLOR]:[/SIZE]
Ubuntu 9.04
Skype 2.0.0.72
TOPCOM Webt@lker 100 USB Headset


[SIZE="3"][COLOR="Red"]Step 1[/COLOR]: Check if you can make the phone ring[/SIZE]

I discovered that when my system beeped the phone rang for a strange reason. To check if this happens in your case do the following:

Install beep

```
sudo apt-get install beep
```


Then try making your phone to ring by issuing the command


```
beep  > /dev/dsp2 
```

(mine was dsp2, so try replacing dsp2 with other devices to find yours e.g. dsp1)

If the phone rings, you're lucky and you can proceed with the other step.



[SIZE="3"][COLOR="Red"]Step 2[/COLOR]: Configure Skype[/SIZE]

Go to Skype -> Options -> Sound Devices and select the ringing device (any working device will do at this point)

Then go to the Notifications menu, select "Incoming Call Ringing" from the list and then click on the Advanced View button. From the options below check the "Execute the following script" checkbox and in the box below write:

```
beep -l 5000 > /dev/dsp2 
```
 (replace dsp2 with your device)

You can modify the value of 5000 which is the duration of ringing. in my case, the value 5000 caused my phone to ring twice. Then click on Apply and then on the Test Event button. A test incoming call should appear and the phone should be ringing.

Good Luck!;)

---

