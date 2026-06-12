---
title: "Wireless Card Trouble Intel® PRO/Wireless 2200BG"
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by razl on 2013-01-03
trouble with the os detecting/installing the right firmware for my acer aspires Intel® PRO/Wireless 2200BG, its an old laptop and im just mesisng around trying to learn bits and bobs as im going along,

 [http://bughost.org/firmware/ipw2200-fw-3.1.tgz](http://bughost.org/firmware/ipw2200-fw-3.1.tgz) the firmware linked from the source forge site ([http://ipw2200.sourceforge.net/firmware.php) seems]("http://ipw2200.sourceforge.net/firmware.php)seems") to be dead


 Any way here is what error its giving me

[  118.244514] ipw2200: ipw2200-bss.fw request_firmware failed: Reason  -2 
[  118.244521] ipw2200: Unable to load firmware: -2
[  118.244526]  ipw2200: failed to register network device
[  118.244572] ipw2200  0000:02:04.0: PCI INT A disabled 
[  118.244624] ipw2200: probe of  0000:02:04.0 failed with error -5h   ------------  There are the main  lines that are giving me the error

---

### Post by razl on 2013-01-03
IDK why the formatting is all messed up was posting this on the backtrack os and wouldn't allow formatting, 

Edit- hoped on a windows machine to hopefully make it a bit more readable sorry

---

### Post by Pjotr123 on 2013-01-03
What Ubuntu version are you using? And please pay some attention to readability in your messages....

---

### Post by razl on 2013-01-03
> **Pjotr123 said:**
> What Ubuntu version are you using? And please pay some attention to readability in your messages....

Backtrack 5.3 , and again sorry wouldn't allow me to format the post (it looked fine as i was posting it ) hopefully it look slightly more readable now

---

### Post by chili555 on 2013-01-03
Try this and let us know if you need help installing it.

---

### Post by Kabooms on 2013-01-03
> **chili555 said:**
> Try this and let us know if you need help installing it.

 yeah i pust put it into lib/firmware right? if so still no joy mate (btw posting on 2nd accound forgot password for first on)

---

### Post by chili555 on 2013-01-03
> yeah i pust put it into lib/firmware right? After you extracted it, right? Let's check:```
ls /lib/firmware | grep ipw
```Ideally, you'll see:> ipw2100-1.3.fw
ipw2100-1.3-i.fw
ipw2100-1.3-p.fw
ipw2200-bss.fw
ipw2200-ibss.fw
ipw2200-sniffer.fw
Is that what you got?

---

### Post by Kabooms on 2013-01-03
ya thats what i got, i reloaded wcid and still not detecting wireless networks,  could it be something to do with rfkill? im not sure how it works but the switch on the front of my laptop doesnt light up orange like it would do in windows when i turn it on

---

### Post by chili555 on 2013-01-03
What does it tell us?```
rfkill list all
dmesg | grep ipw
```Did you reboot or reload the driver after you installed the firmware?```
sudo modprobe -r ipw2200 && sudo modprobe ipw2200
```

---

### Post by haqking on 2013-01-03
[http://www.backtrack-linux.org/forums/showthread.php?t=42681](http://www.backtrack-linux.org/forums/showthread.php?t=42681)

---

### Post by Kabooms on 2013-01-03
root@bt:~# rfkill list all 1: phy0: Wireless LAN 	Soft blocked: no 	Hard blocked: no  Still not showing up in wcid though, now the orange light is flashing tho so feel like im getting somewhere. :D

---

### Post by haqking on 2013-01-03
> **Kabooms said:**
> root@bt:~# rfkill list all 1: phy0: Wireless LAN     Soft blocked: no     Hard blocked: no  Still not showing up in wcid though, now the orange light is flashing tho so feel like im getting somewhere. :D

wicd is notoriously a piece of *cough* in Backtrack.

is the card working from terminal such as

first check to see if daemon is running first of all from terminal

```
wicd
```and then try
```

iwlist wlanx scan
```

where x denotes your adapter

---

### Post by Kabooms on 2013-01-03
ot@bt:~# wcid No command 'wcid' found, 
did you mean:  Command 'wicd' from package 'wicd-daemon' (universe) 
 Command 'scid' from package 'scid' (universe) 

root@bt:~# iwlist wlanx scan wlanx     
Interface doesn't support scanning.

---

### Post by haqking on 2013-01-03
> **Kabooms said:**
> ot@bt:~# wcid No command 'wcid' found, did you mean:  Command 'wicd' from package 'wicd-daemon' (universe)  Command 'scid' from package 'scid' (universe)  root@bt:~# iwlist wlanx scan wlanx     Interface doesn't support scanning.

yes i meant wicd seeing as that is what i wrote and that is the name of the app not wcid ;-)

what does iwconfig...ifconfig show ?

---

### Post by haqking on 2013-01-03
and what was the result of my post #10

---

### Post by chili555 on 2013-01-03
I believe ipw2200 produces an interface eth1.```
sudo iwlist eth1 scan
```You might have to change the Preferences page in Wicd to see eth1. Please see attached.

---

### Post by haqking on 2013-01-03
> **chili555 said:**
> I believe ipw2200 produces an interface eth1.```
sudo iwlist eth1 scan
```You might have to change the Preferences page in Wicd to see eth1. Please see attached.

yes thats right, alot of people forget to check wicd preferences to make sure the correct adaptor number is written in there. Also the OP doesnt need to use sudo as they are in BT which as you can see from posts above they are running as root.

to the OP you can also forget wicd and if adaptor is installed correctly then

```
ifconfig wlan0 up
```or ```
ifconfig eth1 up
``````
iwconfig wlan0 essid "essid"
``````
dhcpcd wlan0
```or assign a static if needed

---

### Post by Kabooms on 2013-01-03
Wow cant thank you guys enough, i see your guys taking time out of your own lives just posting everywhere helping people out, (literally spent a day or so goggling solutions )  i came across lots of dead links,  but yeah i really appreciate your help guys !!

can close this and mark as solved ty terry much again :D

---

### Post by haqking on 2013-01-03
> **Kabooms said:**
> Wow cant thank you guys enough, i see your guys taking time out of your own lives just posting everywhere helping people out, (literally spent a day or so goggling solutions )  i came across lots of dead links,  but yeah i really appreciate your help guys !!

can close this and mark as solved ty terry much again :D

Does that mean you got it fixed ?

if so make reference to what fixed your issue then mark the thread as solved to help others.

Peace

---

### Post by Kabooms on 2013-01-03
Ya its all working now <3

Well the drivers were def a huge help i couldnt find them anywhere all linke were dead 

wget [http://http.us.debian.org/debian/poo...0_0.34_all.deb](http://http.us.debian.org/debian/poo...0_0.34_all.deb) (the one from hackqing gave a 404 error [post 10]) and all the other links i googled were also dead including the sourceforge one linked from the actual Intel site :D

I forgot to mention i am running backtrack on a live cd (un fortuanltey guess i need to install it now)

Then i had to 

sudo modprobe -r ipw2200 && sudo modprobe ipw2200

rfkill list all showed me it was hardlocked untill i preseed the button on the front of my laptop which unlocked it 

iwconfig then showed it as eth1 

change the Preferences page in Wicd to see eth1

And then it showed up my wireless connections and im already learning so much..

Much love and thanks again

---

### Post by haqking on 2013-01-03
> **Kabooms said:**
> Ya its all working now <3

Well the drivers were def a huge help i couldnt find them anywhere all linke were dead 

wget [http://http.us.debian.org/debian/poo...0_0.34_all.deb](http://http.us.debian.org/debian/poo...0_0.34_all.deb) (the one from hackqing gave a 404 error [post 10]) and all the other links i googled were also dead including the sourceforge one linked from the actual Intel site :D

I forgot to mention i am running backtrack on a live cd (un fortuanltey guess i need to install it now)

Then i had to 

sudo modprobe -r ipw2200 && sudo modprobe ipw2200

rfkill list all showed me it was hardlocked untill i preseed the button on the front of my laptop which unlocked it 

iwconfig then showed it as eth1 

change the Preferences page in Wicd to see eth1

And then it showed up my wireless connections and im already learning so much..

Much love and thanks again

You are welcome, that link i posted had a bad source actually, the 34 should of been a 36.

Enjoy

---

### Post by chrinabuntu on 2013-01-11
I have this same card and have been having hella trouble getting it to work in Linux. Bought this laptop from eBay, came with Windows on it. Worked fine, but then I put Linux Mint on it and it would recognize the card, but not connect. (Have since tried several other Linux distros, still no luck.)

Ended up reloading that Windows OS and then it didn't work anymore. Eventually got it working (after much consternation) but still only in Windows. I have also had trouble finding what I need because links are old and dead, etc...but also because the places where I did find some instructions were just too complicated for me to follow. 

For some reason this thread never came up in my previous searches, but am going to follow along when I'm off work and see if I can get mine to work as well.

---

### Post by chili555 on 2013-01-11
> **chrinabuntu said:**
> 
For some reason this thread never came up in my previous searches, but am going to follow along when I'm off work and see if I can get mine to work as well.Please post back if we can help you.

---

### Post by bane058 on 2013-03-03
Thank you I have been trying to figure out how to get my intel card installed for the past day on my toughbook cf-29 H 

I was doing sudo modprobe ipw2100 ipw2200 

and it seems that 

sudo modprobe -r ipw2200 && sudo modprobe ipw2200
Fixed the issue

---

### Post by Tankr32 on 2013-04-22
thank you guys soooooo much ive been trying to figure this out on backtrack 5 r3 for almost a week now and i finally got it to work thanks to you guys so much again thank you.

---

