---
title: "unsupported flash player"
date: 2012-12-05
forum: Multimedia Software
---

### Post by laineywolff on 2012-12-05
cannot stream Amazon Instant Videos... I get the following message when using chrome..."Unsupported Flash Player -- If you're using the Chrome browser with Linux, you must disable PPAPI to continue using Amazon Instant Video. You can also use a different Web browser, like Firefox. Learn more"

How do I disable PPAPI?   (What is PPAPI?)   

I have tried using firefox and I get the following error message "You do not have a supported version of Adobe Flash, a requirement for watching Amazon Instant Videos in your browser.

Clicking the button below will take you to Adobe's Flash installer website. After installing Flash Player, you will be able to instantly ...."  

Tried a few of the things in post by lovinglinux on 4-6-2012... but I have no idea what I am doing or what things mean so after the first two did not fix things I stopped trying.  Sorry I am very green at this and like to understand what I am doing so...


Can anyone help?  Thanks  Lainey

---

### Post by sciguy125 on 2012-12-07
I recently went through this myself.

By default, Chrome uses Google's version of flash through Pepper API (PPAPI).  Amazon doesn't work with that version.  Since it doesn't work in Firefox, you must not have Adobe's version of flash installed.  To get Adobe's, install "flashplugin-installer".  The name is misleading, it will actually install the plugin itself (Due to licensing issues, the binary has to be downloaded directly from Adobe, so you're technically installing a script that automatically downloads and installs flash).

After that, Firefox should work fine.  To get Chrome to work, you'll also have to disable the PPAPI version of flash:
```
- enter "about:plugins" into the address bar of Chrome
- click Details in the upper right corner to have it show all the files
- Scroll down to flash and disable the PPAPI version
```

---

### Post by monkeybrain2012 on 2012-12-07
> **sciguy125 said:**
> I recently went through this myself.

By default, Chrome uses Google's version of flash through Pepper API (PPAPI).  Amazon doesn't work with that version.  Since it doesn't work in Firefox, you must not have Adobe's version of flash installed.  To get Adobe's, install "flashplugin-installer".  The name is misleading, it will actually install the plugin itself (Due to licensing issues, the binary has to be downloaded directly from Adobe, so you're technically installing a script that automatically downloads and installs flash).

After that, Firefox should work fine.  To get Chrome to work, you'll also have to disable the PPAPI version of flash:
```
- enter "about:plugins" into the address bar of Chrome
- click Details in the upper right corner to have it show all the files
- Scroll down to flash and disable the PPAPI version
```

You can install flash-plugin-installer from the Software manager, just install Ubuntu-restricted-extra.

---

### Post by laineywolff on 2012-12-08
THANKS! to sciguy125 and monkeybrain2012... !

I can now stream amazon prime videos using both firefox or chrome.

Lainey

---

