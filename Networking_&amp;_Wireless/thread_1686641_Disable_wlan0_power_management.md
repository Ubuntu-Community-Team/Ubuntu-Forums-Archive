---
title: "Disable wlan0 power management"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by Ginosal on 2011-02-12
Hi everybody. Since wlan0 power management causes malfunctions to my Atheros wireless device, I need to disable power management in order to get a good internet connection even when the computer is battery powered. Power management is set "off" when I plug in wall power and is set "on" when I unplug it. I want to set it always "off". I can do it by using:

```
sudo iwconfig wlan0 power off
```

But when I reboot, I have to do it again! I've tried adding that command to rc.locale, before exit 0, but nothing happens. Then I've tried adding the following lines to /etc/network/interfaces

```
auto wlan0
iface wlan0 inet dhcp
wireless-power off
```

but nothing. What else can I do? Thank you in advance!

---

### Post by Zookalicious on 2011-02-12
I can't give you the source where I read this from (can't bloody well remember) but I just did this same thing two days ago and this is what I did. 

```
gksu gedit /etc/pm/power.d/wireless
```and then I just put 
> 
#!/bin/sh

/sbin/iwconfig wlan0 power off
In the file.

Lastly, 
```

sudo chmod +x /etc/pm/power.d/wireless

```According to the thread that works, and my connection seems significantly more stable now when I try and get on the campus wifi. 

Hope that helps!

---

### Post by Ginosal on 2011-02-12
> **Zookalicious said:**
> I can't give you the source where I read this from (can't bloody well remember) but I just did this same thing two days ago and this is what I did. 

...

Hope that helps!
Hi Zookalicious. Thank you, I'll try your solution, but I must admit that I've found another one while I was waiting for an answer. I'm writing it here, maybe someone will need it. In my first post, I've written that I have also edited /etc/rc.local and added

```
/sbin/iwconfig wlan0 power off
```

But I did not consider that I have to make that command run AFTER the association of the wlan0 connection. So, before the above-mentioned command, I also added

```
sleep 30
```

Of course, everything **before** "exit 0". Well, it seems to work fine! :)

I'll try Zook's solution and I will write about it later! Thank you anyway!

---

### Post by Ginosal on 2011-02-12
> **Zookalicious said:**
> I can't give you the source where I read this from (can't bloody well remember) but I just did this same thing two days ago and this is what I did. 

```
gksu gedit /etc/pm/power.d/wireless
```and then I just put 
In the file.

Lastly, 
```

sudo chmod +x /etc/pm/power.d/wireless

```According to the thread that works, and my connection seems significantly more stable now when I try and get on the campus wifi. 

Hope that helps!

This solution works, too, and works better then the first I've used. rc.local solution worked, too, but there was a problem. as I plugged in and then plugged out again AC power, power management was set to "on" again. But with the solution suggested by Zook, power management for wlan0 will ALWAYS be switched off... Thank you Zook!

---

### Post by Zookalicious on 2011-02-13
Excellent! Glad that worked for you :)

---

### Post by J Caffrey on 2011-05-03
I have a clean install of 11.04. When I try to copy and paste Zook's commands into terminal the file opens but it's blank. I close it without saving and "no such file or directory errors" appears in terminal. What am I doing wrong? This is what appears in terminal.  john@john-WIM2180:~$ gksu gedit /etc/pm/power.d/wireless

(gedit:2856): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2856): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.Y738UV': No such file or directory

(gedit:2856): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
john@john-WIM2180:~$

---

### Post by Ginosal on 2011-05-03
> **J Caffrey said:**
> I have a clean install of 11.04. When I try to copy and paste Zook's commands into terminal the file opens but it's blank. I close it without saving and "no such file or directory errors" appears in terminal. What am I doing wrong?:confused

If you're talking about /etc/pm/power.d/wireless , it doesn't exist, you must create it from scratch and add
```

#!/bin/sh

/sbin/iwconfig wlan0 power off

```

then save.

---

### Post by J Caffrey on 2011-05-03
Thanks for that its working perfectly. I'm a bit rusty having made a comeback to ubuntu.

---

### Post by Ginosal on 2011-05-03
> **J Caffrey said:**
> Thanks for that its working perfectly. I'm a bit rusty having made a comeback to ubuntu.

I'm happy I could help you like Zook helped me... ):P

---

### Post by kozhy on 2011-05-07
thank you , i solved this problem. it was kill me

---

### Post by doogiekd on 2011-09-15
hi. i have followed the instructions exactly as stated above, but the solution is not permanent.

upon reboot, iwconfig states power management is "on."

i thought it must be a syntax error, but i am certain that i did everything correctly - including the chmod command.

doing a manual sudo iwconfig wlan0 power off at every sesssion does turn wlan0 powersave off - but i would really like to make this change permanent. 

any suggestions?

thanx, 

k.

---

### Post by doogiekd on 2011-09-15
dear friends, 

i followed the instructions as indicated above, but my system was still booting with the wlan0 powersave "on."

so i tried entering this command in a file that allows you to enter sudo commands and it will execute those commands at startup. (note: there seems to be dozens of ways to run a sudo command at startup. i found this one to be the best):

the file name is:

rc.local

edit the following file by entering: 

sudo gedit /etc/rc.local

add the lines to disable wlan0 wireless:
sleep 10 (this gives the wireless dongle/card time to to load, before executing the command below)
"iwconfig wlan0 power off"

important! make sure there is a line at the very end that reads:

"exit 0"

this will bypass any errors and allow the system to continue to boot.

you can add other startup commands here as well - very useful.

it should look like this:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sleep 10
iwconfig wlan0 power off
exit 0

---

### Post by Wc2c on 2011-10-08
Thanks Doogie,

Your solution seemingly is the last piece to the puzzle. Now I'm going to have to try this and if it solves my wifi problem at public places. But it is for sure going good from home!

---

### Post by doogiekd on 2011-10-08
wc2c, 

glad i could finally help someone, instead of the other way around...peace.

---

### Post by Wc2c on 2011-10-10
> **doogiekd said:**
> wc2c, 

glad i could finally help someone, instead of the other way around...peace.

Yeah, I havn't really dug deep into the intricate side of linux at all, something to sink into.

Well, I'm at the coffee shop and I realize most websites take few more seconds to load than normal, and if I was surfing for a while this wouldn't be much fun.

It seems I still have to type in the command to power off my eth1.

I will have to look for more solutions. Will post back if I do find anything.

---

### Post by morgs on 2011-12-22
> **Wc2c said:**
> Yeah, I havn't really dug deep into the intricate side of linux at all, something to sink into.

Well, I'm at the coffee shop and I realize most websites take few more seconds to load than normal, and if I was surfing for a while this wouldn't be much fun.

It seems I still have to type in the command to power off my eth1.

I will have to look for more solutions. Will post back if I do find anything.

If your wireless network interface is eth1, then replace wlan0 with eth1 in the above examples.

---

### Post by dedieko on 2012-06-27
> **morgs said:**
> If your wireless network interface is eth1, then replace wlan0 with eth1 in the above examples.

Hello, I just want to say thanks for this workaround

I'm running 12.04 and this wireless hickup is really bugging me.

So, my conclusion:

by creating "wireless" in power.d will disable power switch everytime I unplug/plug the adaptor

and

by adding line in "rc.local" will disable power management of my eth1 at boot.

Thanks.

---

### Post by FuzzyFeat on 2012-07-09
[LIST]
[*]There was a Desktop app that disabled power management clicked. I used it a lot on 10.4. Now I have loaded 12.4 I can no longer find it in the repository. I need it, esp when doing a lot of coppying and backing up. Anyone know where I can find it?
[/LIST]

---

### Post by mfaroukg on 2012-10-30
> **Zookalicious said:**
> I can't give you the source where I read this from (can't bloody well remember) but I just did this same thing two days ago and this is what I did. 

```
gksu gedit /etc/pm/power.d/wireless
```and then I just put 
In the file.

Lastly, 
```

sudo chmod +x /etc/pm/power.d/wireless

```According to the thread that works, and my connection seems significantly more stable now when I try and get on the campus wifi. 

Hope that helps!
Thanks

---

