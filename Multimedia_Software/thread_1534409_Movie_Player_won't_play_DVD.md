---
title: "Movie Player won't play DVD"
date: 2010-07-19
forum: Multimedia Software
---

### Post by Tauriel on 2010-07-19
Hi all,

I've just updated to 10.04 and found out that I can't play original DVDs. Movie Player gives me error message "Could not read from resource" and VLC just ignores all attempts to play the DVD.

Please help!

---

### Post by mc4man on 2010-07-19
Run this in terminal to make sure libdvdcss2 is installed
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Then open vlc - media - open disc and make sure it's looking at proper /dev/[COLOR="Blue"]X[/COLOR] for your drive (/dev/sr0 or /dev/dvd are generally good, if not try /dev/sr1 or /dev/dvd1

---

### Post by tony21 on 2010-07-19
hello first time user here i had the same problem but i tryed what you said and it didnt seem to work

---

### Post by Suranjandeo on 2010-07-19
Hello,
 I have ubuntu 10.04 lucid. When i try to play DVD or any video file in movie player then same error message come. I have installed "gxine". But now when i try to play in gxine or movie player then computer shuts down immediately.
pls help

---

### Post by Tauriel on 2010-09-06
> **mc4man said:**
> Run this in terminal to make sure libdvdcss2 is installed
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Then open vlc - media - open disc and make sure it's looking at proper /dev/[COLOR="Blue"]X[/COLOR] for your drive (/dev/sr0 or /dev/dvd are generally good, if not try /dev/sr1 or /dev/dvd1

Sorry, I tried this, but it's still not working. :(

Can someone else help, please?

EDIT: Actually, it is working fine, I restarted the computer and it's all okay. :)

---

### Post by lumore22 on 2010-09-23
Greetings- 

I have the same problem.iI'm on Lucid v.10.04.  But the error messages I get bounce between "Can't find location"  and a "failed to create dbus-proxy . . . " message. I checked and it seems that I'm missing   ?SettingsDaemon? But I'm not able to find a workaround or fix for this. Well-documented bug but no solution.
What's the command to check for "location" -  my dvdplayer is at /dev/sr0.

Any and all help would be appreciated.

Regards

---

### Post by jimmers on 2010-09-23
Have you installed ubuntu-restricted-extras, available through synaptic.

---

### Post by lumore22 on 2010-09-23
Jimmers -

I installed the restricted extras and every other gstreamer related module/script.

---

### Post by lumore22 on 2010-09-23
Jimmers-

You must really have good karma. A little while ago I hear my dvdplayer rumble. So I decided to test it with a dvd disc. Lo and behold ... it worked.  

Don't know why. If anyone can offer an explanation, I'd really appreciate it.

Thanks for the karma

Regards-

---

### Post by lumore22 on 2010-09-23
Jimmers-

You didn't by any chance do some funky diagnostics on my system? I just ran "ps aux" and got a "?" for the tty col as well as 'rtkit' entry.  Thanks though. Nice to have a high res dvd player working finally.

Regards:popcorn::popcorn:

---

### Post by elguti80 on 2010-09-30
Thanks mac4man,

I did what you suggested and it worked brilliantly...cheers!

Guti

---

### Post by LanceRooke on 2011-10-20
This worked! But jeez, it's a crummy quality DVD player.  Isn't there some better software that can be used?

Run this in terminal to make sure libdvdcss2 is installed
 	Code:
 	sudo /usr/share/doc/libdvdread4/install-css.sh 
Then open vlc - media - open disc and make sure it's looking at proper /dev/[COLOR=Blue]X[/COLOR] for your drive (/dev/sr0 or /dev/dvd are generally good, if not try /dev/sr1 or /dev/dvd1

---

