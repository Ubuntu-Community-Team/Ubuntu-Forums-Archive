---
title: "New Install Help"
date: 2010-09-13
forum: Mythbuntu
---

### Post by Th3Boss on 2010-09-13
Ive never used MythTV or MythBuntu before but I installed MythBuntu today and when I try to watch live tv all it shows is a black screen same goes for recorded shows. I tried fast forwarding and rewinding the recorded show and also leaving it play for awhile and its the same the whole way through.

My tv turner card is [http://www.newegg.com/Product/Product.aspx?Item=N82E16815116010](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116010) 

Im using IVTV MPEG-2 and with composite to connect my dish network box to my card

---

### Post by LowSky on 2010-09-13
on the frontend... Utilities -> Setup -> TV Settings -> Playback -> Playback Profiles (3/8)


change the playback profile to another option.. if you have a nvidia graphics card that is a 8xxx series or higher use VDPAU, if not try on of the others

---

### Post by Th3Boss on 2010-09-13
> **LowSky said:**
> on the frontend... Utilities -> Setup -> TV Settings -> Playback -> Playback Profiles (3/8)


change the playback profile to another option.. if you have a nvidia graphics card that is a 8xxx series or higher use VDPAU, if not try on of the others


Didnt fix it, I tried all of them.

Im using this video card

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814150130](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150130)

---

### Post by tgm4883 on 2010-09-13
Can't do a lot without logs. Please post

```
/var/log/mythtv/mythbackend.log
```

---

### Post by Th3Boss on 2010-09-13
> **tgm4883 said:**
> Can't do a lot without logs. Please post

```
/var/log/mythtv/mythbackend.log
```


Here it is [http://mythtv.pastebin.com/QyAFhEZL](http://mythtv.pastebin.com/QyAFhEZL)

---

### Post by tgm4883 on 2010-09-14
> **Th3Boss said:**
> Here it is [http://mythtv.pastebin.com/QyAFhEZL](http://mythtv.pastebin.com/QyAFhEZL)

Well this seems pretty self explanatory

```
2010-09-13 21:13:24.243 Channel(/dev/video0) Warning: You have not set an external channel changing
                        script for a composite or s-video input. Channel changing will do nothing.
```

Take a look at [http://www.mythtv.org/docs/mythtv-HOWTO-11.html#ss11.3](http://www.mythtv.org/docs/mythtv-HOWTO-11.html#ss11.3)

---

### Post by Th3Boss on 2010-09-14
> **tgm4883 said:**
> Well this seems pretty self explanatory

```
2010-09-13 21:13:24.243 Channel(/dev/video0) Warning: You have not set an external channel changing
                        script for a composite or s-video input. Channel changing will do nothing.
```Take a look at [http://www.mythtv.org/docs/mythtv-HOWTO-11.html#ss11.3](http://www.mythtv.org/docs/mythtv-HOWTO-11.html#ss11.3)


So basically I need to do this?

[http://www.mythtv.org/wiki/Using_an_IR_Blaster_with_MythTV](http://www.mythtv.org/wiki/Using_an_IR_Blaster_with_MythTV)

---

### Post by tgm4883 on 2010-09-14
> **Th3Boss said:**
> So basically I need to do this?

[http://www.mythtv.org/wiki/Using_an_IR_Blaster_with_MythTV](http://www.mythtv.org/wiki/Using_an_IR_Blaster_with_MythTV)

Yep, you have to have a way to change the channel on the external set top box. In the event you aren't using a set top box, then you have hooked up the tuner incorrectly

---

### Post by Th3Boss on 2010-09-21
ok i bought the Standard MythTV LIRC RS232 IR Blaster from [http://www.irblaster.info/](http://www.irblaster.info/) which should be here soon, any good guides for setting it up for dish network?

also I tried playing some dvds on it and when I try it shows a black screen that says Please Wait and then it just goes back to the menu. Any idea what is wrong or how to fix this?

---

### Post by Th3Boss on 2010-09-22
anyone?

---

### Post by larsolav on 2010-09-23
Sorry, can't help with the dish network stuff, but on the DVD side you may want to enable autobuilds if you have not done so yet. Go to [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds) on firefox on the mythbuntu computer and follow the instructions there (after enabling autobuilds, remember to open up Update Manager and check for updates to finish the upgrade). This should update the internal player and should help quite a bit.

However, even after theupdate the internal myth DVD player may struggle with some Disney and Sony DVDs...

---

### Post by alien878 on 2010-09-23
If it thinks your tuner is a capture card, it could be that you haven't connected the tuner to the listings source in the setup.  The log also indicates this:
```
Scheduler, Warning: Listings source 'EIT' is defined, but is not attached to a card input.
```
I suggest you go through the tuner setup in mythtv-setup again to make sure all the options are set right, all the channels defined and connected to the tuner.

As for the DVD issue, that might be something else.  Have you installed the appropriate additional software?

---

### Post by Th3Boss on 2010-09-23
> **larsolav said:**
> Sorry, can't help with the dish network stuff,  but on the DVD side you may want to enable autobuilds if you have not  done so yet. Go to [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)  on firefox on the mythbuntu computer and follow the instructions there  (after enabling autobuilds, remember to open up Update Manager and check  for updates to finish the upgrade). This should update the internal  player and should help quite a bit.

However, even after theupdate the internal myth DVD player may struggle with some Disney and Sony DVDs...

Thanks ill give that a try.

> **alien878 said:**
> 
As for the DVD issue, that might be something else.  Have you installed the appropriate additional software?

What additional software is there to install?

---

### Post by alien878 on 2010-09-23
> **Th3Boss said:**
> What additional software is there to install?[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

You might want to check the mcp.  I think they might have added an option to enable this.

---

### Post by larsolav on 2010-09-23
> **alien878 said:**
> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

You might want to check the mcp.  I think they might have added an option to enable this.

Ah, yes, I forgot about the restricted format issue. This can be installed using Mythbuntu Control Centre as can be seen depicted here: [http://www.mythbuntu.org/files/images/MCC-Proprietary.png](http://www.mythbuntu.org/files/images/MCC-Proprietary.png) (Enable DVD support)

---

