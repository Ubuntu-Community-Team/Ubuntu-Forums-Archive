---
title: "Wireless Internet Slow Ubuntu 12.10"
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by asdf-laptop on 2013-02-09
I have a Lenovo ThinkPad X1 Carbon (3443-CTO). My internet is extremely slow when running Ubuntu (technically Xubuntu 12.10).

Heres my info:

** lspci -nnk | grep -iA2 net**

```

03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0085] (rev 96)
        Subsystem: Intel Corporation Device [8086:c220]
        Kernel driver in use: iwlwifi

```

**iwconfig**

```

usb0      no wireless extensions.
 
lo        no wireless extensions.
 
wlan0     IEEE 802.11abgn  ESSID:"Cisco38373"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C0:C1:C0:BE:EC:06  
          Bit Rate=65 Mb/s   Tx-Power=15 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:784  Invalid misc:389   Missed beacon:0

```


**lsmod**

```

Module                  Size  Used by
snd_hda_codec_hdmi     32049  1
snd_hda_codec_realtek    78048  1
uvcvideo               76750  0
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
btusb                  22475  0
joydev                 17458  0
bnep                   18141  2
rfcomm                 46620  16
bluetooth             209249  22 btusb,bnep,rfcomm
parport_pc             32689  0
ppdev                  17074  0
coretemp               13401  0
kvm                   414071  0
ghash_clmulni_intel    13221  0
hid_logitech_dj        18605  0
aesni_intel            51038  0
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
arc4                   12530  2
usbhid                 46987  1 hid_logitech_dj
hid                   100411  2 hid_logitech_dj,usbhid
cdc_ncm                17366  0
usbnet                 26160  1 cdc_ncm
cdc_wdm                18000  0
cdc_acm                26899  0
microcode              22804  0
psmouse                95595  0
serio_raw              13216  0
snd_hda_intel          33492  4
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0
snd_rawmidi            30513  1 snd_seq_midi
lpc_ich                17062  0
iwlwifi               386874  0
thinkpad_acpi          81199  1
snd_seq_midi_event     14900  1 snd_seq_midi
mac80211              539958  1 iwlwifi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
cfg80211              206797  2 iwlwifi,mac80211
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
nvram                  14363  1 thinkpad_acpi
snd                    78921  21 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,thinkpad_acpi,snd_seq,snd_timer,snd_seq_device
i915                  520621  2
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
wmi                    19071  0
drm_kms_helper         49113  1 i915
tpm_tis                18681  0
drm                   288721  3 i915,drm_kms_helper
i2c_algo_bit           13414  1 i915
mac_hid                13206  0
video                  19336  1 i915
mei                    40691  0
lp                     17760  0
parport                46346  3 parport_pc,ppdev,lp
sdhci_pci              18617  0
sdhci                  32646  1 sdhci_pci

```

Here's a speed test just to show you: 

**[SIZE="4"][COLOR="Orange"]UBUNTU:[/COLOR][/SIZE]**

[IMG]http://www.speedtest.net/result/2498247869.png[/IMG]


Windows 8 (SAME LAPTOP, SAME ADAPTER (WIRELESS))

[IMG]http://www.speedtest.net/result/2498246343.png[/IMG]

As you can see something is clearly wrong. I've been searching the forums for hours and even asked in IRC but no answers or responses at all. I really need your help. Support is what makes this OS great and I really want to delete Windows.

---

### Post by wildmanne39 on 2013-02-09
Hi, please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Thanks

---

### Post by asdf-laptop on 2013-02-09
Thank you Wild Man for the prompt response. Here is the output of the commands you told me to enter:

```

dydz@dydz-TPX:~$ echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
[sudo] password for dydz: 
options iwlwifi 11n_disable=1
dydz@dydz-TPX:~$ sudo modprobe -rfv iwlwifi
rmmod /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
rmmod /lib/modules/3.5.0-23-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.5.0-23-generic/kernel/net/wireless/cfg80211.ko
dydz@dydz-TPX:~$ sudo modprobe -v iwlwifi
insmod /lib/modules/3.5.0-23-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.5.0-23-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 11n_disable=1

```

My speed is still very slow, I'll post a new speed test. For some reason, it seems slower. I did not reboot.

EDIT:

Speed test seems about the same. The results were:

[B] Ping: 18
0.53 Mbps Download
0.64 Mbps Upload
[/B]

---

### Post by wildmanne39 on 2013-02-09
Hi, that usually does it. If it is still slow copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by asdf-laptop on 2013-02-09
I rebooted executed the first 3 commands you gave me to try again (I typed sudo su before using them)

Ctrl+Alt+T doesn't seem to open the terminal for me on my Xubuntu 12.10. 

Anyway, under sudo su I executed the script and attatched is the netinfo.txt. I executed this script after executing the first 3 commands you told me to execute.

Thank you again for the quick help.

---

### Post by wildmanne39 on 2013-02-09
Hi, please change your wireless settings to match the screenshots then reboot.

Also you have two network connections named the same thing I would remove one of them, it is probably causing the connection to jump from one to the other.
Thanks

---

### Post by asdf-laptop on 2013-02-09
It worked! However, you said I have two network connections named the same thing. When I click on the signal icon for networking and click edit. I don't see anything else under wireless connections. Is there a manual way to delete it (via the terminal)? Thanks a lot by the way!

Heres my new speed test:

[IMG]http://www.speedtest.net/result/2498316676.png[/IMG]

I also attatched a new netinfo.txt to make sure maybe it was those commands that showed two networks of the same name.

---

### Post by wildmanne39 on 2013-02-09
Hi, glad it worked! If you do not have any other connection issues then you can leave the second network.

I am not sure how to remove it manually.

If you look at the info in the information you posted from the script, under access points for nm-tool you will see both of them.
Please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by asdf-laptop on 2013-02-09
This is odd, after another reboot -- the speed is slow once again.

---

### Post by wildmanne39 on 2013-02-09
Check and make sure that all the settings you changed in wireless settings stuck.

Also the first commands I gave you only had to be entered once.
Thanks

---

### Post by asdf-laptop on 2013-02-09
The commands in the pictures stuck. I entered the commands in for a third time (as I entered in them twice so I figured the 2nd time it made them null). When I entered them in and rebooted there was a network under "Wired Networks." I deleted that and now it seems to be all good. 

The wired connection showed up after entering in those 3 commands. I just did one more reboot to make sure everything sticks and it didn't. My internet seems to be slow again.

Do those commands not count once I've rebooted?

---

### Post by wildmanne39 on 2013-02-09
Hi, those commands should be permanent, lets have a look please post the contents of:
```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```
Thanks

---

### Post by asdf-laptop on 2013-02-09
It says:

```

options iwlwifi 11n_disable=1

```

also I had to apt-get install gedit and gedit-plugins and i get this when I execute your command: 

** (gedit:2348): WARNING **: Could not load theme icon user-bookmarks-symbolic: Icon 'user-bookmarks-symbolic' not present in theme

** (gedit:2348): WARNING **: Could not load theme icon user-home-symbolic: Icon 'user-home-symbolic' not present in theme

---

### Post by wildmanne39 on 2013-02-09
Hi, that is what it is suppose to say.

Are you running ubuntu installed from the hard drive?
Those messages are not something that stopped the commands from working.
Thanks

---

### Post by asdf-laptop on 2013-02-09
Yeah it's on my hard drive. I was just wondering what they meant. It worked, it's fine. 

Err, I just don't get whats going on with the internet.

---

### Post by wildmanne39 on 2013-02-09
If you have any other connection at the same time as your wireless they will conflict like what is this > Ericsson Business Mobile Networks BV
Thanks
Also you do not have your network secure maybe someone else is using it.
Thanks

---

### Post by asdf-laptop on 2013-02-09
Ok this is interesting. It definitely has something to do with the fact that theres 2 networks with the same name.

If I go to edit and just delete the network. I go offline. The same network shows up. I connect to it. I apply the settings on the picture and the internet acts normal and goes fast.

But after like 2 minutes it's slow again.

EDIT: Yeah my network is secure. I'm monitoring it on a main PC. I live in an area where no one could really even steal my internet. The signal to my neighbor is not strong enough.

EDIT2: I can just keep doing it over and over. I can keep deleting the network from edit and then it pops up again and I connect to it, change the settings and it works fast for 2 minutes.

---

### Post by wildmanne39 on 2013-02-09
I suspect as much.
Remove all connections then reboot and let network manager find your connection then change the settings to match the screenshots and reboot.
Thanks

---

### Post by asdf-laptop on 2013-02-09
Seems to be working. This new problem has arisen since I've been rebooting so much.

It just boots to a black screen or a virtual terminal that says tty1


In grub if I press e and $vt_handoff or set it =7 then it works. I have no idea what this is


As for the internet, I still see 2 access points named the same.

As for the reboot, right now im just removing the handoff thing each time, do you have any support links for that? I cant even find it on the internet with the "$" infront-- all searches just say vt_handoff instead of $vt_handoff


Edit: Internet just went slow again randomly. This is odd.

---

### Post by asdf-laptop on 2013-02-09
I figured it out. There were 2 access points because of my router. My brother or someone turned on a 2.4 AP's--one being 2.4 GHz and the other being 5 GHz.

As soon as I turned off the 2.4 GHz, I saw xubuntu disconnect and connect to the other one which is fast. Now to figure out this black screen thing

---

### Post by wildmanne39 on 2013-02-09
Hi, I am glad it is working.
Start another thread in the appropriate section of the forum for the boot issue.

---

### Post by JamesDavid on 2013-05-23
> **Wild Man said:**
> Hi, please change your wireless settings to match the screenshots then reboot.

Also you have two network connections named the same thing I would remove one of them, it is probably causing the connection to jump from one to the other.
Thanks

Hi Wild Man -- what screenshots are you referring to?  I have a similar issue and would like to try the solution found here before creating a new thread.

Thanks,
James

---

### Post by wildmanne39 on 2013-05-25
Hi, the screenshots were removed by mistake. Here you go.

---

### Post by cchhat01 on 2013-06-24
I recently upgraded to 12.04.2 and am now at the latest kernel supported (3.5.0.34).
I too am experiencing slowness using my Intel 6235 WiFi card in my ultrabook.
Are we anywhere close to having a proper fix that allows use of the 40Mhz bandwidth or are we going to have to live with a sacrificed performance on all intel based N-wifi cards.

I bought the 6235 to place in my notebook for the purpose of exploiting higher bandwidth. disabling n-wifi really defeats the purpose of having bought this card.

---

### Post by cchhat01 on 2013-06-25
> **cchhat01 said:**
> I recently upgraded to 12.04.2 and am now at the latest kernel supported (3.5.0.34).
I too am experiencing slowness using my Intel 6235 WiFi card in my ultrabook.
Are we anywhere close to having a proper fix that allows use of the 40Mhz bandwidth or are we going to have to live with a sacrificed performance on all intel based N-wifi cards.

I bought the 6235 to place in my notebook for the purpose of exploiting higher bandwidth. disabling n-wifi really defeats the purpose of having bought this card.

Solved my own problem.
It wasn't the 11_disable that I needed. Infact, I set 11_disable=0 in the iwlwifi options and what I did instead was turned off power management.
The results are day and night. 
My ping times BEFORE "power [management] off" to my router (192.168.1.1) were in the range of 110 to 200ms
My ping times AFTER "power [management] off" to my router (192.168.1.1) are now 0.900ms to 1.2ms

Ping to google before: 150 - 200 ms
ping to google after 3.7ms - 8ms

All this AND i get to keep 802.11n on both a/g bands.

Awesome.

---

### Post by Redsandro on 2014-02-07
**@cchhat01** how exactly do you turn power management off?
I have a similar problem. My internet starts slow, but after a while it gets normal (fast).

```
ping www.facebook.com
PING star.c10r.facebook.com (31.13.64.65) 56(84) bytes of data.
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=1 ttl=91 time=12866 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=2 ttl=91 time=11858 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=3 ttl=91 time=14622 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=4 ttl=91 time=13614 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=5 ttl=91 time=12608 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=6 ttl=91 time=11601 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=7 ttl=91 time=10598 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=8 ttl=91 time=9591 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=9 ttl=91 time=8588 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=10 ttl=91 time=7584 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=11 ttl=91 time=6576 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=12 ttl=91 time=5569 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=13 ttl=91 time=4560 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=14 ttl=91 time=29.1 ms
^C
--- star.c10r.facebook.com ping statistics ---
14 packets transmitted, 14 received, 0% packet loss, time 16956ms
rtt min/avg/max/mdev = 29.124/9305.105/14622.563/3940.769 ms, pipe 13
```


Also see [AskUbuntu: Network starts slow on Ubuntu 13.10 start or resume](http://askubuntu.com/questions/407282/network-starts-slow-on-ubuntu-13-10-start-or-resume)

---

### Post by Roo8choo on 2014-02-07
> **Redsandro said:**
> **@cchhat01** how exactly do you turn power management off?
I have a similar problem. My internet starts slow, but after a while it gets normal (fast).

```
ping www.facebook.com
PING star.c10r.facebook.com (31.13.64.65) 56(84) bytes of data.
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=1 ttl=91 time=12866 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=2 ttl=91 time=11858 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=3 ttl=91 time=14622 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=4 ttl=91 time=13614 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=5 ttl=91 time=12608 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=6 ttl=91 time=11601 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=7 ttl=91 time=10598 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=8 ttl=91 time=9591 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=9 ttl=91 time=8588 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=10 ttl=91 time=7584 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=11 ttl=91 time=6576 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=12 ttl=91 time=5569 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=13 ttl=91 time=4560 ms
64 bytes from edge-star-shv-06-ams2.facebook.com (31.13.64.65): icmp_seq=14 ttl=91 time=29.1 ms
^C
--- star.c10r.facebook.com ping statistics ---
14 packets transmitted, 14 received, 0% packet loss, time 16956ms
rtt min/avg/max/mdev = 29.124/9305.105/14622.563/3940.769 ms, pipe 13
```


Also see [AskUbuntu: Network starts slow on Ubuntu 13.10 start or resume]("http://askubuntu.com/questions/407282/network-starts-slow-on-ubuntu-13-10-start-or-resume")

I see your Dutch, thats cool. A member from the Dutch Ubuntu Forum (Pjotr) made a whole manual about fixing common wireless problems.
[https://sites.google.com/site/computertip/geendraadloosinternet](https://sites.google.com/site/computertip/geendraadloosinternet)

Maybe this will fix your problem.

Greetings,

Allard

---

