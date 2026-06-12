---
title: "wireless non connection"
date: 2012-11-26
forum: Networking &amp; Wireless
---

### Post by Pedroski55 on 2012-11-26
Hi! I've had this problem for a long time now. Maybe someone here can help me solve it.

My computer sees the wireless network at home, ChinaNet-zbgJ.  The dsl router is brand new, they just changed things to make it faster. I have the password, it is written on the router. Ubuntu says I am connected, but I could never, cannot now, access the internet via wireless at home.

There is no hardware fault. My son uses Win, and connects via wireless. I can connect at work to the wireless network using this computer and Ubuntu. 

Some setting is stopping the connection. Does anyone here have any idea what?? I have read various threads and tried their solutions to no avail.
I  also have Fedora installed. The problem is the same.
[pedro@peterbedroom ~]$ iwconfig
ppp0      no wireless extensions.

lo        no wireless extensions.

em2       no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ChinaNet-zbgJ"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 4C:B1:6C:BB:92:B7   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:15   Missed beacon:0

[pedro@peterbedroom ~]$

---

### Post by wildmanne39 on 2012-11-26
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by Pedroski55 on 2012-11-26
Thanks for your reply, I would really like to know what the problem is. It's beenn going on for a long time now.

Sorry, but I am in China. They apparently don't like your dropbox, they reset the connection:

pedro@pedro-bedro:~$ wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2012-11-27 08:29:50--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 50.17.207.244, 107.20.182.97, 50.19.221.73, ...
Connecting to dl.dropbox.com (dl.dropbox.com)|50.17.207.244|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Retrying.

I can use Astrill VPN, but that only configures Firefox to bypass 'The Great Firewall', won't help wget.
Could you send the script to my gmail?? [EMAIL="peternanjjing@gmail.com"]peternanjjing@gmail.com[/EMAIL] Does it need root privileges?

Don't worry, I went directly there and got it via Firefox!

---

### Post by wildmanne39 on 2012-11-26
Here are directions for running the script without internet so you can do it manually.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by Pedroski55 on 2012-11-26
Here the text info Thanks very much!

---

### Post by ahallubuntu on 2012-11-26
You have a Realtek RTL8188CE wireless card.  There are known problems with the built-in kernel driver for this card.  The usual solution is to build the latest driver from Realtek's website:

[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

---

### Post by Pedroski55 on 2012-11-26
Followed the links and it downloaded a zero byte .tar.gz!!!

I think there is just some setting not right. As I mentioned, at school I can connect to the wireless using Ubuntu. The problem may be in the router, or in my computer, but it is only at home.

---

### Post by wildmanne39 on 2012-11-26
Hi, there is usually an alternative to installing there driver, but you also have a softblock so I am looking for the solution to that, I know we will probably need to blacklist and module but I am not sure of the exact one.
Thanks

---

### Post by wildmanne39 on 2012-11-26
Hi, I guess first lets try:
```
rfkill unblock all
```
and check it with
```
rfkill list all
```
now is the softblock gone?
Thanks

---

### Post by Pedroski55 on 2012-11-26
Take your time, I've had  this problem for at least two years, a bit longer won't matter. I'd just like to know what the problem is, even if it can't be fixed!

---

### Post by Pedroski55 on 2012-11-26
pedro@pedro-bedro:~$ rfkill unblock all
pedro@pedro-bedro:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
pedro@pedro-bedro:~$

---

### Post by wildmanne39 on 2012-11-26
If the softblock changes to no please follow the directions in this link post 6, do everything there.
[http://ubuntuforums.org/showthread.php?p=12171877#post12171877](http://ubuntuforums.org/showthread.php?p=12171877#post12171877)
Thanks

---

### Post by wildmanne39 on 2012-11-26
Also we need to turn power management off:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
``` 
above exit0, then save gedit, close and reboot.
Thanks

---

### Post by Pedroski55 on 2012-11-26
To check it, I will have to unplug the dsl cable. That will take a minute, because when I do, the system will crash. It always does that. Fedora is at kernel 3.6. XX and has finally stopped doing that, but Ubuntu is always a bit later with the kernels. I reported this to Ubuntu bugs, along with a possible solution, but it ain't fixed yet.

I'll probably have to reboot in repair mode. Get back to you!

---

### Post by Pedroski55 on 2012-11-26
I followed your instructions, but I am unable to set the DNS server field. It is not active, I cannot write to it.

---

### Post by wildmanne39 on 2012-11-26
Hi, did you change the setting in the screenshot that my cursor is pointing too? Then you should be able to change the dns server.
Thanks

---

### Post by Pedroski55 on 2012-11-26
Ok, solved that, I didn't have the correct 'Automatic DHCP addresses only' above. Now I have everything. I will reboot, cross your fingers!

---

### Post by Pedroski55 on 2012-11-26
Sorry to say, that did not work. I am attaching a screenshot of the wifi connection info. I am sure I followed the instructions correctly.

It took a while rebooting. That happens when the dsl cable is unplugged!

Sorry again! It connected to the old wifi link, from the old router. I'll try again with the new one, sorry!!

---

### Post by wildmanne39 on 2012-11-26
Hi, post the contents of:
```
gksudo gedit /etc/pm/power.d/wireless
```
and
```
gksudo gedit /etc/modprobe.d/rtl8192ce.conf
```
attach screenshots of network manager settings like mine in this link [http://ubuntuforums.org/showthread.php?p=12171877#post12171877](http://ubuntuforums.org/showthread.php?p=12171877#post12171877)
Also remove the infotext file in your home folder and run the script again and attach the file so we can see the changes in your wireless.
Thanks

---

### Post by Pedroski55 on 2012-11-26
Still not working! Takes me a while to reboot after unplugging the dsl cable, I have to boot some other system to reset the graphics card, or Ubuntu cannot boot.
/etc/pm/power.d/wireless
#!/bin/sh

/sbin/iwconfig wlan0 power off

/etc/modprobe.d/rtl8192ce.conf
options rtl8192ce swenc=1

---

### Post by wildmanne39 on 2012-11-26
Hi, did you change your router settings from 802.11bgn to 802.11bg? if not it will not connect properly.

I also suggest that you take the dash out of your network name.

Can you change wpa to wpa2 in your router settings? it will help.

It shows connected but it is at 1mbs.

I recommend changing channels in the router the other network listed is on the same channel, in the US channel 11 and 1 or usually good to use.

If you do not know how to get into your router settings just ask.

Also did you set ipv6 to ignore in network manager?

You do know that as long as your wired connection is connected that it will override your wireless right?
Thanks

---

### Post by Pedroski55 on 2012-11-26
Thanks for your trouble.
Where should I set 802.11bgn to 802.11bg? In the netinfo.txt it says bgn:

Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)  

I set ipv6 to ignore.

I will have to wait until the girlfriend comes to check the router settings, but the last router would not allow an SSID other than ChinaNet-something The dash could not be excluded. This one isprobably the same, but it is all in Chinese, and my Chinese is not good enough.

Where do I change the channels?? In the router?? Abd the wpa to wpa2??

Yeah, I know that the wireless will be overridden. That's why to check takes a long time, because unplugging the dsl crashes the system!

---

### Post by wildmanne39 on 2012-11-26
Hi, I know it says bgn but that dirver does not support it well.

All the changes that you need to make are in the router.

You could always install the latest driver from the makers of your device as recommended by the other poster that also works most of the time, but you would have to recompile it every time there is an upgrade to the kernel. 
Thanks

---

### Post by Pedroski55 on 2012-11-26
Ok thanks. I'll let you know when I get into the router. Have to wait for my translator, and she has an exam today. 
I'd rather stay with the Ubuntu driver. One day it may just work. The system crashes are related to the atlc driver. That started in Fedora 16, and only recently stopped with the latest kernels. So the wifi may suddenly work after an update! There speaks the optimist!!

This link may interest you:

> Will I ever know what caused the problem?  Maybe this is what fixed it: [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=b94e52f62683dc0b00c6d1b58b80929a078c0fd5](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux.git;a=commitdiff;h=b94e52f62683dc0b00c6d1b58b80929a078c0fd5)

---

### Post by wildmanne39 on 2012-11-26
Hi, I have seen that issue before it is a hard one to solve, I personally only work with wireless.

---

### Post by Pedroski55 on 2012-11-27
I checked the router via 192.168.1.1

I can change the name ChinaNet-zbgJ so I took out the dash. The computer didn't like that, and Network Manager crashed. A restart did not bring the connection up.

There is no setting to tell it what driver to use in the router. I can set the SSID, password, some other stuff, numbers of connections and other stuff. I can change the useradmin password, but nothing about the driver anywhere.

Also, given the settings you recommended, I could not access the router, got a time out. I think that was because of the dns. Maybe I need another comma there and 192.168.1.4 or something I deleted the connection and used its default, then it came up.

Maybe I should download the firmware and try it. Can't get any worse!

---

