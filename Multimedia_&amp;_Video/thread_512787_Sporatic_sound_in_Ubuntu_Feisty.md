---
title: "Sporatic sound in Ubuntu Feisty"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by NUBI2007 on 2007-07-29
Like everyone else that uses the Feisty distro, I have been having no sound since install. I was able  to find a way to reinstall alsa drivers and utils ( I will post that website as soon as i can find it again).  Since then I have had sporadic sound. I believe that feisty is not saving this config on shutdown. It has taken me three or four times of reboots to finally get sound back.

Can anyone verify this? 

if you know, could you PM me through GAIM @ BOL4lfe

Thanks

NUBI

---

### Post by Cappy on 2007-07-29
From [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Configuring_default_soundcards_.2F_stopping_soundcards_from_switching](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Configuring_default_soundcards_.2F_stopping_soundcards_from_switching)


In a terminal type: 

```
sudo asoundconf list 
```
If you have more than one sound card, you should see several entries (You need to know which card produces sound. If you don't know then try the next step for all the entries) 
Now type this in a terminal: 

```
sudo asoundconf set-default-card ENTER_NAME_OF_CARD_HERE 
```

For example, this is what I did: 
```

$ sudo asoundconf list 
Names of available sound cards: 
rev20 
AudioPCI 

$ sudo asoundconf set-default-card AudioPCI

```

---

### Post by NUBI2007 on 2007-07-29
Cappy

thanks for the info. I will try your advice and get back to you about the results

NUBI

---

### Post by NUBI2007 on 2007-07-29
Mostly a success, after rebooting sound came back automatically, but on 2nd reboot, machine hung up before login screen. I will try again tomorrow and see what happens. Thanks again

---

