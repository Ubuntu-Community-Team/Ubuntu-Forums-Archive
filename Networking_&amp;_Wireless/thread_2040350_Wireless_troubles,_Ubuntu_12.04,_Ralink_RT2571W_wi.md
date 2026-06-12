---
title: "Wireless troubles, Ubuntu 12.04, Ralink RT2571W wireless card, HP Pavilion m9040n"
date: 2012-08-10
forum: Networking &amp; Wireless
---

### Post by aqualung347 on 2012-08-10
Hello everyone, I would be grateful for some help. I'm a newcomer to Ubuntu, coming from Windows. I've searched on the forums and haven't really found anything, but since I'm unfamiliar with the lingo, I didn't understand everything I was seeing.

So here is my problem (which is more of an annoyance than a catastrophe): my wireless card connects to the internet, but sometimes after a while it will drastically slow down or stop working completely. At the same time, when I click on the wireless icon at the top right of the screen, it still says it is connected to the network. If I try to restart the computer, it tends to get stuck on the shutting down screen, and I end up having to do a hard reboot. But once it does reboot, the network is working again. 

Information about my system:
HP Pavilion m9040n (HP lists the components here: [http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c01154933](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c01154933))
Dual-booting Ubuntu 12.04 LTS and Windows 7
Wireless card:  Gemtek WUBR-177G [Ralink RT2571W]
As far as I can tell, the driver is rt73usb
Results of $ iwconfig:
> wlan0     IEEE 802.11bg  ESSID:"36PA3"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:19:DE:1B:B4   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:490  Invalid misc:356   Missed beacon:0Results of $ lsmod:
> Module                  Size  Used by
vesafb                 13844  1 
arc4                   12529  2 
snd_hda_codec_hdmi     32474  4 
nvidia              12336440  40 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
snd_hda_codec_realtek   223962  1 
rt73usb                31735  0 
rt2x00usb              20762  1 rt73usb
rt2x00lib              51144  2 rt73usb,rt2x00usb
mac80211              506816  2 rt2x00usb,rt2x00lib
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
cfg80211              205544  2 rt2x00lib,mac80211
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13211  0 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  2 rt73usb,firewire_core
e1000e                156693  0 Network configuration:
> *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:6
       logical name: wlan0
       serial: 00:c0:a8:ff:12:a3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=3.2.0-27-generic firmware=1.7 ip=192.168.1.7 link=yes multicast=yes wireless=IEEE 802.11bgResult of $ iwlist scan:
> wlan0     Scan completed :
          Cell 01 - Address: 00:1D:19:DE:1B:B4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"36PA3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001f7535895
                    Extra: Last beacon: 20400ms ago
                    IE: Unknown: 00053336504133
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C> ~$ uname -mr
3.2.0-27-generic x86_64>  sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] Anyone have an idea what might be going wrong? Does my description of the problem make sense?

---

### Post by chili555 on 2012-08-11
> As far as I can tell, the driver is rt73usbCorrect.> Does my description of the problem make sense? Perfectly. I suspect most of your problem is here:> wlan0 IEEE 802.11bg ESSID:"36PA3"
Mode:Managed Frequency:2.412 GHz Access Point: 00:1D:19:DE:1B:B4
Bit Rate=48 Mb/s Tx-Power=20 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:on
[COLOR="Red"]Link Quality=38/70[/COLOR] Signal level=-72 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:490 Invalid misc:356 Missed beacon:0 I suggest you do anything you can to get the signal quality improved. Rearrange the antenna(s) on the router; try channels 1 or 11. See if there is a power setting in the administration pages of the router. Can it be moved to a higher level?

We might try two things temporarily. These will disappear on reboot but can be made persistent if they help. Please open a terminal and do:```
sudo iwconfig wlan0 power off
```Any improvement? Also try:```
sudo modprobe -r rt73usb
sudo modprobe rt73usb nohwcrypt=Y
```Now is there any improvement?

---

### Post by aqualung347 on 2012-08-12
Thanks for the help, Chili. I'm going to see what I can do to boost the signal. Step one is finding out the username and password for the router--I have permission to use the network, but it doesn't belong to me. The terminal commands you gave me were some help, though. 

```
 sudo iwconfig wlan0 power off
```I let it run for 12 minutes with no result, then closed the terminal.

```
 sudo modprobe -r rt73usb
sudo modprobe rt73usb nohwcrypt=Y
```This shut off the connection, and then had it working again. Good enough for now.

I'm also interested in learning about terminal commands. Am I right in thinking that the last two lines remove the driver from the kernel, then load it again without hardware encryption?

---

### Post by chili555 on 2012-08-13
> I let it run for 12 minutes with no result, then closed the terminal.It isn't really a command that 'runs.' It turns off power management which sometimes makes instability in wireless drivers. If it had no effect, then we can skip it.>  Am I right in thinking that the last two lines remove the driver from the kernel, then load it again without hardware encryption? Correct. Sometimes hardware encryption works better and sometimes software, as you have seen. We need to write a conf file to make it persistent.```
sudo gedit /etc/modprobe.d/rt73usb.conf
```Use leafpad, kate, vim or any other text editor if you don't have gedit. Add one single line to the new empty file:```
options rt73usb nohwcrypt=Y
```Proofread, save and close gedit. You should be all set.

Learn more about available driver parameters with:```
modinfo rt73usb
```In this case it is the *only* parameter available to manipulate.

---

