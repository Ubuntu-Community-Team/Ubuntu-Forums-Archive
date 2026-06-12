---
title: "broadcom wireless problems"
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by Bytewalker on 2006-06-23
Okay i cant get the wireless working and im totally stmped now, i went through the entire procedure at [https://help.ubuntu.com/community/Wi...29%7C%28AND%29](https://help.ubuntu.com/community/Wi...29%7C%28AND%29)

so this is what ive done so far:

apt-get installd ndiswrapper, ndis-utils and ndisgtk

lspci -n shows the broadcom as 14e4:4320, corresponding to bcmwl5a.inf as the correct file to get (i got bcmwl5 too though)

downloaded the then extratd .inf/.sys files

so i did
ndiswrapper -i on the .inf files
then
ndiswrapper -l shows bcmwl5a as driver present, hardware present
then i do
ndiswrapper -d 14e4:4320 bcmwl5a

modprobe ndiswrapper

then "ifup wlan0" brings up this crazy error (i even ifdown'd eth0 before trying this):
>SIOCSIFADDR: No such device
>Bind socket to interface: No such device
>Failed to bring up wlan0.

the ONE thing i think it might be that some1 else mentioned is a conflict with anotehr device (one that doesnt work) thats stopping ndis from being used.. but i cant find anything on how to find this device or disable..

any thoughts greatly appreciated thanks in advance!!!

---

### Post by debrocks on 2006-06-23
Had the same problem. I do know that the bcmwl5 driver works, 5a may work also.
My fix: 
<code>
do lsmod |grep bcm
</code>

this should tell you that a bcm43xx is already there:this driver is installed by default and DOES NOT WORK.

<code>
rmmod bcm43xx
</code>

then navigate to /etc/modprobe.d

edit blacklist file, and add bcm43xx to the bottom of the file

Reboot. 

Go to your network management, and you should see that card, and it should be enabled. Configure it and enjoy.

Best of lucks!

---

### Post by enfield on 2006-06-23
Thumbs up!!  The last post cured my problem with my Dell Inspiron 5150!  :KS

---

### Post by skelooth on 2006-06-23
i get better stability using the native linux driver and the firmware cut from the windows driver personally.

---

### Post by digimars on 2006-06-23
This for some reason does not work for me:

```

kenny@laptop:~$ do lsmod | grep bcm
bash: syntax error near unexpected token `do'
kenny@laptop:~$ sudo do lsmod | grep bcm
sudo: do: command not found
kenny@laptop:~$ lsmod | grep bcm
bcm43xx               138892  0
ieee80211softmac       32384  1 bcm43xx
ieee80211              40072  2 bcm43xx,ieee80211softmac
kenny@laptop:~$ rmmod bcm34xx
ERROR: Module bcm34xx does not exist in /proc/modules
kenny@laptop:~$ sudo gedit /etc/modprobe.d
kenny@laptop:~$

```

I've edited the /etc/modrobe.d/blacklist file, and when I rebooted my computer my wireless light came on.  And when I check my network manager it shows that the wlan0 interface is active.  However, I can not get a connection with it.  And I know that it should work because we have a router that is unsecured and provides IP's via DHCP.

```

kenny@laptop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

```

---

### Post by skelooth on 2006-06-23
did you try

sudo modprobe ndiswrapper
sudo ifconfig eth1 down
sudo ifconfig eth1 up
sudo iwconfig eth1 mode auto
sudo iwconfig eth1 essid mynetwork
sudo dhclient eth1

replacing eth1 with your card and mynetwork w/ ur wireless network name... or you could scan for networks. For some reason what i posted I above will randomly work....

Dude wireless is so touch and go on ubuntu it drives me nuts :P and once you get it working you never know when it will randomly go down....

---

### Post by digimars on 2006-06-23
Ugh, this is driving me crazy...

Well, the inteface wlan0 is now active.

I did 'sudo iwconfig wlan0 essid any' and picked up the correct ESSID.  Then I did 'sudo dhclient wlan0' and it says that I got an IP from the default gateway of 192.168.1.1, which is correct.  But pinging that IP brings back nothing, so I'm still not getting a connection somehow.  I have Ethereal installed, and trying to capture any kind of packets on that interface comes up empty.  How do I scan for networks?  Is there a terminal command for that?

Any other suggestions?  Why is Ubuntu so shoddy with this?  Is it the particular kernels they use?

---

### Post by skelooth on 2006-06-23
i think wireless on linux in general is still very shoddy :(

anyway

iwlist wlan0 scan

that will scan for networks

---

