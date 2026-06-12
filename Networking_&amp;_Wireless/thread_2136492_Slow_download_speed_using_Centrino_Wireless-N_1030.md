---
title: "Slow download speed using Centrino Wireless-N 1030 with Ubuntu 12.04"
date: 2013-04-17
forum: Networking &amp; Wireless
---

### Post by SEKarlos on 2013-04-17
Hi,

Hopefully someone can help an absolute beginner!

I'm not able to receive a download speed of more than 56 KB/s using Ubuntu Release 12.04 (precise) 32-bit, Kernel Linux 3.2.0-41-generic-pae with the Intel Centrino Wireless-N 1030 interface on a Dell XPS L502X laptop. The broadband tariff is unlimited and I'm experiencing this slow speed with the laptop connected to the mains so power management shouldn't be throttling the speed.
 
When I ran the diagnostic for my router it tells me it's downloading up to 511 KB/s.

If I'm running Windows 8 free trail version (both OS are running on same laptop) I'm able to receive roughly 511 KB/s and if I tether the laptop to my mobile i can download over 511 KB/s, using wi fi in each instance. 

Would really appreciate knowing how to solve the slow download speed issue cause compared to windoze this OS rocks!!!


Thanks

SE

---

### Post by wildmanne39 on 2013-04-17
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by DuckHook on 2013-04-17
Hi SEKarlos and welcome to the forum community and to Ubuntu/Linux.

Would like you to open a terminal and do:```
iwconfig | grep -A6 Bit
``````
lsmod | grep iwlwifi
```...that's the letter 'l' in *iwlwifi* and not the number "1'. Also, case matters in Linux. Probably best to copy and paste my code into your terminal to forestall typos. Please post output back to this thread. We are trying to see quality of your connection and if you are using the *iwlwifi* driver, which has been known to cause some problems. If this is your driver, you may have a problem similar to [this]("http://ubuntuforums.org/showthread.php?t=2126715") one, for which we could try [this]("http://ubuntuforums.org/showthread.php?t=2126715&page=3&p=12568035#post12568035") solution. But before jumping the gun, just post back the output of above command first. Do **NOT**, repeat, do **NOT** implement the linked solutions until we ascertain your driver and do further tests. You could render Ubuntu WIFI completely inoperative with the wrong solution so must tread carefully.

:)Beaten to the punch by Wild Man again!

@OP

Always follow Wild Man's instructions first. True guru, that Wild Man.

---

### Post by SEKarlos on 2013-04-17
Hi,

Thanks for trying to resolve, really appreciate it.

Please find the file attached (had to compress it as was told to large to email).

Rgds

---

### Post by SEKarlos on 2013-04-17
@ Duck Hook

Please see below the outputs from the commands you asked me to enter

ubuntu@ubuntu-Dell-System-XPS-L502X:~$ iwconfig | grep -A6 Bit
lo        no wireless extensions.


wwan0     no wireless extensions.


eth0      no wireless extensions.


          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:913   Missed beacon:0


ubuntu@ubuntu-Dell-System-XPS-L502X:~$ lsmod | grep iwlwifi
iwlwifi               366509  0 
mac80211              436493  1 iwlwifi
cfg80211              178877  2 iwlwifi,mac80211



Thanks for you assitance.

---

### Post by wildmanne39 on 2013-04-17
Please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

Also linux drivers work better if you can change your router encryption to wpa2 only if you have that option.

Try channel 1 or 11 after you run the above commands.

You have several networks in your area this creates a nightmare for network manger.
Thanks

---

### Post by DuckHook on 2013-04-17
> **SEKarlos said:**
> ...Thanks for you assitance.

Wild Man is way ahead...

> **Wild Man said:**
> Please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

Also linux drivers work better if you can change your router encryption to wpa2 only if you have that option.

Try channel 1 or 11 after you run the above commands.

You have several networks in your area this creates a nightmare for network manger.
Thanks

...See what I mean?

After implementing his solution, be sure to tell us how it goes.):P

---

### Post by SEKarlos on 2013-04-17
Hi Wild Man,

Thanks for sending the help.

I assumed you intended for me to copy and paste all the code in one go? I did and got the following response: options iwlwifi 11n_disable=1

However, my wifi then disconnected and will not reconnect, I can no longer switch wi fi on (i'm now connected via ethernet cable)!

Did i execute the code incorrectly? 


Rgds

---

### Post by wildmanne39 on 2013-04-17
You need to copy and paste the code one line at a time.
Thanks

---

### Post by SEKarlos on 2013-04-18
Hi Wild Man,

I entered each line one at a time (please see below for details of terminal entries and outputs), but she's still only giving me 56 KB/s unfortunately. For the router I changed to channel 11 and selected  '[COLOR=#000000][FONT=Arial]WPA2-PSK(Wi-Fi Protected Access 2 with Pre-Shared Key)'.

I did notice though that when connected by ethernet the max  download speed is also 56 KB/s, does this suggest it is an issue other than wi fi ? 
[/FONT][/COLOR]










ubuntu@ubuntu-Dell-System-XPS-L502X:~$ echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
[sudo] password for ubuntu: 
options iwlwifi 11n_disable=1
ubuntu@ubuntu-Dell-System-XPS-L502X:~$ sudo modprobe -rfv iwlwifi
rmmod /lib/modules/3.2.0-41-generic-pae/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
rmmod /lib/modules/3.2.0-41-generic-pae/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-41-generic-pae/kernel/net/wireless/cfg80211.ko
ubuntu@ubuntu-Dell-System-XPS-L502X:~$ sudo modprobe -v iwlwifi
insmod /lib/modules/3.2.0-41-generic-pae/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-41-generic-pae/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-41-generic-pae/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 11n_disable=1 11n_disable=1
ubuntu@ubuntu-Dell-System-XPS-L502X:~$

---

### Post by DuckHook on 2013-04-18
I am confident that Wild Man will help you get your wireless working properly sooner or later. However, your airwaves are chock full of WIFI signals competing for the same bandwidth. Do you live/work in a heavily built-up residential/commercial area? You may have to try finding the least congested channel to get the best Rx/Tx throughput.

After you get your own WIFI working again, I recommend downloading and using *wavemon* to look at the WIFI environment around you:```
sudo apt-get install wavemon
```*wavemon* has to be started with root privileges to scan, so:```
sudo wavemon
```...press <F3> to scan. This will give you a graphical real-time look at the competing networks around you, their channels and their strengths. Find a channel with a combination of the least users and the least competing strengths, and set your router to that channel (remember to save, apply and reboot your router). If your laptop does not see it, reboot your laptop. Again, this is for after you have resolved your current WIFI issue.

---

### Post by wildmanne39 on 2013-04-18
Hi, when you  use the wireless you do need to have your ethernet unplugged, and your ethernet is using the wrong driver that is why it is so slow, but I do not do ethernet much so it is not my forte.

Please post the content of:
```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```
Also set your wireless settings to match the screnshots.

---

### Post by SEKarlos on 2013-04-18
Think it's important to mention that I was able to get download speeds of way over 511 KB/s using Ubuntu tethered via wi fi to my mobile phone, which is making me think there's an issue with the Router!

---

### Post by wildmanne39 on 2013-04-18
Thats because it is not using the wireless driver that has problems with wifi connections.
Please do the last thing that I asked with wired connection unplugged and let us know if it helped.
Thanks

---

### Post by SEKarlos on 2013-04-18
HI Wild Man,

I've changed the ipv4 and ipv6 settings as advised. 

The content of the [COLOR=#000000][FONT=Ubuntu Mono]iwlwifi.conf file is:

[/FONT][/COLOR]options iwlwifi 11n_disable=1


Thanks

SE

---

### Post by wildmanne39 on 2013-04-18
Did you also change the dns sever to match the other screenshot?

Has it helped?
Thanks

---

### Post by SEKarlos on 2013-04-18
Hi Wild Man,

Yes, i changed the DNS Server to be 8.8.8.8, 8.8.4.4 for the IPv4 settings. It hasn't resolved the issue unfortunately, still not able to download more than 56 KB/s.

Do you have any other suggestions ? Really appreciate your assistance with this by the way.


Rgds

SE

---

### Post by SEKarlos on 2013-04-18
I did stumble across this information from intel regarding wireless drivers for Linux

[https://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&lang=eng&OSVersion=Linux*&DownloadType=Drivers](https://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&lang=eng&OSVersion=Linux*&DownloadType=Drivers)

The instructions for downloading the the driver are rather complex and I'm reluctant to embark on a path which may make the problem worse, I've only recently crossed the border into Linux world and it's all very unfamiliar!

---

### Post by wildmanne39 on 2013-04-18
We may have to try a new driver but not yet.

Please post the output of:
```
modinfo iwlwifi
```
Thanks

---

### Post by SEKarlos on 2013-04-18
Hope it sheds some light, here you go....

ubuntu@ubuntu-Dell-System-XPS-L502X:~$ modinfo iwlwifi
filename:       /lib/modules/3.2.0-41-generic-pae/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
alias:          iwlagn
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
srcversion:     99F715B156678F68AE86AC4
alias:          pci:v00008086d00000892sv*sd00000466bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000266bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000066bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000426bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000226bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000026bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004466bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004266bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004066bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004464bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004264bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004064bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004466bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004266bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004066bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004822bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004426bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004226bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004026bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001341bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.2.0-41-generic-pae SMP mod_unload modversions 686 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           ack_check:Check ack health (default: 0 [disabled]) (bool)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool)
parm:           no_sleep_autoadjust:don't automatically adjust sleep level according to maximum network latency (default: true) (bool)
ubuntu@ubuntu-Dell-System-XPS-L502X:~$

---

### Post by wildmanne39 on 2013-04-18
Hi, please post the output of:
```

dmesg | grep -e wlan -e iwl

```
How what did you use to determine the connection speed is 56k?
Thanks

---

### Post by SEKarlos on 2013-04-18
Hi,

I'm referring to the System Monitor / Resources Tab , Network History section. 

I have attached a document displaying a screen shot.

---

### Post by SEKarlos on 2013-04-18
Output from [COLOR=#000000][FONT=Ubuntu Mono]dmesg | grep -e wlan -e iwl


[/FONT][/COLOR]ubuntu@ubuntu-Dell-System-XPS-L502X:~$ dmesg | grep -e wlan -e iwl
[   13.645739] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.645779] iwlwifi 0000:03:00.0: setting latency timer to 64
[   13.645835] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   13.645837] iwlwifi 0000:03:00.0: pci_resource_base = f8540000
[   13.645839] iwlwifi 0000:03:00.0: HW Revision ID = 0x34
[   13.646158] iwlwifi 0000:03:00.0: irq 49 for MSI/MSI-X
[   13.646289] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[   13.647542] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   13.664455] iwlwifi 0000:03:00.0: device EEPROM VER=0x716, CALIB=0x6
[   13.664458] iwlwifi 0000:03:00.0: Device SKU: 0X150
[   13.664460] iwlwifi 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   13.729702] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   13.983442] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
[   13.985679] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.410963] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   14.417688] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[   14.514905] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   14.521685] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[   14.618201] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.104181] wlan0: authenticate with 00:1f:33:1a:cf:84 (try 1)
[   17.106686] wlan0: authenticated
[   17.126974] wlan0: associate with 00:1f:33:1a:cf:84 (try 1)
[   17.130542] wlan0: RX AssocResp from 00:1f:33:1a:cf:84 (capab=0x431 status=0 aid=1)
[   17.130547] wlan0: associated
[   17.141154] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[19752.680833] wlan0: deauthenticating from 00:1f:33:1a:cf:84 by local choice (reason=3)
[19757.410413] iwlwifi 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[19757.410541] iwlwifi 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf1b00004)
[19757.410576] iwlwifi 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[19757.410620] iwlwifi 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[19757.411521] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[19761.639053] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[19761.645779] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[19761.762223] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[19764.263412] wlan0: authenticate with 00:1f:33:1a:cf:84 (try 1)
[19764.268182] wlan0: authenticated
[19764.268505] wlan0: associate with 00:1f:33:1a:cf:84 (try 1)
[19764.271174] wlan0: RX AssocResp from 00:1f:33:1a:cf:84 (capab=0x431 status=0 aid=1)
[19764.271178] wlan0: associated
[19764.282537] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
ubuntu@ubuntu-Dell-System-XPS-L502X:~$ ^C
ubuntu@ubuntu-Dell-System-XPS-L502X:~$ 


[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by wildmanne39 on 2013-04-18
I could not see it good enough read it but that will only show the internet speed if it is downloading something I believe while you are looking at it so I recommend typing internet speed test into google and try some of those speed tests.
Thanks

---

### Post by SEKarlos on 2013-04-18
According to [http://www.speedtest.net/](http://www.speedtest.net/)

My Download Speed = 0.43 MB /s.

That equates to 440.32 KB/s, I'm not getting anywhere near that via the wi fi. For example I just streamed a video from BBC News and checked the Ubuntu System Monitor Net Work history while it was streaming. It showed a maximum of 56 KB/s was being downloaded the whole time that video was being streamed. I've included the actual screen shot of that as a .png file so it should be easy to read. I'm assuming the 0.43 MB/s is the download speed to the router itself and not via the Wi Fi ?

Hopefully your not abandoning my cause but understand if this is all becoming annoying for you.


Rgds

SE

---

### Post by wildmanne39 on 2013-04-18
Vidoes are set to stream at a certain rate and that is about right for a video.

The way to tell is internet speed test, if it says it is .43 then that is what it is, you hve to know that the speed changes a some depending on the concestion on the server, try a few more internet speed test sites and see if most of them are in the ball park.
Thanks

---

### Post by SEKarlos on 2013-04-19
Ok, I've subjected the aforementioned wi fi to a few tests using Windows and Ubuntu (Chrome browser used for each, cache cleared before each test).

Each of the following scenarios was timed:

Opened a Flash Animation web page.
Open a web page that displays multiple images.
Download a PDF document.

Supported by either operating system It took roughly the same amount of time to fully display either page or download the pdf.

However, for any of the tests the Ubuntu System Monitor displayed a constant download speed of 56 KB/s whereas the Windows Network monitor displayed a constant download speed of approx 450 KB/s. It was initially this disparity which led me to believe the wi fi supported by Ubuntu was working slower. I can only assume the KB/s displayed in Ubuntu System Monitor is incorrect because the KB/s shown for Windows is in the same Ball Park as the results from independent internet speed tests that were run with Ubuntu.

Sincere apologies Wild Man if you feel you have gone down a blind alley with this but I was misled by the monitor info :oops:


Rgds

SE

---

### Post by chili555 on 2013-04-19
>  I can only assume the KB/s displayed in Ubuntu System Monitor is incorrectI agree. You might try wget:```
wget http://releases.ubuntu.com/precise/ubuntu-12.04.2-desktop-i386.iso
```Check the download speed as in the attached. The speed listed is very close to the maximum that cheap old Chili pays for from his ISP.

Cancel the download by closing the terminal.

---

### Post by SEKarlos on 2013-04-19
Thanks Chilli, I'll give that a try.

I've actually got unlimited broadband supplied free with my Sky package. However I live quite for from the nearest telephone exchange so unfortunately by the time it's reached my pad the bandwidth is poor (that's what they tell me anyhow), only other option is to go with Virgin but it's such a rip off in comparison. They say the old lines will be replaced with fibre optic soon however, can't come soon enough!

---

### Post by SEKarlos on 2013-04-19
Hi Chilli,

I let that run for about 5 minutes and the speed was pretty constant at around 53.1 k/s (yeah k/s not even kb/s :confused:)

Does that seem weird ?

I've attached a screen shot.

---

### Post by chili555 on 2013-04-19
It *does* seem wierd. Have you any way to compare wired ethernet on this or another machine? Please be sure to use *wget* and the same download link.

---

### Post by wildmanne39 on 2013-04-19
Hi chili555, his ethernet is very slow he needs the 8168 and he is using the 8169.
Thanks for helping out I am out of ideas.

---

### Post by chili555 on 2013-04-20
If the ethernet is slow and the wireless is slow, I wonder if it's a driver problem. Could it be a router problem? A firewall problem?```
sudo ufw status
```

---

### Post by SEKarlos on 2013-04-21
Hi Chili,

Here's the return:

ubuntu@ubuntu-Dell-System-XPS-L502X:~$ sudo ufw status
[sudo] password for ubuntu: 
Status: inactive
ubuntu@ubuntu-Dell-System-XPS-L502X:~$ 


What does that tell us?

Also, don't know if it significant but after closing the terminal that download continued from the link you sent!

---

### Post by chili555 on 2013-04-21
> I did notice though that when connected by ethernet the max download speed is also 56 KB/s, does this suggest it is an issue other than wi fi ?
Also:>  Could it be a router problem?I'd go through the router settings with a fine-tooth comb. I'd set everything to defaults except WPA2-PSK and channel 11. Then I'd try again.

Usually, iwlwifi, when 11N is disabled, is fast and reliable. I have a bit more experience with it because I am using it right now. The 5.4 Mb/s download I posted above is from iwlwifi.

It is quite remarkable, in my opinion, that both wireless and ethernet are stuck at 56kb/s.

---

### Post by SEKarlos on 2013-04-21
Hi Chili,

Reset router to factory default and ensured WPA2 option was selected together with Channel 11, still not able to download more than 56 Kib/s (according to System Monitor). Would it help if i sent you a screen grab of the Router settings.

Cheers

---

### Post by chili555 on 2013-04-22
I am very, very low on ideas. In the router, are UPnP and QoS on or off? I suggest disabled for both.

Have you tried a power reset for the router? Unplug it, count to twenty, plug it back in and see if anything is improved or even degraded.

Let's have a look at:```
dmesg | grep 80211
```I will be interested in any CRDA settings.

---

### Post by DuckHook on 2013-04-22
I've no technical knowledge to add, but would like OP to try something...

I don't trust the data being reported by Windows. It is possible that you are getting exactly the same speeds on Windows end, only it is falsely reporting a higher speed. Also possible that Windows is reporting bits per second while Ubuntu is reporting bytes. This would give an apparent difference of 10x on the numerals.

The only sure way I know to compare properly is downloading a large file while timing it. Download identical file in Win and Ubuntu and time with stopwatch (or similar).

It is possible that your max network speed is ~56KB/s and problem is not with Ubuntu at all, but is due to router or ISP.

---

### Post by SEKarlos on 2013-04-29
Hi,

Thanks for the suggestions.

I've done the file download comparison test and it took approx the same amount of time to download the file with either operating system.

Rgds

---

### Post by chili555 on 2013-04-29
> **SEKarlos said:**
> Hi,

Thanks for the suggestions.

I've done the file download comparison test and it took approx the same amount of time to download the file with either operating system.

RgdsSo it is evidently not an Ubuntu problem nor a wireless driver issue, correct?

---

### Post by SEKarlos on 2013-04-29
Hi Chili,

I switched UPnP off as advised, i couldn't find any reference to QoS in the Router settings however!

Here's the output from [COLOR=#000000][FONT=Ubuntu Mono]dmesg | grep 80211[/FONT][/COLOR]

ubuntu@ubuntu-Dell-System-XPS-L502X:~$ dmesg | grep 80211
[   20.362773] cfg80211: Calling CRDA to update world regulatory domain
[   20.571405] cfg80211: World regulatory domain updated:
[   20.571408] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.571411] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.571413] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.571416] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.571418] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.571420] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.623315] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   20.625441] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[31455.702135] cfg80211: All devices are disconnected, going to restore regulatory settings
[31455.702147] cfg80211: Restoring regulatory settings
[31455.702158] cfg80211: Calling CRDA to update world regulatory domain
[31455.711344] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[31455.711347] cfg80211: World regulatory domain updated:
[31455.711348] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[31455.711350] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[31455.711352] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[31455.711353] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[31455.711354] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[31455.711356] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[61768.018957] cfg80211: All devices are disconnected, going to restore regulatory settings
[61768.018969] cfg80211: Restoring regulatory settings
[61768.019009] cfg80211: Calling CRDA to update world regulatory domain
[61768.027058] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[61768.027066] cfg80211: World regulatory domain updated:
[61768.027070] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[61768.027075] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[61768.027080] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[61768.027085] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[61768.027089] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[61768.027094] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[70859.284170] cfg80211: All devices are disconnected, going to restore regulatory settings
[70859.284184] cfg80211: Restoring regulatory settings
[70859.284202] cfg80211: Calling CRDA to update world regulatory domain
[70859.294444] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[70859.294447] cfg80211: World regulatory domain updated:
[70859.294448] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[70859.294449] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[70859.294451] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[70859.294453] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[70859.294454] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[70859.294455] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[80575.717812] cfg80211: All devices are disconnected, going to restore regulatory settings
[80575.717827] cfg80211: Restoring regulatory settings
[80575.717845] cfg80211: Calling CRDA to update world regulatory domain
[80575.728596] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[80575.728606] cfg80211: World regulatory domain updated:
[80575.728610] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[80575.728617] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[80575.728624] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[80575.728630] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[80575.728636] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[80575.728641] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
ubuntu@ubuntu-Dell-System-XPS-L502X:~$

---

### Post by chili555 on 2013-04-29
Looks awesome to me. It looks like you could also turn off N speeds in the router, unless you need it for other devices on the network.> cfg80211: (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

---

### Post by SEKarlos on 2013-04-29
Thanks Chii,

What does '[COLOR=#000000][I]cfg80211: (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)' tell us ?

Interestingly last week i was downloading at 120 Kib/s and this last few days it's dropped to 80 Kib/s.[/I][/COLOR]

---

### Post by SEKarlos on 2013-04-29
Sorry Chili, but what's N speeds? I can't find any reference to that in the router settings.

Thanks

---

### Post by chili555 on 2013-04-29
It tells us that the router and the driver want to use the 5kHz band; i.e. N speeds if possible. N speeds have been very troublesome for the iwlwifi driver for some time. Often, Intel devices will connect but refuse to pass traffic unless N is disabled. 

In my own case, my ancient, stone-age WRT54G with dd-wrt firmware, isn't even capable of N speeds and my iwlwifi device works just perfectly. Of course, I also can't stream high definition video without N, but, in my opinion, a laptop is a pretty poor way to watch a movie. But, hey, that's just me.

End rant.

---

### Post by SEKarlos on 2013-04-29
Thanks Chili,

It's a shame Linux isn't the norm instead Windows (one day maybe!).

Could you let me know how to disable the N speeds please?

---

### Post by SEKarlos on 2013-04-29
Is it the 'g only' setting ?

---

### Post by chili555 on 2013-04-29
In the router, it's probably the B and G only setting. To disable it in the driver, do this: [http://ubuntuforums.org/showthread.php?t=2125952&p=12594190#post12594190](http://ubuntuforums.org/showthread.php?t=2125952&p=12594190#post12594190)

---

### Post by b-harip on 2013-11-28
Thanks to this thread. I followed WildMan's instructions on the first page and my connections are not dropping off anymore.

---

