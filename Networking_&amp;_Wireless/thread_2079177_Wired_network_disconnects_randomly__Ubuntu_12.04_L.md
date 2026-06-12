---
title: "Wired network disconnects randomly  Ubuntu 12.04 LTS"
date: 2012-11-01
forum: Networking &amp; Wireless
---

### Post by sunny2303 on 2012-11-01
Hello everybody,

I am a total newbie to ubuntu as well as this forum, so please forgive me if I am not complying with any basics here. I have installed ubuntu on my HP Pavilion DV6-7040TX Laptop through wubi. I have installed ubuntu to be able to build CM10.

My wired network connects perfectly .  But whenever I try to do "repo sync" which you must be knowing is a very time consuming download, connection disconnects after say 1 hour or so..  

Bigger worry is that I am unable to resume network unless i restart ubuntu, as a result my download resume options come to an end (like the screen command)..  There is nothing wrong with my wired broadband connection as well as other things like ethernet cable (it runs perfectly in windows 7 for longer downloads).

Request help.  

PS: please let me know the information you will need (any commands to be issued on terminal) and I will try and provide.

---

### Post by varunendra on 2012-11-01
Please post outputs of (after using the connection for 5-10 minutes) :
```
lspci -nnk | grep -iA2 net
lsmod
ifconfig
```

---

### Post by sunny2303 on 2012-11-02
> **varunendra said:**
> Please post outputs of (after using the connection for 5-10 minutes) :
```
lspci -nnk | grep -iA2 net
lsmod
ifconfig
```
 
At work, right now.  Will surely post the necessary details.  thanks a lot for helping me.

---

### Post by sunny2303 on 2012-11-02
lspci -nnk | grep -iA2 net

```

0a:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1795]
    Kernel driver in use: wl
--
0b:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1818]
    Kernel driver in use: r8169

```lsmod

```

Module                  Size  Used by
pppoe                  17875  2 
pppox                  13342  1 pppoe
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
lib80211_crypt_tkip    17390  0 
wl                   2568210  0 
nouveau               774641  0 
ttm                    76949  1 nouveau
mxm_wmi                12979  1 nouveau
psmouse                97443  0 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72627  0 
serio_raw              13211  0 
videodev               98259  1 uvcvideo
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_compat_ioctl32    17128  1 videodev
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  473298  3 
lib80211               14381  2 lib80211_crypt_tkip,wl
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         46978  2 nouveau,i915
mei                    41616  0 
drm                   241921  6 nouveau,ttm,i915,drm_kms_helper
i2c_algo_bit           13423  2 nouveau,i915
wmi                    19256  2 mxm_wmi,hp_wmi
hp_accel               25976  0 
video                  19596  2 nouveau,i915
lis3lv02d              19876  1 hp_accel
input_polldev          13896  1 lis3lv02d
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 


```ifconfig

```

eth0      Link encap:Ethernet  HWaddr 08:2e:5f:73:eb:5f  
          inet6 addr: fe80::a2e:5fff:fe73:eb5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4920 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3020954 (3.0 MB)  TX bytes:504847 (504.8 KB)
          Interrupt:43 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:128.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2305 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2305 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:233463 (233.4 KB)  TX bytes:233463 (233.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:182.238.145.126  P-t-P:172.31.29.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:4626 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2894217 (2.8 MB)  TX bytes:387945 (387.9 KB)

```

---

### Post by varunendra on 2012-11-02
> **sunny2303 said:**
> lspci -nnk | grep -iA2 net

```

0b:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.** RTL8111/8168B** PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1818]
    Kernel driver in use: [COLOR=Red]**r8169**[/COLOR]

```
This chip and driver combination is known for such problems. Please go to [Realtek's site]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false") and download the latest recommended driver - r8168.

Extract the files from the downloaded archive to a folder and follow the installation instructions included in the extracted files, which is:

[LIST=1]
[*]open a terminal
[*]goto the folder where you have extracted the files
[*]run the following command: ```
sudo ./autorun.sh
```
[/LIST]
However, if it doesn't work (sometimes happens), then retry :
```
sudo su
./autorun.sh
exit

```

Also, disable IPv6 as an additional measure (just copy-paste the following command in the terminal):
```
echo -e "\n# force-disable IPv6\nnet.ipv6.conf.all.disable_ipv6=1\nnet.ipv6.conf.default.disable_ipv6=1\nnet.ipv6.conf.lo.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
It will add the following lines at the end of your /etc/sysctl.conf file (you can also do it manually if you wish):
> # force-disable IPv6
net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6=1 			 		

Reboot, retry the connection and post back how it goes.

---

### Post by Dakster01 on 2012-11-03
Hi there.
 
I have exactly the same problem and it started in the last 2 or 3 days since installing the latest updates. I update as new updates are released so it must be one of the released patches within the last week or so. Before this issue my 12.04 server was rock solid network wise. 
 
Could any of the patches in the last few days be the cause? For the record I am using kernel driver 3c59x and kernel modules 3c59x and already have ipv6 turned off.

---

### Post by varunendra on 2012-11-03
> **Dakster01 said:**
> I have exactly the same problem....Hi Dakster01, and welcome to the forums!

These kind of problems may be caused by a number of reasons, although the symptoms and effects may look same. Accordingly, I'd suggest to start a new thread of your own, and post the outputs of the commands I asked in my first post. Then post a link to the thread here, if you wish, so we can follow.

---

### Post by Dakster01 on 2012-11-03
Thanks varunendra.

I have created a separate thread here:
[http://ubuntuforums.org/showthread.php?t=2080326](http://ubuntuforums.org/showthread.php?t=2080326)

---

### Post by sunny2303 on 2012-11-05
Dear Varun,

Sorry for the delayed revert... I followed the suggested solution to the last word.. and it did update the driver.. however the issue still persists.

Anything else I need to try or update?

---

### Post by danelwillis on 2012-11-05
try using a different network manager, it could be something simple Wcid is a good in my opinion

---

### Post by varunendra on 2012-11-05
> **sunny2303 said:**
> however the issue still persists.
Let's check the current status. Pleas post the outputs of :
```
lspci -nnk | grep -iA2 net
lsmod
ifconfig
```

---

### Post by sunny2303 on 2012-11-06
An update from my side:  Finally I have found that following command works for me to restart the network connection without restarting ubuntu
 
```
sudo service network-manager restart
```
 
Keeping this is in mind, will the following script help to automate running of this command in the event of network disconnection. I mean, if the network disconnects, will this script help to restart the network connection without manual intervention
 
```
start on started network-manager
stop on runlevel [016]

script
  while true; do
    if ifconfig eth0 | grep -q "inet addr:"; then
       # echo "all ok!"
    else
       service network-manager restart
    fi
    sleep 5
  done
end script

```
 
Please let me know as I barely know anything about scripts and this is what I googled, though I am not sure if it will help and more importantly not cause any damage.
 
Thanks.

---

### Post by varunendra on 2012-11-06
> **sunny2303 said:**
> will this script help to restart the network connection without manual intervention....
I don't know much about scripting, so not sure how it will work. But even if it does as expected, it is obviously not a solution, just a crude workaround (crude - since it'll break the connection momentarily).

Accordingly, I'd suggest to post the outputs I asked in my previous post so we all can see if the correct driver is loading now, and whether there are any configuration or traffic problems.

If you are inclined to use the nm workaround, then you should probably give wicd a shot as danelwillis suggested. It is simpler and, in some cases (especially wireless though), is reported to be more stable than nm. But disable or uninstall nm if you try wicd or anything else. Using two network managers simultaneously will cause more problems.

---

### Post by sunny2303 on 2012-11-12
Added the following script to a file and saved it as netcheck.sh

```

while true; do
    ## method #1 
    ## check if network is down, if yes, restart network service 
    #if ifconfig eth0 | grep -q "inet addr:"; then 
    #    echo "all ok";
    #else
    #    service network-manager restart;
    #fi
    #sleep 5; #let's check network status again after 5 seconds;

    ## methode #2
    ## restart network by default after 10 min
    service network-manager restart;
    echo "network service restarted...";
    sleep 600; 
done

```

Everytime I do any activity such as Repo Sync which takes lot of time and needs continuous net connection. In another terminal window, I trigger this script by:

```

sudo sh netcheck.sh

```

This has solved my issue, as network manager restarts at regular intervals and my download completes without any network disconnection issue.

Hope this wil help someone else too.. Marking this thread as solved :)

---

### Post by varunendra on 2012-11-12
> **sunny2303 said:**
> ```

while true; do
*<snip>*
    ## methode #2
    ## restart network by default after 10 min
    service network-manager restart;
    echo "network service restarted...";
    sleep 600; 
done

```
Interesting 'fix' :) Congratulations !

You never posted those outputs I asked for so we could see if there are any holes to patch. But as Aamir said - "Aal iz vel" (if YOUR heart believes so) ;)

One suggestion to test its reliability though. Try downloading some file from a service which doesn't support 'Resume' function (like 'Free' downloading from rapidshare or hotfile), and see if the download breaks or not when '*nm-restart*' is triggered while downloading. I suspect it'll break but am not sure. Try it and please post feedback. If it continued, it can be a really cool workaround afterall.

Regards.

---

