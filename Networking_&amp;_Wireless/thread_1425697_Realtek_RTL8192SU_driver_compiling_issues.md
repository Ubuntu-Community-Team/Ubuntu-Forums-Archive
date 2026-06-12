---
title: "Realtek RTL8192SU driver compiling issues"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by NeverSage on 2010-03-09
My wifi issue has been driving me crazy for days and am hoping the good people here might be able to help me out. I'm a Linux newbie, so please be gentle. 

My card has the Realtek rtl8192su usb chipset. First I tried using ndiswrapper which worked except I had to do it every time I restarted the computer. I figured if I had to spend a lot of time getting it to work correctly I might as well do it natively in Linux. I emailed Realtek and got the newest driver (rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.2010 0202.tar.gz). After much trial and error and reading many forums I got it to work using chili555's directions on the first page of this thread: [http://ubuntuforums.org/showthread.php?t=1329254](http://ubuntuforums.org/showthread.php?t=1329254). The problem is it didn't keep after the reboot. I'm assuming this has something to do with the module. I don't see it in /etc/modules folder but honestly I'm not sure if I'm supposed to. I'd like to add it into /etc/modules through gedit like topsykretts from the same thread, but of course I wouldn't be able to add the line r8192se_pci since I'm using a different chipset. I don't know where to find the information on what to use, though. 

Another issue from the directions given on that same thread:

from terminal cd back to the installed directory

then 

sudo ./wlan0up


When I do this ./wlan0up just says "No such file or directory".

If I didn't provide enough info, I'm sorry. Please let me know what other information you need. I'd like to add that on the computer I'm having these issues with I'm not technically running Ubuntu... It's Linux Mint. To my understanding there should be no difference when it comes to these drivers though.

Thanks for any help you can give me.

---

### Post by chili555 on 2010-03-09
Does this kick your wireless device to life?```
sudo modprobe r8192se_pci

```If it it the correct module, then you can find out with:```
iwconfig
```If you have a wireless interface, wlan0, perhaps, then add it to */etc/modules* on its own line:```
r8192se_pci
```Proofread, save and close your text editor. Does it work after a reboot? If not, post back and we'll fine tune.

---

### Post by NeverSage on 2010-03-10
When I do the sudo modprobe I get:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 6: ignoring bad line starting with 'blacklist.conf'
WARNING: /etc/modprobe.d/blacklist line 7: ignoring bad line starting with 'blacklist.conf'
WARNING: /etc/modprobe.d/blacklist line 8: ignoring bad line starting with 'blacklist.conf'
FATAL: Module r8192se_pci not found.

And with iwconfig I get:

lo        no wireless extensions.

eth0      no wireless extensions.


:-/

---

### Post by wannabeerased on 2010-03-10
Not promising I'll actually be of any help, but I'm trying to get the same chipset running, is there a public link I can get that firmware from?

---

### Post by NeverSage on 2010-03-10
Here: [http://www.megaupload.com/?d=GQNDYLF3](http://www.megaupload.com/?d=GQNDYLF3)

Good luck!

---

### Post by chili555 on 2010-03-10
> rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.2010 0202.tar.gz> r8192se_pciOops! We have a mismatch here. When you compiled the module, what was the rXXX.ko file that got created? Not r8192se_pci, evidently. If you can't see for sure in your folder, rtl8712etc. you may have to recompile. Post back with your findings if you are unsure.

If you can find the module, simply do:```
sudo modprobe some_module
```Of course, substitute the name of the module you built, without the .ko extension. If your wireless comes to life, add the module:```
sudo gedit /etc/modules
```Add a new separate line:```
some_module
```Now, we need to clean up a few other things:```
sudo mv /etc/modprobe.d/ndiswrapper  /etc/modprobe.d/ndiswrapper.conf
```By any chance, is ndiswrapper fighting the native module you built?

In order to clean up *blacklist*, we need to see it. Please post:```
cat /etc/modprobe.d/blacklist
```We will fix it.

---

### Post by NeverSage on 2010-03-11
> **chili555 said:**
> Oops! We have a mismatch here. When you compiled the module, what was the rXXX.ko file that got created? Not r8192se_pci, evidently. If you can't see for sure in your folder, rtl8712etc. you may have to recompile. Post back with your findings if you are unsure.

If you can find the module, simply do:```
sudo modprobe some_module
```Of course, substitute the name of the module you built, without the .ko extension. If your wireless comes to life, add the module:```
sudo gedit /etc/modules
```Add a new separate line:```
some_module
```Now, we need to clean up a few other things:```
sudo mv /etc/modprobe.d/ndiswrapper  /etc/modprobe.d/ndiswrapper.conf
```By any chance, is ndiswrapper fighting the native module you built?

In order to clean up *blacklist*, we need to see it. Please post:```
cat /etc/modprobe.d/blacklist
```We will fix it.

I'm just going to post everything since I don't want to leave out anything important.  I recompiled and got this:

```
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.31-14-generic/build M=/home/htpc/Realtek  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/htpc/Realtek/cmd/rtl871x_cmd.o
  CC [M]  /home/htpc/Realtek/cmd/rtl8712_cmd.o
  CC [M]  /home/htpc/Realtek/crypto/rtl871x_security.o
  CC [M]  /home/htpc/Realtek/debug/rtl871x_debug.o
  CC [M]  /home/htpc/Realtek/eeprom/rtl871x_eeprom.o
  CC [M]  /home/htpc/Realtek/efuse/rtl8712_efuse.o
  CC [M]  /home/htpc/Realtek/hal/rtl8712/hal_init.o
  CC [M]  /home/htpc/Realtek/hal/rtl8712/usb_ops.o
  CC [M]  /home/htpc/Realtek/hal/rtl8712/usb_ops_linux.o
  CC [M]  /home/htpc/Realtek/hal/rtl8712/usb_halinit.o
  CC [M]  /home/htpc/Realtek/io/rtl871x_io.o
  CC [M]  /home/htpc/Realtek/io/rtl8712_io.o
  CC [M]  /home/htpc/Realtek/ioctl/rtl871x_ioctl_query.o
  CC [M]  /home/htpc/Realtek/ioctl/rtl871x_ioctl_set.o
  CC [M]  /home/htpc/Realtek/ioctl/rtl871x_ioctl_linux.o
  CC [M]  /home/htpc/Realtek/ioctl/rtl871x_ioctl_rtl.o
  CC [M]  /home/htpc/Realtek/led/rtl8712_led.o
  CC [M]  /home/htpc/Realtek/mlme/ieee80211.o
  CC [M]  /home/htpc/Realtek/mlme/rtl871x_mlme.o
  CC [M]  /home/htpc/Realtek/mp/rtl871x_mp.o
  CC [M]  /home/htpc/Realtek/mp/rtl871x_mp_ioctl.o
  CC [M]  /home/htpc/Realtek/os_dep/linux/io_linux.o
  CC [M]  /home/htpc/Realtek/os_dep/linux/xmit_linux.o
  CC [M]  /home/htpc/Realtek/os_dep/linux/cmd_linux.o
  CC [M]  /home/htpc/Realtek/os_dep/linux/mlme_linux.o
  CC [M]  /home/htpc/Realtek/os_dep/linux/recv_linux.o
  CC [M]  /home/htpc/Realtek/os_intf/osdep_service.o
  CC [M]  /home/htpc/Realtek/os_intf/linux/os_intfs.o
  CC [M]  /home/htpc/Realtek/os_intf/linux/usb_intf.o
  CC [M]  /home/htpc/Realtek/pwrctrl/rtl871x_pwrctrl.o
  CC [M]  /home/htpc/Realtek/recv/rtl871x_recv.o
  CC [M]  /home/htpc/Realtek/recv/rtl8712_recv.o
  CC [M]  /home/htpc/Realtek/rf/rtl871x_rf.o
  CC [M]  /home/htpc/Realtek/rf/rtl8712_rf.o
  CC [M]  /home/htpc/Realtek/sta_mgt/rtl871x_sta_mgt.o
  CC [M]  /home/htpc/Realtek/xmit/rtl871x_xmit.o
  CC [M]  /home/htpc/Realtek/xmit/rtl8712_xmit.o
  LD [M]  /home/htpc/Realtek/8712u.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/htpc/Realtek/8712u.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
```

So it appears 8712u is the module.

I used sudo mv to clean up the ndiswrapper stuff.

I did the modprobe and iwconfig and got:



```
htpc@htpc ~ $ sudo modprobe 8712u
[sudo] password for htpc: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 6: ignoring bad line starting with 'blacklist.conf'
WARNING: /etc/modprobe.d/blacklist line 7: ignoring bad line starting with 'blacklist.conf'
WARNING: /etc/modprobe.d/blacklist line 8: ignoring bad line starting with 'blacklist.conf'
htpc@htpc ~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     unassociated  Nickname:"rtl_wifi"
          Mode:Auto  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
Needless to say my wireless didn't come to life :-/.  I stuck the module in gedit /etc/modules anyway.  Is that OK or should I take it out?


Did the cat /etc/modprobe.d/blacklist and got:

```
htpc@htpc ~ $ cat /etc/modprobe.d/blacklist
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist.conf b43
blacklist.conf b43legacy
blacklist.conf ssb
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
```

I don't know if ndiswrapper is fighting with the linux drivers.  It shouldn't because I did a complete uninstall on it but maybe there's something that synaptic missed?

BTW. I'm using Wicd instead of network manager.  Just thought I'd mention that in case it might affect something.

---

### Post by wannabeerased on 2010-03-11
Can't say I've had much luck either.  Went through the whole make install process (received a ton of warnings during the make, yours seemed to go a lot smoother...).  Still when I plug in my USB receiver, dmesg shows it trying to load a bunch of other modules, with warnings about them being staging modules and then how it's unable to get firmware it wants for it.  Pretty much identical to the output in this post: [http://ubuntuforums.org/showthread.php?t=1365082&highlight=RTL8192SU](http://ubuntuforums.org/showthread.php?t=1365082&highlight=RTL8192SU)
I'd get pretty much all the same output for all those commands he's running, so my wifi APPEARED to be there, but couldn't actually ever see anything.

So I added those modules, and (after checking what else was in modprobe -l) the old pci one and ndiswrapper to the blacklist, I made a new blacklist-wireless.conf file because using just blacklist didn't see, to be working and gave that warning all the time.

```
robbo@robbo-mythtv:~$ cat /etc/modprobe.d/blacklist-wireless.conf
blacklist ieee80211_crypt
blacklist ieee80211_crypt_wep
blacklist ieee80211_crypt_tkip
blacklist ieee80211_crypt_ccmp
blacklist ieee80211_rsl
blacklist r8192s_usb
blacklist r8192se_pci
blacklist ndiswrapper

```

So after a quick reboot, I plug in my USB wireless and... I get some lighting activity followed by a complete system hang.  I was tailing the dmesg output to see what it was loading, looked to have been picking up some r87... stuff but due to the hang, I couldn't save the output.

Not sure why I didn't think to ask til now, but are those 32 or 64bit drivers?  I'm running 64bit :?

Who knows, if you try a few things I did there, you might get it all up and running if that's all my problem was.

---

### Post by chili555 on 2010-03-11
@NeverSage --> Needless to say my wireless didn't come to life :-/. Isn't this clearly a wireless interface with the hint that it's nickname is rtl-wifi?> wlan1     unassociated  Nickname:"rtl_wifi"
          Mode:Auto  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0Do you see networks when you click the Wicd icon?You can safely do:```
sudo gedit /etc/modprobe.d/blacklist
```Amend the file to:```
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
```Proofread, save and close gedit. Also, please do:```
sudo mv /etc/modprobe.d/blacklist  /etc/modprobe.d/blacklist.conf 
```

---

### Post by chili555 on 2010-03-11
@wannabeerased --

I'm really confused! The file you compiled is supposed to have the firmware in it. I wonder why it didn't get loaded. Would you please start a new thread and start by telling me what the file is that you compiled, specifically the version. Also:```
uname -r
```If you have or can get:```
lsusb
```Thanks.

---

### Post by NeverSage on 2010-03-11
@wannabeerased,

I think they're 32bit, actually :-/.  Realtek is real quick with emailing drivers if you email them with a request.  Why they can't just post them on their website, I don't know.

@ chili555,

My card isn't seeing any networks.  This could be because it looks like Wicd doesn't see my card.  But you're right, from that message it does look like it should be working.  When I get off work I'll switch from Wicd and give network manager another shot.  I'll also clean up my blacklist stuff.

---

### Post by chili555 on 2010-03-11
> My card has the Realtek rtl8192su usb chipset.I am working on several Realtek issues on this forum, all of which have the same symptoms. The driver grabs the device, an interface is created, wlanx, usually, but the device will not scan for networks and Network Manager will not allow it to connect. Everything looks perfect except it doesn't work.

I have been searching extensively and found this:  [http://ubuntuforums.org/showpost.php?p=8790489&postcount=97](http://ubuntuforums.org/showpost.php?p=8790489&postcount=97)

I was especially interested in this part:> For those that are using laptops with internal wifi cards and trying to use an external usb wifi dongle, on mine the internal must be on i.e. blue light for any external wifi dongle to work.

Once it connects I have to click on network manager and it will show both adapters are connected then click on disconnect for the internal card.And this:> I originally disabled the internal adapter in Windows. This is the major stumbling block that prevents having a wireless connection even though ndiswrapper is on, driver installed and device recognized.This also means that any blacklists for your internal card must be removed.

You, Mr. NeverSage, have been selected to be our test pilot! Please remove all your Broadcom blacklists and push that wireless switch to activate your internal card. Now see if your external USB device comes to life. I have my fingers crossed.

---

### Post by NeverSage on 2010-03-12
> **chili555 said:**
> You, Mr. NeverSage, have been selected to be our test pilot! Please remove all your Broadcom blacklists and push that wireless switch to activate your internal card. Now see if your external USB device comes to life. I have my fingers crossed.

I have some great news!  After I removed Wicd and reinstalled the network manager, everything works!  I did this following all of chili555's advice.  Actually, I got it working before I did your most recent advice (above).  Thanks for the help!  I'll try to pay it forward to the best of my ability :)

---

### Post by chili555 on 2010-03-12
Great news! I am glad it's working for you. Enjoy.

---

### Post by NeverSage on 2010-08-29
Soooooo it's back to not working again.   I just installed lucid, recompiled the driver, and was setting up the card. It works, I'm posting this through that computer in fact, the problem is every time I reboot I have to manually load the module by cd-ing to the directory and doing 

```
sudo insmod 8712u.ko
```
I have "8712u" in my etc/modules file same as when I was running Linux Mint so I don't understand why it's not getting loaded on boot.

I should add that this is a fresh install of Lucid on a new partition.  The /home directory is on a separate partition and is unchanged from my Linux Mint install.

Do you have any ideas?

---

### Post by chili555 on 2010-08-30
Please cd to the correct directory and do:```
make clean
make 
sudo make install
```Now reboot and see if the behavior is improved.

---

### Post by NeverSage on 2010-08-30
> **chili555 said:**
> Please cd to the correct directory and do:```
make clean
make 
sudo make install
```Now reboot and see if the behavior is improved.

Everything seems to go fine until 

```
sudo make install
```Then it gives me

```
Makefile:11: /config: No such file or directory
make: *** No rule to make target `/config'.  Stop.
```In the end still no wifi after reboot.  I had to manually do "insmod" again.

---

### Post by chili555 on 2010-08-30
> Makefile:11: /config: No such file or directory
make: *** No rule to make target `/config'.  Stop.Please post the README or INSTALL file; whichever includes the installation instructions. You can make it an attachment to your reply with that little paperclip in the reply box.

---

### Post by NeverSage on 2010-08-30
Strangely enough the installation instructions came on a ppt, which I can't attach :-/

The tar.gz is on the Realtek website though: [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true")

If that link doesn't work [here]("http://www.realtek.com.tw/downloads/") is the download page. It's under wireless lan ic >IEEE 802.11b/g/n single chip

Thanks for the help

---

### Post by chili555 on 2010-08-30
Please try this. I just did and it worked for me:```
cd correct/install/directory
sudo su
make clean
make
make install
exit
```Please let me know.

---

### Post by NeverSage on 2010-08-31
> **chili555 said:**
> Please try this. I just did and it worked for me:```
cd correct/install/directory
sudo su
make clean
make
make install
exit
```Please let me know.

That worked!!!! Thanks for helping me out yet again, chili555!

---

### Post by chili555 on 2010-08-31
> That worked!!!! Thanks for helpingGreat! Glad it's working now.

---

### Post by brubizu on 2010-10-06
Hi.... I got a ENCORE ENUWI-NX2 and can't make it work in any way..... 

lsusb:
```
Bus 001 Device 004: ID 0bda:8192 Realtek Semiconductor Corp.
```

dmesg:
```
[  160.521181] 3  2  1  0  4  8  7  6  5  
[  160.533479] Dot11d_Init()
[  160.533488] rtl819xU:unknown rf chip, can't set channel map in function:rtl819x_set_channel_map()
[  160.533492] 
[  160.576483] rtl819xU: --->FirmwareDownload92S()
[  160.576488] 
[  160.576499] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  160.580576] rtl819xU:request firmware fail!
[  160.580583] 
[  160.580890] rtl819xU:Firmware Download Fail!!4544
[  160.580895] 
[  160.596981] rtl819xU: --->FirmwareDownload92S()
[  160.596987] 
[  160.596997] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  160.601675] rtl819xU:request firmware fail!
[  160.601680] 
[  160.601870] rtl819xU:Firmware Download Fail!!4544
[  160.601873] 
[  160.601880] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  160.601883] 
[  160.627619] rtl819xU: --->FirmwareDownload92S()
[  160.627627] 
[  160.627643] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  160.632267] rtl819xU:request firmware fail!
[  160.632273] 
[  160.632517] rtl819xU:Firmware Download Fail!!4544
[  160.632521] 
[  160.651370] rtl819xU: --->FirmwareDownload92S()
[  160.651377] 
[  160.651393] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  160.665266] rtl819xU:request firmware fail!
[  160.665271] 
[  160.666132] rtl819xU:Firmware Download Fail!!4544
[  160.666137] 
[  160.666150] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  160.666154] 
[  174.253212] rtl819xU: --->FirmwareDownload92S()
[  174.253218] 
[  174.253229] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  174.257562] rtl819xU:request firmware fail!
[  174.257570] 
[  174.257875] rtl819xU:Firmware Download Fail!!4544
[  174.257880] 
[  174.276722] rtl819xU: --->FirmwareDownload92S()
[  174.276729] 
[  174.276744] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  174.280983] rtl819xU:request firmware fail!
[  174.280989] 
[  174.281374] rtl819xU:Firmware Download Fail!!4544
[  174.281378] 
[  174.281388] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  174.281392] 
[  456.651185] rtl819xU: --->FirmwareDownload92S()
[  456.651190] 
[  456.651201] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  456.655422] rtl819xU:request firmware fail!
[  456.655427] 
[  456.656114] rtl819xU:Firmware Download Fail!!4544
[  456.656120] 
[  456.674200] rtl819xU: --->FirmwareDownload92S()
[  456.674208] 
[  456.674223] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  456.679349] rtl819xU:request firmware fail!
[  456.679354] 
[  456.679589] rtl819xU:Firmware Download Fail!!4544
[  456.679593] 
[  456.679601] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  456.679606] 

```

Running Lucid (10.04) kernel 2.6.32-21-generic


I followed these steps [http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html](http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html) (with the sudo su modification...)

but simply doesn't work

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

sudo ifconfig wlan0 up:
```
SIOCSIFFLAGS: Temporarily unavaible resource
```

any ideas???

---

### Post by chili555 on 2010-10-06
First, let's try to fix the firmware issue. Let's see if the needed firmware is actually on your system:```
sudo updatedb
locate rtl8192sfw.bin
```This will take a few moments, please be patient.

You probably have the firmware in /lib/firmware/RTL8192S[COLOR="Red"]E[/COLOR]. However, your driver is looking in /lib/firmware/RTL8192S[COLOR="Red"]U[/COLOR].> usb 1-2: firmware: requesting RTL8192S[COLOR="Red"]U[/COLOR]/rtl8192sfw.binIf you confirm that that's the case, let's copy over the firmware to the correct directory:```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU
```Reboot and let us have your report. Include the dmesg listings as above.

---

### Post by Edoaigor on 2011-01-16
Hi all, I followed this thread and many others and lost the whole week end trying to figure out how to install this ****** usb network adapter without success. :(
First of all: if i want to use Kubuntu 10.10 or 10.04 what USB wireless adaptor would work out of the box??
secondly: do you suggest I simply throw the Belkin Surf adaptor I have in the trash and/or try to sell it on e-bay to some windows user?
I tried everything but my computer does not want to recognize the usb adapter no matter what I do.
iwconfig says there are no wireless adaptors,
lsusb sees one belkin device and the regular usb hubs
when I try to make install something goes wrong all the time (I get a bunch of no directory, no permission or whatever messages)
Moreover, is there a way to turn the thing on or it simply turns on by itself?
when I grep the dmesg I see the usb device gets connected buy I don't see it as a network adapter.. :(

Help

---

### Post by chili555 on 2011-01-16
> **Edoaigor said:**
> Hi all, I followed this thread and many others and lost the whole week end trying to figure out how to install this ****** usb network adapter without success. :(
First of all: if i want to use Kubuntu 10.10 or 10.04 what USB wireless adaptor would work out of the box??
secondly: do you suggest I simply throw the Belkin Surf adaptor I have in the trash and/or try to sell it on e-bay to some windows user?
I tried everything but my computer does not want to recognize the usb adapter no matter what I do.
iwconfig says there are no wireless adaptors,
lsusb sees one belkin device and the regular usb hubs
when I try to make install something goes wrong all the time (I get a bunch of no directory, no permission or whatever messages)
Moreover, is there a way to turn the thing on or it simply turns on by itself?
when I grep the dmesg I see the usb device gets connected buy I don't see it as a network adapter.. :(

HelpWould you please start a new thread and post: ```
lsusb

```Send me a private message if I don't catch it right away.

---

### Post by nazriel on 2011-01-17
Hmm. Try this way:

```

cd /usr/src/linux
sudo make xconfig
Device Drivers -> Stagging Drivers -> RealTek RTL8712U [*]
sudo make && make modules_install

sudo reboot

```

driver should load and dmesg should print:

```

[    2.008661] usb 1-4: New USB device found, idVendor=0bda, idProduct=8171
[    2.008818] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.008974] usb 1-4: Product: RTL8188S WLAN Adapter 
[    2.009132] usb 1-4: Manufacturer: Manufacturer Realtek 
[    2.009286] usb 1-4: SerialNumber: 00e04c000001
[    2.009520] usb 1-4: usb_probe_device
[    2.009523] usb 1-4: configuration #1 chosen from 1 choice
[    2.009787] usb 1-4: adding 1-4:1.0 (config #1, interface 0)
[    2.009853] r8712u 1-4:1.0: usb_probe_interface
[    2.009855] r8712u 1-4:1.0: usb_probe_interface - got id
[    2.009857] r8712u: DriverVersion: v7_0.20100831
[    2.010023] r8712u: register rtl8712_netdev_ops to netdev_ops
[    2.010178] r8712u: USB_SPEED_HIGH with 4 endpoints
[    2.010658] r8712u: Boot from EFUSE: Autoload OK


```

Ok, go forward.

```

sudo ifconfig wlan0 up
sudo iwlist scan
sudo iwconfig wlan0 essid [type name of your wlan ssid]
sudo iwlist scan
sudo dhcpcd

```

Your network should be running now.
Problems I am facing now are how to force Wicd to detect that dongle.

I've added this script to ~/.bash_profile
```
sudo ifconfig wlan0 up
sudo iwlist scan
sudo iwconfig wlan0 essid [type name of your wlan ssid]
sudo iwlist scan
sudo dhcpcd

```
 So each time I am login in, connection is gettin up, as you cant manage it with Wicd or network manager.


All those things were going on:
Gentoo (sorry for that, just want to help here), kernel - 2.6.37, dhcpcd 5.2.8, wireless-tools 29

Update:
Wifi-radar works fine, no idea why Wicd is slacking ;)

---

### Post by rocksockdoc on 2011-04-25
It looks like a LOT of people have been similarly burned by this Ubuntu bug:
- [Ubuntu Karmic 32bit Realtek 8192SU driver]("http://ubuntuforums.org/showthread.php?p=10719084#post10719084")
- [Realtek RTL8192SU driver compiling issues]("http://ubuntuforums.org/showthread.php?t=1425697")
-[ [STAGING] realtek rtl8192su chipset based USB wireless devices fail to work    ]("http://ubuntuforums.org/showpost.php?p=10125636&postcount=17")
**- **[Mvix Solido driver (rtl8712/8172) on 10.04]("http://ubuntuforums.org/showthread.php?t=1466185")
- [Firmware for Realtek 8192  ]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/firmware-for-realtek-8192-a-761714/page2.html")
etc.
[B] 
To help others, here's my summary of my particular workaround to this Ubuntu bug.

[/B]> **rocksockdoc said:**
> Thanks. That helped a lot to understand and  work around this (apparently known) Ubuntu bug which sidetracked me for a  day.

I detailed my efforts to insert an external USB WiFi radio into my laptop in this thread:
- [**How do we tell Ubuntu 10.04 to use a DIFFERENT wireless radio card?**]("http://ubuntuforums.org/showthread.php?p=10718746#post10718746")

On my version of a pristine Ubuntu 10.04 laptop installation:
```
$uname -a
...
Linux library 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:24:35 UTC 2011 i686 GNU/Linux

```At first, Ubuntu would not recognize the [Amped UA600 USB WiFi radio adapter ]("http://www.ampedwireless.com/support/model/ua600.html")when it was plugged into the laptop USB port.

```

$ ifconfig | grep wlan   
...
eth0 Link encap:Ethernet  HWaddr 00:a0:c3:3a:93:38
wlan0 Link encap:Ethernet  HWaddr 00:0a:8d:37:b3:ba

```First, I determined the device identifier using 'list short USB":
```

$ lsusb
...
Bus 002 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. 

```Then, in the /var/log/messages (dmesg | tail), I determined what driver Ubuntu was (mistakenly) looking for:
```

usb 2-1: new high speed USB device using ehci_hcd and address 2
usb 2-1: configuration #1 chosen from 1 choice
r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned. <=== huh?
 ...
Linux kernel driver for RTL8192 based WLAN cards
Copyright (c) 2007-2008, Realsil Wlan
...
rtl8192_proc_init_one+0x25/0x460 [r8192s_usb]
rtl8192_usb_probe+0x148/0x191 [r8192s_usb]       **[COLOR=DarkRed]<==== NOTE: This will be useful for the modinfo [/COLOR]**command syntax!
...
usbcore: registered new interface driver rtl819xU [COLOR=DarkRed]**  <=== NOTICE the "U" (Ubuntu has only the "E")**[/COLOR]
usb 2-1: firmware: requesting RTL8192SU/rtl8192sfw.bin
...
usb 2-1: USB disconnect, address 3
...

```Placing that keyword into "module information", I could see the desired driver:
```

$ modinfo r8192s_usb
...
filename:       /lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
...

```A quick look in the  /lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless directory  shows an "rtl818x" directory with the following contents:

```

$ ls -alsF /lib/modules/2.6.32-31-generic/kernel/drivers/net/wireless/rtl818x/*
...
44 -rw-r--r--  1 root root 43176 2011-04-08 16:36 rtl8180.ko
72 -rw-r--r--  1 root root 73640 2011-04-08 16:36 rtl8187.ko

```The problem appears to be that Ubuntu is looking for the following location  (which doesn't exist):
```

$ ls /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/rtl8192sfw_bin
...
ls: cannot access /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/rtl8192sfw_bin: No such file or directory

```The file exists (rtl8192sfw_bin); it's just in a different location on Ubuntu:
```

$ ls -alsF /lib/firmware/RTL8192S**[COLOR=DarkRed]E[/COLOR]**
...
/lib/firmware/RTL8192S**[COLOR=DarkRed]E[/COLOR]**:
total 244
-rw-r--r-- 1 root root 75984 2010-12-14 08:26 rtl8192sfw492.bin
-rw-r--r-- 1 root root 89616 2010-12-14 08:26 rtl8192sfw74.bin
-rw-r--r-- 1 root root 80976 2010-12-14 08:26 rtl8192sfw.bin

```[Post #35]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034/comments/35") and [post #36]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034/comments/36") of [this thread]("http://ubuntuforums.org/showpost.php?p=10125636&postcount=17") provided a (different sized, same-named file):
-[ [STAGING] realtek rtl8192su chipset based USB wireless devices fail to work    ]("http://ubuntuforums.org/showpost.php?p=10125636&postcount=17")



Here's what I did to obtain that differently-sized file (I guess I should call it a "driver"):
```

http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
    $ gunzip rtl8192sfw.bin.gz
    $ sudo mkdir /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**
    $ sudo mv rtl8192sfw.bin /lib/firmware/RTL8192S**[COLOR=DarkRed]U[/COLOR]**/.

```Finally, I was able to get Ubuntu to recognize the external WiFi radio when plugged in:
```

$ ifconfig | grep wlan
...
wlan0     Link encap:Ethernet  HWaddr 00:0a:8d:37:b3:ba
wlan1     Link encap:Ethernet  HWaddr f8:78:8c:a1:45:f4

```Now that the driver is finally working, I can get back to the original question asked in that thread:
- [**How do we tell Ubuntu 10.04 to use a DIFFERENT wireless radio card?**]("http://ubuntuforums.org/showthread.php?p=10718746#post10718746")

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189999&stc=1&d=1303756077[/IMG]

---

### Post by walt.smith1960 on 2011-04-25
Sort of a hijack but I think relevant.  My RTL8192SU adapter (TrendNet TEW649UB)works out of the box with Natty.  Great!!  Until I put the machine in suspend.  It'll suspend fine but won't wake up from suspend.  I can unplug then replug the adapter and it will come alive and work perfectly.  I have a thread about this in the Natty testing forum.  This adapter suspends and resumes flawlessly in 10.10 with the firmware patch.  I have an ath9k adapter and an old TrendNet TEW424UB which will suspend and resume perfectly in Natty.  I'm guessing there's something with   the R8712U module and I assume the 2.6.38 kernel that are not happy together. The problem occurs on a Gigabyte desktop machine and an IBM Thinkpad so it's not just one chipset that's the problem.  It also occurs with Natty 32 bit and Xubuntu 32 bit.  I probably should file a bug report but I'm not sure how to go about it.  Apport is not activated.

---

### Post by NeverSage on 2011-08-26
I always fear updating my kernel since every time I have trouble getting my wireless card working again.

chili555, you've always helped me before some I'm hoping you'll be able to give me a hand again. I'm still running Lucid. I updated the kernel and recompiled the driver as you said earlier in this thread (which worked last time) but it didn't work. I thought maybe it had something to do with the driver being old so I downloaded the newest version of the driver and again compiled it like before but still no luck. At this point I'm stumped. I've been messing around with it for a couple hours but I can't seem to get it working. Is it possible the new and old version of the drivers are conflicting?

Thanks

---

### Post by chili555 on 2011-08-26
> **NeverSage said:**
> I always fear updating my kernel since every time I have trouble getting my wireless card working again.

chili555, you've always helped me before some I'm hoping you'll be able to give me a hand again. I'm still running Lucid. I updated the kernel and recompiled the driver as you said earlier in this thread (which worked last time) but it didn't work. I thought maybe it had something to do with the driver being old so I downloaded the newest version of the driver and again compiled it like before but still no luck. At this point I'm stumped. I've been messing around with it for a couple hours but I can't seem to get it working. Is it possible the new and old version of the drivers are conflicting?

ThanksPlease remind me of your details. Please post:```
lsusb
uname -r
lsmod
```Thanks.

---

### Post by NeverSage on 2011-08-26
> **chili555 said:**
> Please remind me of your details. Please post:```
lsusb
uname -r
lsmod
```Thanks.

It's just that my wifi card doesn't work for some reason. When I compile and install the drivers everything appears OK but network manager says "device not ready".

```
htpc@htpc:~$ lsusb
Bus 004 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 07aa:0047 Corega K.K. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
htpc@htpc:~$ uname -r
2.6.32-33-generic
htpc@htpc:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
appletalk              27215  0 
ppdev                   5259  0 
snd_hda_codec_nvhdmi     3840  1 
snd_hda_codec_via      27111  1 
nvidia              10382593  30 
snd_hda_intel          22069  2 
snd_seq_dummy           1338  0 
snd_hda_codec          74201  3 snd_hda_codec_nvhdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_seq_oss            26722  0 
8712u                 308178  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  17375  0 
r8192s_usb            346908  0 
output                  1871  1 video
agpgart                31724  1 nvidia
asus_atk0110            9017  0 
snd                    54244  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_seq_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
lp                      7028  0 
psmouse                63677  0 
serio_raw               3978  0 
pcspkr                  1518  0 
i2c_nforce2             5199  0 
parport                32635  2 ppdev,lp
evbug                   1741  0 
shpchp                 28835  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
usbhid                 36110  0 
hid                    67288  1 usbhid
floppy                 53016  0 
forcedeth              49556  0 
pata_amd                8766  0 
ahci                   32360  3 

```

---

### Post by walt.smith1960 on 2011-08-26
Excuse me for sticking my nose in here but has this hoary old glitch arisen again?
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

One of the good things about 11.04 is the putting to rest of this problem.

---

### Post by chili555 on 2011-08-26
Well, you do have dueling and probably conflicting drivers. Let's kick one out:```
sudo su
echo "blacklist r8192s_usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us hear your report.

---

### Post by chili555 on 2011-08-26
> **walt.smith1960 said:**
> Excuse me for sticking my nose in here but has this hoary old glitch arisen again?
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

One of the good things about 11.04 is the putting to rest of this problem.Possibly. I suggest we try the blacklist first and then, if it's not working, we'll look at dmesg.

I always appreciate your nose; it's generally spot-on correct. Thanks!

---

### Post by NeverSage on 2011-08-26
> **chili555 said:**
> Well, you do have dueling and probably conflicting drivers. Let's kick one out:```
sudo su
echo "blacklist r8192s_usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us hear your report.

That worked!!! Thanks yet again chili555 :p. I always have trouble with this card when updating; do you have any advice to make it go smoother next time?

Also, thanks for the advice walt.smith1960. I should probably do an install of 11.04 at some point.

---

### Post by chili555 on 2011-08-26
The next kernel update you get, I would not recompile. See if r8192s_usb works then:```
sudo modprobe r8192s_usb
```If it does, remove the blacklist; if not, recompile.

---

### Post by walt.smith1960 on 2011-08-26
> **NeverSage said:**
> That worked!!! Thanks yet again chili555 :p. I always have trouble with this card when updating; do you have any advice to make it go smoother next time?

Also, thanks for the advice walt.smith1960. I should probably do an install of 11.04 at some point.

If you're happy with your current setup, you might hold off and go with 11.10 once it's been out 2 or 3 weeks.  I'm using the "don't use this if you're doing anything important" versions and I'm liking the Gnome-Shell implementation so far.  11.10 has a choice of 5 desktops.

---

### Post by NeverSage on 2011-08-28
Thanks guys! I'll take your advice.

---

### Post by aguilla1 on 2011-09-03
I am using Ubuntu 11.04 and the reason I bought an external dong is because the blue light sometimes does not come on. (When it does I don't need the external wireless card). Is it worth it for me to get the latest driver, try and find the appropriate changes in various files and hope it works? 
 
AG
 
> **chili555 said:**
> I am working on several Realtek issues on this forum, all of which have the same symptoms. The driver grabs the device, an interface is created, wlanx, usually, but the device will not scan for networks and Network Manager will not allow it to connect. Everything looks perfect except it doesn't work.
 
I have been searching extensively and found this: [http://ubuntuforums.org/showpost.php?p=8790489&postcount=97](http://ubuntuforums.org/showpost.php?p=8790489&postcount=97)
 
I was especially interested in this part:And this:This also means that any blacklists for your internal card must be removed.
 
You, Mr. NeverSage, have been selected to be our test pilot! Please remove all your Broadcom blacklists and push that wireless switch to activate your internal card. Now see if your external USB device comes to life. I have my fingers crossed.

---

### Post by chili555 on 2011-09-16
> **aguilla1 said:**
> I am using Ubuntu 11.04 and the reason I bought an external dong is because the blue light sometimes does not come on. (When it does I don't need the external wireless card). Is it worth it for me to get the latest driver, try and find the appropriate changes in various files and hope it works? 
 
AGIs your internal device an RTL8192SU? We ought to troubleshoot what is happening, or not, when the internal doesn't start up as expected. For example, is the driver loaded?```
lsmod | grep 819
```If that's the problem, we can easily fix it.

---

### Post by praseodym on 2011-09-16
> I am using Ubuntu 11.04 and the reason I bought an external dong is because the blue light sometimes does not come on. (When it does I don't need the external wireless card). Is it worth it for me to get the latest driver, try and find the appropriate changes in various files and hope it works?

AG

Do you also have an *internal* device? Maybe you need to unload *that* driver permanently or temporarily according to this UDEV-rule if the USB-device is plugged in:

[http://ubuntuforums.org/showpost.php?p=11247931&postcount=13](http://ubuntuforums.org/showpost.php?p=11247931&postcount=13)

Replace **b43** of that example with the module of your internal device.

```
lspci -nnk | grep -iA2 net
```
gives you the answer

---

### Post by Cimmo on 2011-11-24
Ubuntu 11.10 - 32 bit - kernel 3.0
I got an usb wireless stick with this chip
```
Bus 001 Device 003: ID 0bda:8192 Realtek Semiconductor Corp. RTL8192U 802.11n Wireless Adapter
```

Tried many firmwares included the one under /lib/firmware/RTL8192SE/ but with no luck
```
[  658.420023] usb 1-3: new high speed USB device number 3 using ehci_hcd
[  658.831175] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
[  658.834307] ieee80211_crypt: registered algorithm 'NULL'
[  658.834309] ieee80211_crypt: registered algorithm 'TKIP'
[  658.834311] ieee80211_crypt: registered algorithm 'CCMP'
[  658.834313] ieee80211_crypt: registered algorithm 'WEP'
[  658.834314] 
[  658.834315] Linux kernel driver for RTL8192 based WLAN cards
[  658.834316] Copyright (c) 2007-2008, Realsil Wlan
[  659.329988] Dot11d_Init()
[  659.329993] End of initendpoints
[  659.331253] usbcore: registered new interface driver rtl819xU
[  659.737692] rtl819xU:request firmware fail!
[  659.737694] 
[  659.737697] rtl819xU:ERR in init_firmware()
[  659.737698] 
[  659.737700] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[  659.737701] 
[  659.737703] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  659.737704] 
[  660.529207] rtl819xU:request firmware fail!
[  660.529208] 
[  660.529210] rtl819xU:ERR in init_firmware()
[  660.529211] 
[  660.529212] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[  660.529213] 
[  660.529215] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  660.529216] 

```

I have seen at page 3 there is another user brubizu with same chip but different dmesg errors, didn't find the solution, any help?

---

### Post by praseodym on 2011-11-24
Try this firmware:
```
wget http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin
sudo mkdir /lib/firmware/RTL8192SU
sudo cp rtl8192sfw.bin /lib/firmware/RTL8192SU
```

---

### Post by Cimmo on 2011-11-24
> **praseodym said:**
> Try this firmware:
```
wget http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin
sudo mkdir /lib/firmware/RTL8192SU
sudo cp rtl8192sfw.bin /lib/firmware/RTL8192SU
```

Do I need to reboot? Give me same error

---

### Post by praseodym on 2011-11-24
Driver reload
```
sudo modprobe -rfv r8192u_usb
sudo modprobe -v r8192u_usb
```
or reboot. Check:

```
iwconfig
rfkill list
lsmod
modinfo r8192u_usb | egrep '0BDA|8192'
dmesg | egrep 'rtl8|r8|firm'
sudo iwlist scan
```

---

### Post by Cimmo on 2011-11-24
Still no luck, here is the output:
```
marco@marco-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g/n  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

marco@marco-desktop:~$ rfkill list

marco@marco-desktop:~$ lsmod
Module                  Size  Used by
r8192u_usb            248351  0 
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
binfmt_misc            17292  1 
joydev                 17393  0 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                73673  0 
serio_raw              12990  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
tpm_tis                14002  0 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
mei                    36466  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
pata_marvell           12763  0 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
i915                  505108  3 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
e1000e                139814  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915

marco@marco-desktop:~$ modinfo r8192u_usb | egrep '0BDA|8192'
filename:       /lib/modules/3.0.0-13-generic/kernel/drivers/staging/rtl8192u/r8192u_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
firmware:       RTL8192U/data.img
firmware:       RTL8192U/main.img
firmware:       RTL8192U/boot.img
alias:          usb:v0BDAp8709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8192d*dc*dsc*dp*ic*isc*ip*

marco@marco-desktop:~$ dmesg | egrep 'rtl8|r8|firm'
[  119.662852] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
[  120.161331] usbcore: registered new interface driver rtl819xU
[  120.518397] rtl819xU:request firmware fail!
[  120.518401] rtl819xU:ERR in init_firmware()
[  120.518404] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[  120.518408] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  120.857712] rtl819xU:request firmware fail!
[  120.857715] rtl819xU:ERR in init_firmware()
[  120.857718] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[  120.857720] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!

marco@marco-desktop:~$ sudo iwlist scan
[sudo] password for marco: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

marco@marco-desktop:~$ 

```

---

### Post by Cimmo on 2011-11-28
Someone?

---

### Post by chili555 on 2011-11-28
> **praseodym said:**
> Try this firmware:
```
wget http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin
sudo mkdir /lib/firmware/RTL8192SU
sudo cp rtl8192sfw.bin /lib/firmware/RTL8192SU
```This is the wrong firmware and the wrong location:> marco@marco-desktop:~$ modinfo r8192u_usb | egrep '0BDA|8192'
filename:       /lib/modules/3.0.0-13-generic/kernel/drivers/staging/rtl8192u/r8192u_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
[COLOR="Red"]firmware:       RTL8192U/data.img
firmware:       RTL8192U/main.img
firmware:       RTL8192U/boot.img[/COLOR]Please try this:```
sudo mkdir /lib/firmware/RTL8192U
sudo cp /lib/firmware/RTL8192E/* /lib/firmware/RTL8192U
sudo modprobe -rfv r8192u_usb
sudo modprobe -v r8192u_usb
```Now is it working?

---

### Post by Cimmo on 2011-11-28
> **chili555 said:**
> This is the wrong firmware and the wrong location:Please try this:```
sudo mkdir /lib/firmware/RTL8192U
sudo cp /lib/firmware/RTL8192E/* /lib/firmware/RTL8192U
sudo modprobe -rfv r8192u_usb
sudo modprobe -v r8192u_usb
```Now is it working?

Yes now we go a little bit further!
```
[350092.098212] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
[350092.101325] ------------[ cut here ]------------
[350092.101336] WARNING: at /build/buildd/linux-3.0.0/fs/proc/generic.c:586 proc_register+0xa8/0x140()
[350092.101338] Hardware name:         
[350092.101340] proc_dir_entry 'net/ieee80211' already registered
[350092.101341] Modules linked in: r8192u_usb(C+) parport_pc ppdev dm_crypt bnep rfcomm bluetooth binfmt_misc joydev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq psmouse serio_raw snd_timer snd_seq_device tpm_tis snd soundcore mei(C) snd_page_alloc lp parport usbhid hid pata_marvell firewire_ohci firewire_core crc_itu_t i915 drm_kms_helper drm e1000e i2c_algo_bit video [last unloaded: r8192u_usb]
[350092.101370] Pid: 11294, comm: modprobe Tainted: G         C  3.0.0-13-generic #22-Ubuntu
[350092.101372] Call Trace:
[350092.101378]  [<c1047982>] warn_slowpath_common+0x72/0xa0
[350092.101381]  [<c11770f8>] ? proc_register+0xa8/0x140
[350092.101384]  [<c11770f8>] ? proc_register+0xa8/0x140
[350092.101387]  [<c1047a53>] warn_slowpath_fmt+0x33/0x40
[350092.101389]  [<c11770f8>] proc_register+0xa8/0x140
[350092.101392]  [<c11774a8>] create_proc_entry+0x58/0xa0
[350092.101407]  [<f98a21c7>] ieee80211_debug_init+0x23/0xe5c [r8192u_usb]
[350092.101415]  [<f98a200c>] rtl8192_usb_module_init+0xc/0x110 [r8192u_usb]
[350092.101419]  [<f98a2000>] ? 0xf98a1fff
[350092.101422]  [<c1001125>] do_one_initcall+0x35/0x170
[350092.101425]  [<f98a2000>] ? 0xf98a1fff
[350092.101429]  [<c10829fd>] sys_init_module+0xad/0x210
[350092.101433]  [<c152cc24>] syscall_call+0x7/0xb
[350092.101435] ---[ end trace e3b10181471289a1 ]---
[350092.101438] ieee80211_crypt: registered algorithm 'NULL'
[350092.101439] ieee80211_crypt: registered algorithm 'TKIP'
[350092.101441] ieee80211_crypt: registered algorithm 'CCMP'
[350092.101442] ieee80211_crypt: registered algorithm 'WEP'
[350092.101444] 
[350092.101444] Linux kernel driver for RTL8192 based WLAN cards
[350092.101445] Copyright (c) 2007-2008, Realsil Wlan
[350092.101448] ------------[ cut here ]------------
[350092.101450] WARNING: at /build/buildd/linux-3.0.0/fs/proc/generic.c:586 proc_register+0xa8/0x140()
[350092.101452] Hardware name:         
[350092.101453] proc_dir_entry 'net/rtl819xU' already registered
[350092.101455] Modules linked in: r8192u_usb(C+) parport_pc ppdev dm_crypt bnep rfcomm bluetooth binfmt_misc joydev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq psmouse serio_raw snd_timer snd_seq_device tpm_tis snd soundcore mei(C) snd_page_alloc lp parport usbhid hid pata_marvell firewire_ohci firewire_core crc_itu_t i915 drm_kms_helper drm e1000e i2c_algo_bit video [last unloaded: r8192u_usb]
[350092.101480] Pid: 11294, comm: modprobe Tainted: G        WC  3.0.0-13-generic #22-Ubuntu
[350092.101482] Call Trace:
[350092.101484]  [<c1047982>] warn_slowpath_common+0x72/0xa0
[350092.101487]  [<c11770f8>] ? proc_register+0xa8/0x140
[350092.101489]  [<c11770f8>] ? proc_register+0xa8/0x140
[350092.101492]  [<c1047a53>] warn_slowpath_fmt+0x33/0x40
[350092.101494]  [<c11770f8>] proc_register+0xa8/0x140
[350092.101497]  [<c11774a8>] create_proc_entry+0x58/0xa0
[350092.101506]  [<f9ab3499>] rtl8192_proc_module_init+0x29/0x40 [r8192u_usb]
[350092.101514]  [<f98a20f3>] rtl8192_usb_module_init+0xf3/0x110 [r8192u_usb]
[350092.101517]  [<c1001125>] do_one_initcall+0x35/0x170
[350092.101519]  [<f98a2000>] ? 0xf98a1fff
[350092.101522]  [<c10829fd>] sys_init_module+0xad/0x210
[350092.101524]  [<c152cc24>] syscall_call+0x7/0xb
[350092.101526] ---[ end trace e3b10181471289a2 ]---
[350092.101877] usbcore: registered new interface driver rtl819xU
[350100.664017] usb 1-4: new high speed USB device number 4 using ehci_hcd
[350101.297070] Dot11d_Init()
[350101.297075] End of initendpoints
[350103.797042] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[350104.264448] ========>ieee80211_parse_info_param(): athros AP is exist
[350104.264452] ========>ieee80211_parse_info_param(): athros AP is exist
[350104.878950] ========>ieee80211_parse_info_param(): athros AP is exist
[350104.878953] ========>ieee80211_parse_info_param(): athros AP is exist
[350106.107826] ========>ieee80211_parse_info_param(): athros AP is exist
[350106.107829] ========>ieee80211_parse_info_param(): athros AP is exist
[350106.312574] ========>ieee80211_parse_info_param(): athros AP is exist
[350106.312577] ========>ieee80211_parse_info_param(): athros AP is exist
[350124.437467] ========>ieee80211_parse_info_param(): athros AP is exist
[350124.437471] ========>ieee80211_parse_info_param(): athros AP is exist
[350124.642330] ========>ieee80211_parse_info_param(): athros AP is exist
[350124.642333] ========>ieee80211_parse_info_param(): athros AP is exist
[350128.073475] usb 1-4: USB disconnect, device number 4
[350128.073835] rtl819xU:==========>rtl8192_down()
[350128.073836] 
[350128.073839] read_nic_byte TimeOut! status:-19
[350128.073841] write_nic_byte TimeOut! status:-19
[350128.083774] read_nic_dword TimeOut! status:-19
[350128.083776] write_nic_dword TimeOut! status:-19
[350128.083783] rtl819xU:<==========rtl8192_down()
[350128.083784] 
[350128.100024] rtl819xU:=============>wlan driver to be removed
[350128.100026] 
[350128.110077] rtl819xU:wlan driver removed
[350128.110078] 
[350135.940019] usb 1-3: new high speed USB device number 5 using ehci_hcd
[350136.572794] Dot11d_Init()
[350136.572799] End of initendpoints
```

---

### Post by chili555 on 2011-11-28
Are the *dmesg* listings just as gruesome after a reboot?

---

### Post by Cimmo on 2011-11-28
> **chili555 said:**
> Are the *dmesg* listings just as gruesome after a reboot?

Actually I am sorry, Ubuntu 11.10 hides the network icon when connected to the lan.
It works, thanks! Seems although very slow 1Mb/s and a bit unstable, but I will test more.

---

