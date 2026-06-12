---
title: "Toshiba Satellite L500D wireless please help"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by slo82 on 2010-02-12
[http://ubuntuforums.org/showthread.php?p=8817238&posted=1#post8817238](http://ubuntuforums.org/showthread.php?p=8817238&posted=1#post8817238)

ok the above link is a thread i started yesterday but the helpfull guy ran out of ideas then i realised there was a dedicated networking section on this forum,  im new here and want wireless to work on my laptop to retain its portability. 

can someone please help me. im lost, should i reinstal Ubuntu and run the updates for a clean start on this, i have very limited knowledge but not afraid to get my hands dirty and wonr give up. i just need someone to light the way for me.

any help will be greatly appreciated thanx in advance people

Adrian

---

### Post by chili555 on 2010-02-12
When you did this command:```
[COLOR="Red"]sudo su -[/COLOR]
root@slo82-laptop:~# make
make: *** No targets specified and no makefile found. Stop.
```You told the system with the little hypen, that you also wanted to change directories to the root's home directory, which it did:> root@slo82-laptop:[COLOR="Red"]~[/COLOR]Since you were no longer in the directory '/home/slo82/Desktop/rtl8192se_linux_2.6.0010.1012.2009' then you were no longer in the directory containing the Makefile and associated files.

Please try again, with:```
sudo su
```No hyphen.> not afraid to get my hands dirty and wonr give up.Outstanding!!

---

### Post by slo82 on 2010-02-12
thanx chilli i worked that out already mate, the tread with the how tooo had comments further down that i read then quickly realised...

im still confused with this, ill be honest alot of this im just cutting and pasting without even the slight understanding of what alot of it means.

so anyway the link with the 10 steps what ever i used i got all the way through it to the point of saying rebood and it should work,  but nope ive missed something...

...im just a little worried after trying a few different threads etc that i may render the wireless useless, like start a how too then end up halfway through it STUCK, then get advice from someone else something different will i end up with a mess....

but anyway regardless i appreciate any help you can give and i hope to somehow return the favour one day...

---

### Post by chili555 on 2010-02-12
Let's go back to basics. Let's rebuild the module. Please cd to the correct directory and do:```
sudo su
make clean
make
make install
```Does it make and make install with *NO* errors? (It does for me with no warnings or errors.) Warnings are OK, but not errors. Next, please do:```
updatedb
```We will rebuild a searchable database so we can find virtually anything on your computer. It takes a few moments, so be patient.```
locate r8192se_pci.ko
```Do you find it, like this?> /lib/modules/2.6.31-19-generic/kernel/drivers/net/wireless/r8192se_pci.koIf so, then do:```
modprobe r8192se_pci
```Does the module load with no complaints? If so, see if a wireless interface was created:```
iwconfig
```If so, click Network Manager and connect.

Does it stick after a reboot? Post back and let us know your progress.

---

### Post by slo82 on 2010-02-12
mate your post there worked perfectly, straight up no errors or anything,

i can see the wireless in the network manager, BUT (there is always a BUT) 

i rebooted and it loads on reboot even,

trick is, i put the security KEY in when it asks for it, but it never connects, it just keeps spinning like its trying to connect but never does,  i can see a few networks in my area and yea just cant connect.

any ideas?

---

### Post by northd_tech on 2010-02-12
Is your WiFi router/radio using the [older] WEP, WPA, WPA2, tkip, etc. encryption slo82?  Those key/encryption settings sound like your [new ;) ] problem to me.  The Realtek 8192SE sounds much easier to work with than the Realtek 8192E that I've been swearing at for months now (Toshiba Satellite P505D laptop).  

You might do a search here for the "Realtek 8192SE" threads (you'll probably see chili555's name on some of the more recent ones too). ;) 

It might help to check your router documentation or their website and maybe post the router model and make.  Searching for that router model might turn something up here too.

edit:  If there's a coffee shop/internet cafe, McDonalds/Arby's, or library in your neighborhood that is still open and has "open" (unencrypted) WiFi, it might be worth a quick trip there to check that out by process of elimination to see if you can connect wirelessly now.

---

### Post by slo82 on 2010-02-12
ill quickly just as a temp experiment disable the security on my wireless. and see if it connects, if so ill play with the security and see if i find something that works.

---

### Post by chili555 on 2010-02-12
> i put the security KEY in when it asks for itWEP or WPA? In which drop-down slot?

---

### Post by slo82 on 2010-02-12
well i disabled the security on my router, with no security it still wont connect...

its a 64bit wep key,   all i am doing is clicking on the network icon next to clock top right then it tries to connect and that is as far as it gets even with the security disabled as i briefly tried...

(oh it asked for a key in a pop up window)

---

### Post by northd_tech on 2010-02-12
> **chili555 said:**
>  Next, please do:```
updatedb
```We will rebuild a searchable database so we can find virtually anything on your computer. It takes a few moments, so be patient.

Hi chili555,

FWIW- my ubuntu throws the following error when updating the **locate** database:

> updatedb: can not open a temporary file for `/var/lib/mlocate/mlocate.db'
This works though:

```
sudo updatedb
```It took several ( <= 10 ) minutes too.

---

### Post by slo82 on 2010-02-12
sudo updatedb

well i went into teminal and ran that, only takes about 30sec then yea searched fror wireless connections again and its working, im sending this from my wireless ubuntu laptop...   now for the test ill reset the machine and see how it goes...   thanx so so much mate u are a life saver

---

### Post by chili555 on 2010-02-13
Glad it's working! Have fun.

---

