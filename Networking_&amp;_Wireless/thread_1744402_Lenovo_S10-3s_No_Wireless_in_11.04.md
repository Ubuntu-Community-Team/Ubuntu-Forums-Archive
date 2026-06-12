---
title: "Lenovo S10-3s No Wireless in 11.04"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by DieseL1988 on 2011-04-30
SIGH! I thought this had been fixed, so I upgraded, and now I have massive problems.

I've blacklisted acer-wmi as that was the fix previously, but that has no effect.

When I do an rfkill list it tells me brcmwl-0 is hard blocked, regardless of where the hard switch is. The hard switch is working fine for the bluetooth...

Any ideas?

---

### Post by DieseL1988 on 2011-04-30
Nevermind, solved.

Basically, you have to make sure you've got rfkill in a state where acer-wireless is softblocked and the actual wireless is NOT hardblocked. Then and only then can you unload acer-wmi and blacklist it.

---

### Post by aamir_must on 2011-05-02
I am also having the same Problem with 11.04, I had tried rfkill unblock all but it did'nt helped I am still not getting any wireless. :(

I also have Lenovo S 10-3s Ideapad.  Please help.

---

### Post by aamir_must on 2011-05-02
:KS

I think I have solved the Problem atleast temporarily and the Wireless is working, here is what I have done.

$ rfkill list all
$ sudo rmmod -f acer_wmi
$ sudo rfkill unblock all
$ sudo su
# echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf
# exit

:)

---

### Post by garfieldpbj on 2011-05-07
Hi

Can anyone tell me how they fixed it? All details please.. I am not able to fix it by following the instructions..

---

### Post by garfieldpbj on 2011-05-07
I just want to report a solution I used, with my Lenovo s10-3s (probably the same trick for s10-3 or any other Lenovo). I booted into windows, and used the "hardware switch", which is actually the Fn+F5 combination, turn wifi on, and rebooted.. 

Now I can even use both Fn+F5 and the manual switch at the computer side in ubuntu.. :-)

---

### Post by nas123 on 2011-05-08
Same here.
Lenovo Thinkpad Edge E520
Centrino Wireless-N 1000 
ubuntu 11.04

loaded acer_wmi at boot and disabled wireless

blacklist acer_wmi

all works just fine

---

### Post by mandaofpune on 2012-05-31
Hey thanks a lot..

I have a Sony Vaio with Intel Centrino -N 1000 wireless adaptor and I recently upgraded by Ubuntu 10.04 to 11.04 and suddenly no wireless networks were detected.. 

Read quite a few posts on this forum.. and finally bumped here.. I tried the $rfkill list all
and it showed "Soft blocked: yes" for acer-wireless 
so I did $sudo rmmod -f acer_wmi
and my wirelss was detected instantaneously !!!

I am really happy :) This is my first instance of successfully solving something by reading forum posts.. (as you would guess I am a newbie to Ubuntu)

Forum rocks!! Thanks guys :)

[B]I still can't figure out why this worked: 
$rkfill list all 
said that for sony-wifi (and my laptop is a Sony Vaio), there were no blocks.. There was a soft block only for acer wireless

Any idea?[/B]

---

### Post by mandaofpune on 2012-05-31
BTW... I also found out that if I just do the first two steps:

$ rfkill list all     (this shows me that there is still a soft block for acer wifi)
$ sudo rmmod -f acer_wmi   (this removes the module acer_wmi)

then the problem is solved only for the current session (i.e. untill I reboot). It is also fine if I hibernate and start again. But if I reboot then the wireless is again not detected. So I did all the steps i.e. above two followed by these:


$ sudo rfkill unblock all
$ sudo su
# echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf
# exit

Now I can get the wireless even after I reboot :) I am happy :)

---

