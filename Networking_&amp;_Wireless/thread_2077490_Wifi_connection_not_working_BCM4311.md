---
title: "Wifi connection not working: BCM4311"
date: 2012-10-28
forum: Networking &amp; Wireless
---

### Post by alyssajesse on 2012-10-28
Hi all,
I bought a secondhand refurbished Dell Latitude d430 laptop yesterday and installed Ubuntu 11.10 onto it. Wifi was working fine on the Windows XP it had installed on it but when I installed ubuntu it was not picking up the connection. I have seen that this is a fairly common problem however I am having difficulties following the instructions on various threads. For some reason, since I started trying various solutions, the laptop is now not picking up internet even when connected directly to the modem. I have another computer here that can use internet so I am able to download anything needed onto a flash drive and install it onto the pc in question if someone is able to talk me through what I need to do. Thanks in advance.

---

### Post by twipley on 2012-10-28
Hello, and welcome to the forums.

Is there any reason for you not to have installed the latest release (12.10)? I have installed it fresh on many computers last week, and I never have had any problem wi-fi-wise.

Make sure also that "install this third-party software" is ticked upon install. Should be working that way from USB flash drive boot. (Otherwise, just press the "try it now" button to proceed without installation for testing purposes.

---

### Post by alyssajesse on 2012-10-28
Hi,
I did not install the most current version as I was given a cd with the 11.10 version on it and uploaded from there. I was meaning to update it once I had installed it. I knew my wifi did not work on Ubuntu but I was initially able to get internet via a wired connection. However now my wired internet connection has stopped working for some reason, and I am unable to update to the newest version. I have tried to uninstall and then reinstall the version that I have because I thought that maybe I had messed around with the network settings in some way when trying to sort out the wifi connections, but my computer still won't pick up internet. I did tick install 3rd party software, but I guess seeing as it wasn't the newest update that doesn't make much difference.

---

### Post by Hadaka on 2012-10-28
Hi, are you able to boot into Ubuntu 11.10?, but just not able to access
the internet?.. * IF you can, then please enter a command so you can be
helped to figure out how to activate your wifi card. To do this...boot into
Ubuntu, then press ctrl/alt/t...this brings up a terminal. Enter the command

```
lspci -nnk | grep -iA3 net
```copy and paste the results back so you may be helped.

thanks

---

### Post by alyssajesse on 2012-10-28
elf@elf-wok:~$ lspci -nnk | grep -iA3 net  
 09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)  
 	Subsystem: Dell Device [1028:0201]  
 	Kernel driver in use: tg3  
 	Kernel modules: tg3  
 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)  
 	Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]  
 	Kernel modules: wl, ssb 



Thanks for helping! Feeling pretty frustrated.

---

### Post by NikTh on 2012-10-29
Hi , 

you will need Internet connection to run bellow commands. 

```
sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo apt-get remove bcmwl-kernel-source
```

Reboot your PC without the Ethernet cable and see if wireless works. 

Thanks

---

### Post by alyssajesse on 2012-10-30
Hey,
Unfortunately, I can not access any form of internet on the laptop in question as for some reason my wired connection stopped working also, although when I initially installed Ubuntu it was working fine via wired. I'm unsure why this has stopped working  - I tried to uninstall and then reinstall the version of Ubuntu I have. I thought that maybe I had messed around with some setting and that if I reinstalled it would go back to that magical time when I had been able to at least get some form of internet, but no luck so far :(
So - although I have come across the solution you have supplied in multiple forums, I am unable to use this myself to fix the problem. 
 If I download the newest Ubuntu onto a dvd, then try and install that onto the laptop could that perhaps fix / make a dent in my problem? I tried to download 12.10 onto a flash drive but it wouldn't boot the computer from it. 
Any questions/comments and help much appreciated! A computer man has quoted me $80 to get all fixed but I want to give it a go myself first - will be much more satisfying and more in the linux spirit.

---

### Post by squakie on 2012-10-30
I just had the same problem and got help that fixed it.  Follow this link:

[http://ubuntuforums.org/showthread.php?t=2077104](http://ubuntuforums.org/showthread.php?t=2077104)

---

### Post by alyssajesse on 2012-10-31
Thanks! I followed that link and now its almost working - it's able to pick up that there is wifi available, however it won't let me connect, and when I restart the computer it can't recognize any wifi until I go through it all again. One of the things I noticed is when I do the following commands that Wild Man posted I get these responses - 
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43 sudo rmmod -f b43
ERROR: Removing 'b43': No such file or directory
sudo rmmod -f ssb
ERROR: Removing 'ssb': No such file or directory
sudo modprobe b43

I got really excited because when I entered the last line, it told me it was able to detect wireless networks and I thought my problems were over.
I forgot tomention, I have now installed the latest Ubuntu (12.10) but still having the same problems.

---

### Post by squakie on 2012-10-31
If the very first time you tried sudo rmmod -f b43 it failed like that, and given what is happening when you boot, you should only need to do the following:

sudo echo b43 >> /etc/modules

note there are spaces between sudo and echo, echo and b43, b43 and >>, and >> and /etc/modules

Also, it is VERY important to be sure there are 2 ">" just as I have shown.  You should be able to just copy the above line and paste it into a terminal.

Then reboot and see what happens.

---

### Post by alyssajesse on 2012-10-31
When I try that, the following comes up -

bash: /etc/modules: Permission denied

---

### Post by squakie on 2012-10-31
Try this instead:


[LIST]
[*]open a terminal window
[*]type:
[/LIST]
gksudo gedit /etc/modules


[LIST]
[*]go to the end of the file and add the following line:
[/LIST]
b43


[LIST]
[*]click save
[*]close the window
[*]reboot
[/LIST]

---

### Post by alyssajesse on 2012-10-31
Done that - now it recognises that there is wifi available without me having to type commands every time I turn on the computer, but it still won't connect :(

---

### Post by NikTh on 2012-10-31
> **alyssajesse said:**
> Done that - now it recognises that there is wifi available without me having to type commands every time I turn on the computer, but it still won't connect :(

Why won't connect ? 

Is this a password (WiFi key) problem ? What is the error message ? 

You can try this code and then reboot to test again 

```
echo 'options b43 nohwcrypt=1' | sudo tee /etc/modprobe.d/b43.conf
```

Thanks

---

### Post by squakie on 2012-10-31
Another thing I have occasionally found is that if you tried to connect once, put in an incorrect passkey/pass phrase, the system remembers this - Try edit connections under the network manager icon.  I normally have people delete the existing connection definition, then try to connect - you'll need to enter the passkey/ pass phrase, so be sure to enter the correct one as recommended by NikTh.

---

### Post by sthitaprajna on 2012-10-31
Hello all,

I have a similar case as alyssajesse. Just installed  Ubuntu 12.10 on my old macbook. I am using another computer to  troubleshoot through. I can't seem to get the driver for my wireless  card to work nor can I hook up to ethernet directly. 

Here is some information from the lspci -nnk | grep -iA3 net code:

 00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
              Subsystem: NVIDIA Corporation Device [10de:cb79]
              Kernel driver in use: forcedeth
              Kernel modules: forcedeth
  --
  03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
              Subsystem: Apple Inc. Device [106b:008d]
              Kernel driver in use: b43-pci-bridge
              Kernel modules: ssb


I  followed a few posts with no success including some from this feed,  totally lost, any information on a direction I can take would be greatly  appreciated. Thanks!

---

### Post by squakie on 2012-10-31
While I appreciate your willingness, please open your own thread.  This thread is about a separate wireless adapter from yours.  In threads, we are trying to help the person who opened the thread.  What you have done, if you don't know, is called thread hijacking, and it is not a polite thing to do.  I see you are new so you probably just didn't know these things.

---

### Post by sthitaprajna on 2012-10-31
10-4 Thanks squakie.

---

### Post by alyssajesse on 2012-11-01
It's definitely not a password problem. I have deleted the existing connection just to make 100% sure and tried again and it is still not working. I have another laptop (the one I am using now) using the wifi I am trying to connect with, so I know the password I have is correct, and that the wifi connection itself is working fine. NikTH - there is no error message as such, it just keeps trying to connect and then eventually times out and a little bubble pops up and says "Wireless Network - Disconnected - you are now offline" I tried the code you suggested and rebooted but it hasn't changed anything, as far as I can tell.

---

### Post by NikTh on 2012-11-01
Are you using Ubuntu (I mean the vanila version) or a flavor like Lubuntu ? 
Maybe the first box that ask for password is for network manager to obtain privileges ? (this happens to Lubuntu). 

What is your protection ? Wep , Wpa2 ? 

Thanks

---

### Post by alyssajesse on 2012-11-01
I am using Ubuntu. The box in which I enter the password says the following - Wireless Network Authentication Required. Authentication required by wireless network. Using WPA/WPA2 as far as I can tell

---

### Post by NikTh on 2012-11-01
Do you have Internet connection ? via Ethernet cable ? If yes then do

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get remove bcmwl-kernel-source
```

reboot and try again. 

Maybe this is a problem with router configuration.. you can access the page and change the protocol from g => to => n => or b+g and try again. 

**Or maybe the password is to small?** 
some routers (mine included) required a password from 8 to 64 characters. If I put a password 6 or 7 characters then is not working. 

Thanks

---

### Post by alyssajesse on 2012-11-01
I can't access any internet on the laptop in question, wired or wireless. In regards to the password being too small for the router - the laptop I am using right now uses the same password and it is fine. the password is 11 characters long.

---

### Post by alyssajesse on 2012-11-01
"Maybe this is a problem with router configuration.. you can access the page and change the protocol from g => to => n => or b+g and try again."

Sorry, I don't understand what you mean by this. I'm completely new to all this, I need step by step detailed instructions if possible.

---

### Post by NikTh on 2012-11-01
If other Laptop(s) work without a problem , then is not a configuration problem in router. We will not change the router's config. 

Are you using network-manager or wicd ? 
Also give the results of these commands 

```
nmcli nm status 
lsmod
lspci -nnk | grep -iA2 net
``` 

You can try to add manual your connection in network-manager . Try bellow
```
gksudo nm-connection-editor
``` 

Add a wireless connection with your ESSID and Password and make sure that "available to all users" and "connect automatically" are selected.

Thanks

---

### Post by alyssajesse on 2012-11-01
Hey, these are the results I get -
  	 	 	 	 	 	   elf@elfwok:~$ nmcli nm status  
 RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN       
 running         connecting      enabled         enabled    enabled         disabled   
 elf@elfwok:~$ lsmod  
 Module                  Size  Used by  
 parport_pc             31968  0  
 ppdev                  12817  0  
 rfcomm                 37276  12  
 arc4                   12473  2  
 bnep                   17707  2  
 joydev                 17161  0  
 coretemp               13168  0  
 snd_hda_codec_idt      59761  1  
 kvm                   357806  0  
 gpio_ich               13159  0  
 ssb_hcd                12749  0  
 dell_wmi               12601  0  
 sparse_keymap          13658  1 dell_wmi  
 b43                   347284  0  
 pcmcia                 39509  0  
 dell_laptop            17161  0  
 dcdbas                 14054  1 dell_laptop  
 mac80211              461161  1 b43  
 microcode              18209  0  
 snd_hda_intel          32515  3  
 snd_hda_codec         111547  2 snd_hda_codec_idt,snd_hda_intel  
 snd_hwdep              13272  1 snd_hda_codec  
 yenta_socket           27095  0  
 pcmcia_rsrc            18191  1 yenta_socket  
 lpc_ich                16925  0  
 psmouse                84843  0  
 pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc  
 snd_pcm                80163  2 snd_hda_intel,snd_hda_codec  
 serio_raw              13031  0  
 btusb                  17950  0  
 bluetooth             183228  22 rfcomm,bnep,btusb  
 mac_hid                13037  0  
 cfg80211              175375  2 b43,mac80211  
 bcma                   34483  1 b43  
 snd_seq_midi           13132  0  
 snd_rawmidi            25382  1 snd_seq_midi  
 wmi                    18590  1 dell_wmi  
 wl                   2442848  0  
 ssb                    50087  2 ssb_hcd,b43  
 snd_seq_midi_event     14475  1 snd_seq_midi  
 snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event  
 snd_timer              24411  2 snd_pcm,snd_seq  
 snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq  
 snd                    61991  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 lib80211               14040  1 wl  
 i915                  457161  3  
 drm_kms_helper         45271  1 i915  
 drm                   230463  4 i915,drm_kms_helper  
 i2c_algo_bit           13197  1 i915  
 video                  18847  1 i915  
 soundcore              14599  1 snd  
 lp                     13299  0  
 snd_page_alloc         14036  2 snd_hda_intel,snd_pcm  
 parport                40753  3 parport_pc,ppdev,lp  
 firewire_ohci          35521  0  
 firewire_core          57492  1 firewire_ohci  
 crc_itu_t              12627  1 firewire_core  
 sdhci_pci              18155  0  
 sdhci                  27830  1 sdhci_pci  
 tg3                   130448  0  
 elf@elfwok:~$ lspci -nnk | grep -iA2 net  
 09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)  
 	Subsystem: Dell Device [1028:0201]  
 	Kernel driver in use: tg3  
 --  
 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)  
 	Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]  
 	Kernel driver in use: b43-pci-bridge  
 elf@elfwok:~$

---

### Post by Hadaka on 2012-11-01
Hi, please verify your settings are correct .

```
click the "systems settings" icon- left side launcher bar
click "Network" icon
click "Wireless"
click "configure" tab...lower right
verify automatic connect is checked
verify correct SSID
verify available to others is checked
click "wireless security"
veriy connection name ..ssid...
verify "connect automatic" is checked
set "security" to Wpa/Wpa2 personal
Verify correct "password"
verify availabe to others is checked
click "save"
boot and try again 
```

if this doenst help..hopefully NickTh can figure it out.

---

### Post by Hadaka on 2012-11-01
@NikTh  i see bcma and wl in the lsmod report....

---

### Post by alyssajesse on 2012-11-02
Thanks for the suggestions Hadaka. Unfortunately that hasn't made a difference. :(

---

### Post by NikTh on 2012-11-02
> **Hadaka said:**
> @NikTh  i see bcma and wl in the lsmod report....

bcma is a depend for b43 driver , but wl is not. Maybe this conflict and causes the problem.

@alyssajesse run this command and reboot 

```
sudo apt-get purge bcmwl-kernel-source
``` 

Then give again the results 

```
lsmod
``` 

Thanks

---

### Post by alyssajesse on 2012-11-02
elf@elfwok:~$ lsmod  
 Module                  Size  Used by  
 nls_iso8859_1          12617  1  
 uas                    17556  0  
 usb_storage            39350  1  
 parport_pc             31968  0  
 rfcomm                 37276  12  
 bnep                   17707  2  
 ppdev                  12817  0  
 arc4                   12473  2  
 joydev                 17161  0  
 snd_hda_codec_idt      59761  1  
 gpio_ich               13159  0  
 coretemp               13168  0  
 kvm                   357806  0  
 dell_wmi               12601  0  
 sparse_keymap          13658  1 dell_wmi  
 snd_hda_intel          32515  3  
 snd_hda_codec         111547  2 snd_hda_codec_idt,snd_hda_intel  
 snd_hwdep              13272  1 snd_hda_codec  
 snd_pcm                80163  2 snd_hda_intel,snd_hda_codec  
 dell_laptop            17161  0  
 dcdbas                 14054  1 dell_laptop  
 pcmcia                 39509  0  
 microcode              18209  0  
 lpc_ich                16925  0  
 psmouse                84843  0  
 snd_seq_midi           13132  0  
 btusb                  17950  0  
 bluetooth             183228  22 rfcomm,bnep,btusb  
 serio_raw              13031  0  
 yenta_socket           27095  0  
 pcmcia_rsrc            18191  1 yenta_socket  
 pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc  
 snd_rawmidi            25382  1 snd_seq_midi  
 b43                   347284  0  
 snd_seq_midi_event     14475  1 snd_seq_midi  
 snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event  
 mac80211              461161  1 b43  
 mac_hid                13037  0  
 ssb_hcd                12749  0  
 cfg80211              175375  2 b43,mac80211  
 snd_timer              24411  2 snd_pcm,snd_seq  
 snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq  
 i915                  457161  3  
 drm_kms_helper         45271  1 i915  
 drm                   230463  4 i915,drm_kms_helper  
 i2c_algo_bit           13197  1 i915  
 snd                    61991  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 wmi                    18590  1 dell_wmi  
 bcma                   34483  1 b43  
 soundcore              14599  1 snd  
 snd_page_alloc         14036  2 snd_hda_intel,snd_pcm  
 video                  18847  1 i915  
 lp                     13299  0  
 parport                40753  3 parport_pc,ppdev,lp  
 firewire_ohci          35521  0  
 firewire_core          57492  1 firewire_ohci  
 sdhci_pci              18155  0  
 sdhci                  27830  1 sdhci_pci  
 crc_itu_t              12627  1 firewire_core  
 ssb                    50087  2 b43,ssb_hcd  
 tg3                   130448  0

---

### Post by NikTh on 2012-11-02
wl (STA driver) seems to removed successfully. 

Still can't you connect ?

---

### Post by Hadaka on 2012-11-02
Hi, reading this thread it looks like you first loaded ubuntu 11.10
and the wired connection was working, then you loaded  12.10
and both the wired and wireless stopped working. Lets take a look
at your current version and also see if the wireless card is seeing any
networks out there.

```
lsb_release -a 
``````
iwlist wlan0 scan 
```you can toggle the wireless on and off with the Fn/F2 key
on a Dell...have you tried that? Be mindful that there is no
light or message when you do this. so, Fn/F2 once=off
Fn/F2 again=on

and...does the windows os still connect to the net?

---

### Post by alyssajesse on 2012-11-02
Hey Hadaka,
In regards to switching the f2/fn key, I had no idea, and I would of laughed ALOT if that had fixed it. However, here is the info you asked for - 

	   elf@elfwok:~$ lsb_release -a  
 No LSB modules are available.  
 Distributor ID:	Ubuntu  
 Description:	Ubuntu 12.10  
 Release:	12.10  
 Codename:	quantal  
 elf@elfwok:~$ iwlist wlan0 scan  
 wlan0     Scan completed :  
           Cell 01 - Address: 00:04:ED:B2:2B:5B  
                     Channel:1  
                     Frequency:2.412 GHz (Channel 1)  
                     Quality=63/70  Signal level=-47 dBm   
                     Encryption key:on  
                     ESSID:"wlan-ap" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s  
                               18 Mb/s; 36 Mb/s; 54 Mb/s  
                     Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s  
                     Mode:Master  
                     Extra:tsf=0000000e7b74ae9d  
                     Extra: Last beacon: 9320ms ago  
                     IE: Unknown: 0007776C616E2D6170  
                     IE: Unknown: 010882848B961224486C  
                     IE: Unknown: 030101 
                     IE: Unknown: 2A0104 
                     IE: Unknown: 32048C98B060  
                     IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000  
                     IE: Unknown: 3D1601050700000000000000000000000000000000000000  
                     IE: Unknown: 3E0100 
                     IE: IEEE 802.11i/WPA2 Version 1  
                         Group Cipher : CCMP  
                         Pairwise Ciphers (1) : CCMP  
                         Authentication Suites (1) : PSK  
                     IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00  
                     IE: Unknown: 0B050C002D127A  
                     IE: Unknown: 7F0101 
                     IE: Unknown: DD07000C4304000000  
                     IE: Unknown: 0706415520010E10  
                     IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000  
                     IE: Unknown: DD1A00904C3401050700000000000000000000000000000000000000

---

### Post by alyssajesse on 2012-11-02
When you say toggle the fn/f2 key does that mean hold them down together push them one after the other?
Also, I am not running windows on the computer in question, I wiped it when I installed Ubuntu because I had a similar problem when I installed Ubuntu on my other laptop and it was easily fixed, so I figured it wasn't going to be a big deal :(

---

### Post by Hadaka on 2012-11-02
Hi, yes the Fn key is "function"
so,,,press the Fnkey..hold...press th F2 key...on/off
release both. Your scan shows the card is seeing a network
but..doesnt want to connect...odd problem. Lets see if both
the wired and wireless cards are driver loaded.

```
dmesg | grep -E 'b43|tg3' 
```

thanks

---

### Post by Hadaka on 2012-11-02
Here is another, grasping at straws idea, i read a recent post
that 12.10 loads with the "Airplane mode" switched active/on

on the launcher bar...left side..click system settings, then network
the airplane mode indicator is in the lower left corner.

tis going to be funny if this is infact the problem.

---

### Post by Hadaka on 2012-11-02
Here's another thought, from your iwlist wlan0 scan
it saw a network. with the ssid of wlan-ap, im guessing
that is your router's ssid..which is good...it sees it, but doesnt
connect...now the password for wlan-ap, while you stated it is
correct..it may not be. It may have been entered correctly but...
it IS case sensitive...so if you have mixed numbers and letters in the
keycode...check to see that they match exactly as they do for the router
and the other computer that does connect to the router. And while 12.10
is the latest and greatest...its newly released and still a little buggy, with
your older computer, 12.04 probably would have been a better choice.
12.10 is packed with more goodies, which takes more processor use and
there by runs a little warmer than 11.10 or 12.04. Bottom line, after being
frustrated for 4 days trying to get this up and running..i would suggest a clean
install, of 12.04. and...be advised, dell-broadcom will NOT just work with 12.04
it will require loading the b43 wireless driver.** check the upper/lower case letters
in your network password and let us know what you would like to do next.

---

### Post by alyssajesse on 2012-11-03
Hey,
I just turned on my laptop, to try out the most recent suggestions, and it connected to the internet all on its own! I'm not sure why and I'm not sure if this is a permanent thing but YAY! Thank you Thank you Thank you to everyone who has helped me!!!!

---

### Post by NikTh on 2012-11-03
OK, good news ! 

You can mark the thread as solved by clicking on "thread tools" above. 

Thanks

---

### Post by taiar on 2012-11-08
> **NikTh said:**
> Hi , 

you will need Internet connection to run bellow commands. 

```
sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo apt-get remove bcmwl-kernel-source
```Reboot your PC without the Ethernet cable and see if wireless works. 

Thanks

Had an update last night that brokes my wireless on Ubuntu 12.10 and this moning was lost but **NikTh** tip completely saves the day.

Thanks a lot!

:guitar:

---

