---
title: "Solution for Ubuntu 12.04 and realtek N8101 NIC wired network not working"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by stargazer30 on 2012-04-23
Hi All,

I'm new so appologies if this is the wrong forum.  I wanted to share a solution for this issue as I've been searching for days to fix it.

So problem.

ubuntu 12.04 and its kernel 3.2.0-23 is not compatible with the RTL8101E/RTL8102E PCI Express Fast Ethernet controller

When booting from the live CD wired connection fails, even after the MAC is set (its blank by default)

The issue is with the default module r8169.ko used by the kernel, it needs to be blacklisted.  

sudo gedit /etc/modprobe.d/blacklist-network
then add a line to the file
r8169.ko
and save

Solution
The correct driver/module is on the realtek site called r8101, but the source code won't compile on the new kernel.  

I found this link which has the source and patch which can be applied to it to allow it to compile on the new kernel and produce the r8101.ko file.
[https://build.opensuse.org/package/files?package=r8101&project=home%3AAkoellh%3AKernelmodules]("https://build.opensuse.org/package/files?package=r8101&project=home%3AAkoellh%3AKernelmodules")

Once the r8101.ko file is made the script fails to install it so next copy it to;
/lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/ethernet/realtek/

Then I installed it using these commands
sudo depmod -a
sudo modprobe r8101

The last step is to fix the missing MAC address and restart network manager using these commands, you can use any MAC you like, don't have to use 00:28:C7:0A:42:A2

sudo service network-manager stop
sudo ifconfig eth0 down 
sudo ifconfig eth0 hw ether 00:28:C7:0A:42:A2
sudo ifconfig eth0 up
sudo service network-manager start

Then plug in the network cable and away we go :-)

David

---

### Post by stargazer30 on 2012-04-23
Just tried rebooting and the new module loads at start up but I loose the MAC address so every reboot I need to run..

sudo ifconfig eth0 down 
sudo ifconfig eth0 hw ether 00:28:C7:0A:42:A2
sudo ifconfig eth0 up

Anyone know how to set the mac during boot to avoid this?

---

### Post by KomodoDave on 2012-08-27
stargazer30, you're my personal hero! Your solution fixed my wireless on Toshiba Satellite A660-18N which had spontaneously broken after a seemingly harmless update relating to network security packages on Ubuntu 12.04. Until this point it had been working without issue.

I've spent hours searching for a solution, if you hadn't posted I don't know where I'd be right now. Thank you so much, I'm seriously grateful that you shared this solution!

For you - I believe this post may help your MAC address issue, though I suspect you've solved it by now:

[http://ubuntuforums.org/showthread.php?t=1724802](http://ubuntuforums.org/showthread.php?t=1724802)

For others - here's a concise outline of the steps you need; the blacklist line stargazer mentions is slightly incorrect, and some of the manual steps he specifies are unnecessary if you run commands as sudo (or at least they were in my case).

* Note that in my particular case this made my wireless connection reappear in the network dropdown in taskbar, but after rebooting below I had to press the keyboard shortcut to reenable wireless adapter, which had been disabled by the original issue. I had  MAC address issue like that reported by OP.*

**Ubuntu 12.04:  RTL8101E/RTL8102E Realtek Fix**:

Download the attached file to ~/Downloads

Then;

```
sudo gedit  /etc/modprobe.d/blacklist.conf
```Add line:

```
blacklist r8169
```Save and close, then run:

```
sudo update-initramfs -u && cd ~/Downloads && tar xvf r8101-1.022.00.tar.bz2 && cd r8101-1.022.00 && sudo sh autorun.sh
```After completion of this command, reboot and you're good to go!

Happy days :D

---

### Post by chili555 on 2012-08-27
> sudo gedit  /etc/modprobe.d/blacklist-networkThis is poor practice. In a future release of Ubuntu,the file will be removed if it doesn't end in .conf. The second best solution is to rename it:```
sudo mv /etc/modprobe.d/blacklist-network /etc/modprobe.d/blacklist-network*.conf*
```The best solution is to simply add your blacklist to the proper file, /etc/modprobe.d/blacklist.conf at the end.

---

### Post by KomodoDave on 2012-08-27
> **chili555 said:**
> This is poor practice. In a future release of Ubuntu,the file will be removed if it doesn't end in .conf. The second best solution is to rename it:```
sudo mv /etc/modprobe.d/blacklist-network /etc/modprobe.d/blacklist-network*.conf*
```The best solution is to simply add your blacklist to the proper file, /etc/modprobe.d/blacklist.conf at the end.

Thanks for the info chili555, will modify my post and change my own file now.

---

### Post by chili555 on 2012-08-27
> will modify my post and change my own file now.Looks perfect!

---

### Post by naskolux on 2012-08-29
Hi,
I followed the instructions and my (wireless) network card works now. However, when I restart my computer it takes a long time to boot because it waits (cannot find) network configuration. In order to get my card going I have to run every time I turn on my computer:
sudo service network-manager start
How could I make my network card work automatically at startup?

---

### Post by chili555 on 2012-08-29
> **naskolux said:**
> Hi,
I followed the instructions and my (wireless) network card works now. However, when I restart my computer it takes a long time to boot because it waits (cannot find) network configuration. In order to get my card going I have to run every time I turn on my computer:
sudo service network-manager start
How could I make my network card work automatically at startup?Please start your own new thread. This involves wired ethernet, not wireless.

---

### Post by ivikas on 2012-10-22
> **naskolux said:**
> Hi,
I followed the instructions and my (wireless) network card works now. However, when I restart my computer it takes a long time to boot because it waits (cannot find) network configuration. In order to get my card going I have to run every time I turn on my computer:
sudo service network-manager start
How could I make my network card work automatically at startup?

Try adding your command to end of file either  .bash_profile or .bashrc and it will take up on system boot.These files should be in your home directory.

if bash_profile or .bashrc is not in home directory copy them from /etc/skel

---

### Post by acoluthus on 2012-11-03
Hi-
noob here.
I'm trying a few of these but don't quite understand the instructions
--------------
chili555 	
Re: Solution for Ubuntu 12.04 and realtek N8101 NIC wired network not working
Quote:
sudo gedit /etc/modprobe.d/blacklist-network
This is poor practice. In a future release of Ubuntu,the file will be removed if it doesn't end in .conf. The second best solution is to rename it:
Code:

sudo mv /etc/modprobe.d/blacklist-network /etc/modprobe.d/blacklist-network.conf

**The best solution is to simply add your blacklist _to the proper file,_ /etc/modprobe.d/blacklist.conf at the end. **
--------------------

-How do I determine "the proper file"?
-Is this "sudo mv /etc..blacklist..." all I have to run,to fix it?
also: in another part of this thread, it recommends a download. how do you download when the network is off? 

Is there a 'best' option for this same issue (that I may've not found yet?)

Thanks-

---

### Post by chili555 on 2012-11-03
> in another part of this thread, it recommends a download. how do you download when the network is off?You'll need to download the file to another computer and transfer it on a USB stick or similar. In order to compile the package, you will also need linux-headers-generic and build-essential and their dependencies. The exact details depend on your Ubuntu version and architecture; i.e. 32- or 64-bit. Please run and post:```
lsb_release -d
arch
```> -How do I determine "the proper file"?It was told to you just above:> The best solution is to simply add your blacklist to the proper file, [COLOR="Red"]/etc/modprobe.d/blacklist.conf[/COLOR] at the end. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```At the end, add one new line:```
blacklist r8169
```Proofread, save and close gedit. That's all you need to do in regard to blacklists.You can now safely skip the parts about /etc/modprobe.d/blacklist-network.

Post the details and we'll proceed.

---

### Post by acoluthus on 2012-11-04
Thanks for your response and info/support in the process---

I ran
**lsb_release -d** and got: _Ubuntu 12.04.1 LTS_
**arch**  and got: _x86_64_

I downloaded the **r8181-1.022.00.tar.bz2**, transferred by USB to the Linux CPU, and extracted. 

Then I ran:**sudo gedit /etc/modprobe.d/blacklist.conf** but after hitting "enter" it opened a text box with a list of blacklisted items/replaced by.. but didn't know where to enter the 2nd line(couldn't do it in Terminal while the text box was open)

Then I tried entering **blacklist 8169** in the text box and "save", and closing the box, but got the following message in Terminal:_(gedit:3275): Gtk-CRITICAL **: gtk_tree_selection_get_selected:  assertion `GTK_IS_TREE_SELECTION(selection) ` failed_

`hope I didn't screw anything up..(I -really- don't know the command language in -any- capacity/ apologies--)  ((I think i did get the instructions confused))/sorry...

I appreciate your follow up and guidance, and will watch for your reply-  AC.

---

### Post by chili555 on 2012-11-04
>  [COLOR="Red"]r8181[/COLOR]-1.022.00.tar.bz2Are you sure that's the package you downloaded? Is it r8101 instead?

Let's check your blacklist:```
cat /etc/modprobe.d/blacklist.conf
```Is the last line:```
blacklist [COLOR="Red"]r[/COLOR]8169
```If so, you are good to go! If not; if it is instead 'blacklist 8169' then you will need to re-do your work:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Proofread carefully before you save and close gedit.> (gedit:3275): Gtk-CRITICAL **: gtk_tree_selection_get_selected: assertion `GTK_IS_TREE_SELECTION(selection) ` failedA normal and harmless warning.

In order to compile this, you will need build-essential and linux-headers-generic _and their dependencies_. Before we break our backs with this big task, let's check to be sure which device you have. Please run and post:```
lspci -nn | grep 0200
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by acoluthus on 2012-11-04
Hi! 

1) yes, the package downloaded -is- **r8101**-1.022.00.tar.bz2

2) the last line under the blacklist search is: **blacklist r8169**

3) **lspci -nn | grep 0200** ran, results:
_01:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [llab:4362] (rev 19)_

----question for later: should I continue with the "Quetzal"upgrade after this, and/or would running that upgrade off a cdr a)re-screw this network connectivity issue or b) resolve it? < just curious..--

continued gratefulness--/AC.

---

### Post by chili555 on 2012-11-04
> 11ab:4362That's not a Realtek r8169 device; it's a Marvell sky2 device. What's not working about your wired ethernet? Since it doesn't fit this thread, please start your own new thread and tell the doctor all about it.> $ modinfo [COLOR="Red"]sky2[/COLOR] 
filename:       /lib/modules/3.5.0-17-generic/kernel/drivers/net/ethernet/marvell/sky2.ko
version:        1.30
license:        GPL
author:         Stephen Hemminger <shemminger@linux-foundation.org>
description:    Marvell Yukon 2 Gigabit Ethernet driver
srcversion:     0311E817050256BFC5B9ACF
<snip>
alias:          pci:v0000[COLOR="Red"]11AB[/COLOR]d0000[COLOR="Red"]4362[/COLOR]sv*sd*bc*sc*i*


---

### Post by acoluthus on 2012-11-04
Chilli555:
thanks... I was going off the original thread/issue of the same error message at the top  of the original post. I don't know the 'guts' of hardware or software if it was 'realtek' or not..
I deeply apologize if this has been mis-posted, I just didn't know any different, but was going off the "solved" end of the same original error message.
Thank you -very-much for your time on this; I'll start a new thread as recommended-

---

### Post by chili555 on 2012-11-04
No apology is needed. We were all new at one time, even me! I'll look forward to your post.

---

### Post by jaber426 on 2013-03-03
thank

---

### Post by hey1234 on 2013-05-24
@komdodev
i ran these commands as you have mentioned but my system got stuck(hanged) after sometime.What should i do??

---

### Post by lazy1990 on 2013-06-04
add all those three commands in /etc/rc.local then all those will be run when ubuntu is loading

---

### Post by it.helpdesk.getech on 2013-08-19
Just wanted to say thank you for the HP G61 Netcard Fix. I am on line. This is also the reason why I love Ubuntu because of people like yourselves. This is what make the Forum Great.

---

### Post by Nicholas_Stafford on 2013-10-07
The link no longer works. what is the new one?

---

### Post by chili555 on 2013-10-07
> **Nicholas_Stafford said:**
> The link no longer works. what is the new one?The attachment in post #3 works and a slightly newer version is here: [http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PFid=7&Level=5&Conn=4&DownTypeID=3](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PFid=7&Level=5&Conn=4&DownTypeID=3)

---

### Post by ttinoo on 2013-12-10
Sorry, didn't know where to post this. Wifi can't find any networks, wired connection works normally. It's my first Linux ever, Ubuntu 12.04. I have been using it for two days now. Never used wifi with Windows, so I dont know if the controller is broken or something.

I tried post #3 solution, and got this:

```
Check old driver and unload it.
Build the module and install
/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.c:5396:1: virhe: expected &#8221;=&#8221;, &#8221;,&#8221;, &#8221;;&#8221;, &#8221;asm&#8221; or &#8221;__attribute__&#8221; before &#8221;rtl8101_init_board&#8221;
/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.c:5799:1: virhe: expected &#8221;=&#8221;, &#8221;,&#8221;, &#8221;;&#8221;, &#8221;asm&#8221; or &#8221;__attribute__&#8221; before &#8221;rtl8101_init_one&#8221;
/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.c:5926:1: virhe: expected &#8221;=&#8221;, &#8221;,&#8221;, &#8221;;&#8221;, &#8221;asm&#8221; or &#8221;__attribute__&#8221; before &#8221;rtl8101_remove_one&#8221;
/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.c:7851:12: virhe: &#8221;rtl8101_init_one&#8221; esittelemättä täällä (ei funktiossa)
/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.c:7852:2: virhe: funktio &#8221;__devexit_p&#8221; esitelty implisiittisesti [-Werror=implicit-function-declaration]
/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.c:7852:25: virhe: &#8221;rtl8101_remove_one&#8221; esittelemättä täällä (ei funktiossa)
/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.c:7488:12: varoitus: &#8221;rtl8101_poll&#8221; defined but not used [-Wunused-function]
/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.c:869:1: varoitus: &#8221;rtl8101_xmii_reset_pending&#8221; defined but not used [-Wunused-function]
/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.c:885:1: varoitus: &#8221;rtl8101_xmii_link_ok&#8221; defined but not used [-Wunused-function]
/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.c:894:1: varoitus: &#8221;rtl8101_xmii_reset_enable&#8221; defined but not used [-Wunused-function]
/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.c:1117:1: varoitus: &#8221;rtl8101_link_option&#8221; defined but not used [-Wunused-function]
/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.c:1239:1: varoitus: &#8221;rtl8101_set_speed_xmii&#8221; defined but not used [-Wunused-function]
/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.c:1565:1: varoitus: &#8221;rtl8101_gset_xmii&#8221; defined but not used [-Wunused-function]
/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.c:1776:27: varoitus: &#8221;rtl8101_ethtool_ops&#8221; defined but not used [-Wunused-variable]
/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.c:1811:13: varoitus: &#8221;rtl8101_get_mac_version&#8221; defined but not used [-Wunused-function]
/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.c:1879:1: varoitus: &#8221;rtl8101_print_mac_version&#8221; defined but not used [-Wunused-function]
/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.c:4584:1: varoitus: &#8221;rtl8101_release_board&#8221; defined but not used [-Wunused-function]
/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.c:5729:1: varoitus: &#8221;rtl8101_check_eeprom&#8221; defined but not used [-Wunused-function]
cc1: some warnings being treated as errors
make[3]: *** [/home/tino/Lataukset/r8101-1.022.00/src/r8101_n.o] Virhe 1
make[2]: *** [_module_/home/tino/Lataukset/r8101-1.022.00/src] Virhe 2
make[1]: *** [modules] Virhe 2
make: *** [modules] Virhe 2
tino@tino:~/Lataukset/r8101-1.022.00$ 


```

Theres some finnish words :S

---

### Post by chili555 on 2013-12-10
> **ttinoo said:**
> Sorry, didn't know where to post this. Wifi can't find any networks, ***wired connection works normally.*** It's my first Linux ever, Ubuntu 12.04. I have been using it for two days now. Never used wifi with Windows, so I dont know if the controller is broken or something.

I tried post #3 solution, and got this:

Please start a new thread and include details of your wireless device:```
lspci -nn | grep 0280
```This thread is about wired ethernet, not wireless. The driver you downloaded and tried to compile is also for wired not wireless.

---

### Post by tat3 on 2014-02-03
I followed the instructions, but still have no luck, any ideas????

t> at@Tat:~$ sudo gedit  /etc/modprobe.d/blacklist.conf
[sudo] password for tat: 
tat@Tat:~$ sudo update-initramfs -u && cd ~/Downloads && tar xvf r8101-1.022.00.tar.bz2 && cd r8101-1.022.00 && sudo sh autorun.sh
update-initramfs: Generating /boot/initrd.img-3.8.0-35-generic
r8101-1.022.00/
r8101-1.022.00/src/
r8101-1.022.00/src/r8101.h
r8101-1.022.00/src/r8101_n.c
r8101-1.022.00/src/rtl_eeprom.c
r8101-1.022.00/src/rtltool.c
r8101-1.022.00/src/rtltool.h
r8101-1.022.00/src/rtl_eeprom.h
r8101-1.022.00/src/Makefile_linux24x
r8101-1.022.00/src/rtl_ethtool.h
r8101-1.022.00/src/Makefile
r8101-1.022.00/readme
r8101-1.022.00/autorun.sh
r8101-1.022.00/Makefile

Check old driver and unload it.
Build the module and install
/home/tat/Downloads/r8101-1.022.00/src/r8101_n.c:5396:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8101_init_board’
/home/tat/Downloads/r8101-1.022.00/src/r8101_n.c:5799:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8101_init_one’
/home/tat/Downloads/r8101-1.022.00/src/r8101_n.c:5926:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl8101_remove_one’
/home/tat/Downloads/r8101-1.022.00/src/r8101_n.c:7851:12: error: ‘rtl8101_init_one’ undeclared here (not in a function)
/home/tat/Downloads/r8101-1.022.00/src/r8101_n.c:7852:2: error: implicit declaration of function ‘__devexit_p’ [-Werror=implicit-function-declaration]
/home/tat/Downloads/r8101-1.022.00/src/r8101_n.c:7852:25: error: ‘rtl8101_remove_one’ undeclared here (not in a function)
/home/tat/Downloads/r8101-1.022.00/src/r8101_n.c:7488:12: warning: ‘rtl8101_poll’ defined but not used [-Wunused-function]
/home/tat/Downloads/r8101-1.022.00/src/r8101_n.c:869:1: warning: ‘rtl8101_xmii_reset_pending’ defined but not used [-Wunused-function]
/home/tat/Downloads/r8101-1.022.00/src/r8101_n.c:885:1: warning: ‘rtl8101_xmii_link_ok’ defined but not used [-Wunused-function]
/home/tat/Downloads/r8101-1.022.00/src/r8101_n.c:894:1: warning: ‘rtl8101_xmii_reset_enable’ defined but not used [-Wunused-function]
/home/tat/Downloads/r8101-1.022.00/src/r8101_n.c:1117:1: warning: ‘rtl8101_link_option’ defined but not used [-Wunused-function]
/home/tat/Downloads/r8101-1.022.00/src/r8101_n.c:1239:1: warning: ‘rtl8101_set_speed_xmii’ defined but not used [-Wunused-function]
/home/tat/Downloads/r8101-1.022.00/src/r8101_n.c:1565:1: warning: ‘rtl8101_gset_xmii’ defined but not used [-Wunused-function]
/home/tat/Downloads/r8101-1.022.00/src/r8101_n.c:1776:27: warning: ‘rtl8101_ethtool_ops’ defined but not used [-Wunused-variable]
/home/tat/Downloads/r8101-1.022.00/src/r8101_n.c:1811:13: warning: ‘rtl8101_get_mac_version’ defined but not used [-Wunused-function]
/home/tat/Downloads/r8101-1.022.00/src/r8101_n.c:1879:1: warning: ‘rtl8101_print_mac_version’ defined but not used [-Wunused-function]
/home/tat/Downloads/r8101-1.022.00/src/r8101_n.c:4584:1: warning: ‘rtl8101_release_board’ defined but not used [-Wunused-function]
/home/tat/Downloads/r8101-1.022.00/src/r8101_n.c:5729:1: warning: ‘rtl8101_check_eeprom’ defined but not used [-Wunused-function]
cc1: some warnings being treated as errors
make[3]: *** [/home/tat/Downloads/r8101-1.022.00/src/r8101_n.o] Error 1
make[2]: *** [_module_/home/tat/Downloads/r8101-1.022.00/src] Error 2
make[1]: *** [modules] Error 2
make: *** [modules] Error 2

---

### Post by chili555 on 2014-02-03
I would certainly try the newer version r8101-1.024 here: [http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PFid=7&Level=5&Conn=4&DownTypeID=3](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PFid=7&Level=5&Conn=4&DownTypeID=3)  I rebooted into my 3.8.0-xx kernel and it builds without error.

---

### Post by vinoth4 on 2014-03-01
> **chili555 said:**
> I would certainly try the newer version r8101-1.024 here: [http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PFid=7&Level=5&Conn=4&DownTypeID=3](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PFid=7&Level=5&Conn=4&DownTypeID=3)  I rebooted into my 3.8.0-xx kernel and it builds without error.

It does not compile in 3.11. I get the same issue as above posted.

---

### Post by chili555 on 2014-03-02
> **vinoth4 said:**
> It does not compile in 3.11. I get the same issue as above posted.Please try:```
cd ~/Desktop/r8101-1.024.00  [COLOR="#FF0000"]<--or wherever you downloaded it[/COLOR]
sudo make clean
wget http://sf.net/projects/mancha/files/misc/r8101-1.024.00_linux3.10.diff
patch -p1 < r8101-1.024.00_linux3.10.diff
sudo make
sudo make install
```Please let us and the searchers know how it goes.

---

### Post by Owen_Mehegan on 2014-04-04
I'm running 12.04 with a 3.5.0 kernel. Tonight I swapped a new motherboard into this system, it booted normally, but I found that the network wasn't working. ifconfig shows only an lo interface, no eth0. lspci shows that this is an RTL8101E network interface, so here I am.

I successfully compiled the r8101 driver downloaded from the Realtek site, and it shows up when I run lsmod, so it's loaded OK. I do not have any other Realtek drivers loaded. Yet even after reboot, I still have no eth0 interface. If I try to bring it up manually with ifup, I get: 'eth0: ERROR while getting interface flags: No such device.'

Anyone know what might be wrong here?

---

### Post by chili555 on 2014-04-04
Let's verify a few things:```
lspci -nn | grep 0280
dmesg | grep r8
lsmod | grep r8
```Thanks.

---

### Post by Owen_Mehegan on 2014-04-05
Well, by sheer chance, I figured out what was wrong. In order to make debugging easier, I went to hook up a USB wifi adapter to this system, and I ran 'ip addr' to check what the interface name was. In the output of that I also noticed an eth1 interface. Given that the MAC addresses were completely dissimilar, I guessed that this might be my lost ethernet interface. I changed my /etc/network/interfaces file to reference eth1, saved, ran ifup eth1, and it came up perfectly! I removed the wifi and rebooted, and the eth1 is still fine. Very strange - why didn't it get identified as eth0? 

For what it's worth, the lspci output with your grep filter would not have found anything. Here's the actual line for the NIC in my system:

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)

---

### Post by chili555 on 2014-04-05
> For what it's worth, the lspci output with your grep filter would not have found anything. You are quite correct; I made a mistake and I apologize. It should have been:```
lspci -nn | grep 0200
```And then we'd see:> 01:00.0 Ethernet controller [[COLOR="#FF0000"]0200[/COLOR]]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05) > Very strange - why didn't it get identified as eth0? It happens once in a while; udev is an imperfect tool. You can certainly ignore it and, as you've seen, everything will work perfectly well. If you are super OCD and it bothers you, edit /etc/udev/rules.d/70-persistent-net.rules and also /etc/network/interfaces and immediately reboot. You seem pretty adept, so I'll leave the details to you. If you get stuck, post back and we'll be glad to help.

---

