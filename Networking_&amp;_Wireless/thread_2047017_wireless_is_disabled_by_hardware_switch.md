---
title: "wireless is disabled by hardware switch"
date: 2012-08-24
forum: Networking &amp; Wireless
---

### Post by bhargo on 2012-08-24
hi all..
I am kind of new to ubantu. I am facing this problem " wireless disabled by hardware switch " can someone please help me ?
 
I have following information::
output of rfkill list 
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


output of rfkill unblock all
bhargav@bhargav-Inspiron-1018:~$ rfkill unblock all
bhargav@bhargav-Inspiron-1018:~$ rfkill list 
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

I have tried 
bhargav@bhargav-Inspiron-1018:~$ ifconfig wlan0 up
SIOCSIFFLAGS: Permission denied

Can someone please help me..? I desperately need wireless in my dell inspiron mini -1018

---

### Post by bhargo on 2012-08-24
Anybody ???

---

### Post by kurt18947 on 2012-08-24
There are very knowledgeable wireless networking people here.  I am not one but I assume you've tried any hardware or key combination switches?  Being both hard blocked and soft blocked almost seems like there's a hard switch somewhere turned off.  You could try this from a sudo account in terminal:

"sudo rfkill unblock all"

I'm doubtful but it's worth a try.

---

### Post by bhargo on 2012-08-24
Thanks Kurt..I had tried that and it did nothing...!

Thanks anyways!

---

### Post by chili555 on 2012-08-24
Please tell us which Ubuntu version you are running:```
lsb_release -d
```We wonder what dell module is loaded:```
lsmod | grep dell
```Thanks.

---

### Post by bhargo on 2012-08-26
bhargav@bhargav-Inspiron-1018:~$ lsb_release -d
Description:    Ubuntu 12.04.1 LTS
bhargav@bhargav-Inspiron-1018:~$ lsmod | grep dell
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
bhargav@bhargav-Inspiron-1018:~$ 



Thanks in advance

---

### Post by chili555 on 2012-08-26
Please try:```
sudo modprobe -r dell-laptop
sudo rfkill unblock all
rfkill list all
```Any change?

What model Dell is it?

---

### Post by hawkmage on 2012-08-26
I don't know if this is related but on an HP laptop I have there is a BIOS setting that turns off the Wireless adapter if a wired interface is plugged in.

---

### Post by bhargo on 2012-08-27
Mine is a dell inspiron mini laptop 1018


and i guess these commands did not work

bhargav@bhargav-Inspiron-1018:~$ sudo modprobe -r dell-laptop
[sudo] password for bhargav: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.config, it will be ignored in a future release.
bhargav@bhargav-Inspiron-1018:~$ sudo rfkill unblock all
bhargav@bhargav-Inspiron-1018:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes



@hawkmage dude..this is a new problem i am encountering.. I had used wireless and wired connections in my system previously...anyways I would like to try ur solution if u could please elaborate as to what exactly u have done with the bios settings..

---

### Post by chili555 on 2012-08-27
> WARNING: All config files need .conf: /etc/modprobe.d/blacklist.config, it will be ignored in a future release.We'd better take a look and try to fix that first. Please run and post:```
cat /etc/modprobe.d/blacklist.config
```We'll find out what's in there and place it in the correct spot and then delete this incorrect file.> I don't know if this is related but on an HP laptop I have there is a BIOS setting that turns off the Wireless adapter if a wired interface is plugged in. I think he's suggesting you look around in the computer's BIOS to make sure any settings related to wireless enable and not disable it. Almost all computers will safely run Linux with the BIOS set to DEFAULT.

---

### Post by bhargo on 2012-08-27
bhargav@bhargav-Inspiron-1018:~$ cat /etc/modprobe.d/blacklist.config
blacklist hp-wmi
bhargav@bhargav-Inspiron-1018:~$ 


and I will check bios...! Thank u..!;)

---

### Post by chili555 on 2012-08-27
> Mine is a dell inspiron mini laptop 1018And then:> blacklist hp-wmiI highly doubt that [COLOR="Red"]hp[/COLOR]-wmi is in any way applicable to a Dell. I'd remove the file:```
sudo rm /etc/modprobe.d/blacklist.config
```

---

### Post by bhargo on 2012-08-29
Dude.. i did that..but with no relief...can u suggest further course of action..!

---

### Post by chili555 on 2012-08-29
Please do:```
rfkill list all
```Now do:```
sudo modprobe -r dell-laptop [COLOR="Red"]<--it may be dell-wmi[/COLOR]
sudo rfkill unblock all
rfkill list all
```Any change? Now press the wireless button, F2, I believe.```
rfkill list all
```Any change?

---

### Post by bhargo on 2012-08-30
bhargav@bhargav-Inspiron-1018:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
bhargav@bhargav-Inspiron-1018:~$ sudo modprobe -r dell-laptop
[sudo] password for bhargav: 
bhargav@bhargav-Inspiron-1018:~$ sudo rfkill unblock all
bhargav@bhargav-Inspiron-1018:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
bhargav@bhargav-Inspiron-1018:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
bhargav@bhargav-Inspiron-1018:~$ 


Still no help dude!

---

### Post by chili555 on 2012-08-30
Please check in the computer's BIOS to be sure there are no settings that enable and disable wireless. Reset the BIOS to defaults. Then try:```
rfkill list all
```Try the F2 button.```
rfkill list all
```Try Fn+F2.```
rfkill list all
```You might also try Alt+F2 and Ctrl+F2.

---

### Post by bhargo on 2012-08-31
I tried on BIOS..It has wireless settings with options ENABLED and DISABLED.. they were all enabled..


and i tried all these commands before posting in this forum..I have tried them again now with no respite.. 

anything else we can do??


Thanks again!

---

### Post by chili555 on 2012-08-31
Did you reset the BIOS to Default?

---

### Post by bhargo on 2012-09-02
Solved...!

Thanks a ton dude..!U made my life looot easier! Thank u so much!!

I did not know how to restore the defaults..!

googled it and did it..!

Thanks again!):P):P):P):P

---

### Post by chili555 on 2012-09-02
Awesome! Glad it's working.

Please use thread tools at the top to mark Solved.

---

### Post by bhargo on 2012-09-02
Now that it is solved..Would u tell me if u do this for living..?
Does Ubantu pay u ?

---

### Post by chili555 on 2012-09-02
I have been retired for many years. I do this for the fun of it. I learn quite a lot and enjoy the challenge. Here is my entire payday:> Thanks a ton dude..!U made my life looot easier! Thank u so much!!Those rewards are all I seek.

When I first started in Linux, there were forums where people were rude and aloof. I vowed right then that if I ever knew enough to answer a single question, that I'd do so politely and with respect. I'd like to think that my example has lead others to answer posts the same way. If you are enjoying Ubuntu and are happy with your forum experience, I am a happy man.

---

### Post by bhargo on 2012-09-03
Its nice to meet you sir..

All the best!

---

### Post by 11arbor on 2012-09-29
I recently had the same problem with ubuntu 12.04 installed on an hp envy spectre xt. 
It turned out to be a bios problem and resetting to defaults fixed it. The funny thing is, I don't know how the bios setting was changed in the first place. 

Another temporary fix I found was to do
$ sudo rmmod hp_wmi
$ sudo rfkill unblock all
And then the wifi+bluetooth would work. 
However, adding hp_wmi to the blacklist file did not solve the problem after re-booting.

---

### Post by chili555 on 2012-09-29
> However, adding hp_wmi to the blacklist file did not solve the problem after re-booting.Please show me:```
cat /etc/modprobe.d/blacklist.conf | tail -n5
```

---

### Post by baba7890 on 2012-12-16
Many many thanks, this made our day much much better.
The bios default reset was the thing that worked (Dell Inspiron 1018), after trying many different more complicated solutions that were presented online.
Take a bow!

---

### Post by muzzyr on 2013-01-06
hi there
I have same problem, I tried the rfkill command, but it changes nothing. any suggestion?
my laptop is a Lenovo 460 with Ubuntu 12.04

---

### Post by chili555 on 2013-01-06
> **muzzyr said:**
> hi there
I have same problem, I tried the rfkill command, but it changes nothing. any suggestion?
my laptop is a Lenovo 460 with Ubuntu 12.04Let's see:```
rfkill list all
```Are you quite certain the wireless key combination is set to turn the wireless on? Does the LED change?

---

### Post by marinaG0 on 2013-06-07
Same problem here. It wasn't a BIOS problem though. 
```
 
rfkill unblock all

``` solved it.

---

