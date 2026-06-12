---
title: "Conexant AC-Link Audio audio card no sound !!!!!"
date: 2005-10-13
forum: Multimedia &amp; Video
---

### Post by caocheng on 2005-10-13
no support ?

---

### Post by Darkning on 2005-10-20
I'm having the same problem....It just doesn't play sound. :( Can anyone help us out?

---

### Post by Darkning on 2006-02-17
C'mon people! Help us out! This topic's been here like, 4 months already!!! That should've been plenty of time for somebody to take 5 minutes to help explain the problem. Thanks again.

---

### Post by arjunsharma on 2006-02-18
please help I have the same problem!

Arjun

---

### Post by jerrad.brown on 2006-04-19
So uh... Ubuntu doesn't like Conexant Audio? I can't find much of anything on Conexant Audio drivers for linux... I'm wondering if straight up Debian drivers would work.... However, I did notice that everyone on this thread is an Ubuntu newb.... wonder if we're all being annoying and the higher-ups aren't gracing us with their presence....

---

### Post by drjeckill on 2006-05-15
[http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/) : You can get a "riptide" driver. According to another forum, it works. I should  be able to tell you more about it within few days. Otherwise, good luck. I'm interested in the results.

---

### Post by sigup on 2007-01-13
> **drjeckill said:**
> [http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/) : You can get a "riptide" driver. According to another forum, it works. I should  be able to tell you more about it within few days. Otherwise, good luck. I'm interested in the results.

haaa,i went to linuxant too and i found it to be asking money too. i don't blame them but it is conexant to be blame for not supporting linux user community.Back in 2000, most manufacturer try to include linux driver but this conexant is not. i really hate those profiteer gluton.....](*,)

---

### Post by Shadowfire on 2007-04-05
To all you guys struggling with the Conexant AC-Link Audio audio card.  Phantom, a friend who has a Gateway Laptop (7330GZ model).  In his quest of moving Ubuntu to his laptop (not just his desktop).  He was able to cure his no sound blues on his laptop by doing the following:

1. Open up the volume control.

2. Go to **Edit**.

3. Go to **Preferences**.

4. Scroll down list to **Extrenal Amplifier**. (check it)

5. Once it is check - close that out.

6. Go back to the volume control panel.

7. You should now see a **Switches TAB** at top. (select it)

8. Search for the **External Amplifier** on the list you see. 

9. Uncheck the **External Amplifier**.

10. Now close out  and go test your sound. 


Phantom and I hope this will help everyone who is having no sound issues with the Conexant AC-Link Audio.  

*Please understand that it is very hard to cover every nook and cranny with all the items that Linux covers, especially when the main maufactures of these devices don't help out much if any with the creation of drivers or software for linux.  

A big thanks to the very hard working Open Source community, because of them, we are able to benefit with such a great OS like Linux.  Share or help when you can!

Cheers!
Shadowfire

---

### Post by mrfredman on 2007-04-17
I am having the same issue, but I'm running KDE, so it seems my volume control bar is different, and I am unable to fix my system using the methods posted here. I was wondering if someone could adapt this guide for use with KDE, or is there any solution out there that I can just run from the command line?

---

### Post by mayoko185 on 2007-05-04
I have the the 7330gz laptop and use kubuntu and I had to do the following to get sound to work. 

In terminal type: alsamixer, then you your arrow key to move over to "External" and press "m" etc out and you should have sound again.

Note I had to toggle external a few times before it really worked lol

hope I helped ^^

---

### Post by lexarrow on 2007-05-05
I have the same problem on a HP Pavilion dv2025nr laptop. I tried the solutions posted but don't see "External Amplifier" in alsamixer or volume control.

Isn't it odd though that when running on battery I have sound but when AC powered I have no sound at all?

Patiently...waiting... :)

---

### Post by lexarrow on 2007-05-26
I've put in a howto [here]("http://ubuntuforums.org/showthread.php?t=455147")

---

### Post by RockHero on 2007-07-28
well heres what i did

went to the control panel
went to add new hardware (classic view) (new view try printers and other hardware)
yes, connected
add a new hardware device (at bottom)
search comp for hardware
sound, video and game controlers
audio codecs, next
bam
go to ur sound and audio devices icon in the control panel, should work

thats what worked for ME

Rock out :guitar:

---

### Post by NoelG on 2007-08-17
> **Darkning said:**
> C'mon people! Help us out! This topic's been here like, 4 months already!!! That should've been plenty of time for somebody to take 5 minutes to help explain the problem. Thanks again.

It was easy ,just go to the device manager, click on  conexant ac-link than ckick remove ,shut down,restart you slould now have sound It worked for me Good Luck

---

### Post by mcsquared on 2007-10-24
mrfredman, I have the conexant AC0Link Audio audio card on my notebook, too And tried Shadowfire's method. It worked on Ubuntu, but this method also worked on all the other distros I've tried, whole all, ALSO, had no sound after install. The trick is the External Amplifier thingy. All the sound manager have it tucked away somewhere in preference of the sound manager and with each variation of Linux distro, they all have this External Amplifier either checked or unchecked .  Once you find it (I am using PCLOS myself these days and it's KDE and had no sound initially either).  Depending on it's state of checked-ness (grin), just undo or check that item and you should get sound working no matter it be KDE based or not.
  
Ms. Max with thanks to Shadowfire

---

