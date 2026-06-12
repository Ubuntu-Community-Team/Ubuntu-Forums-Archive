---
title: "HP g60 wireless issue"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by baldy4eva on 2010-10-24
I have an HP g60 running a vanilla Maverick installation, and the wifi  has cease working. I've tried booting while pressing the switch and  various other combinations of switch presses, but nothing is seeming to  work. 

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
```Any help would be much appreciated

---

### Post by baldy4eva on 2010-10-24
Just need to add that I was getting a n output of  **udevd-work [???] open /dev/null** during boot a couple of times before the wireless gave up. The question marks were 3 different numbers each time. Since the wireless has stopped working, I'm not seeing this.

---

### Post by chili555 on 2010-10-24
Does the wireless switch turn the LED on and off? Is the module hp-wmi loaded?```
lsmod | grep wmi
```May I see your dmesg, please?```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```You will find a file dmesg.zip in your home directory; please attach it to your reply using the little paper-clip above the reply text box.

Please see attached.

---

### Post by baldy4eva on 2010-10-24
The LED is built into the button. During boot, it's Orange, and once I reach login, it turns Blue. pressing the button doesn't change the colour or seem to  affect it in any way.

```
 ~$ lsmod | grep wmi
snd_rawmidi            22207  2 snd_usbmidi_lib,snd_seq_midi
hp_wmi                  6435  0 
snd_seq_device          6912  3 snd_seq_midi,snd_seq,snd_rawmidi
snd                    64117  18 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_seq,snd_rawmidi,snd_timer,snd_seq_device

```
Looks like the hp-wmi isn't being loaded 


Please find dmesg.zip attached as requested and, thanks

---

### Post by chili555 on 2010-10-24
I don't see anything obviously amiss in your *dmesg*. Let's see if removing hp_wmi has any effect:```
rfkill list all
sudo rmmod -f hp_wmi
rfkill list all
```Thanks.

---

### Post by baldy4eva on 2010-10-24
output after a reboot is ```
$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
```But even after that, wireless is greyed out in network manager. Tried holding the button on a reboot too :confused:

---

### Post by chili555 on 2010-10-24
> phy0: Wireless LAN
    Soft blocked: yes
Is there any change if you do:```
sudo rfkill unblock all
rfkill list all
```I am a bit low on ideas.

---

### Post by baldy4eva on 2010-10-24
> **chili555 said:**
> Is there any change if you do:```
sudo rfkill unblock all
rfkill list all
```I am a bit low on ideas.
  Not really. Each time I reboot, the wireless card is blocked again. I've tried holding the wifi button on each reboot, but still, hp-wmi loads. It doesn't help that the wifi button is just a little press button with integrated LEDs.
I do seem to remember that when running Windows, the led glowed Blue when connected, orange when disconnected. In Ubuntu, It was orange when connected and blue when disconnected. So it's swapped over. Now it just sits there and glows blue at me... MIffed!

---

### Post by chili555 on 2010-10-24
I guess I do not understand clearly. Why are you holding down the wireless button as you boot? Did you read somewhere that it fixes your problem?

Did or did it not change the state of rfkill when you manually removed hp_wmi?```
sudo rmmod -f hp_wmi
```If it did, we can blacklist hp_wmi; however, it won't help anything if we don't know what, if anything, it fixes.

Once again, does it or does it not help to do:```
sudo rmmod -f hp_wmi
```Does it or does it not help to do:```
sudo rfkill unblock all
rfkill list all
```

---

### Post by baldy4eva on 2010-10-24
> **chili555 said:**
> I guess I do not understand clearly. Why are you holding down the wireless button as you boot? Did you read somewhere that it fixes your problem? 
I'd read in another thread that it may be the cause. Someone mentioned that they had to power down their wifi before turning their system off to ensure that it would be found on the next reboot. Doesn't seem to achieve anything on mine, so I guess I'll give up on that one

> **chili555 said:**
> Did or did it not change the state of rfkill when you manually removed hp_wmi?```
sudo rmmod -f hp_wmi
```If it did, we can blacklist hp_wmi; however, it won't help anything if we don't know what, if anything, it fixes.
Yes, when I input ```
sudo rmmod -f hp_wmi
``` and input ```
rfkill list all
``` it now reads```
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```> **chili555 said:**
> Once again, does it or does it not help to do:```
sudo rmmod -f hp_wmi
```Does it or does it not help to do:```
sudo rfkill unblock all
rfkill list all
```
When I run this, Network Manager is showing wireless enabled, but it is not showing any available networks. I've tried adding a network manually, but again, it didn't work. 

I've also tried running a Live distro of Maverick, just to see if wireless was available... It wasn't. As I recall, when I set up Maverick on this laptop, wireless was working and I installed all the updates during the process.

---

### Post by chili555 on 2010-10-25
Please do:```
sudo su
echo "blacklist hp_wmi" >> /etc/modprobe.d/blacklist.conf
gedit /etc/rc.local
```Add a new line right above the line 'Exit 0':```
rfkill unblock all
```Now reboot and do not press the button. Is the LED orange or blue? When you click the Network Manager icon, do you see networks? What is the result of:```
sudo iwlist scan
```Thanks.

---

### Post by baldy4eva on 2010-10-25
Done as you suggested. The button is still blue and Network Manager is showing Wireless as Disconnected.  I' getting ```
[FONT=monospace]sudo iwlist scan 

[/FONT]lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```

---

### Post by chili555 on 2010-10-25
We have a wireless interface, wlan0! According to your *dmesg*, no interface was created previously, so we are making some progress. Please post:```
dmesg | grep -e ath5k -e wlan
```Thanks.

---

### Post by baldy4eva on 2010-10-25
Yeah, things are looking up! :D Not tried connecting yet, as it should detect my network straight away, right?

```
$ dmesg | grep -e ath5k -e wlan
[   14.121750] ath5k 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[   14.121764] ath5k 0000:07:00.0: setting latency timer to 64
[   14.121823] ath5k 0000:07:00.0: registered as 'phy0'
[   14.829861] Registered led device: ath5k-phy0::rx
[   14.829887] Registered led device: ath5k-phy0::tx
[   14.829891] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   15.134087] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by chili555 on 2010-10-25
Are you connected with an ethernet cable? Network Manager will disable the wireless in preference to wired: [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has been managed for themPlease detach the cable, wait a few moments for NM to notice the change in state and click the NM icon. Do you see your network?

---

### Post by baldy4eva on 2010-10-25
Success!! My home network was detected straight away, and the light remained blue. After a reboot with the network cable detached, I got the Wireless Networks Available pop-up! Password entered, and now using wire less..

Thanks for all your help Chili :D I'll mark this thread as solved :D

---

### Post by chili555 on 2010-10-25
Woo hoo! Glad it's working. I suspect we have helped a few searchers, too.

---

### Post by bford16 on 2010-10-25
I have a similar problem on my HP dv7-1232NR.  The machine has an Atheros wifi card, and it usually works fine.  But now and then the wifi will suddenly become disabled.

Supposedly touching the wifi LED will enable/disable wifi, but this has never worked for me.  I suspect there is a key combination that does this, but I have been unable to find it.  Last night, after reading several different forums, I realized that "rfkill list" was showing 2 wifi cards!```
hp_wifi
soft blocked: no
hard blocked: no

phy0
soft blocked: no
hard blocked: yes
```
After some detective work, I realized that "hp_wifi" was provided by "hp_wmi."  So I did this:```
sudo modprobe -r -f hp_wmi
sudo modprobe -r -f ath5k
```Then restarted the laptop.  The wifi came up immediately and works as desired.  I did not blacklist hp_wmi; I don't think it was the culprit.  I think what happened was that I somehow accidentally triggered the hardware killswitch by some unknown key combination.  I will try to find evidence to back up my theory, and repost to this thread.

---

### Post by baldy4eva on 2010-10-25
Update: Well the wifi is now working, but after a reboot (I had to go to the shop.. lol), Network manager is not finding my network :s... I might try the ```
 sudo modprobe -r -f ath5k
``` to see if it helps. Failing that I'll have a look on the other threads.

---

### Post by bford16 on 2010-10-25
UPDATE:

I found the key combination to turn wireless on and off (for my dv7-1232NR).  Here's what i did.

I switched to a tty (using Ctrl+Alt+F4).  I ran ```
showkey -k
``` With showkey running, I tapped the wireless button. Nothing happened; showkey did not display any data. Then I pressed the Quickplay button (looks like a letter Q next to the Power button).  That turned the wireless off!  Showkey said```
keycode 46 press
keycode 46 release
```Unfortunately pressing the Quickplay button by itself did not turn the wireless back on.  But when I held my finger on the wireless button, and pressed the Quickplay button, the wireless did in fact come back on.  Success!!

---

### Post by baldy4eva on 2010-10-25
Well... I don't know what I did, but it's working again! I followed your [ctrl]+[alt]+[F4] tip and entered ~showkey -k as you suggested.  I just kept pressing the wireless button (no Quickkey on a G60)... Then the button turned orange! Sorted again! Back onto my wireless and happy once more! :D

...Until a reboot! Ooops! :s

---

### Post by bford16 on 2010-10-26
> **baldy4eva said:**
> Well... I don't know what I did, but it's working again! I followed your [ctrl]+[alt]+[F4] tip and entered ~showkey -k as you suggested.  I just kept pressing the wireless button (no Quickkey on a G60)... Then the button turned orange! Sorted again! Back onto my wireless and happy once more! :D

...Until a reboot! Ooops! :s

Did showkey give you any output when you touched the wireless button?

---

### Post by baldy4eva on 2010-10-26
No... No output on showkey -k. Guess I'll just read through this thread again to get it going.

---

### Post by mdhunn on 2010-10-26
> **chili555 said:**
> Please do:```
sudo su
echo "blacklist hp_wmi" >> /etc/modprobe.d/blacklist.conf
gedit /etc/rc.local
```Add a new line right above the line 'Exit 0':```
rfkill unblock all
```Now reboot and do not press the button. Is the LED orange or blue? When you click the Network Manager icon, do you see networks? What is the result of:```
sudo iwlist scan
```Thanks.

Thanks, I was pulling my hair out trying to figure out what got corrupted.

What worked for me was blacklisting hp_whi and adding ath9k to /etc/modules.  I had to do that when my laptop was new.
I'm not sure where ath5k came from, I've allways used ath9k, I don't know if ath5k supports both bands (2 and 5 Ghz) that my g60's card supports

---

### Post by chili555 on 2010-10-26
> I'm not sure where ath5k came fromIt's from baldy4eva's dmesg.zip. See his previous posts.

---

### Post by whitneybdy on 2011-02-24
I was directed here because of an issue that I origionally tried to trouble shoot on [this post]("https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/146402").

Having tried both methods, I am still unable to connect.

Should I attempt to just reinstall the driver?

Thanks.

---

### Post by chili555 on 2011-02-24
> **whitneybdy said:**
> I was directed here because of an issue that I origionally tried to trouble shoot on [this post]("https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/146402").

Having tried both methods, I am still unable to connect.

Should I attempt to just reinstall the driver?

Thanks.I noticed in your posts that your ethernet is connected and you have an IP address. Network Manager is designed to disallow a wireless connection if you have wired. Please detach the ethernet cable, wait a few moments for NM to notice the change in state and run and post:```
rfkill list all
sudo rfkill unblock all
rfkill list all
sudo iwlist wlan0 scan
```Is yours an HP laptop as the previous posters?

---

### Post by onetimivan on 2011-07-24
Thanx a lot, solved in a sec.:D

---

