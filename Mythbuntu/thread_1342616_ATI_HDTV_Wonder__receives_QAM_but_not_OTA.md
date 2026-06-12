---
title: "ATI HDTV Wonder  receives QAM but not OTA"
date: 2009-11-30
forum: Mythbuntu
---

### Post by grenloch101056 on 2009-11-30
Just purchased two ATI HDTV Wonders and installed them in my 64 bit system running mthbuntu 9.04.  I tried 9.10 first but my PVR-500 wasnt playing nice so i downgraded to 9.04.

The HDTV wonders can tune unencrypted QAM256 from comcast just fine.  The trouble starts when I hook my OTA antenna up and try to scan channels.  It will scan through and not find a single channel.  On the backend setup terminal screen i keep getting the error when i try to scan, "DiSEqCDevTree, no device tree".  Through googling i found this to be an error with LNB control even though im just using a terrestrial antenna.  I found a post from 2 years ago that a user who was viewing OTA channels had to set the LNB settings, I tried that to no avail. 

I know the OTA antenna works fine, it was working with my previous capture card as well as hooked directly to my tv.  Any help would be greatly appreciated.

---

### Post by Senkoboy on 2009-12-01
I am running Unbuntu 8.10 Intrepid 64bit, with Myth 0.21, frontend and backend on the same box. I have a PVR-150 for analog and a ATI HDTV Wonder for OTA digital.  My ATI HDTV works fine.  I follow the information here [http://ubuntuforums.org/showthread.php?t=923078&highlight=ati+hdtv]("http://ubuntuforums.org/showthread.php?t=923078&highlight=ati+hdtv") to download the firmware for the card.

Told the backend it was a DVB card, set for OTA and scanned for channels, works good.  I get the ETI program guide also.

---

### Post by AKADAP on 2009-12-01
> **grenloch101056 said:**
> Just purchased two ATI HDTV Wonders and installed them in my 64 bit system running mthbuntu 9.04.  I tried 9.10 first but my PVR-500 wasnt playing nice so i downgraded to 9.04.

The HDTV wonders can tune unencrypted QAM256 from comcast just fine.  The trouble starts when I hook my OTA antenna up and try to scan channels.  It will scan through and not find a single channel.  On the backend setup terminal screen i keep getting the error when i try to scan, "DiSEqCDevTree, no device tree".  Through googling i found this to be an error with LNB control even though im just using a terrestrial antenna.  I found a post from 2 years ago that a user who was viewing OTA channels had to set the LNB settings, I tried that to no avail. 

I know the OTA antenna works fine, it was working with my previous capture card as well as hooked directly to my tv.  Any help would be greatly appreciated.

Are you trying to use both inputs on the card? I haven't found any way to tell the card to use the other input. It is likely that the channel scan is using the cable input and since it is cable will not find any 8vsb signals. Try putting the antenna on the cable input and see if it finds channels that way.

---

### Post by grenloch101056 on 2009-12-01
> **AKADAP said:**
> Are you trying to use both inputs on the card? I haven't found any way to tell the card to use the other input. It is likely that the channel scan is using the cable input and since it is cable will not find any 8vsb signals. Try putting the antenna on the cable input and see if it finds channels that way.


I'll def give that a shot tonight after work.  Do you think it would use the cable input for 8vsb and the other port for QAM?  It really boggles my mind that the card can receive QAM fine but not OTA.

---

### Post by Senkoboy on 2009-12-01
Try deleting the card and starting over with the settings for OTA.  Can this card be set up for both OTA and QAM at the same time? I don't know.

---

### Post by grenloch101056 on 2009-12-01
> **Senkoboy said:**
> Try deleting the card and starting over with the settings for OTA.  Can this card be set up for both OTA and QAM at the same time? I don't know.

i assumed the only difference between OTA and QAM is choosing the frequency type when scanning channels, unless im missing something?

---

### Post by blackoper on 2009-12-01
> **grenloch101056 said:**
> i assumed the only difference between OTA and QAM is choosing the frequency type when scanning channels, unless im missing something?

there are two different coax inputs on the ati hdtv card. I believe atsc uses the input closest to the edge of the card and not the same input as the qam tuner.

---

### Post by grenloch101056 on 2009-12-01
> **blackoper said:**
> there are two different coax inputs on the ati hdtv card. I believe atsc uses the input closest to the edge of the card and not the same input as the qam tuner.

excellent, ill give that a shot

---

### Post by grenloch101056 on 2009-12-02
thanks to blackoper and akadap i got it working!  The 8vsb and cable share the same coax input, which is closer to the top of the card.  Still dont understand why the 8vsb coax connector is different from the qam connector, but it doesnt matter at this point.

---

