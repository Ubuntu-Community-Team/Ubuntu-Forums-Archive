---
title: "Wireless light constantly blinking on Compaq Presario CQ60 laptop"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by James2k on 2010-05-13
I have a Compaq Presario CQ60 laptop and have one of those wireless light indicators. For me the light glows orange when the wireless is OFF and blue when the wireless is ON. In Ubuntu 9.10 (Karmic) the light was always orange, even if the Wireless was on, but my wireless worked right out of the box so I was grateful for that, but since upgrading to Ubuntu 10.04 (Lucid) I've noticed that my wireless light alternates between orange and blue frequently and sometimes flashes madly when wireless activity is occurring.

I was wondering if there is a fix for this as it can get quite annoying, the light sometimes stays blue for a while but will ultimately keep going back to orange and vice-versa, my friend who also has a Compaq Presario CQ61 (Revised model of mine) has his wireless light constantly blinking orange and blue no matter what.

The wireless itself works fine, I can connect to any wireless connection and use it without having to install anything else, so it does work out of the box, which again, I'm grateful for.

The wireless adapter is a Atheros AR5001 Wireless network adapter. Do I need to install additional packages or drivers to get the wireless adapter to work properly?

Hope someone can help me!

Thanks,

---

### Post by Paulo Carvalho on 2010-05-27
Hi there funny, I am looking for the same solution!

---

### Post by btmitchell on 2010-06-01
Same problem also  (although I'm using a CQ61)..

---

### Post by Iron_maiden_forever on 2010-06-04
To fix this bug I did as per this [advice]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250211/comments/52"):

root@ubuntu-laptop:/# echo none > /sys/class/leds/ath9k-phy0\:\:rx/trigger
root@ubuntu-laptop:/# echo none > /sys/class/leds/ath9k-phy0\:\:tx/trigger

*you should be root to do this. If you don't know your root password, set one ('sudo passwd root').

'ls' /sys/class/leds/ to change the above commands accordingly.

@ubuntu-laptop:~$ ls /sys/class/leds/
ath9k-phy0::assoc/ ath9k-phy0::rx/    hp::hddprotect/    
ath9k-phy0::radio/ ath9k-phy0::tx/    mmc0::/ 

Also, you will save it in a script so you don't have to repeat the commands every time your computer restarts:

@ubuntu-laptop:/$ sudo gedit /etc/network/if-up.d/wlan-no-blink

Put this in your script (remember to change 'ath9k-phy*x' if necessary; eg. 'iwl-phy*X'):

#!/bin/sh
if [ "$IFACE" = "wlan0" ]; then
	for dir in /sys/class/leds/ath9k-phy*x; do
		echo none > $dir/trigger
	done
fi

Now make it executable:
@ubuntu-laptop:/$ sudo chmod a+x /etc/network/if-up.d/wlan-no-blink

Done!

---

### Post by gonzalioz on 2010-08-10
Hi,

I have a compaq presario CQ61 and having the same problem. I tried to perform the steps in the post above, but I don't really understand what to do.

I copy pasted the first command and get this:

taco@taco-laptop:~$ root@ubuntu-laptop:/# echo none > /sys/class/leds/ath9k-phy0\:\:rx/trigger
bash: /sys/class/leds/ath9k-phy0::rx/trigger: Permission denied
taco@taco-laptop:~$

I am sorry, but can somebody explain it to me again in simple english and for a 4 year old :).

Thanks a lot in advance!

---

### Post by James2k on 2010-08-28
Thanks for the fix, however I have since moved to the madwifi atheros drivers for packet injection support on my card. The wireless light just stays orange when the madwifi driver is in use, which isn't a major issue for me. 

For people using the standard ath5k and ath9k drivers though, the above solution works great.

---

### Post by James2k on 2010-09-12
I've switched back to the ath5k driver for better support. I'll go through the fix for anyone having difficulty:

First of all you will need to be root to run these commands so open up a terminal window and type:

```
sudo -s
```Type in your password to drop to root@ubuntu.

First off all you will need to find if your system is using the Atheros 5k or 9k driver. So you can run the following commands in the terminal we've opened to find out:

```
echo none > /sys/class/leds/ath9k-phy0\:\:rx/trigger
echo none > /sys/class/leds/ath5k-phy0\:\:tx/trigger

```For Compaq CQ60's the driver is ath5k however executing both of these commands, you will find one will execute with no errors and one will execute with the directory not found error. Whatever one executes silently is the ath driver in use. In my case, the ath5k driver.

Upon executing the command that is relative to your ath driver you should find the wireless light changes and now doesn't blink when network activity is occurring.

However, the change we have done will not be saved permanently, we have to create a script to make sure the wireless light doesn't blink on each reboot of the machine.

Run the following command in terminal:

```
gedit /etc/network/if-up.d/wlan-no-blink
```And now add the following into the blank text file:

```

#!/bin/sh
if [ "$IFACE" = "wlan0" ]; then
    for dir in /sys/class/leds/ath5k-phy*x; do
        echo none > $dir/trigger
    done
fi

```**This example is for the ath5k driver, if you are using the ath9k driver, make sure you change number 5 to 9**

Now you have the script, save and close gedit. Now in the terminal window, run the following command:

```
chmod a+x /etc/network/if-up.d/wlan-no-blink
```Now upon each reboot your wireless light change will be saved.

Thanks again Iron_maiden_forever for posting the fix and gonzalioz, hopefully I've helped you understand the process a bit better.

---

### Post by marcopolo1981 on 2010-09-16
I have a CQ60, and have the same 'problem'. Only I never thought it was a problem, as it only flashes when data is being transferred. When idle, it stays blue. The way I saw it, it was letting me know that data was being transferred. Does it actually have a negative effect when it does this?

---

### Post by James2k on 2010-09-16
You are correct the wireless light blinks when data is being transferred. I found this an annoyance more than an actual problem. But like I said for Compaq Presario CQ61 users, the wireless light constantly blinks every second regardless (Well it did for my friend), so that's why I wanted to disable mine blinking.

---

### Post by chaceos on 2010-09-20
I have the same problem except I'm using an HP Pavillion dv6000. For the record, after installation of Ubuntu 10.4 everything goes well and I'm very happy. 
Anyway this blinking wasn't happening in windows xp and this is the only reason I realize this might be a problem. Like said above it only blinks when data is transfering.
My questions:
Atheros 5k or Atheros 9k is a wireless driver?
What if my pavillion dv6000 has none of them?
Is there another way to be sure?
and if I have another driver how is the correction of the script above??

Thanks very much guys(meaning girls2)! Keep doing good!

P.S. Not very good English, Very noob.

---

### Post by Nodaki on 2010-10-20
The fix listed did not work on my HP 8510P.


```
root@xxxxxx:/sys/class/leds/mmc0::# ls /sys/class/leds/mmc0\:\:
brightness  device  max_brightness  power  subsystem  trigger  uevent
```

The rx and tx subdirectories do not exist. 

Running this did not return errors but did not do anything either.

```
root@xxxxxx:/sys/class/leds# echo none > /sys/class/leds/mmc0::/trigger
```


 Any other ideas?

---

### Post by ruionwriting on 2010-12-01
None of the above solutions worked for me. My laptop is an HP nx9420 and i'm running Maverick (10.10).

The solution can be found [here]("http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops"):

Run in terminal:
```
gksudo gedit /etc/modprobe.d/wlan.conf
```

Add the line:
> options iwlcore led_mode=1

Just reboot and that's it. Works flawlessly.

---

### Post by Tiekiller2 on 2011-01-13
> **James2k said:**
> I've switched back to the ath5k driver for better support. I'll go through the fix for anyone having difficulty:

First of all you will need to be root to run these commands so open up a terminal window and type:

```
sudo -s
```Type in your password to drop to root@ubuntu.

First off all you will need to find if your system is using the Atheros 5k or 9k driver. So you can run the following commands in the terminal we've opened to find out:

```
echo none > /sys/class/leds/ath9k-phy0\:\:rx/trigger
echo none > /sys/class/leds/ath5k-phy0\:\:tx/trigger

```For Compaq CQ60's the driver is ath5k however executing both of these commands, you will find one will execute with no errors and one will execute with the directory not found error. Whatever one executes silently is the ath driver in use. In my case, the ath5k driver.

Upon executing the command that is relative to your ath driver you should find the wireless light changes and now doesn't blink when network activity is occurring.

However, the change we have done will not be saved permanently, we have to create a script to make sure the wireless light doesn't blink on each reboot of the machine.

Run the following command in terminal:

```
gedit /etc/network/if-up.d/wlan-no-blink
```And now add the following into the blank text file:

```

#!/bin/sh
if [ "$IFACE" = "wlan0" ]; then
    for dir in /sys/class/leds/ath5k-phy*x; do
        echo none > $dir/trigger
    done
fi

```**This example is for the ath5k driver, if you are using the ath9k driver, make sure you change number 5 to 9**

Now you have the script, save and close gedit. Now in the terminal window, run the following command:

```
chmod a+x /etc/network/if-up.d/wlan-no-blink
```Now upon each reboot your wireless light change will be saved.

Thanks again Iron_maiden_forever for posting the fix and gonzalioz, hopefully I've helped you understand the process a bit better.


I had the same problem, after a clean install with Windows 7. The above worked. after installing 10.04 twice, the first time my nvidia drivers did not wrk properly, everything now works flawlessly. Anyways thx for the solution.

---

### Post by sailorboy on 2011-02-12
I have the presario cq-61-420 (amd athlon/ati) with the atheros wlan and it seems to blink during data Xfr, and goes blue at idle at various hot-spots. At home, it seems to continually alternate (works fine otherwise)- so may differ with router configs or # clients using it.
 I think I'll leave it alone since it clues me as to data xfr which can be erratic at some places. 
 These forums ARE a big plus- thanx to everyone.

---

### Post by smackdown on 2012-01-09
I had a second fresh installation on my HP 6530b with Ubuntu 10.10 and this flashing BLUE / Orange LED was driving me crazy as well. jeez. 

OK, HOW I FIXED IT ... just turned the bluetooth ON from the icon next to the wifi icon , lol . how lame.

I went trough 5 min registration process just to share that, I must be loco.

---

### Post by MARP1961 on 2012-01-09
This has just worked on my Compaq Presario CQ70. Thanks so much! The wireless light has always flickered orange and blue but not any more.

---

### Post by timbraun on 2012-01-25
> **ruionwriting said:**
> None of the above solutions worked for me. My laptop is an HP nx9420 and i'm running Maverick (10.10).

The solution can be found [here]("http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops"):

Run in terminal:
```
gksudo gedit /etc/modprobe.d/wlan.conf
```

Add the line:


Just reboot and that's it. Works flawlessly.
This was the clue I needed for my HP 8510p. The wireless module name is now iwl_legacy, so my /etc/modprobe.d/wlan.conf contains :

```
# 1 means don't blink
options iwl_legacy led_mode=1

```

---

