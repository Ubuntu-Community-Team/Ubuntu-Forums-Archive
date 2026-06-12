---
title: "Fatal : Module ndiswrapper not found"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by dccmgb on 2013-01-27
When trying to install a Asus USB-N13 wireless adapter (via the Windows Driver Application) a get the error "Fatal: Module ndiswrapper not found". The adapter installs but does not work. I confirmed that the ndiswrapper is not found via
 
sudo modprobe ndiswrapper
 
I read another post that there is a problem with ndiswrapper 1.57 and that there is a fix in version 1.58 on SourceForge.net. Can someone list all the commands needed to install 1.58 as I am not very technical? Or is there another option to install the wireless driver? Thanks.  :)

---

### Post by ajgreeny on 2013-01-27
See section #4 of [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) which tells you in detail how to compile and install ndiswrapper in 12.04 and I assume 12.10.

It worked fine in my Lubuntu 12.04 where I had exactly the same error message after using the repo versions of ndiswrapper and ndisgtk.

---

### Post by dccmgb on 2013-01-27
Thanks.  I have version 12.10 and installed all the necessary ndiswrapper applications via Synaptics but still got the fatal error after that (also removed and installed again).  There is a problem with ndiswrapper 1.57 for 12.10 as outlined in this link (so I am not able to use any Windows drivers)
[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1023645](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1023645)
 
This link lists the proposed solution in reply #16.  However, I am unsure if all the commands are listed to execute that proposed solution, for example, how to you extract a tarball, how do you create the folder he is suggesting, and so on.  Sorry but I am very light on the technical side.

---

### Post by Bucky Ball on 2013-01-27
Are you sure you need it? Have you done an update with the USB dongle plugged in? Checked 'Additional Drivers'?

With the dongle plugged in, please run these two commands in a terminal, one after the other:

```
lsusb
iwconfig
```... and post the results here. The dongle sounds like it is being recognised and happening so it might be another problem. You may need to turn off wireless N or some other tweak.

---

### Post by dccmgb on 2013-01-28
Thanks.  Listed below is the requested output.  One thing I did not mention is that the adapter did install but then the "Fatal ndiswrapper" message was displayed.  I just assumed it was installed incorrectly because it is not working and the message seemed to indicate why.

dccmgb@ubuntu:~$ lsusb
Bus 001 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 003: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]
Bus 001 Device 004: ID 1307:0330 Transcend Information, Inc. 63-in-1 Multi-Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 03f0:8207 Hewlett-Packard FHA-3510 2.4GHz Wireless Optical Mobile Mouse
dccmgb@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

dccmgb@ubuntu:~$

---

### Post by Bucky Ball on 2013-01-28
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2772](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2772)

The driver there could possibly work. It is for your device. Install instructions will come with the download. Very easy.

You shouldn't need ndiswrapper for this device but the problem is, with ndiswrapper installed you are not going to get anything else to install. You'll need to uninstall ndiswrapper and possibly blacklist some things to find out. ndiswrapper is largely superseded now days.

Once again, have you looked in Additional Drivers? Done an update via a cable with the dongle plugged in?

---

### Post by dccmgb on 2013-01-28
Ok, I removed the XP driver I installed via ndiswrapper and removed all the ndiswrapper applications.  I found the realtek driver for my adapter via the link you provided.  Before I install that, where do I look for the additional drivers?  Is that in Software Sources?  If yes, I see additional drivers but not sure where to go from there.

---

### Post by chili555 on 2013-01-28
I thought rtl8192cu was installed in 12.10 by default:```
$ modinfo rtl8192cu | grep 17AB
alias:          usb:v[COLOR="Red"]0B05[/COLOR]p[COLOR="Red"]17AB[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```Please try to load it and let's see what happens:```
sudo modprobe rtl8192cu
dmesg | grep rtl
iwconfig
```Thanks.

---

### Post by dccmgb on 2013-01-28
Thanks.  I loaded a new copy of Ubuntu 12.10 and installed all the updates.  Once running, Ubuntu did not recognize the adapter until I removed it and the inserted again.  The wireless connection was then established (so some driver was loaded automatically) and so I disconnected my wired connection to see if the wireless connection would hold.  It did not hold, only lasted a few minutes - the same initial problem that I had - so back to square one.  Perhaps I should download the Linux driver from realtek and try to use the insall.sh file.  What do you think?

---

### Post by chili555 on 2013-01-28
> **dccmgb said:**
> Thanks.  I loaded a new copy of Ubuntu 12.10 and installed all the updates.  Once running, Ubuntu did not recognize the adapter until I removed it and the inserted again.  The wireless connection was then established (so some driver was loaded automatically) and so I disconnected my wired connection to see if the wireless connection would hold.  It did not hold, only lasted a few minutes - the same initial problem that I had - so back to square one.  Perhaps I should download the Linux driver from realtek and try to use the insall.sh file.  What do you think?
I'd like to see the results I requested, please.

The downloaded file would be of doubtful use on a 3.5.xx kernel, in my opinion.

---

### Post by dccmgb on 2013-01-28
Here are the results of your request, below.  I did confirm this adapter to work when under in Windows XP.  As mentioned, it works for about 5 minutes with Ubuntu, then dies.

dccmgb@ubuntu:~$ sudo modprobe rtl8192cu
[sudo] password for dccmgb: 
dccmgb@ubuntu:~$ dmesg | grep rtl
[   14.742261] rtl8192cu: Chip version 0x11
[   14.838520] rtl8192cu: MAC address: 08:61:6e:cd:ba:fd
[   14.838524] rtl8192cu: Board Type 0
[   14.838790] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   14.838862] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[   14.839700] usbcore: registered new interface driver rtl8192cu
[   15.029348] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   15.029989] rtlwifi: wireless switch is on
[   15.085700] rtl8192cu: MAC auto ON okay!
[   15.120903] rtl8192cu: Tx queue select: 0x05
dccmgb@ubuntu:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

dccmgb@ubuntu:~$

---

### Post by chili555 on 2013-01-28
Can you please get a temporary wired ethernet connection and do:```
sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
```That will install a new and, hopefully more stable rtl8192cu. Reboot and let us have your report.

---

### Post by dccmgb on 2013-01-28
I completed the command, rebooted, but the adapter is still timing out after a few minutes.

---

### Post by chili555 on 2013-01-29
> **dccmgb said:**
> I completed the command, rebooted, but the adapter is still timing out after a few minutes.Let's try a temporary driver parameter:```
sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu swenc=1
```If it helps, we'll write one file and make it persistent.

---

### Post by dccmgb on 2013-01-29
I keyed in the commands you requested, restarted, and the wireless network worked about 5 minutes then disconnected.  I did chat with ASUS this morning and they said this USB-N13 is not supported in Ubuntu 12.10 even though it is realtek 8192cu.

Let me know if any other suggestions.  Also, can you direct me to where I can find which wireless adapter will work with 12.10?

---

### Post by chili555 on 2013-01-29
> I keyed in the commands you requested, [COLOR="Red"]restarted[/COLOR], and the wireless network worked about 5 minutes then disconnected.Please try without restarting. As I said, this is a temporary parameter; in this instance, 'temporary' means 'disolves on restart.'

---

### Post by dccmgb on 2013-01-29
Thanks.  This seems to have worked, the adapter connect by itself after I keyed in that second command.  After that, there were a couple of times it looked as if it might disconnect but stayed online.  Let me run this for a couple of hours to be sure.  

What did these command change?

---

### Post by chili555 on 2013-01-29
It sets the driver to use software encryption (WPA, WPA2, WEP, etc.) rather than hardware. Sometimes one works better than the other, as here.

If you'd like to make it permanent, please do:```
gksudo gedit /etc/modprobe.d/rtl8192cu.conf
```Add a single line:```
options rtl8192cu swenc=1
```Proofread, save and close gedit.

---

### Post by dccmgb on 2013-01-29
Thanks so much.  Is there any security risk using software encryption versus hardware once I make this change permanent?  One of the reasons I am moving to Ubuntu is for its better network security environment.  

Also, is there a router setting that would have possibly solved this?

---

### Post by dccmgb on 2013-01-29
The gedit brought up a blank page.  Am I supposed to type that single line on that blank page and then save it?

I thought maybe I would see the entire conf file?

---

### Post by dccmgb on 2013-01-29
Sorry I just timed out again on the wireless.  does the temporary command only last so long?  I noticed when I first checked about 1/2 hour ago that it time out also but I thought maybe because I had to log back in.  

I don't mean to be taking all your time.  Perhaps you can point me to an approved adapter list for 12.10 if that is a better route to go.

---

### Post by chili555 on 2013-01-29
> Is there any security risk using software encryption versus hardware once I make this change permanent? None that I am aware of.> The gedit brought up a blank page. Am I supposed to type that single line on that blank page and then save it?Yes.> I thought maybe I would see the entire conf file? There is none until you create it.

Please try the conf file and reboot before you give up.

---

### Post by dccmgb on 2013-01-29
I made the change, rebooted, but the network still times out.  How would I check to ensure the change was made correctly, so that swenc=1?

---

### Post by chili555 on 2013-01-30
Is your conf file correct?```
cat /etc/modprobe.d/rtl8192cu.conf
```What does this tell us?```
cat /sys/module/rtl8192cu/parameters/swenc
```As an interesting point, I modprobbed the parameter on my own system and got:> chili@Think410:~$ cat /sys/module/rtl8192cu/parameters/swenc
N
N I assume represents NO and suggests the parameter is boolean; that is Y or N rather than an integer; 0 or 1. Modinfo says:```
~$ modinfo rtl8192cu 
filename:       /lib/modules/3.5.0-22-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
srcversion:     1FCC18D8443E2E6299DC139
<snip>
[COLOR="Red"]parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)[/COLOR]
parm:           debug:Set debug level (0-5) (default 0) (int)
```There certainly is a conflict between these statements: Set to 1 for software crypto (default 0) AND: (bool).

After you check the parameter as I've suggested above and if it still doesn't work, please edit the file again to read:```
options rtl8192cu swenc=Y
```Proofread, save and close the text editor and reboot.

Any improvement?

---

### Post by dccmgb on 2013-01-30
The first question yielded:  swenc=1
The second question yielded:  Y
I then made a temporary change (via your previous instructions) to change swenc=Y.  It took the change, I then did a modprobe to confirm that swenc=1, but the adapter then timed out again, as before.  So again, it works for about 5 minutes and then drops the signal.

---

### Post by dccmgb on 2013-01-30
FYI, perhaps another clue.  I noticed that when running Windows XP, the wireless adapter always blinks a blue LED and stays connected to the network.  When running under 12.10, the LED stays constant (no blinking) and disconnects in about 5 minutes.

---

### Post by chili555 on 2013-01-30
> The first question yielded: swenc=1I hope you meant: ```
options rtl8192cu swenc=1
```...and that you changed it to:```
options rtl8192cu swenc=Y
```If that's so, then I have no further ideas. I suggest you search this forum for 'working USB adapters' and blacklist rtl8192cu and move on. I'm sorry I could not be of further assistance.

---

### Post by dccmgb on 2013-01-30
After I made the temporary change so that swenc=Y (via [SIZE=3][FONT=Calibri]sudo modprobe -r rtl8192cu and  [/FONT][/SIZE]
[FONT=Calibri][SIZE=3]sudo modprobe rtl8192cu swenc=Y), I[/SIZE][/FONT] then did a modprobe rtl8192cu which showed swenc=1.  Are you saying it should have showed swenc=Y after the temporary change?

---

### Post by dccmgb on 2013-01-30
also, would the ufw affect this in any way?  I turned it off this afternoon but the adapter still timed out.

---

### Post by chili555 on 2013-01-30
> **dccmgb said:**
> After I made the temporary change so that swenc=Y (via [SIZE=3][FONT=Calibri]sudo modprobe -r rtl8192cu and  [/FONT][/SIZE]
[FONT=Calibri][SIZE=3]sudo modprobe rtl8192cu swenc=Y), I[/SIZE][/FONT] then did a modprobe rtl8192cu which showed swenc=1.  Are you saying it should have showed swenc=Y after the temporary change?After a temporary change, this should be the result:```
$cat /sys/module/rtl8192cu/parameters/swenc
Y
```To make 'Y' the default, change this:```
gksudo gedit /etc/modprobe.d/rtl8192cu.conf
```...to this:```
options rtl8192cu swenc=Y
```> also, would the ufw affect this in any way?Not at all.

---

### Post by dccmgb on 2013-01-31
I made the changes permanent as you recommended, then confirmed the change was made to "Y", but the adapter still dropped the signal.  At one time it held for about 2 hours but then dropped.  And still only ever had a steady blue LED versus a blinking LED (as it works under XP)
 
Two more things.  I cannot find any recommended adapters for 12.10, but maybe not looking in the right places.  Do you know of any?  Second, is ndiswrapper still an option, so to use the Windows version of the driver?
 
Thanks so much for your help, you have been very gracious with your time.

---

