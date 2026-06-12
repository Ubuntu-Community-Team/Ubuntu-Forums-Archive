---
title: "Flash trouble with amd 64"
date: 2010-06-06
forum: Multimedia Software
---

### Post by MHail on 2010-06-06
I successfully installed flash with help from this [page]("http://ubuntuforums.org/showthread.php?t=1358591&highlight=adobe+amd64"), but I am unable to run anything flash. YouTube always gets "An error occurred, please try again later". Pandora loads half way. I then get a red box above the loading screen. Hulu and flash games give me a gray box. I appreciate any help because I have run out of ideas to fix this one. 



Running firefox 3.6 under Ubuntu 10.04

---

### Post by gordintoronto on 2010-06-06
What happens when you go to this page:
 [http://www.adobe.com/software/flash/about](http://www.adobe.com/software/flash/about)

Did you turn off all special effects?

---

### Post by MHail on 2010-06-06
I get a flash successfully installed animation.

Special Effects?

---

### Post by gordintoronto on 2010-06-06
Oops, I misspoke. Under Preferences/Appearance, "Visual Effects." Many people find they interfere with flash.

---

### Post by MHail on 2010-06-06
Gaahh it did not work. I turned off all effects and I still get errors.

---

### Post by WinterRain on 2010-06-07
I'm not sure what you did before, but the following always works for me.

Remove any flash you have installed, and get the 64bit flash file here [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

Then extract it and put it in /usr/lib64/mozilla/plugins and restart firefox. Works perfect for me.

If you are unsure how to do this, to extract the file, just right click and "extract here". Make sure it's on your desktop. Then do in terminal: (you can copy and paste it)
```
sudo cp ~/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
```
Restart firefox, done.

---

### Post by MHail on 2010-06-07
> **WinterRain said:**
> I'm not sure what you did before, but the following always works for me.

Remove any flash you have installed, and get the 64bit flash file here [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

Then extract it and put it in /usr/lib64/mozilla/plugins and restart firefox. Works perfect for me.

If you are unsure how to do this, to extract the file, just right click and "extract here". Make sure it's on your desktop. Then do in terminal: (you can copy and paste it)
```
sudo cp ~/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
```Restart firefox, done.

I have tried what you suggested. This flash issue happened after I  upgraded from 9.10. Firefox updated along with it and all of a sudden  flash does not work.

---

