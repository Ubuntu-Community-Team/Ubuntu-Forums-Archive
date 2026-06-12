---
title: "after upgrade to Ubuntu 10.10 wireless is down/disabled/not working"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by devanggohel on 2011-05-31
Hi,

I was using Lenovo B460 with ubuntu 10.04 and finally decided to upgrade to 10.10.

But later I found that my wireless wasnt working and in Network manager was always showing it disabled.

I searched on the net and forums... so many tips and tricks I tried
Some said reinstall broadcom drivers some said to reinstall network manager itself
but in the end everything was useless.

later I found that 
***$ sudo rfkill list***
commad showed that wireless was soft-blocked.

so finally got root of the problem.
So here's a workaround solution for wireless problem you might also facing.

***$sudo gedit /etc/rc.local***

copy paste this code snippet just before*** exit 0 ***line
[B][I]
wifiblocked=$(lsmod | grep acer_wmi | wc -l)
if [ $wifiblocked -eq 1 ]; then
    rmmod -f acer_wmi
fi
rfkill unblock all[/I][/B]

and restart or
just run the shell script file in your command prompt with this command
***$sudo /etc/rc.local***

And it works for me!

---

### Post by nikkilee on 2012-03-03
I have same problem, but totally new to ubuntu, please how do I fix the wireless by doing as described above.
nikki

---

### Post by 23dornot23d on 2012-03-03
If you follow the instructions .... and put the commands as follows into a terminal ...

***sudo gedit /etc/rc.local***

it will first ask for your password so that you can edit the following file .....

the following will display ...

[IMG]http://img824.imageshack.us/img824/759/snapshot7d.jpg[/IMG]

After cutting and pasting the text in to it .....

It will then look like this .....


[IMG]http://img818.imageshack.us/img818/1337/snapshot8d.jpg[/IMG]



From what the person says that wrote it ...... save it and a reboot should get it to work ....

---

### Post by windowslicker on 2012-03-11
Thank you! Having experienced wifi connection problems in 10.04 I decided to upgrade to 10.10 which was causing much frustration due to the default wifi hard block. While searching for a solution over the past few days it seems to be a common problem. I'm sure there's a reason for 10.10 to be hard blocked by default but this is causing a lot of people a lot of problems. I was about to give up and stay with 10.04 before I found this tread. Hopefully this will be taken in to consideration in future releases.

Thanks again for passing this on.
:KS

*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.

---

