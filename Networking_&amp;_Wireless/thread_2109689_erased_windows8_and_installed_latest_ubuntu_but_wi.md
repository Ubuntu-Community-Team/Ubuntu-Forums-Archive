---
title: "erased windows8 and installed latest ubuntu but wireless doesnt work"
date: 2013-01-28
forum: Networking &amp; Wireless
---

### Post by Tom6153 on 2013-01-28
I brought an advent monza t200 red laptop
it had windows 8 preinstalled so swapped it for 64 bit ubuntu 12.10 (the latest one)
now the wireless doesnt work and it had been working with windows 8
i looked at the troubleshooting guide and i opened the terminal and found out that my computer uses a realtek wireless, product : rtl8188ce 802.11b/g/n wifi adapter
i then went to the realtek website and found a list of products which could perhaps fix my problem
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

however it seems that these products are listed acording to the type of linux kernal
ubuntu 12.10 uses the kernal 3.5.4 but i cant find that on the list
also what do i do when i do manage to download the right bit of software?

please help as i am stuck
thankyou

---

### Post by chili555 on 2013-01-28
You will probably have much better luck with the pre-built backports package. Let's verify your exact hardware before we proceed. Please open a terminal and run and post:```
lspci -nn | grep 0280
```

---

### Post by furything on 2013-01-28
[SIZE=2]Looks like you can use it see these posts for things you need to do

[[64 bit] Realtek *RTL8188CE* (rev 1)/*Ubuntu 12.10*/Lenovo Edge 14 ...]("http://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CDQQFjAA&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D2096334&ei=8owGUeaALsqV0QXitIAI&usg=AFQjCNGBY0sUxN6R_vt1ZwBeYgYEi3znIg&sig2=RrvEG_5fwvTUmugNTzso3w&bvm=bv.41524429,d.d2k")

[*12.10* x64 - *RTL8188CE* - Intermittent/Slow Internet ... - Ask *Ubuntu*]("http://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&ved=0CEUQFjAB&url=http%3A%2F%2Faskubuntu.com%2Fquestions%2F205575%2F12-10-x64-rtl8188ce-intermittent-slow-internet-connection&ei=8owGUeaALsqV0QXitIAI&usg=AFQjCNETcOqQJ0Urvm7HqXC7vlmHodJSlw&sig2=JGm5YJDHzQbGWFlffdsuRw&bvm=bv.41524429,d.d2k")[/SIZE]

---

### Post by Tom6153 on 2013-01-28
so i read all this below and i reckon i can do it but i dont know much about using the terminal, i got the realtek driver on another computer and put it on my pendrive but how would i unzip the file and get it installed? what commands would i type in?


Hi,

You need to blacklist some modules do this in the terminal:
 	Code:
 	sudo gedit /etc/modprobe.d/blacklist.conf 
Then at the very bottom of the page, paste these lines in:
 	Code:
 	blacklist rtl8192cu blacklist rtl8192c_common blacklist rtlwifi 
Save the file!

Then download the Realtek RTL8188CE driver from here:

[http://www.realtek.com.tw/downloads/...oads=true#2282]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=272&DownTypeID=3&GetDown=false&Downloads=true#2282")

Open a terminal, example: say the download went to your Downloads directory in your home directory. You would do:
 	Code:
 	cd ~/Downloads unzip (ZIPFILENAME) cd (NEWDIRECTORY_CREATED) chmod 755 ./install.sh sudo ./install.sh 
Then add you correct module like this:
 	Code:
 	sudo gedit /etc/modules 
And add
 	Code:
 	8188ce 
To the bottom of the list, this will make it load automatically at start up, then save the file.
You will need to do the reinstall of the software from Realtek on each kernel update. So keep the file handy.

Reboot and you should be able to connect.

Hope that helps!

---

### Post by chili555 on 2013-01-28
Why wouldn't you suggest linux-backports-modules-cw instead of compiling from source code?

Is the module named 8188ce? I thought it built rtl8192ce.

---

### Post by coldnovember on 2013-01-28
I am having this same issue. I have a HP 2000 Notebook PC and installed Ubuntu over Windows 8. My wifi, which worked perfectly before, now does not wok. Please help. My terminal window is saying:

cam@cam-HP-2000-Notebook-PC:~$ lspci -nn | grep 0280
06:00.0 Network controller [0280]: Ralink corp. Device [1814:539b]
cam@cam-HP-2000-Notebook-PC:~$ 

Can someone please help me on this issue?

---

### Post by Tom6153 on 2013-01-28
Why wouldn't you suggest linux-backports-modules-cw instead of compiling from source code?

im sorry i dont understand what that means
and i tried putting in the command that you listed above and it didnt work

---

### Post by chili555 on 2013-01-28
> **Tom6153 said:**
> Why wouldn't you suggest linux-backports-modules-cw instead of compiling from source code?

im sorry i dont understand what that means
and i tried putting in the command that you listed above and it didnt workPlease get a temporary wired ethernet connection and do:```
sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
```After it's done, reboot and let us have your report.

---

### Post by chili555 on 2013-01-28
> **coldnovember said:**
> I am having this same issue. I have a HP 2000 Notebook PC and installed Ubuntu over Windows 8. My wifi, which worked perfectly before, now does not wok. Please help. My terminal window is saying:

cam@cam-HP-2000-Notebook-PC:~$ lspci -nn | grep 0280
06:00.0 Network controller [0280]: Ralink corp. Device [1814:539b]
cam@cam-HP-2000-Notebook-PC:~$ 

Can someone please help me on this issue?Your decice is supposed to work with the module rt2800pci. Please open a terminal and do:```
sudo modprobe rt2800pci
```Does your wireless spring to life? If so, let's load it automatically on boot:```
sudo su
echo rt2800pci >> /etc/modules
exit
```If that's not the answer, please start your own new thread and I'll be happy to assist.

---

### Post by coldnovember on 2013-01-28
I tried this and now it is saying that it is hard blocked. i started a new thread at 

[http://ubuntuforums.org/showthread.php?p=12479970#post12479970](http://ubuntuforums.org/showthread.php?p=12479970#post12479970)

can someone please help!!!

---

### Post by Tom6153 on 2013-01-29
ok did it..... :)

tom@tom-Monza-T200:~$ sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-headers-3.5.0-17
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  linux-backports-modules-cw-3.6-3.5.0-22-generic linux-image-3.5.0-22-generic
Suggested packages:
  fdutils linux-doc-3.5.0 linux-source-3.5.0 linux-tools
The following NEW packages will be installed
  linux-backports-modules-cw-3.6-3.5.0-22-generic
  linux-backports-modules-cw-3.6-quantal-generic linux-image-3.5.0-22-generic
0 upgraded, 3 newly installed, 0 to remove and 248 not upgraded.
Need to get 14.8 MB of archives.
After this operation, 42.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates/main linux-image-3.5.0-22-generic amd64 3.5.0-22.34 [11.8 MB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates/main linux-backports-modules-cw-3.6-3.5.0-22-generic amd64 3.5.0-22.8 [2,983 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates/main linux-backports-modules-cw-3.6-quantal-generic amd64 3.5.0.22.28 [2,658 B]
Fetched 14.8 MB in 26s (554 kB/s)                                              
Selecting previously unselected package linux-image-3.5.0-22-generic.
(Reading database ... 141805 files and directories currently installed.)
Unpacking linux-image-3.5.0-22-generic (from .../linux-image-3.5.0-22-generic_3.5.0-22.34_amd64.deb) ...
Done.
Selecting previously unselected package linux-backports-modules-cw-3.6-3.5.0-22-generic.
Unpacking linux-backports-modules-cw-3.6-3.5.0-22-generic (from .../linux-backports-modules-cw-3.6-3.5.0-22-generic_3.5.0-22.8_amd64.deb) ...
Selecting previously unselected package linux-backports-modules-cw-3.6-quantal-generic.
Unpacking linux-backports-modules-cw-3.6-quantal-generic (from .../linux-backports-modules-cw-3.6-quantal-generic_3.5.0.22.28_amd64.deb) ...
Setting up linux-image-3.5.0-22-generic (3.5.0-22.34) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-22-generic /boot/vmlinuz-3.5.0-22-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-22-generic /boot/vmlinuz-3.5.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-22-generic /boot/vmlinuz-3.5.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-22-generic /boot/vmlinuz-3.5.0-22-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-22-generic
Found initrd image: /boot/initrd.img-3.5.0-22-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-backports-modules-cw-3.6-3.5.0-22-generic (3.5.0-22.8) ...
update-initramfs: Generating /boot/initrd.img-3.5.0-22-generic
Setting up linux-backports-modules-cw-3.6-quantal-generic (3.5.0.22.28) ...

---

### Post by Tom6153 on 2013-01-29
You made it work!!!! thank you

---

### Post by chili555 on 2013-01-29
> **Tom6153 said:**
> You made it work!!!! thank youAwesome! Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

