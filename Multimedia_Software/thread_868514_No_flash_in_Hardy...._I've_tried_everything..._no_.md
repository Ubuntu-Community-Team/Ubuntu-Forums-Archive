---
title: "No flash in Hardy.... I've tried everything... no firefoxrc in 3.0.1"
date: 2008-07-23
forum: Multimedia Software
---

### Post by LobsterBA on 2008-07-23
Hello all... this is my first post. I've been a UBUNTU user for a few years, and the last thing to keep me from never logging into windows again is flash support.

I have tried EVERYTHING and read EVERY post on the net regarding sound in hardy.

I have no firefoxrc file to edit. I'm on an XFI fatality with OSS

I would do anything for a solution..... sans paying 250 for support. Isn't that the idea behind linux ?? :)

Any last resorts?

Thanks,
Brandon

---

### Post by tuxxy on 2008-07-23
Is it just sound in flash or general system sound that wont work, if just flash then is it only webapps?

---

### Post by LobsterBA on 2008-07-23
youtube for example... havent tried offline flash.

Give me an example to try and I shall. I have video.... no sound.

This is undeniably frustrating as a GPGPU researcher. I should know what the problem is, but I'm not a sound guy; just a video guy. :(

Thanks for the quick reply by the way.

---

### Post by tuxxy on 2008-07-23
What do you mean you have no firefoxrc, cant you open it with

```
gksudo gedit /etc/firefox/firefoxrc
```

Theres a common simple fix that involves you replacing one line I beleive, am sure you have akready researched this thgouh

---

### Post by LobsterBA on 2008-07-23
Yep.... It is not a file on my system, i.e. nonexists.

Did this happen in 3.0.1? If I remove this version... install 2.0.. the file is there. I still get no fix, and there is no reason why I shouldnt have the latest firefox distro.

/*frustration*/

---

### Post by XxsydenxX on 2008-07-24
i got mine working by.

sudo apt-get install ubuntu-restricted-extras

---

### Post by rockstarrem on 2008-07-24
Also, you've probably tried this but it's worth saying:

```

sudo apt-get install libflashsupport

```

---

### Post by LobsterBA on 2008-07-24
Done both of them :(

I did see some OSS problems with ALSA when installing .20 today.

I don't know the interface between OSS and ALSA. Should ALSA be purged from my system?

---

### Post by LobsterBA on 2008-07-24
/*bump*/
very problematic

---

### Post by LobsterBA on 2008-07-24
I've followed the comprehensive sound sticky (obviously non-comprehensive) with XFI Fatality. No dice as assumed.

---

### Post by Sef on 2008-07-24
> /*bump*/
very problematic

Please do not bump unless 24 hours have gone by.  Bumping sooner can get you an infraction.  We are all volunteers here, so at times support can be very fast, and at other times, it can be slower than what one desires.  

> Give me an example to try and I shall. I have video.... no sound.

1) Do you have sound otherwise?

2) What is your sound card?

3) Have you uninstalled the flash before reinstalling it?

---

### Post by LobsterBA on 2008-07-26
Sef,

Very sorry for bumping at an incorrect time. I'll remember to not let it happen again. I'm new to the forums and apologize.

1) I do have sound... such as rythmbox
2) Creative XFi Fatality
3) yes

---

### Post by Yellow Pasque on 2008-07-26
Is this the x86_64 Ubuntu? (you have 4GB of RAM and a C2Q, so I would hope so)
If it is, do you have a copy of libflashsupport.so in /usr/lib32/ ? This is what it took for me to get sound in Flash, though I'm using OSS4, so I don't know if that makes a difference.

You can also try the version of libflashsupport.so that I compiled with OSS support and install the alsa-oss wrapper package. Make sure you uninstall the repo package of libflashsupport first.

Save the libflashsupport.so.gz to your Desktop
[http://ubuntuforums.org/attachment.php?attachmentid=69426&d=1210377383](http://ubuntuforums.org/attachment.php?attachmentid=69426&d=1210377383)
```
sudo apt-get install alsa-oss
sudo apt-get remove libflashsupport
cd ~/Desktop; gunzip libflashsupport.so.gz; sudo mv libflashsupport.so /usr/lib
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox-addons/plugins
```
If you're running x86_64:
```
sudo cp /usr/lib/libflashsupport.so /usr/lib32/
```

---

### Post by LobsterBA on 2008-07-27
Thank you VERY much Temujin. For the first time I have flash audio.

Rythmbox and Firefox don't like eachother, but I assume that is an OSS problem. I can't run multiple audio streams from the two simultaneously. I can live like this, but is there a fix?

Once again.... thank you very much.

---

### Post by LobsterBA on 2008-07-27
Oh yeah, and Skype now has a prob..... wont start with error snd_config failed :(

---

### Post by Yellow Pasque on 2008-07-27
I didn't know skype used libflashsupport. You might want to try the OSS version of Skype.

---

### Post by zagor on 2008-07-29
> **LobsterBA said:**
> Thank you VERY much Temujin. For the first time I have flash audio.



Great, really!
I too have always been struggling with flash on amd64 and followed all possible guides, including the sticky post in multimedia, lately.

This is the first time flash audio works.

Thank you very very much!

---

### Post by sashswash on 2008-08-27
> **zagor said:**
> Great, really!
I too have always been struggling with flash on amd64 and followed all possible guides, including the sticky post in multimedia, lately.

This is the first time flash audio works.

Thank you very very much!

Likewise, I've been struggling to get flash audio working on amd64 - thanks for the fix! This ought to be flagged.

---

### Post by jandersonjohn on 2008-11-03
Correct, no firefoxrc with the new version... but even with the new .so, no sound... I seriously dislike installing useless packages (the extras with sun java, etc). System ran great except Adobe's flash and youtube.

the libflashsupport.so suggested and the symbolic links, etc... no sound on youtube
otherwise great sound (ubunto studio, i do use sound a lot)

---

