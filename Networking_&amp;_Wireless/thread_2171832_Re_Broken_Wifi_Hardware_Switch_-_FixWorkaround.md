---
title: "Re: Broken Wifi Hardware Switch - Fix/Workaround?"
date: 2013-09-01
forum: Networking &amp; Wireless
---

### Post by spiderDuck on 2013-09-01
Hello. I seem to have a similar problem. Although my switch is still there (on the left side of the laptop) it does't seem t respond whether I turn it on or off.  For newbees like me soldering seems impossible. Isn't there a more easy solution? I'm afraid I'm gonna ruin my motherbard.

---

### Post by wildmanne39 on 2013-09-01
Moved to own thread, your issue is not the same as the OP's and it is best to start your own thread!
Thanks

---

### Post by wildmanne39 on 2013-09-01
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by spiderDuck on 2013-09-02
Ok. I've attached the info.

---

### Post by wildmanne39 on 2013-09-02
Tap your wireless button one time then run this command to see if it is still blocked:
```
rfkill list all
```some computers have more then one button to turn wireless on or use function keys like fn + f2.
Thanks

---

### Post by spiderDuck on 2013-09-03
I tried all the combinatons and it still says that the wireless is hardware blocked.
If I open up my laptop is there a way to understand if the hardware switch is broken? What should I look for?

---

### Post by wildmanne39 on 2013-09-03
I do not suggest physical repairs.

Go into your bios and see if you can enable wireless there, possibly mess with last state under advance if you have that option or reset your bios.
Thanks

---

