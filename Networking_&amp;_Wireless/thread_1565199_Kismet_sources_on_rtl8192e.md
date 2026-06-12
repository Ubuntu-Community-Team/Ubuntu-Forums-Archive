---
title: "Kismet sources on rtl8192e"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by justkillingtime on 2010-08-31
hi this is my first post and im an ultimate noob....

 Ok so i have a samsung n130 netbook running 32bit 10.4 netbook edition (ubuntu). 

 My wirless is a realtek rtl8192e and yes it was a nightmare to get working. I was using ndiswrapper but have reinstalled linux since then and now its running on the native 32bit driver provided by realtek it works.... phew. And i managed to get kismet installed...phew... but not working ... bugger. its saying All packet sources are in error state. i need to config kismet i know this but how? i cant find a config file with source=none none etc like its reccomended i have tried to there are alot of config files. i ran sudo gedit /etc/kismet.conf and it seemed to make a new gedit page not finding one... and my interface is this wlan0??? that doesnt work but if it isnt this then what part of iw config am i actually looking at? and what would the name be? i have tried interface=wlan0 name= RTL8192e (and with a variety of different caps) 

 iwconfig
 lo     no wireless exstension
eth0   no wireless exstensions << both are expected as these arent my wireless card 
wlan0 802.11bg ESSID:'000740CDBC16' Nickname:'rtl8192e' 
          Mode: Managed Frequency=2.462 GHz Access Point: 00:07:40:E8:81:C8
          bit rate=1mb/s RTS:off Fragment:off
          Power management:off
          link quality=65/100 signal strength= -69dBm Noise level=-102 Dbm 
           (the rest of the options = #0 

 Also while im at it im totally new to ubuntu minus getting the few pieces i got to work working i have been building but when i make i need to extract to the home folder and i run (sudo su) and then build from there (make,make install) which is a really sloppy way of doing it how do u navigate to a specific folder correctly as it always ses everyway ive tried Bash: this is a directory or Bash; this is not a directory or Bash: file not found make needs 'makefile' 


 THANKYOU IN ADVANCE 
  ash :)

---

### Post by justkillingtime on 2010-08-31
those smilies werent intended just the way it is on the terminal soz

---

### Post by chili555 on 2010-08-31
You will probably want to do:```
sudo gedit /etc/kismet/kismet.conf
```Scroll down to the 'sources' section and you will probably change it to:```
source=r8192_pci,wlan0,Realtek
```It may or may not work.

Please see section 12 here:```
less /usr/share/doc/kismet/README.gz
```Your card is not listed. The README may be out of date or else it ***really*** doesn't work.

Kismet doesn't work with everything.

---

### Post by justkillingtime on 2010-09-01
ok thanks but honestly when i run gedit it opens a blank page with no source code but i ran nautilus and found the directory using the /etc/usr  ... and found the file but im confused because it has # infront of every line which surely disables the script? i will try ur suggested name and interface right after breakfast and post if it worked or not but i do know kismet is not the best of programs i would just really like to crack my dads 'uncrackable network' ps he knows im trying.

---

### Post by chili555 on 2010-09-01
It has # in front of the explanatory comments but then further on down, the operative things are not commented out.

I will be surprised if it works on your Realtek.

---

