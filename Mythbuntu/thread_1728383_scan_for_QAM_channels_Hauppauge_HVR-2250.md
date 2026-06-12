---
title: "scan for QAM channels Hauppauge HVR-2250"
date: 2011-04-13
forum: Mythbuntu
---

### Post by brian_hayward on 2011-04-13
My cable provider recently switched their basic cable over from analog to digital so i went out and purchased a Hauppauge HVR-2250.  MythTv can find the Hauppauge card and in MythWeb it lists both tuners as up and not recording.  However i am unsure what i should set my "Frequency Table" and "Modulation" parameters to when scanning for channels.  I did a few scans and set the previous parameters to different values but when i try to watch a newly scanned channel there is no picture.  I tried to google this issue but i am comming up empty handed, i don't think i am using the correct search terms.  the channels are not encrypted because i plugged the cable into my roommates tv and did a channel scan and they all showed up on the tv.  i also tried calling my cable company tech support but the gentleman i was talking to was either an incredible tool or he was told to give people like me the run around.  I am running Mythbuntu 10.04.  Any advice, suggestions or ideas are greatly appreciated.  Thanks.

---

### Post by uteck on 2011-04-14
I am going from memory, but I think I use the cable-hrc setting and QAM64 to scan for channels.

Right now I only get the unencrypted local channels, but my provider (Wide Open West) is going to provide all basic channels unencrypted when they switch to digital in the next few months. :D

---

### Post by ilcapo09 on 2011-04-14
First make sure you know if your provider has QAM 64 or 256. You can look it up at [http://www.silicondust.com/support/channels/]("http://www.silicondust.com/support/channels/")

Select the right QAM type and run a scan selecting Cable HRC.

Hope that helps

---

### Post by agamotto on 2011-04-16
Yes, digital cable is usually 'cable' or 'cable-hrc.'  The modulation is usually 'QAM-64.'  The only thing that might gob up the works is if your cable provider doesn't assign the channels as they appear at SD.  Example:  I had Mediacom as my provider, and the digital channels were sent as 51 through 56, then - whatever., ie. 54-21.  The channel guide they provide to SD gives channels such as 109, 110, 111, etc...  The only way that you can get the channels to go where they 'belong' with the guide, is to use one of their digital tuner boxes... which strips out the side-channels, and renders the tuner in a digital television set quite pointless.

As they were quite unwilling to help find a solution, I dropped cable, and just record OTA.. anything else I fetch from the internet.

---

### Post by ilcapo09 on 2011-04-16
> The only thing that might gob up the works is if your cable provider doesn't assign the channels as they appear at SD. Example: I had Mediacom as my provider, and the digital channels were sent as 51 through 56, then - whatever., ie. 54-21. The channel guide they provide to SD gives channels such as 109, 110, 111, etc... The only way that you can get the channels to go where they 'belong' with the guide, is to use one of their digital tuner boxes... which strips out the side-channels, and renders the tuner in a digital television set quite pointless.

What I did to solve that was to replace the xmltvid in mythweb. So even if channel X was on a different number than what the guide in SD said, I would still get the correct listings

---

### Post by agamotto on 2011-04-19
I might have gone that route, but this was simply the final reason for me to leave Mediacom as a customer.  I no do business with companies that expect me to jump through hoops.  Thankfully, with Miro and the wide variety of programming available OTA in my area, I don't need cable anymore!

---

