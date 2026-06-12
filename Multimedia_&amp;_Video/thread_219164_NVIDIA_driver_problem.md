---
title: "NVIDIA driver problem"
date: 2006-07-19
forum: Multimedia &amp; Video
---

### Post by Sidhy on 2006-07-19
I dont really have any problem with installing the driver, but when I have the driver installed using:
> 
sudo apt-get install nvidia-glx


where I got asked to install some other basic things which I accepted anyway .. the problem is when I have rebooted my system x just starts with the nvidia driver but when I try to switch to the terminal using alt+ctrl+f1 my screen is totally messed up cant read anything also cant switch back. And that's not all when I restart/shutdown my computer I get the same problem. I can't take any screenshot because its totally messed up cant see a thing.

---

### Post by tseliot on 2006-07-19
Try point 13 of the Problems Section:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

---

### Post by Sidhy on 2006-07-19
hmm this sounds like the problem thanks .. I will try it now

---

### Post by tseliot on 2006-07-19
Try that suggestion. Then if it works and you don't want to lose the bootsplash youcan try this, I'm not sure it will work though:

put "splash" back and add "vga=792" beside it.

then type:
```
sudo update-grub
```

and reboot

---

### Post by Sidhy on 2006-07-19
Well I didn't add "vga=792" , but its working now so thanks alot :) 

also I got another question .. 
I installed the nforce drivers for my sound and ethernet card. but how can I see if they are loaded and used as the default ?

---

### Post by tseliot on 2006-07-19
> **Sidhy said:**
> Well I didn't add "vga=792" , but its working now so thanks alot :) 

also I got another question .. 
I installed the nforce drivers for my sound and ethernet card. but how can I see if they are loaded and used as the default ?

I have never had an nforce mobo therefore I wouldn't know how to help you.

If everything works fine then you shouldn't worry.

---

### Post by Sidhy on 2006-07-19
well I was just wondering if I did it right ;) thats all .. but ok I will let it be as it is from now on. was rly annoyed by that buggy gfx problem, couldn't update anything or press ctrl+alt+backspace if X was stuck had to reboot everytime but now thats over

---

