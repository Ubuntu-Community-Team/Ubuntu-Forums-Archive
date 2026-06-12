---
title: "broadcom 43xx works on one install, doesn't on another?"
date: 2012-11-09
forum: Networking &amp; Wireless
---

### Post by Yougo on 2012-11-09
-------------------------
this link takes you to the solution: [>>click me<<](http://ubuntuforums.org/showpost.php?p=12347567&postcount=5)
read on if you want to verify the problem.
-------------------------


Can somebody help me out with this one:

i have two installs of 12.10x64 on my acer aspire 9300. 
-the first is a fresh install (let's call it "A"), 
-the second is my 'tinker and alpha update version', which is a continuous upgrade since 11.04 (let's call this one "B").

my wireless card is a broadcom BCM4311 802.11b.g. WLAN

"A" just can't connect/detect the card, Network Manager doesn't even list the card, let alone show available networks.

"B" shows and connects fine, on b43-fwcutter

i've tried every driver, b43, bcmwl*, STA, i looked at possible blacklists and cleared them. i tried setting up "A" exactly like "B", but it won't budge :( i tried google it but all that is just incomplete, a fat lie or just not true for my special case it seems.

the only thing i can think of is that i ran an update on "A" that i haven't yet done on "B". i think there was a kernel update in there... now i'm scared to upgrade "B" as it might break my wireless there too.

thing is, i've been running on a wired connection for a while now, and was too busy to consider checking wifi, I just found out today when i unplugged, and don't know when this went wrong.

is there anything i can do, any log or file to post to figure out why "A" doesn't work and "B" does?

---

### Post by Yougo on 2012-11-10
Bumping, cause I haven't found any explanations yet...

---

### Post by wildmanne39 on 2012-11-10
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by Yougo on 2012-11-10
Hi, thanks for your reply.

here's the txt file.
i noticed some errors at the bottom about missing files. 
why are those missing? are these files available in the repositories but not downloaded due to dependency mistakes, or are these files supposed to be generated during install/use?

the file tells me to go download the drivers from the vendor, but really, the ones in the repo's should be fine right?

I did run the script on the working installation as well to see what it should look like, and i see it is much longer, containing all sorts of info about wireless accespoints.

---

### Post by wildmanne39 on 2012-11-10
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Reboot
Thanks

---

### Post by Yougo on 2012-11-11
Thanks, worked a treat! could have sworn i tried that one before though:-k

anyways, consider this thread solved :)

---

### Post by wildmanne39 on 2012-11-11
Glad it is working!!!
Enjoy

---

