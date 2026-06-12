---
title: "Slow wireless lan speed with Ralink RT2500 chip (solved)"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by ausmuso on 2009-05-04
My Belkin 802.11g wireless lan card has a RaLink RT2500 chip. Intrepid correctly recognises this chip and gets a wireless link working. However, the speed negotiation protocol somehow goes wrong and the connection defaults to the lowest possible speed i.e. 1MB/s.
It is possible to set the speed much higher, eg. to 36MB/s manually by entering
[quote]
	sudo iwconfig wlan0 rate 36M
[unquote]
By the way, you have to have some patience with the wireless icon on the top bar because
it doesn't update quickly.

I reckon it is a pain always to have to enter this command manually so I looked for a way to do it automatically. I finished up embedding the command in one of the start-up script towards the end of the boot cycle.

The script I picked was /etc/init.d/anacron, which I kludged as follows:
[quote]

     (start of  anacron script)
	|
	|
	|
# Short-Description: Handle anac(h)ronistic cron
### END INIT INFO
# /etc/init.d/anacron: start anacron
#

PATH=/bin:/usr/bin:/sbin:/usr/sbin

# kludge to speed up wlan0
iwconfig wlan0 rate 36M
# end kludge

test -x /usr/sbin/anacron || exit 0

. /lib/lsb/init-functions

case "$1" in
  start)
	|
	|
      (etc)
[unquote]

Now wlan0 comes up perfectly at 36Mb/s every time.

Purists will be horrified at the though of hacking around in bootscripts like this . But hey, I reckon Linux
is there to serve me, not the other way round, and this kludge works fine for me.

---

### Post by Nphyx on 2009-05-15
thanks for this fix man, hopefully a more elegant solution exists. What about putting it in the networking boot scripts instead?

---

### Post by nAvde on 2009-06-22
Hi there,

I have another problem with my rt2500. I have slow download speed. I say download, because upload is not a problem. I use Ubuntu 9.04 server, rt2500pci, and I already tried the above mentioned fix. I can easily upload ~550 KB/s (which is as it should be), but download won't go more than ~180-190 KB/s (and with my notebook, Win XPSP3, I get 1MB/s).

Anyone any ideas?

---

### Post by dennisvanderpool on 2009-06-24
Thanks! :) I got exactly the same problem and solved it the same way as you supposed! Thank you for sharing! :D

---

### Post by GREZZO16 on 2009-07-08
> **nAvde said:**
> Hi there,

I have another problem with my rt2500. I have slow download speed. I say download, because upload is not a problem. I use Ubuntu 9.04 server, rt2500pci, and I already tried the above mentioned fix. I can easily upload ~550 KB/s (which is as it should be), but download won't go more than ~180-190 KB/s (and with my notebook, Win XPSP3, I get 1MB/s).

Anyone any ideas?


i have the same problem on an old desktop Philips freeline LS1000.
the "hack" to improve the connection speed is ok, but the download speed is a pain.

i've read some time ago on a blog that the drivers are limited but i cannot confirm.

byeee

---

### Post by demonon on 2009-07-11
Can someone explain to me what for script I place in which folder.
The description is kinda vague to me, but that's probably because I am a linux novice.

---

### Post by RavanH on 2009-07-12
Please have a look at my working solution on [http://ubuntuforums.org/showthread.php?p=7605785]("http://ubuntuforums.org/showthread.php?p=7605785") and let me know if you see/find any problems with it :)

It basically is a switch from Network Manager to Wicd, which allows for easy addition of a pre-connection script... No need for editing core files!

---

### Post by demonon on 2009-07-15
I just checked out that topic.
Still thanks for replying!

---

### Post by hhh on 2009-07-25
Thanks to the OP. I can't believe it, this worked for a Belkin F5D7070 Wireless USB adapter that works with the rt73usb driver in Jaunty. NetworkManager showed a connection speed of 54M but I could tell from [http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/) that I was getting only half of what the card could do on Windows. Setting the speed at 24M has it equal or better and shows another bar of signal strength. I was about to dump my Ubuntu partition. THANK YOU!

---

### Post by acutshall1 on 2009-08-14
# kludge to speed up wlan0
iwconfig wlan0 rate 36M
# end kludge

Tried entering the above and it stated I did not have permissions... I am the only person and the administrator on my computer,what gives?

---

### Post by acutshall1 on 2009-08-14
never mind I found the link on permissions; entered but it did not help still 1.52mbps

---

### Post by Mosaab on 2009-09-02
I did that but I still have a really slow lan connection !! I was trying to solve this issue for ages but no luck!

---

### Post by foxy123 on 2009-10-04
The solution in the first post helped me on Jaunty but on Karmic changing the rate has no effect on the actual speed but only on the reported speed in the NM connection information. Does anyone have the same issue in Karmic?

---

### Post by RavanH on 2009-10-05
@ Mosaab and foxy123,

Have you tried [http://ubuntuforums.org/showthread.php?p=7605785](http://ubuntuforums.org/showthread.php?p=7605785) ? I have not tested on Karmic but if you could please try and tell me if that DOES or also DOES NOT work on Karmic? 

Thanks :)

RavanH

---

### Post by foxy123 on 2009-10-15
> **RavanH said:**
> @ Mosaab and foxy123,

Have you tried [http://ubuntuforums.org/showthread.php?p=7605785](http://ubuntuforums.org/showthread.php?p=7605785) ? I have not tested on Karmic but if you could please try and tell me if that DOES or also DOES NOT work on Karmic? 

Thanks :)

RavanH
Hey RavanH, as I understand your solution is essentially about how to automate 'sudo iwconfig wlan0 rate 11M' command. Unfortunately this command does not do anything in Karmic.

---

### Post by foxy123 on 2009-10-17
interesting thing is that iwconfig shows that the speed is as it should:
```
~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"THEHILL"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:01:A1:0F:56   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

```

But it is actually 0.7Mb/s (see the image attached).

---

### Post by RavanH on 2009-10-19
> **foxy123 said:**
> Hey RavanH, as I understand your solution is essentially about how to automate 'sudo iwconfig wlan0 rate 11M' command. Unfortunately this command does not do anything in Karmic.

Yes, I understood that and am worried about it because I would like to upgrade to Karmic asap, except when this issue remains. 

The thing is that with Wicd you can specify the command to be executed *just before* or *just after* (if that might work better) the connection is set up. So I was wondering if somehow that would make a difference...

---

### Post by foxy123 on 2009-10-24
OK, it looks like a kernel bug [http://bugzilla.kernel.org/show_bug.cgi?id=13362](http://bugzilla.kernel.org/show_bug.cgi?id=13362) and it does not seem to be fixed despite of what is said here: [http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?p=33572#p33571](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?p=33572#p33571)

I tried ndiswrapper but it does not work with WPA security. However I have Zenwalk installed so I tried it there. While the rt2500 driver is as slow there as in Ubuntu, ndiswrapper works perfectly and I have the full speed. So I am seriously thinking about migrating to some other distro...

---

### Post by Pokerface17123 on 2009-12-14
I have the same issue in 9.10 Karmic. The iwconfig wlan0 rate 54M does  not solve the issue. Any updates on a fix?

---

### Post by foxy123 on 2009-12-16
I am not sure what has happened but I have currently a full speed with my rt2500pci driver. Has anyone else experienced any performance boost recently?

---

### Post by foxy123 on 2009-12-17
I had good speed for 2 days but it is back to 0.5Mb/s after router's reboot. I do not know what had actually happened.

---

### Post by RavanH on 2009-12-21
Got the same bizarre stuff happening since upgrading to Karmic. First after a clean (re-)install I was happy to see the card working full speed with Network Manager out of the box. No fixes or going to Wicd needed but after a while, the card seemed to start falling apart. Sudden drops in speed or even disconnecting and not seeing any signals anymore. Some days no problem, other days mostly off-line... VERY frustrating!

I decided to go for trusty old Wicd again, but the card behaves the same there too now :( I have the distinct feeling that Karmic+Network Manager+54M speed just pushed my RT2500 over the edge. Now it has become so erratic and behaves just broken, I am looking for an USB alternative...

This in combo with suspend/hibernate never having worked and now also battery management all screwed, I am tempted to go back to M$ Win... (sorry for cursing)

 - sigh -

---

### Post by foxy123 on 2009-12-22
I have found a sort of temporary solution. Low speed does not bother me when I just surf the Internet. However, if I need to download something big either from the Internet or my local network I use the Windows driver with ndiswrapper. The main problem with it is that it does not connect using WPA security. There is a walkaround for this, though not very efficient that's why I do not use it on a constant basis.

You may need to recompile ndiswrapper applying a patch, though some people claim it does not matter. You will find instruction **[COLOR="DarkOrange"][here]("http://ubuntuforums.org/showthread.php?p=8426311")[/COLOR]**. Then you have to issue the following command during ndiswrapper's attempt to connect: ```
sudo renice +19 $(pidof wpa_supplicant)
``` It usually takes me a several attempts to connect (thus the reason I do not use it as default setup). If if it works for you may put the command in /etc/rc.local before "exit" line.

What I usually do when I need a faster connection is do ```
sudo modprobe -r rt2500pci
``` in terminal, which removes temporarily rt2500 driver and ndiswrapper kicks in automatically.

---

### Post by sles on 2010-05-25
Just upgraded from 8.04 ( I used rt2500 driver in it, compiled it myself) to 10.04 and see very slow (less then 1 Mbit) wifi connection with rt2500pci. 
The same problem with 2.6.34 from ppa.
Unfortunately, I can't compile rt2500 with 2.6.32 and newer kernels, so I need a solution.
I tried to change speed with iwconfig, it helps, but only for several seconds.
And see many frame errors on wi-fi interface of wi-fi router.
Is there any way to get back my wi-fi connection? :-)

---

