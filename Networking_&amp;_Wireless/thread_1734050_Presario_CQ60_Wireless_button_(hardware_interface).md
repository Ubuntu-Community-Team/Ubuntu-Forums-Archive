---
title: "Presario CQ60 Wireless button (hardware interface)"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by jacob.harris9799 on 2011-04-19
Hey all!

I have Ubuntu 10.10 dual installed with Win. Vista on a Compaq Presario CQ60. 

Keep in mind while reading that I have no accessible ethernet connection, and a paper due tomorrow.

In vista, i have no problems.

In ubuntu, when i boot it up, log in, and then right click the network gadget on the notification bar, it says wireless is enabled. when i left click, it says device not ready.

my concern is that it is some driver or backdoor package that i need to download. 

however, i cant download it through ubuntu, and i do not know how to open the windows partition through ubuntu.



If it will help the process, i have a flash drive and a portable hard drive..

Thank you so much!!! and i would greatly appreciate any and all help.... thank you sooooo much!!!

---

### Post by josephmills on 2011-04-19
could we see if the button is on go to Applications-->Accessories-->Terminal   then type in ```
rfkill list all
``` then could I see a ```
 lsmod | grep ath5k
``` it should look like this ```
Presario-CQ60-Notebook-PC:~$ lsmod | grep ath5k
ath5k                 130083  0 
mac80211              231959  1 ath5k
ath                     8153  1 ath5k
cfg80211              144694  3 ath5k,mac80211,ath
led_class               2633  1 ath5k

```
could I also see a ```
lsmod | grep ath5k
``` it should look like this ```
joseph-Compaq-Presario-CQ60-Notebook-PC:~$ lsmod | grep ath5k
ath5k                 130083  0 
mac80211              231959  1 ath5k
ath                     8153  1 ath5k
cfg80211              144694  3 ath5k,mac80211,ath
led_class               2633  1 ath5k

``` 
Do these match up?

---

### Post by jacob.harris9799 on 2011-04-19
Im using my phone to post these, so on command line section at a time, sorry!

Rfkill list all
0: hp-wifi: Wireless LAN
     Soft blocked: yes
     Hard blocked: no
1: phys wireless LAN
     Soft yes
     Hard no

---

### Post by jacob.harris9799 on 2011-04-19
Lsmod | grep ath5k
Ath5k.                130051.  0
mac80211.        231541.  1.  Ath5k
ath.                         8153.    1. Ath5k
Cfg80211.          144470.    3 ath5k, mac89211, ath
Led_class.           2633.        1. Ath5k


Ok, so what does this clmmand actually do?

---

### Post by josephmills on 2011-04-19
> **jacob.harris9799 said:**
> Lsmod | grep ath5k
Ath5k.                130051.  0
mac80211.        231541.  1.  Ath5k
ath.                         8153.    1. Ath5k
Cfg80211.          144470.    3 ath5k, mac89211, ath
Led_class.           2633.        1. Ath5k


Ok, so what does this clmmand actually do?

ls mod lists the modules(parts of driver i think? dmesg shows things that load with the kernel grep is a filter you need a driver please look at this [http://ubuntuforums.org/showthread.php?t=1716547](http://ubuntuforums.org/showthread.php?t=1716547)     do what post # 9 says and tell us how it works out

---

### Post by jacob.harris9799 on 2011-04-19
Response:

E:Could not get lock /var/lib/dpkg/lib-  open (resource temporarily unavailable)
E:unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by josephmills on 2011-04-19
> **jacob.harris9799 said:**
> Response:

E:Could not get lock /var/lib/dpkg/lib-  open (resource temporarily unavailable)
E:unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

shoot I forgot to say close synaptic after reloading
so you can just close synaptic and then do ```
sudo apt-get upgrade
```

---

### Post by chili555 on 2011-04-19
> Rfkill list all
0: hp-wifi: Wireless LAN
[COLOR="Red"]Soft blocked: yes[/COLOR]
Hard blocked: no
1: phys wireless LAN
[COLOR="Red"]Soft yes[/COLOR]
Hard no Please try:```
sudo rfkill unblock all
```Now is the wireless working?

---

### Post by jacob.harris9799 on 2011-04-19
Haha no worries! Retrying now!

---

### Post by jacob.harris9799 on 2011-04-19
0 upgraded,installed, to remove, not upgraded.

Hmm?

---

### Post by josephmills on 2011-04-19
make sure you do what chill says that is one smart person right there ):P

---

### Post by jacob.harris9799 on 2011-04-19
Chilli555

**THANK YOUUUUU!!!!!!!!!!**

It works now!! Marking as solved!

Thank you for your time!

---

### Post by chili555 on 2011-04-19
You're welcome. I'll be back to answer when you ask how to make it permanent after reboot...

---

### Post by jacob.harris9799 on 2011-04-19
Or you could tell me now, or do I need to reboot?

---

### Post by jacob.harris9799 on 2011-04-20
You can answer now........... please and thank you!

---

### Post by josephmills on 2011-04-20
> **jacob.harris9799 said:**
> You can answer now........... please and thank you!

Did you reboot yet ?

---

### Post by jacob.harris9799 on 2011-04-20
Yes

---

### Post by josephmills on 2011-04-20
> **jacob.harris9799 said:**
> Yes

i assume that the wireless is working? Please take a look at this
[http://www.ubuntu.com/ubuntu/licensing](http://www.ubuntu.com/ubuntu/licensing)
[http://www.ubuntu.com/ubuntu/philosophy](http://www.ubuntu.com/ubuntu/philosophy)
[https://help.ubuntu.com/community/FreeFormats](https://help.ubuntu.com/community/FreeFormats)

---

### Post by jacob.harris9799 on 2011-04-20
I jinxed it. Not it doesn't work. Even tried the rfkill unblock all

---

### Post by josephmills on 2011-04-20
> **jacob.harris9799 said:**
> Lsmod | grep ath5k
Ath5k.                130051.  0
mac80211.        231541.  1.  Ath5k
ath.                         8153.    1. Ath5k
Cfg80211.          144470.    3 ath5k, mac89211, ath
Led_class.           2633.        1. Ath5k


Ok, so what does this clmmand actually do?

see we never got 
```
 dmesg | grep ath5k 
```
 as 
**dmesg**
lists all things that the kernel sees on boot(or something like that) And
**grep**
is a filter 
**ath5k** 
is the driver 
So 
**dmesg+grep+driver= driver on start up**
so 
** grep **
is a filter and it shows you the "filtered objects" in a different color.
 So if you don't see it when typed into the terminal then the firmware is not there  l  Am I right??
**source**
dmesg=http://unixhelp.ed.ac.uk/CGI/man-cgi?dmesg+8
grep=http://unixhelp.ed.ac.uk/CGI/man-cgi?grep

---

### Post by chili555 on 2011-04-20
Please do:```
sudo gedit /etc/rc.local
```Add a single line above exit 0:```
rfkill unblock all
```Proofread carefully, save and close gedit. Reboot.

Now is your wireless working?

---

### Post by jacob.harris9799 on 2011-04-26
> **chili555 said:**
> 
Now is your wireless working?

sorry it has taken o long, havent had time to breathe seems like!

just did everything and **YES!!!** it works thank the Lord Hallelujah Yall!!!!

yes, yall. i may be a state level winner in cyber security, but im still from Dixie! ( Alabama, for the Northern Aggression Fans :p) Im just joking. The only thing i have ever seen abot dixie is the liscense tag, which read "stars Fell on Dixie".... believe it or not, the only comet/meteorite to ever hit a person hit an old lady about 3 miles from where i sit right now. Little place calle Sylacauga. What a name, what a place!


Anyways! thanks! i owe yall one!

---

### Post by somnob on 2011-04-27
dude thanks.
my moms laptop with kubuntu has this problem.
it was driving me nuts. 
thank you so much:lol::D

---

### Post by googeek on 2011-05-13
dude thanks indeed!

---

### Post by zoidorous on 2011-10-24
> **chili555 said:**
> Please try:```
sudo rfkill unblock all
```Now is the wireless working?
hi chili555 i have a Compaq persario cq60 with a wireless problem.
tried your command and it unblocked the software side but not the hard ware now i get this

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


does anyone have any more ideas, also i don't seem to be able to open synaptic in 11.10 has it been removed?

---

