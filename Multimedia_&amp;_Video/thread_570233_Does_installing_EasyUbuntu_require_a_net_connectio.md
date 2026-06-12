---
title: "Does installing EasyUbuntu require a net connection?"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by pykus on 2007-10-08
I installed EasyUbuntu and I was very excited to start watching movies and such, but it seems I have to have a net connection to install the various components?? Is that right? I don't have my wireless working with Ubuntu yet and this is frustrating me greatly. I want to get my wireless working, but I have no idea when that's going to happen. I'm completely new to this and I don't want to have to wait until some unknown time in the possibly distant future to get to watch my movies and listen to my music. Someone please tell me there's a way to get the actual useful parts downloaded so I can transfer them over. Why would that even be the way things work in the first place? Why require a net connection to get things installed? That doesn't seem like it's very user friendly to me.

---

### Post by overdrank on 2007-10-09
> **pykus said:**
> I installed EasyUbuntu and I was very excited to start watching movies and such, but it seems I have to have a net connection to install the various components?? Is that right? I don't have my wireless working with Ubuntu yet and this is frustrating me greatly. I want to get my wireless working, but I have no idea when that's going to happen. I'm completely new to this and I don't want to have to wait until some unknown time in the possibly distant future to get to watch my movies and listen to my music. Someone please tell me there's a way to get the actual useful parts downloaded so I can transfer them over. Why would that even be the way things work in the first place? Why require a net connection to get things installed? That doesn't seem like it's very user friendly to me.

Hi and welcome, please post the output of the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware and we may be able to help. If you have a wired connection it will make it easier to install what is need for the wireless.

---

### Post by pykus on 2007-10-09
In retrospect I should have been more clear. I have no wired internet. My machine can also boot Windows, so I have been trying to download files and transfer them to Linux with my external hard drive. Sorry about the confusion.

In any case, my immediate problem is solved as I got my internet connected. I'm still curious about how to get the pieces that download automatically for future reference though. I'm at work now, but I'll post what you requested as soon as I get home.

Thanks! :-)

pykus

---

### Post by pykus on 2007-10-09
Here is the result of lspci:

0000:00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01)0000:00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 01)0000:00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 01)0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:03.0 CardBus bridge: Texas Instruments PCI1420
0000:02:03.1 CardBus bridge: Texas Instruments PCI1420
0000:02:04.0 Communication controller: Agere Systems LT WinModem (rev 02)
0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 41)
0000:02:09.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)

---

### Post by overdrank on 2007-10-10
> **pykus said:**
> In retrospect I should have been more clear. I have no wired internet. My machine can also boot Windows, so I have been trying to download files and transfer them to Linux with my external hard drive. Sorry about the confusion.

In any case, my immediate problem is solved as I got my internet connected. I'm still curious about how to get the pieces that download automatically for future reference though. I'm at work now, but I'll post what you requested as soon as I get home.

Thanks! :-)

pykus

Ok great so you have wireless working. These link will help with codecs and restricted formats
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
Good luck!

---

### Post by pykus on 2007-10-10
> **overdrank said:**
> Ok great so you have wireless working. These link will help with codecs and restricted formats
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
Good luck!

That's magnificent! Thanks! :-)

I also think I figured out the logic behind the EasyUbuntu downloading the parts instead of just including them in the package. Correct me if I'm wrong, but it looks like EasyUbuntu was set up as an easy way to access many completely separate items that are downloadable on their own, but have no relationship to eachother and therefore no reason to be included in a single package. So if I had a list of the things EasyUbunto helps install I could just as well have downloaded each of them when I was running Windows and installed them without necessarily having internet access through Ubuntu. Is that right?

Thanks again! - pykus

---

### Post by overdrank on 2007-10-10
> **pykus said:**
> That's magnificent! Thanks! :-)

I also think I figured out the logic behind the EasyUbuntu downloading the parts instead of just including them in the package. Correct me if I'm wrong, but it looks like EasyUbuntu was set up as an easy way to access many completely separate items that are downloadable on their own, but have no relationship to eachother and therefore no reason to be included in a single package. So if I had a list of the things EasyUbunto helps install I could just as well have downloaded each of them when I was running Windows and installed them without necessarily having internet access through Ubuntu. Is that right?

Thanks again! - pykus

Hi and well yes and no. Easyubuntu and automatix handle all the dependency issues for you. So if you were to download a .deb file to install something it might have some dependency issues. But you are on the right track and good luck! :KS

---

