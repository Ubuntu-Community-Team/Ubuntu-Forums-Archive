---
title: "Belkin F6D4050 v2 not working"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by BenAdamson on 2010-01-04
Hi, I recently started using Linux and want to use my Belkin F6D4050 v2 for wifi. I tried using NDISWrapper as it did not work "out of the box", but it still does not work. When I open NDISWrapper, I get an error box stating that it can't tell if the hardware is present. When I look at the driver through NDISWrapper, it is called rt2870. When I close the error box, it is listed as connected, but there is no flashing of the LED on the dongle. This is what I get from sudo lsusb:
```
Bus 001 Device 005: ID 050d:935b Belkin Components
```What should I do to get this device working?
Thanks,
Ben Adamson
EDIT: I am using a 32 bit system if it helps

---

### Post by th0mas on 2010-01-04
same here... I'm about to sell it if I can't get it working...

there seems to be some relevant information here :
[http://linux-wless.passys.nl/query_hostif.php?hostif=USB](http://linux-wless.passys.nl/query_hostif.php?hostif=USB)

"As of kernel 2.6.31, this device ID is not claimed by the rt2800usb or rt2870sta drivers."

I tried it on 2 laptops: one with jaunty + one with fresh karmic
I tried ndiswrapper with original .inf and other rt* modules
=> nothing appears when I type 'iwconfig'...

help ! :)

---

### Post by BenAdamson on 2010-01-04
Has anybody got any ideas?

---

### Post by BenAdamson on 2010-01-05
Shameless self bump

---

### Post by focwiz on 2010-01-05
> **BenAdamson said:**
> Shameless self bump
I can only assume you carefully went through each step in the ndiswrapper troubleshooting sticky at the top of this forum?

---

### Post by BenAdamson on 2010-01-07
> **focwiz said:**
> I can only assume you carefully went through each step in the ndiswrapper troubleshooting sticky at the top of this forum?
Sorry, but it is a bit too confusing and difficult for me.

---

### Post by wah fun on 2010-01-08
I also have this same problem! I have a post on this forum asking for help and giving my setup and output from several commands(search for Belkin N150 to find post). So far no one has responded with a valid suggestion. Does anyone from ubuntu ever see any of these posts? Since this problem seems to be common, surely someone who is technically proficient can solve this problem.

So much for the rant. I really like ubuntu but this wireless thing is frustrating. I would appreciate help also.

thx

---

### Post by BenAdamson on 2010-01-08
Has anyone in the community got any ideas?
Thanks,
Ben

---

### Post by Kevbert on 2010-01-08
Please take a look at [[COLOR="Red"]this[/COLOR]]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8564490"). 
Ndisgtk can be found on the Ubuntu install CD in the /pool/main/n/ndisgtk... directory. It can be installed by double-clicking on the ndisgtk...deb file (where ... is the version of ndisgtk). The installed program will appear under System-Administration and if my memory serves me correctly 'Windows drivers'.

---

### Post by BenAdamson on 2010-01-08
Thanks for the reply, but did you even read my post? [B]I have already used NDISWrapper.
[/B]Also, I already tried the instructions that you linked to, but they were for a different version of my adapter so didn't work.

---

### Post by apeterh on 2010-01-18
I've just managed to get my Belkin F6D4050 with the same ID (ID 050d:935b) working by following the tutorial here:

[Karmic: RALINK RT2870STA USB WiFi Tutorial]("http://ubuntuforums.org/showthread.php?t=1342593")

Only using the RT3070 drivers instead of the RT2870 ones (see my post in that thread for a couple more details).

---

### Post by wah fun on 2010-01-25
Well BenAdamson,

Looks like no one can help! Have you found any other resources?

thx

---

### Post by AmbrociousXP on 2010-02-12
I'm having the EXACT problems too and with the EXACT wireless Belkin model. I really hope there is a solution soon so I can stop using Windows and jump into Ubuntu as quickly as I can...there's a Microsoft storm coming...don't want to be in it when it arrives.

---

### Post by wah fun on 2010-04-29
> **BenAdamson said:**
> Thanks for the reply, but did you even read my post? [B]I have already used NDISWrapper.
[/B]Also, I already tried the instructions that you linked to, but they were for a different version of my adapter so didn't work.

Ben,
After some time, I am back at trying to get this working in ubuntu 9.10. I have tried numerous so-called fixes that I am beginning to wonder if it can be fixed. So, I thought I would check to see if you were still trying or had found a fix. If you have, would you post it? It appears that many users encounter this same problem.

thx,
wah fun

---

### Post by BenAdamson on 2010-04-29
Hi, I haven't found a fix for it yet, so keep looking!
I'm still wondering if it's possible. :(

---

### Post by BenAdamson on 2010-05-03
bump?

---

### Post by BenAdamson on 2010-05-09
Somebody must know..... :( :confused:
I've been trying for a while now.

---

### Post by viulian on 2010-05-15
I've got it running!

The latest drivers from Ralink (namely: DPO_RT3070_LinuxSTA_V2.3.0.2_20100412) are not perfect.

I've applied the hints of waterhead from here: [http://www.linuxforums.org/forum/wireless-internet/159738-ubuntu-9-10-wusb100v2-solved-2.html#post767134](http://www.linuxforums.org/forum/wireless-internet/159738-ubuntu-9-10-wusb100v2-solved-2.html#post767134) (as well as the one next after).

Here are the detailed steps:

a) rename existing kernel module:

```
/lib/modules/`uname -r`/kernel/drivers/staging/rt3070/rt3070sta.ko
```

to

```
/lib/modules/`uname -r`/kernel/drivers/staging/rt3070/rt3070sta.ko.disabled
```

Then, run depmod just to be sure.

b) unpack the RT3070 driver into /usr/local/src and go inside the folder.

Rename

```
RT2870STA.dat
RT2870STACard.dat
```

to

```
RT3070STA.dat
RT3070STACard.dat
```

c) update the file common/rtusb_dev_id.c and add at the end of the device ids the following line:

```
        {USB_DEVICE(0x050D,0x935B)}, /* Belkin F6D4050 v2 */
```

d) edit the file os/linux/usb_main_dev.c and after the line:

```
MODULE_DESCRIPTION("RT2870 Wireless Lan Linux Driver");
```

add this one:

```
MODULE_LICENSE("GPL");
```

so that you get:

```
MODULE_DESCRIPTION("RT2870 Wireless Lan Linux Driver");
MODULE_LICENSE("GPL");
```

e) 

make 
make install
modprobe rt3070sta

The moment I inserted the new module, everything started to work (I didn't have to restart Network Manager).

---

### Post by BenAdamson on 2010-05-15
Thanks for the guide, but I'm really new to linux. Could you say the exact things I need to do (exact commands etc) please?
Thanks,
Ben :)

---

### Post by wah fun on 2010-05-20
viulian - thx for your reply. I tried your solution several times but it did not work for me. I am wondering why you chose the 3070 driver because Ralink advised me that the F6D4050 v2 uses the 2870 driver? 

Ben - FYI... It isn't the best solution, but I have ubuntu 10.04 (32 bit) running as a guest OS in virtualbox (I am using virtualbox 3.1.8 for windows) on a windows xp host. It works like a charm with full support for wireless. However, I am not sure whether the pc is still as secure using linux this way as it would be installing linux to its own partition. I am researching this now.  But, running ubuntu this way at least gives me a better feel for it.

And, as users like viulian, keep coming up with ways that work for them, maybe one of the techniques will work for us as well.
Keep searching.

---

### Post by viulian on 2010-05-20
wah fun - yeah, I also tried that first time - managed to successfully compile it, renamed existing modules - but somehow, on modprobe, the ra0 (this is how it appears to me, the wireless interface), failed to show up.

While searching around, I found some reports that a guy reported success for the first version F6D4050 (not v2 like ours) using driver 3070. Since I didn't have anything else to try - I said why not.

Is true that the vendor id of Belkin internal chip  (0x050D) is present in the 2870 driver, and nothing with 0x050D is found on the newer driver. However, I just went ahead and put in the USB_DEVICE line, and bingo. It started to work.

I than had to modify the network configuration file so the card would authenticate at boot and not on X session start.

Later edit:
wah fun - did you remove all modules from the /lib/modules related to ra2870 and 3070 ? Maybe somehow the existing ones are loading first. Maybe I did not mention - I'm running Ubuntu 9.10.

---

### Post by stoner_di on 2010-05-22
Thanks for this method. But it does not work for me. Once installed, Network manager shows that the wireless network is no active and in no way can it turn on.
Plese help my for this problem.
I have system Ubuntu 10.04 amd64.

---

### Post by wah fun on 2010-05-24
viulian,

Are you using 32 bit or 64 bit? I might try to dl 9.10 and give it a try. Oh, and yes, I did remove all the references to rt2870 and rt3070 from the /lib/modules.

thx

---

### Post by Anonymous Citizen on 2010-05-24
Why would you guys need to remove reference to the drivers in /lib/modules? My problem is [here]("http://ubuntuforums.org/showthread.php?t=1491797") and I'm returning an error that says my drivers are not 64-bit. After each installation of a driver do you need to delete the files in /lib/modules if it doesn't work?

---

### Post by viulian on 2010-05-24
wah fun: I'm running 32bit version of Ubuntu 9.10.

Anonymous Citizen: the kernel checks /lib/modules/... and it loads anything from there that matches the devices that it finds. I don't really know the internals, but each module from /lib/modules/... reports what device id / vendor id it supports (let's say about hardware modules) and if so, and if the module is not blacklisted, the kernel loads it. So, if you need to compile a different module (with a different name - or located in a different place in /lib/modules/... hierarchy), then you might find that the kernel loads the one that you don't want.
I also checked your thread, but to me it seems that you might go to Belkin website and download the 64bit driver version for Windows, and continue from there. I have no experience with ndiswrapper ...

---

### Post by wah fun on 2010-06-07
viulian,

I dl'd 9.10 32 bit and gave it a try. Alas, no success. I tried the 3070 driver following your guide and lsusb shows the Belkin usb is connected and recognized. lsmod shows the driver to be installed. However, I get no light on the usb indicating connectivity and obviously cannot connect to the wireless network.

But I appreciate users like yourself who know enough to try different things so that the rest of us can follow and enjoy success. Keep up the good work.

It is difficult to believe however that as many Belkin usb users as there are that someone hasn't figured out the problem.

I will continue to search for a solution. I do like ubuntu and use it for wired connections. 

thx for you suggestions.

---

### Post by viulian on 2010-06-08
wah fun, I would like to see some of your log messages, outputs, and what other steps you may have done. Just saying "it doesn't work, but thanks for tutorial" - it doesn't help...
For example you did not say anything about configuring the network interfaces, etc. What is your /etc/network/interfaces ?
If you list your files, somebody might notice something not properly done.

Things that I'd like to see:
a) a list of modules that you have in /lib/modules/.. related to rt2870 and rt3070
b) the output of iwconfig
c) the output of ifconfig

Below you will find a list of files on my Ubuntu, so that you can compare to your setup:

Here's my output of lsmod:

```
root@dev:~# lsmod | grep rt3070sta
rt3070sta             568784  1
```

I've also added it to /etc/modules to be loaded at runtime (just one line, with the module name).

Here's Belkin in lsusb:

```
Bus 002 Device 002: ID 050d:935b Belkin Components
```

Second:

a) make sure you have the files /etc/Wireless/RT2870STA/RT2870STA.dat (801 bytes) and /etc/Wireless/RT3070STA/RT3070STA.dat (1098 bytes).
b) make sure that you have configured it in your /etc/network/interfaces

```
auto ra0
iface ra0 inet dhcp
wpa-driver wext
wpa-ssid <ESSID here>
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <big number here>
```

c) make sure that in the /lib/modules you removed all ra2870sta/ra3070sta that the kernel may have. Reboot to make sure.

Here's what I have:

```
./2.6.31-21-generic/kernel/drivers/net/wireless/rt3070sta.ko
./2.6.31-21-generic/kernel/drivers/staging/rt2870
./2.6.31-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko.disabled
./2.6.31-21-generic/kernel/drivers/staging/rt3070
./2.6.31-21-generic/kernel/drivers/staging/rt3070/rt3070sta.ko.disabled

```

As you can see, the Ralink driver is installed in net/wireless and not in staging.

Here's my iwconfig:

```
ra0       Ralink STA  ESSID:<ESSID here>  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:1D:7E:4A:FC:FE
          Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:<Encryption key here>
          Link Quality=100/100  Signal level:-67 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

The nickname appears to be of 2870, however, this value is found in the 3070 source code, so it's the 3070 driver anyway (as the module name is correctly generated).

One thing that I did is first tried to compile the version 2870 (which I think also put the /etc/Wireless/RT2870STA folder there). I don't know if this folder is read by the rt3070sta driver, but I just have it there. I cannot remove it now and try it out, because I'm not at home anymore and if I break something - nobody can fix :)

---

### Post by happylinuxguy on 2010-07-31
Here's a solution that worked perfectly for me..........
Ubuntu 10.04 Lucid Lynx 64 bit
```

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "050d 935b" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig

```If you see that your card is working now, you need to make it load at boot time or when you plug the card in.  

```

sudo gedit /etc/udev/rules.d/f6d4050v2.rules

```Contents of rules file....
```

# UDEV-Rule for f6d4050v2 ID 050d:935b
SUBSYSTEM=="usb", SYSFS{idVendor}=="050d", SYSFS{idProduct}=="935b", RUN+="/sbin/modprobe rt2870sta"

```Restart udev so it will load your module.  (or reboot if you prefer)

```

sudo service udev reload

```I modified instructions from this article to work for this specific Belkin NIC.
[http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6)

---

### Post by wah fun on 2010-09-05
Hey all of you that still do not have this usb adapter working. After trying numerous "fixes" with no success, I just gave up. But, really liking the linux concept, I came back after several weeks to give it another go. As I had removed ubuntu from my test machine, I decided to dl the beta version of 10.10 just for grins. Much to my surprise, my Belkin F6D4050v2 N150 wireless usb network adapter worked out of the box! Joy, joy, joy.

Now, the next giant hurdle. The usb adapter IS working fine but the connect speed is only 54 mbps (802.11g speed) not the 130-150 mbps I get in windows. Just getting started, but so far, I have edited the rt2870sta.dat file found in /etc/Wireless/RT2870STA (which I had to create and not even sure if the new system uses it but I found this edit in the forum and thought I would give it a try) to change the wirelessmode= from 5 to 6 (the 6 is supposed to force 802.11n speed)- still only get the 54 mbps.

Now, if anyone knows how to get the Belkin usb adapter to connect at higher speeds, I would appreciate it. I too will keep searching and trying.

Anyway, you might want to give the new ubuntu a try, or if you are adventuresome, try to update just the kernel to the new 2.6.35.

---

### Post by themusicalduck on 2010-09-06
> **wah fun said:**
> 
Anyway, you might want to give the new ubuntu a try, or if you are adventuresome, try to update just the kernel to the new 2.6.35.

Did you do anything else at all to get it to work? I have the same dongle (actually, the version 1 I think) and it still does not do anything in Maverick for me.

I've also gone through nearly every 'fix' I could find on Google and nothing has worked.

Only bought it today, so might try and take it back tomorrow if I still don't get anywhere. Hopefully they will take it back off me.

---

### Post by wah fun on 2010-09-06
musicalduck,

Actually no I didn't have to do anything. It worked when I booted after doing the install. No blacklisting, nothing. Since the native driver in ubuntu is working for me, I haven't tried compiling the rt2870 driver from Ralink. It might give better speeds and it might work with your setup. You can google rt2870 for linux and dl the current version which is 2.4 I believe.

It has been a heck of a ride trying to get this usb to work so I am not sure what to suggest. It really seems to be a hit and miss proposition with linux. But I think the value of linux is worth the effort.

Good luck!

---

### Post by wah fun on 2010-09-09
Ben, et. al,

After the Belkin usb worked in 10.10, I was cleaning out my file folder regarding this matter and was reading everything to see if I wanted to save anything since this has been such a laborious effort. I viewed a file that I had named incorrectly (my naming convention)and could not remember ever using it so I saved it. Well, out of curiosity and never one to just give up on anything, I installed ubuntu 9.10 and used the file - to my surprise it worked! I installed ubuntu 10.04 and used the file - it worked! I installed Mepis 8.5 and used the file - it worked! I installed debian 5 and used the file - it worked!

So, I can't say this is 'the' solution but it does seem to work. Give it a try, it might work for you. One note: do your install without the usb inserted then apply the solution.

Here it is: (I am sorry I can't give credit to the individual who discovered this, so if you are that person and you recognize your work, Thank You!)
_____________________________________________________________
A little Trick to add the ID 050d:935b for the Belkin F6D4050 v.2000 to the System and
simply (and hopefully) use the rt2870sta that comes with the system (staging), if the new driver v2.3.0.0 from Ralink don't work properly.

First remove the new compiled driver if necessary:

cd
cd RT2870_LinuxSTA_V2.3.0.0
su
make uninstall

(or -if you used the make//checkinstall routine- : use synaptic to remove+purge the 'rt2870' .deb)


If you previously did not manually compile the driver from Ralink start here.

Add the ID:

su
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "050d 935b" > /sys/bus/usb/drivers/rt2870/new_id' | tee /etc/modprobe.d/rt2870sta.conf
modprobe -rf rt2870sta
modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig


The solution works? Ok, load the driver at startup
su
echo rt2870sta | tee -a /etc/modules
_____________________________________________________________

Good luck

---

### Post by gordonreid1992 on 2010-09-09
> **happylinuxguy said:**
> Here's a solution that worked perfectly for me..........
Ubuntu 10.04 Lucid Lynx 64 bit
```

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "050d 935b" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig

```If you see that your card is working now, you need to make it load at boot time or when you plug the card in.  

```

sudo gedit /etc/udev/rules.d/f6d4050v2.rules

```Contents of rules file....
```

# UDEV-Rule for f6d4050v2 ID 050d:935b
SUBSYSTEM=="usb", SYSFS{idVendor}=="050d", SYSFS{idProduct}=="935b", RUN+="/sbin/modprobe rt2870sta"

```Restart udev so it will load your module.  (or reboot if you prefer)

```

sudo service udev reload

```I modified instructions from this article to work for this specific Belkin NIC.
[http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6)

i've done all of that, if the router is WPA encrypted then connection is impossible, it just keeps asking for the key, if i make it an unsecured connection then all is well. any ideas?
i heard that the card apparently works in 10.10, work a shot of doing a dist-upgrade when the network is unsecured?

---

### Post by oregonsownjollyjimbo on 2010-09-25
Yeah! The solution given by happylinuxguy for Ubuntu 64-Bit also worked for 32-Bit. I'm a total Linux noob, so please don't laugh at me if there is no difference in using this with 32-Bit or 64-Bit. Thanks happylinuxguy!

:guitar:

---

### Post by oregonsownjollyjimbo on 2010-09-25
Also... try entering the WEP key. I use a secured internet connection and the above solution worked just dandy.

---

### Post by gordonreid1992 on 2010-09-26
10.10 fully supports this card out the box.

---

