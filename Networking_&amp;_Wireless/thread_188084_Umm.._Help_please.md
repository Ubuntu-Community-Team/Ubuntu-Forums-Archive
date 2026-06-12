---
title: "Umm.. Help please"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by davidpring2005 on 2006-06-03
I'm having problems installing my wireless. i've tried MR. nickm"s guide and the wiki guide to no avail.

So far i get this when i try to use fwcutter:

[B]david@david-laptop:~$ sudo bcm43xx-fwcutter -w /lib/firmware /home/david/Desktop/bcmwl5.sys
fwcutter can cut the firmware out of /home/david/Desktop/bcmwl5.sys
  filename :  bcmwl5.sys
  version  :  3.100.46.0
  MD5      :  38ca1443660d0f5f06887c6a2e692aeb

extracting bcm43xx_microcode2.fw ...
extracting bcm43xx_microcode4.fw ...
extracting bcm43xx_microcode5.fw ...
*****: Sorry, it's not posible to extract "bcm43xx_microcode11.fw".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.*****: But this can be added in the future...
extracting bcm43xx_pcm4.fw ...
extracting bcm43xx_pcm5.fw ...
extracting bcm43xx_initval01.fw ...
extracting bcm43xx_initval02.fw ...
extracting bcm43xx_initval03.fw ...
extracting bcm43xx_initval04.fw ...
extracting bcm43xx_initval05.fw ...
extracting bcm43xx_initval06.fw ...
extracting bcm43xx_initval07.fw ...
extracting bcm43xx_initval08.fw ...
extracting bcm43xx_initval09.fw ...
extracting bcm43xx_initval10.fw ...
david@david-laptop:~$[/B]

---

### Post by darkshadow on 2006-06-03
That output is fine just ignore the one error it is normal

---

### Post by davidpring2005 on 2006-06-03
i started step 7 in nickm's guide:
" 7) Use your new Wireless connection
From what i remember network manager should now show up by your clock and display your current connection, if your lucky it will show a series of bars, this means your now using your wireless connection so lucky you!
If it doesnt, right click on it and tick "Enable Wireless" then left click on it
and select the wirless network of your choice.
"
but the Enable wireless option is not there.

---

