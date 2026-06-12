---
title: "smartphones and ubuntu: theory and practise for a newby"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by ginestre on 2010-08-14
Hello everyone.

How do I (in theory and in practice) plug my HTC Wildfire Android smartphone into my 10.04 Ubuntu laptop so that I can exchange files? I assumed it would be possible, maybe even easy, because both are linux. But if I use the USB cable, the phone tels me it's connected but the computer doesn't seem to know. 

Can anyone give me an idiot's guide to what is needed?

TIA

---

### Post by Aearenda on 2010-08-14
On my HTC Desire, when I plug the USB cable in an alert pops up and I have to tell it whether to charge only, allow data access, or allow tethering. Until I do this the computer doesn't see it, though it is possible to choose one of these for future connections in Settings under 'Connect to PC'. Is there something in settings on the Wildfire like this?

---

### Post by ginestre on 2010-08-14
> **Aearenda said:**
>  Is there something in settings on the Wildfire like this?

Yes, but I don't seem to know how to work it. The options are 
1) charge only
2) HTC Sync - If I choose this it tells me to download some software (for windows only) to my PC
3) Mount as disk drive.

I've tried all options, buy clearly (3) seems the most promising. And if I choose that, and try to open stuff on the phone, I get a mesage saying that USB connection is open so I should desist or break the connection.

But the PC doesn't see any connection anywhere that I can make out.

---

### Post by Aearenda on 2010-08-14
It's 'Mount as disk drive' that should make this work - and it does, for me with the HTC Desire and Ubuntu 10.04 (Lucid). If you are still using 8.10 as your profile suggests, try starting a Lucid live CD to test it.

BTW, what it does is mount the phone's SD card as a drive on the computer - not the other way around.

---

### Post by ginestre on 2010-08-14
> **Aearenda said:**
> It's 'Mount as disk drive' that should make this work - and it does, for me with the HTC Desire and Ubuntu 10.04 (Lucid). If you are still using 8.10 as your profile suggests, try starting a Lucid live CD to test it.

BTW, what it does is mount the phone's SD card as a drive on the computer - not the other way around.

Thanks for the clarification- that's what I'd assumed. But it still doesn't happen for me, don't know why. I've downloaded an app from the market, called websharing,which lets me connect via wireless and webdav- but this will only work at home when the router is on, and not when I'm away.

(And thanks for pointing out the error in my profile, which I've also updated!)

---

### Post by dmizer on 2010-08-14
Dropbox is also an option. [https://www.dropbox.com](https://www.dropbox.com)

You can find a dropbox app in the market, and there is a dropbox package which integrates with nautilus as well: nautilus-dropbox

Edit:
andFTP (also in the market) allows for file transfer via ssh (sftp). It also supports RSA keys so you could use it from remote as well. I've used this for a while and it's a very nice app.

---

### Post by ginestre on 2010-08-14
I've solved the problem here, and it was a silly issue. I had plugged the HTC wildfire into a USB hub, which I always use because my laptop only has 2 usb ports. The use of a hub was making it fail.

When I plugged the phone directly into the laptop, and not through the hub, it was instantly visible. So if anyone else can't see their android phones, this may be why. When you plug it in directly, it all works fine.

Thanks to everyone for their input.

---

### Post by Aearenda on 2010-08-14
Great that you solved it - odd that mine works even through a USB hub! I suppose there are hubs and then there are hubs...

---

