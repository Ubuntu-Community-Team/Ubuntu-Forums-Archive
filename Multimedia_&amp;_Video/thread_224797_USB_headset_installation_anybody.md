---
title: "USB headset installation anybody?"
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by impeteperry on 2006-07-28
Hi
Has anybody been able to use a USB headset for use with somthing like "Skype"

I bought one "Cyber Accoustics" as soon as I signed up for "Skype". It didn't work of course. I called "Cyber Accoustics" fqr help. I got "Linux, what's that?" in so many words.

Thanks for any help

---

### Post by TheDietzer on 2007-02-03
I have a Cyber Acoustics AC-850 headset and had this same problem.

Solution:

1) Edit the file "/etc/modprobe.d/alsa-base".  Use the command:

      sudo gedit /etc/modprobe.d/alsa-base

    At the bottom of this file there is a section entitled "Prevent
    abnormal drivers from grabbing index 0" and the following line:

      options snd-intel8x0m index=-2

    Comment out that line like so:

      # options snd-intel8x0m index=-2


2) Select "System" -> "Preferences" -> "Sound" and at the bottom
    of the menu, for "Default Sound Card", select "USB Device xxxx"
    where xxxx is a numerical designation of your Cyber Acoustics
    driver.

3) Reboot.

Your sound card should be disabled, and both the Cyber Acoustic 
head phones and attached microphone should be working if your
volume control settings are correct.  I have tested the headphone
and microphone with the Skype test call and they worked fine.

Cheers.

---

### Post by impeteperry on 2007-02-03
Thanks, but  then, how do I re-set my sound card to work normally?

---

### Post by chargemaster on 2007-02-07
Dietzer

Thanks for the how to on getting a USB Microphone to work. I tried your suggestion and it worked perfectly. I tested it using both streamtuner and Skype.

Thanks again
Rick

---

