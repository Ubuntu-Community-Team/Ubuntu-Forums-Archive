---
title: "youtube not working {11.10 64 bit FF}"
date: 2012-02-15
forum: Multimedia Software
---

### Post by YossiHarel on 2012-02-15
hey
i install today 11.10 64 Bit on my Dell laptop & i have 2 problems:

1- I use the Firefox browser & for some reason You Tube is not working. I tried to find some information but I could not understand anything. 
I do see a Flash Player installed on my system.
any idea ?!

2-I can not directly change the brightness from the settings. Dedicated buttons on my computer also  does not change the brightness. what is the problem ?

Thanks

---

### Post by kc1di on 2012-02-15
Go to software center or synaptic if you have int installed and install ubuntu-restricted-extras and ubuntu-restricted-addons

then see if youtube works.

---

### Post by YossiHarel on 2012-02-15
> **kc1di said:**
> Go to software center or synaptic if you have int installed and install ubuntu-restricted-extras and ubuntu-restricted-addons

then see if youtube works.

1 - Thanks for the quick reply. 2 - only install? I do not have to delete something before? I ask because I see that I have Flash installed and what you are telling me to install also contains flash. Not be a conflict?

---

### Post by wolfen69 on 2012-02-15
Go [here]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") and install the flash-aid firefox add-on. It should clear things up.

---

### Post by YossiHarel on 2012-02-15
> **wolfen69 said:**
> Go [here]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") and install the flash-aid firefox add-on. It should clear things up.

Okay .. I will try it. Thank you

---

### Post by YossiHarel on 2012-02-15
ubuntu-restricted-extras and ubuntu-restricted-addons already installed and nothing changed. youtube still not working. BTW.. i can watch youtube videos when i open a tweet on twitter.. strange

still need help for both problems
1-youtube 
2- Dell [B]brightness buttons

Thanks
[/B]

---

### Post by Leppie on 2012-02-15
Could you post a screenshot of a page with a video you were trying to watch on youtube?

---

### Post by YossiHarel on 2012-02-15
> **Leppie said:**
> Could you post a screenshot of a page with a video you were trying to watch on youtube?

Here is a link: [http://imageshack.us/photo/my-images/39/screenshotat20120215210.png/](http://imageshack.us/photo/my-images/39/screenshotat20120215210.png/)[IMG]http://ubuntuforums.org/%3Ca%20href=http://imageshack.us/photo/my-images/838/screenshotat20120215210.png/%20target=_blank%3E[IMG]http://img838.imageshack.us/img838/5616/screenshotat20120215210.png[/IMG][IMG]http://imageshack.us/photo/my-images/838/screenshotat20120215210.png/][IMG]http://img838.imageshack.us/img838/5616/screenshotat20120215210.th.png[/IMG][IMG]http://imageshack.us/photo/my-images/838/screenshotat20120215210.png/][IMG]http://img838.imageshack.us/img838/5616/screenshotat20120215210.png[/IMG]

---

### Post by YossiHarel on 2012-02-15
update: I installed the Chromium browser and YouTube  works properly there. Why on Firefox is not working?

---

### Post by kc1di on 2012-02-15
> **YossiHarel said:**
> update: I installed the Chromium browser and YouTube  works properly there. Why on Firefox is not working?
if it's working on Chromium it's not a flash issue as they both use the same file.  

What addons and extensions do you have installed in FF ?

you might try disabling them one at a time and see if it makes any difference.

---

### Post by YossiHarel on 2012-02-15
> **kc1di said:**
> if it's working on Chromium it's not a flash issue as they both use the same file.  

What addons and extensions do you have installed in FF ?

you might try disabling them one at a time and see if it makes any difference.

Not installed anything since I installed Ubuntu today. All I have now installed is what was installed in the main installation of the system today

---

### Post by YossiHarel on 2012-02-15
update: i did this in the terminal: 
sudo apt-get remove --purge adobe-flashplugin flashplugin* nspluginwrapper
then: 
sudo apt-get install --reinstall adobe-flashpluginand 
now youtube work on firefox but wtf is Gnash sef player that youtube is asking me to install ?

---

### Post by Leppie on 2012-02-16
gnash is an open source flash player.

---

### Post by BelugaWail on 2012-02-18
This may not help at all.

I was having issues with youtube playing correctly in firefox on ubuntu 11.10.  I uninstalled gnash using:

sudo apt-get remove gnash

Now youtube plays correctly, however, firefox now generates a warning at the top of the page stating that "additional plugins are required to display all the media on this page".

I do not get this warning when running chrome.

I'm not sure what the issue is but I believe it is related to gnash.

---

### Post by YossiHarel on 2012-02-22
hey guys how are you?
everything works perfectly now!

thank u all for your help

---

