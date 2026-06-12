---
title: "Flash in Opera doesn't work any more"
date: 2011-06-19
forum: Multimedia Software
---

### Post by cyclohexan on 2011-06-19
Hi,
after I upgraded from Lucid to Natty, Flash doesn't work in Opera any more.
In Firefox I have no problems.

As suggested in [another]("http://ubuntuforums.org/showthread.php?t=1660953") thread, I tried installing Flash-Aid for Firefox and reinstalled Flash with this extension, but no luck.
I also tried purging and reinstalling Opera:
sudo apt-get purge opera
sudo apt-get install opera
No luck.

Any suggestions?

---

### Post by no2498 on 2011-06-20
wile using opera go to the adobe site re down load flash player

---

### Post by cybrsaylr on 2011-06-20
I'm using Opera 11.11 with Natty with no problems and flash worked fine all along.

---

### Post by wolfen69 on 2011-06-20
Go to menu>settings>preferences>advanced tab>content>plugin options>shockwave flash>change path. Then you could point it to /usr/lib/mozilla/plugins or you could you could download the [flash file]("http://get.adobe.com/flashplayer/") (make sure it's the .tar.gz version) extract it and put it in ~/.mozilla/plugins

Then you can point opera as instructed above to ~/.mozilla/plugins (this worked for me)

---

### Post by cyclohexan on 2011-06-21
I checked my plugin options, but they seem to be OK.
/usr/lib/mozilla/plugins is included as it has always been.
I installed adobe-flashplugin via apt-get. (flashplugin-installer has been removed automatically what seems to be OK)
It still works in Firefox, but not in Opera.
Again the plugin has been found in the plugin options, but it didn't work.
Then I downloaded the file from the Adobe website, included it in the plugin options and deactivated the path to the other flash location to avoid conflicts. I restarted Opera, but it still didn't work.

My system is a 32 bit Ubuntu.
At my work I have a 64 bit Ubuntu, and there it works. However at work it was a fresh Ubuntu install, and at home it was a dist-upgrade.
Btw my opera at work has a working flash but the browser is so slow that I'm forced to use firefox there. My Opera at home (32 bit) works fast as hell, but no flash.

---

### Post by no2498 on 2011-06-21
? do you have turbo turned on
i need to turn it off to use flash

---

### Post by cyclohexan on 2011-06-21
Turbo is off.

---

### Post by no2498 on 2011-06-22
do you allow popups as flash player is a popup

---

### Post by cyclohexan on 2011-06-22
My popup preference is: "Block unwanted popups."
I just tried out "Open all popups", but it doesn't help.

---

### Post by no2498 on 2011-06-22
do you allow cookies

thats my last guess

---

### Post by cyclohexan on 2011-06-23
Yes. However only from the site I visit.

---

### Post by no2498 on 2011-06-23
that should be good enough

the restricted extras is the only other thing i can think of

---

### Post by cyclohexan on 2011-06-23
You mean the package ubuntu-restricted-extras?
It wasn't installed. I installed it, but flash still doesn't work.

---

### Post by wolfen69 on 2011-06-23
In a previous post, you said you had opera pointed towards /usr/lib/mozilla/plugins. I had that exact config, but it wouldn't work until I downloaded the libflashplayer.so file, then create a plugins folder in ~/.mozilla (put libflashplayer.so in the newly created plugins folder) and point opera to that. It worked for me.

---

### Post by no2498 on 2011-06-24
i hope that helps him

---

### Post by cyclohexan on 2011-06-25
Hi wolfen,

that's what I tried as I wrote this:
> **cyclohexan said:**
> Then I downloaded the file from the Adobe website, included it in the plugin options and deactivated the path to the other flash location to avoid conflicts. I restarted Opera, but it still didn't work.

---

### Post by Duncan Williams on 2011-06-25
verify flash version:
[http://kb2.adobe.com/cps/155/tn_15507.html](http://kb2.adobe.com/cps/155/tn_15507.html)

flash control panel:
[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager09.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager09.html)

Opera uses a different version of flash than other browsers (might be more applicable to windows and IE) but check you have right version:
[http://www.google.com/search?q=flash%20opera](http://www.google.com/search?q=flash%20opera)

---

### Post by cyclohexan on 2011-06-25
As I already wrote in the title of this thread, flash doesn't work any more. 
However the links you posted require a working flash.

My problem is not a wrong flash version that does not work with certain websites or under certain circumstances. It does not work at all. With no website.

---

### Post by Duncan Williams on 2011-06-25
from previous experience with flash in opera (windows) 
The wrong version
`doesn't work at all'

However the version I have onboard works fine in opera and ubuntu / peppermint and has for months.

---

### Post by cyclohexan on 2011-11-10
Since upgrading to oneiric it works again.

---

