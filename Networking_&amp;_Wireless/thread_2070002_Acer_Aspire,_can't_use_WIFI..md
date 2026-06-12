---
title: "Acer Aspire, can't use WIFI."
date: 2012-10-11
forum: Networking &amp; Wireless
---

### Post by behedwin on 2012-10-11
Hey

I have a Acer Aspire V3-571G 15.6" HD
with: GeForce GT 630 2 GB, Core i5-3210M, 8GB RAM, 500GB HDD, DVD±RW, BT, W7H

I am new to linux and ubuntu.
I bought this computer for schoolwork and to learn ubuntu and linux.

I have just installed Ubuntu.
But i cant get my wireless network to work.

Can anyone help and find what the issue is?
The network works when i connect the cable to the computer, but i cant activate the wireless network.

Please help

---

### Post by behedwin on 2012-10-11
ok i found some kind of fix, i think.
But i dont understand it
I need a good walkthrough what i should do.

[http://ubuntuforums.org/showthread.php?t=1967515](http://ubuntuforums.org/showthread.php?t=1967515)


Remember, i have never used ubuntu before :)


Hope someone can help

---

### Post by wildmanne39 on 2012-10-11
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by behedwin on 2012-10-11
ok here goes

dont have a clue what that file contains lol

note also that i suddenly got the wireless network to work
it just hapend after i restarted a few times when doing other stuff.

but when reading about the issue it seems it is unstable and somehave issues with the wireless just shutting down suddenly
so far it have not happend for me

---

### Post by wildmanne39 on 2012-10-11
Hi, please do:
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
Then reboot and that should take care of the problem.
Thanks

---

### Post by behedwin on 2012-10-11
thanks for your help
but if you dont mind, explain what you did here :)

im new, dont have a clue what any of this meant
you could have told me to format the computer or something worse, download a keylogger or anything.... 

but maybe ill know what this meant in a while when i used ubuntu a bit more :)

---

### Post by wildmanne39 on 2012-10-11
Hi, with some acer laptops the module that I said to blacklist keeps the wireless card from being turned on so you blacklist it and it fixes the problem.
Thanks

---

