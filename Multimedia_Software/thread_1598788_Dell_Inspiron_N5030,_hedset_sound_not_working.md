---
title: "Dell Inspiron N5030, hedset sound not working"
date: 2010-10-17
forum: Multimedia Software
---

### Post by sathyashrayan on 2010-10-17
Dear group,
  Just got a Dell Inspiron N5030. Internal speaker works. I can make a skype test service with internal speaker device. When I plugged the head phone, the head phone does not work. No problem with the head phone indeed. Any help? I have searched the forum for N5030 key word. But never able to find one. 

I am using Ubuntu 10.04 LTS
 - the Lucid Lynx - released in April 2010 and supported until April 2013. 

Hope this information is sufficient.

Please guide me thanks..

---

### Post by Mustache Villain on 2010-10-17
Try running this command in terminal:
```
alsamixer
```

(You might have to install the "alsa-utils" package.)

Try putting up the volume for all of the devices.

---

### Post by sathyashrayan on 2010-10-17
> **Mustache Villain said:**
> Try running this command in terminal:
```
alsamixer
```(You might have to install the "alsa-utils" package.)

Try putting up the volume for all of the devices.

Hi,
  Thanks for your reply. I have done that. All 100% except "Beep".

---

### Post by sathyashrayan on 2010-10-17
I did "hwinfo" and got

```

                       Intel 82801I (ICH9 Family) HD Audio Controller

```

Any clue? Is my device not working?

---

### Post by sathyashrayan on 2010-10-19
Any luck?

---

### Post by sathyashrayan on 2010-10-24
Any one?

---

### Post by sathyashrayan on 2010-10-28
I got this corrected by automatic update from resporatries. Thanks for the help

---

### Post by arvat on 2010-11-09
Still have the same problem, even if I did updates

---

### Post by christopher2405 on 2011-05-09
Sorry for bumping up if you've already got this fixed, but I was having this same problem. I'm now on 11.04, but I seem to recall having the same problem (and more importantly fix) on 10.10.

If you click on the volume icon in your taskbar and then select Sound Preferences, you should see an "Output" tab. At the very bottom, there is a "Connector" setting. When you have your headphones connected, change this to Analogue Headphones, as shown in the picture.

I think this should probably happen automatically, but it doesn't always so you may need to do it whenever you connect a headset.

There may be some sort of Terminal command which achieves the same thing, in which case you could create a shell script and perhaps automate the process.

As an aside, does anyone know how compatible openSuSE with KDE is with this particular computer (as in does compiz work, do Wi-Fi and ethernet work out of the box, etc.)? I'm not intending to get rid of Ubuntu (although I can't stand Unity), I'm just exploring new distros.

---

