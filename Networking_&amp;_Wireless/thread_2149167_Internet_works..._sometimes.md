---
title: "Internet works... sometimes"
date: 2013-05-27
forum: Networking &amp; Wireless
---

### Post by LittleHorn on 2013-05-27
Hello,

Not sure if I should be posting this on the Absolute Beginners Section or here. I am a novice when in comes to linux, but i am trying to learn. 

I am dual booting (Windows 7 and Ubuntu 12.10), when I'm on Windows the internet works fine. It has been a few months since i have used Ubuntu, so when i logged on a few days ago there were tons of new updates. After the updates my internet started acting funny. It will work at first, but after a few minutes of surfing online it starts to slow down considerably, then eventually stops all together. When ever I reboot the computer or router I experience the exact same problem (it works, then it doesn't). When I try using the trace route function from the network tools, the program freezes and i have to force close it. I've read a couple other forums and found people who also had internet problems, but not quite the same as mine. 

After looking around online, I have a hunch that it has something to do with the DNS configuration, but I have no idea how to fix it. Any help will be greatly appreciated.

---

### Post by varunendra on 2013-05-28
> **LittleHorn said:**
> After the updates my internet started acting funny. It will work at first, but after a few minutes of surfing online it starts to slow down considerably, then eventually stops all together.

Hi, welcome to the forums LittleHorn!

Please show us the outputs of -
```
uname -mr
lspci -nnk | grep -iA2 net
iwconfig
```

While posting the code, click on **#** button above the edit box to auto-generate 'Code' tags, then copy-paste the output in-between the tags.

---

### Post by LittleHorn on 2013-05-28
```
littlehorn@littlehorn-W3x0ET:~$ uname -mr
3.5.0-31-generic x86_64
littlehorn@littlehorn-W3x0ET:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)
    Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4060]
    Kernel driver in use: iwlwifi
--
04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
    Subsystem: CLEVO/KAPOK Computer Device [1558:3700]
    Kernel driver in use: r8169
littlehorn@littlehorn-W3x0ET:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"LittleHorn"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:D6:10:A8:A0   
          Bit Rate=48 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:9876  Invalid misc:447   Missed beacon:0

littlehorn@littlehorn-W3x0ET:~$ 


```

Thanks for the reply and the warm welcome. I posted the output above. 

I think I found a solution to this problem on my own :cool:. While browsing a little more I found this [https://developers.google.com/speed/public-dns/docs/using](https://developers.google.com/speed/public-dns/docs/using)

Followed these instructions:


[LIST=1]
[*]In the **System** menu, click **Preferences**, then click **Network Connections**. 
[*]Select the connection for which you want to configure Google Public DNS. For example:
[LIST]
[*]To change the settings for an Ethernet connection, select the **Wired** tab, then select your network interface in the list. It is usually called **eth0**. 
[*]To change the settings for a wireless connection, select the **Wireless** tab, then select the appropriate wireless network. 
[/LIST]
  
[*]Click **Edit**, and in the window that appears, select the **IPv4 Settings** or **IPv6 Settings** tab. 
[*]If the selected method is **Automatic (DHCP)**, open the dropdown and select **Automatic (DHCP) addresses only** instead. If the method is set to something else, do not change it. 
[*]In the **DNS servers** field, enter the Google Public DNS IP addresses, separated by a space:
[LIST]
[*] For IPv4: 8.8.8.8 and/or 8.8.4.4. 
[*] For IPv6: 2001:4860:4860::8888 and/or 2001:4860:4860::8844 
[/LIST]
  
[*]Click **Apply** to save the change. If you are prompted for a password or confirmation, type the password or provide confirmation. 
[/LIST]
Im not sure if this is a permanent fix, but for the last hour I have been surfing the web (Both Firefox and Chrome) with absolutly no problems. What do you think?

---

### Post by varunendra on 2013-05-28
> **LittleHorn said:**
> ```

littlehorn@littlehorn-W3x0ET:~$ iwconfig

wlan0     IEEE 802.11abgn  ESSID:"LittleHorn"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:D6:10:A8:A0   
          **Bit Rate=48 Mb/s**   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          **Link Quality=[COLOR="#FF0000"]37/70[/COLOR]**  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:9876  Invalid misc:447   Missed beacon:0

```
<snip>
Im not sure if this is a permanent fix, but for the last hour I have been surfing the web (Both Firefox and Chrome) with absolutly no problems. What do you think?
Well, as long as it works well for you, definitely don't try to fix it :)

However, given the nature of the problem you described (that I quoted), I think the problem is not related with DNS, and so may reoccur.

The signal strength doesn't look good. Is it same on windows 7 (37/70) ?

If (and ONLY IF) the problem occurs again, especially when there is a continuous stream of data (like a heavy download), you may try -
```
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi swcrypto=1
```
Then try to connect again and see if it improves. It is a temporary change that will be lost on reboot. We can make it permanent if required.

Whether it remains good, or gets slow again, please report back. Thanks!

---

### Post by LittleHorn on 2013-05-28
```
littlehorn@littlehorn-W3x0ET:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"LittleHorn"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:D6:10:A8:A0   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
         ** Link Quality=52/70**  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3731  Invalid misc:75   Missed beacon:0


```

Tested again and got better results. I checked the link quality in Windows 7 through the "Event Viewer" (not an easy task) and i got around 83/100 to 97/100. Not really sure why the connection is better in Windows since I am not moving any closer or further from the router, but I will keep you updated. Thanks alot for the help :D

---

### Post by varunendra on 2013-05-29
> **LittleHorn said:**
> ...but I will keep you updated.....and I'm sure it'll be appreciated by many more than myself alone :)
Thanks for your interest in that.

---

### Post by wildmanne39 on 2013-05-29
Hi, this > For IPv4: 8.8.8.8 and/or 8.8.4.4usually makes the speed much faster and most people set ipv6 to ignore.

Usually disabling N speed with the driver parameter helps along with what Varun mentioned.
Thanks

---

### Post by LittleHorn on 2013-05-30
So far so good. It has been two days and I haven't had a single "Server Not Found" or "This webpage is not avaliable" window pop up. :P

---

### Post by Hadaka on 2013-05-30
Hi Littlehorn,
I have been following along and would like to try something if you 
are up to it. There is a power setting for your iwlwifi module and it
is currently set at 1 by default...I would like to see if your signal strength
57/70 will increase by increasing the power level...it should cause no harm
and will go back to default once you boot your machine.
check current signal strength..
```
iwconfig
```
increase power..
```
sudo modprobe -rfv iwlwifi
sudo modprobe iwlwifi power_level=5
```
check signal strength..
```
iwconfig
```
after you post the output...boot and it will go back to default power_level=1
thanks.

---

### Post by LittleHorn on 2013-05-30
**Before**
```

littlehorn@littlehorn-W3x0ET:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"LittleHorn"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:D6:10:A8:A0   
          Bit Rate=104 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:88  Invalid misc:48   Missed beacon:0


```
[B]
After

[/B]```
littlehorn@littlehorn-W3x0ET:~$ sudo modprobe -rfv iwlwifi[sudo] password for littlehorn: 
remove (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) && /sbin/modprobe -r mac80211
rmmod /lib/modules/3.5.0-31-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.5.0-31-generic/kernel/net/wireless/cfg80211.ko
littlehorn@littlehorn-W3x0ET:~$ sudo modprobe iwlwifi power_level=5
littlehorn@littlehorn-W3x0ET:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"LittleHorn"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:D6:10:A8:A0   
          Bit Rate=12 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:19   Missed beacon:0

```

didn't really look like it made much difference at first. I had to reboot because my connection froze for a bit. After reboot, connection is fine. Since [COLOR=#000000]varunendra showed me the iwconfig command, i have been checking my signal strength periodically. So far I have found that i get the best connection VERY late at night, and the worst connection during the day. 

**here are the results after reboot**

```


```[/COLOR]```
littlehorn@littlehorn-W3x0ET:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"LittleHorn"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:D6:10:A8:A0   
          Bit Rate=104 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:509  Invalid misc:96   Missed beacon:0



```[COLOR=#000000]


[/COLOR]

---

### Post by wildmanne39 on 2013-05-30
It sounds like you are getting interference on the channel you are using, I suggest you try 1 or 11 if you have not already.
Thanks

---

### Post by varunendra on 2013-05-31
Also, you seem to be getting quite variable speeds at different times. You may play with 'iwconfig rate' command to see if a fixed speed makes anything better. For example, to fix the speed to 48 Mb/s -
```
sudo iwconfig wlan0 rate 48M
```

Or, to set it to a maximum of 54 Mb/s and lower, as suitable -
```
sudo iwconfig wlan0 rate 54M auto
```

To set it to auto again -
```
sudo iwconfig wlan0 rate auto
```

Fixing the speed to a lower value than maximum possible sometimes helps in cases where connection freezes during high traffic. Just play with different supported speeds, and don't expect too much :D

Oh, and to get the 'supported' speeds -
```
sudo iwlist wlan0 scan
```

Keep us posted! :)

---

### Post by LittleHorn on 2013-06-01
So it has been a few days and I have not seen any problems with my internet connection. 

@Varunedra, I tried changing the rate to 48 and 54M and did not see a difference. but thanks.
@Wild Man, not sure how to change the channel that I am using. For now I think I'm just going to leave things the way they are since I am not having any issues.

@ALL, thank you all so much for the helpful suggestions. If the problem comes back in the future, i will definitely come back to this page for possible solutions. Also, not sure about the forum protocol here, should I mark this thread as "Solved" now?

---

### Post by varunendra on 2013-06-01
> **LittleHorn said:**
> Also, not sure about the forum protocol here,
Apart from 'good behaviour', there is not really much of a 'protocol' :)

> should I mark this thread as "Solved" now?
If you find the solution satisfactory, you should. It just tells others that the thread contains a solution that worked for you and may possibly solve the problem for them too.

Cheers !

---

