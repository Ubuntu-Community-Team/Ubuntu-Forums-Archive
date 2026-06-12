---
title: "Video Capture with Pinnacle Studio movieBox Plus"
date: 2008-10-18
forum: Multimedia Software
---

### Post by digitalchemystery on 2008-10-18
I've recently decided now would be a good time to start transferring old VHS family videos to DVD. So, I found an old VCR and picked up a Pinnacle Studio movieBox Plus from Best Buy -- figuring that it wouldn't come with Linux support out of the box.

The situation turned out to be a bit worse than I'd expected -- there doesn't seem to be any information on how to get this device to work. What is required (either in general or specifically) to get hardware like this working? I know I'm not alone with a problem like this, so let's figure out some sort of solution. That's the Ubuntu way, isn't it?

Here's the output of lsusb:
Bus 002 Device 007: ID 2304:0223 Pinnacle Systems, Inc. [hex] DazzleTV Sat BDA Device

And the output of dmesg:
[ 3132.449048] usb 2-9: new high speed USB device using ehci_hcd and address 9
[ 3132.583538] usb 2-9: configuration #1 chosen from 1 choice


Where would I start looking for access to this device? Maybe some way to capture raw output?

Thanks for any help--

---

### Post by 73ckn797 on 2008-11-15
I have the same capture device just purchased for my son. It will be used on a Vista system. We have a camera that connects with firewire. It can directly connect to the computer and works with Vista. I am going to look into trying that first then mess with using Movie Box via firewire for the older camera.

I have another camera that requires USB connection. I figure the USB connection will go through the Movie Box then via firewire to the computer. Movie Box has a firewire in/out connection.

Keep in touch on any progress and I will do the same.

Here is my latest info posted on an earlier thread:
[http://ubuntuforums.org/showthread.php?t=920023](http://ubuntuforums.org/showthread.php?t=920023)

---

### Post by Davlav on 2009-10-19
Hi,

I am also considering purchasing this device.

In my case, I would like to use it to capture PAL video from a camera.

May I ask what is the status of the research to make it work?

Thanks for your help!

Best regards,

David

---

### Post by 73ckn797 on 2009-10-20
> **Davlav said:**
> Hi,

I am also considering purchasing this device.

In my case, I would like to use it to capture PAL video from a camera.

May I ask what is the status of the research to make it work?

Thanks for your help!

Best regards,

David

There are no drivers for Linux to use this device that I have found. A camera that can use fire wire is the only thing that I have found works. There are other methods but you would have to search the forums for that. I have been successful with the fire wire connection.

---

### Post by digitalchemystery on 2009-10-22
I ended up taking the device back. I don't know enough yet to write drivers or discover how to get something like that to work. Not really sure where to go for it either.

---

### Post by 73ckn797 on 2009-10-23
Have you checked into video capture cards? 

Info here: [http://en.wikipedia.org/wiki/MythTV#Supported_tuner_cards](http://en.wikipedia.org/wiki/MythTV#Supported_tuner_cards)

---

