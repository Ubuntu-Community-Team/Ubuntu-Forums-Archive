---
title: "How to install Ralink RT5370 usb cards."
date: 2012-03-31
forum: Networking &amp; Wireless
---

### Post by lJ9%3MR&gt;sa on 2012-03-31
First, go to [http://www.ralinktech.com/en/04_support/license.php?sn=5016](http://www.ralinktech.com/en/04_support/license.php?sn=5016) and download the driver. You need to put in name and email. I just put in Name: lol email: [EMAIL="lol@lol.com"]lol@lol.com[/EMAIL]. Now extract it to your desktop. You need to probably extract it and extract it again since in the first archive is a tar file. Once you have extracted it, I recommend renaming it to an easier, shorter name like "ralink". Once you are done renaming, you need to open the folder and go to the folder "os" then in to the folder "linux". Once you are in that folder, open "config.mk" with your preferred text editor. ex: gedit... Now, scroll down until you find: 
```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n
```Now change the "n" to a "y" (Without quotes of course!)

Now scroll down again until you find(should be right under last one):
```
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
```Like before, change "n" to a "y".
Save.

Now, we have to blacklist some other conflicting drivers.
Open Terminal again.
Type:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```NOTE: you can open the blacklist file with you preferred text editor besides gedit if you like.
Scroll down to the very bottom of the blacklist file.
Type:
blacklist rt2800usb
blacklist rt2870sta

I'm not sure if blacklisting rt2870sta does anything, but I do it just in case. ;)
Save.
[COLOR=DarkRed]Reboot.[/COLOR] (THIS IS VERY IMPORTANT)

Once back in at the desktop, open Terminal.
"cd" to your Desktop.
```
cd /home/YOURUSERNAME/Desktop
```Replace your "YOURUSERNAME" with your Ubuntu username.
Once you are "cd" in to your desktop, you need to "cd" again to your ralink folder.
```
cd ralink
```You can change the name "ralink" to whatever you named the folder.
Type this:
```
sudo su
[COLOR=DarkRed]make clean[/COLOR]
make
make install
modprobe rt5370sta
exit
```During "make", if you get warnings, don't freak out. It's ok. Now, if it worked correctly, Network Manager should be able to find networks and connect to them. Congrats! You got your net working! Now, reboot and see if it works.
Happy browsing!

---

### Post by lJ9%3MR&gt;sa on 2012-03-31
If this works for anyone else, can a mod sticky it?

---

### Post by lJ9%3MR&gt;sa on 2012-03-31
bump

---

### Post by lJ9%3MR&gt;sa on 2012-04-01
bump.

---

### Post by dnewman4952 on 2012-04-01
Worked for me, thanks.

---

### Post by parovelb on 2012-04-02
it does not work for me
```
root@lenchi:/home/parovelb/Namizje/RT3090# make install
make -C /home/parovelb/Namizje/RT3090/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/parovelb/Namizje/RT3090/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/parovelb/Namizje/RT3090/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.2.0-21-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3090sta.ko /lib/modules/3.2.0-21-generic/kernel/drivers/net/wireless/
install: statusa »rt3090sta.ko« ni mo&#269; ugotoviti s stat: No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/parovelb/Namizje/RT3090/os/linux'
make: *** [install] Error 2
root@lenchi:/home/parovelb/Namizje/RT3090# modprobe rt3090sta
FATAL: Module rt3090sta not found.

```

---

### Post by dnewman4952 on 2012-04-02
Make sure you have gcc installed, and try again. I had the same problem before installing gcc.

---

### Post by DenisF on 2012-04-21
Hello,

I have to add:
blacklist rt2x00
in /etc/modprobe.d/blacklist.conf for working.
To know that I've done:
modprobe -l | grep wireless

Thanks

---

### Post by Laobi on 2012-04-22
For **TP-LINK TL-WN321G v5** (version 5) adapter you have to also edit the file common/rtusb_dev_id.c (in the driver folder) before compiling the driver.

Read with *lsusb*, the adapter's ID is **f201:5370**.  To make the driver recognize it, edit rtusb_dev_id.c :

Within the file find the paragraph that looks like this:

```
#ifdef RT5370
	{USB_DEVICE(0x148F,0x5370)}, /* Ralink 5370 */	
	{USB_DEVICE(0x148F,0x5372)}, /* Ralink 5370 */	
	{USB_DEVICE(0x13D3,0x3365)}, /* Azurewave */
	{USB_DEVICE(0x13D3,0x3329)}, /* Azurewave */
	{USB_DEVICE(0x2001,0x3C15)}, /* Alpha */
	{USB_DEVICE(0x2001,0x3C19)}, /* Alpha */
	{USB_DEVICE(0x2001,0x3C1C)}, /* DLink */
	{USB_DEVICE(0x2001,0x3C1D)}, /* DLink */
	{USB_DEVICE(0x043E,0x7A12)}, /* Arcadyan */
	{USB_DEVICE(0x043E,0x7A22)}, /* LG innotek */
#endif // RT5370 //

```

and add the following line:

```
	{USB_DEVICE(0xF201,0x5370)}, /* TP-LINK TL-WN321Gv5 */

```

so it will look like this:

```
#ifdef RT5370
	{USB_DEVICE(0x148F,0x5370)}, /* Ralink 5370 */	
	{USB_DEVICE(0x148F,0x5372)}, /* Ralink 5370 */	
	{USB_DEVICE(0x13D3,0x3365)}, /* Azurewave */
	{USB_DEVICE(0x13D3,0x3329)}, /* Azurewave */
	{USB_DEVICE(0x2001,0x3C15)}, /* Alpha */
	{USB_DEVICE(0x2001,0x3C19)}, /* Alpha */
	{USB_DEVICE(0x2001,0x3C1C)}, /* DLink */
	{USB_DEVICE(0x2001,0x3C1D)}, /* DLink */
	{USB_DEVICE(0x043E,0x7A12)}, /* Arcadyan */
	{USB_DEVICE(0x043E,0x7A22)}, /* LG innotek */
	[COLOR="Red"]{USB_DEVICE(0xF201,0x5370)}, /* TP-LINK TL-WN321Gv5 */[/COLOR]
#endif // RT5370 //

```

and then compile the driver.

---

### Post by nickasrock on 2012-05-20
Start from the first post.

Thanks heaps it worked for me and i am only a newbie.> Code:
sudo su
make clean
make
make install
modprobe rt5370sta
exit


Put the line of code in the terminal one at a time and press enter.I have been trying to fix this for months and now its fully functional.

I learnt some new things today.

Thank you

---

### Post by petermckinley on 2012-06-08
This guy is a genius, hats off. I'm a newbie and it looked intimidating so I tried other posts elsewhere first which didn't work, came back to this and eureka, worked first time. Editing the config.mk file was the step that was missed elsewhere. Took me a minute to figure out the text editor in Lubuntu is called Leafpad, duh.

£3 150MBps wifi, whoop!!

---

### Post by moskovich on 2012-07-22
Hi,
I strictly followed the instructions in this post, it did change something but still, i cannot use it. 

Look at the screenshot, some adapter has showed up (it wasn't there before this post) BUT it is unavailable and The wireless on/off
switch refuses to go "on".

Can someone please help with this ?
I am a newbie, so please "be simple" with me..:confused:
thanks

---

### Post by lJ9%3MR&gt;sa on 2012-07-24
> **moskovich said:**
> Hi,
I strictly followed the instructions in this post, it did change something but still, i cannot use it. 

Look at the screenshot, some adapter has showed up (it wasn't there before this post) BUT it is unavailable and The wireless on/off
switch refuses to go "on".

Can someone please help with this ?
I am a newbie, so please "be simple" with me..:confused:
thanks

This may not be the correct driver for your device... It should be though. I've never seen or had a problem like this before. Do you have a wireless switch? Usually it will be on the keyboard like Fn+F3 or something. It will have a picture of wifi bars or will have a word. Try turning on any hardware switches. If that doesn't work, open Terminal and type ```
sudo rfkill list all
``` if it shows yes on any of the listings put ```
sudo rfkill unblock all
``` in Terminal. If it still doesn't work, you may need to look for someone with a higher knowledge of Linux than me. :)

---

### Post by moskovich on 2012-07-25
Hi, i will describe a little more, maybe it will help a bit.

I run mint on Lenovo Thinkpad x61. 
Both linux and windows cannot recognize the onboard wifi 
adapter despite its physical switch is on, so i assume it is
damaged and unfunctional. 

Thats why i bought an usb dongle(wifi) which i can't make work with my Linux Mint 13 maya cinnamon 

When i "*lsusb*" i get this:

> $ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader

I see that there is some wireless adapter but I can't say if it is the onboard adapter or the usb dongle

The "*sudo rfkill list all*" command gives me this

> 0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

the "*sudo rfkill unblock all*"
doesn't change a thing :(

Any ideas?

---

### Post by Martin7182 on 2013-03-29
> **faxmanloveswaffles said:**
> If this works for anyone else, can a mod sticky it?

Thanks a lot! 
My device finally works, updating the blacklist like you suggested did the trick.

Martin

---

