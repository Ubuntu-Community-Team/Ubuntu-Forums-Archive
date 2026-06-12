---
title: "problems withs wlan / Intel Pro 4965 / Lenovo 3000 N200"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by Strohfeuer on 2009-02-08
Hello all, I have problems to get my wireless lan running. My laptop is a Lenovo 3000 N200 0769 and I'm using Ubuntu 8.10.

I'm leaving my country for at least 3 months in 10 days and I therefore I need wireless, can someone please help me? I tried it the last days but without any results via ndiswrapper, so I uninstalled it.

The output according this post [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) is attached as txt-file in the compressed folder.

---

### Post by Strohfeuer on 2009-02-08
If you need more information please let me know! I really don't know what do and it's so important!

---

### Post by Guille Damke on 2009-02-08
Hi Strohfeuer,
I have the same wireless card, in a different computer, and it is recognized even using the live CD. Probably you can try it.
It seems to me that your card is already recognized by the OS. One thing you may try is to check the file 
```
 /etc/network/interfaces 
```
It should look like this:
```
auto lo
iface lo inet loopback
```
To check it, you can use:
```
cat /etc/network/interfaces
```

If you have extra lines, do this:
1. Create a backup of the file (for security):
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```
2. Then edit the file adding a comment character '#' (with no single-cuotes) at the beginning of each extra line, just leave the 2 lines that I posted.
To edit, you can use:
```
sudo gedit /etc/network/interfaces 
```
3. Save the file, exit and reboot. Then you should be able to see the networks in the network manager applet located next to the clock. Besides, you should always use this manager, it works very well.

Finally, I would try to boot from a live CD and check if the wireless card is detecting networks, because this card should be sopported out-of-the-box.
Good luck.

---

### Post by gnusci on 2009-02-08
But you have not configured your ESSID yet, it appear **ESSID:""**, as you can see from the output of iwconfig:

[PHP]wlan0     IEEE 802.11abgn  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=15 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/PHP]

I can see your wireless working properly. Try to configure manually

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Once you get your interface working, you only need to use the working settings.

---

### Post by ugm6hr on 2009-02-08
Do you have wifi access point at home to test?

It does appear that the iwlagn Intel driver is correctly installed.

If you are travelling (or live in) Europe or Japan:
[http://www.ubuntu.com/getubuntu/releasenotes/810#Only%20US%20wireless%20channels%20enabled%20by%20default%20on%20Intel%203945](http://www.ubuntu.com/getubuntu/releasenotes/810#Only%20US%20wireless%20channels%20enabled%20by%20default%20on%20Intel%203945)

Does Network Manager find any networks at all?

Try ```
iwlist scan
```

---

### Post by Strohfeuer on 2009-02-09
> **Guille Damke said:**
> Hi Strohfeuer,
I have the same wireless card, in a different computer, and it is recognized even using the live CD. Probably you can try it.
It seems to me that your card is already recognized by the OS. One thing you may try is to check the file 
```
 /etc/network/interfaces 
```
It should look like this:
```
auto lo
iface lo inet loopback
```
To check it, you can use:
```
cat /etc/network/interfaces
```

If you have extra lines, do this:
1. Create a backup of the file (for security):
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```
2. Then edit the file adding a comment character '#' (with no single-cuotes) at the beginning of each extra line, just leave the 2 lines that I posted.
To edit, you can use:
```
sudo gedit /etc/network/interfaces 
```
3. Save the file, exit and reboot. Then you should be able to see the networks in the network manager applet located next to the clock. Besides, you should always use this manager, it works very well.

Finally, I would try to boot from a live CD and check if the wireless card is detecting networks, because this card should be sopported out-of-the-box.
Good luck.

Sorry, I was so busy today. Thanks for all the help.

The file contains the lines you quoted. I will try to use the live CD tomorrow when I'm on the road.

The manager looks like this (connect via cable). 

[IMG]http://img407.imageshack.us/img407/9758/screenshot1ca6.jpg[/IMG]

When I remove my cable there is no option selected. 

> **gnusci said:**
> But you have not configured your ESSID yet, it appear **ESSID:""**, as you can see from the output of iwconfig:

[PHP]wlan0     IEEE 802.11abgn  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=15 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/PHP]

I can see your wireless working properly. Try to configure manually

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Once you get your interface working, you only need to use the working settings.

Thank you, these are good news. I will work through this How-To and keep you posted!

> **ugm6hr said:**
> Do you have wifi access point at home to test?

It does appear that the iwlagn Intel driver is correctly installed.

If you are travelling (or live in) Europe or Japan:
[http://www.ubuntu.com/getubuntu/releasenotes/810#Only%20US%20wireless%20channels%20enabled%20by%20default%20on%20Intel%203945](http://www.ubuntu.com/getubuntu/releasenotes/810#Only%20US%20wireless%20channels%20enabled%20by%20default%20on%20Intel%203945)

Does Network Manager find any networks at all?

Try ```
iwlist scan
```

Thanks ugm6hr. I live in Europe but will travel to the US for 3 months, I made the changes in the file. Tomorrow I will test it.

Unfortunately I have no wifi acces point right here but a few days ago I had and I couldn't get it work. Normally I have a switch to put on my bluetooth and wireless. But it only works for bluetooth under Ubuntu.

> 
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

What does it mean? Is it working?

---

### Post by ugm6hr on 2009-02-09
> **Strohfeuer said:**
> Unfortunately I have no wifi acces point right here but a few days ago I had and I couldn't get it work. Normally I have a switch to put on my bluetooth and wireless. But it only works for bluetooth under Ubuntu.

What does it mean? Is it working?

What happened when you tried to use the wifi a few days ago?  It is difficult to work out what the problem was / is without more detail.

For example, did the wifi access point appear in the Network Manager list (as in the screenshot you posted)?

Did the icon change to suggest it was trying to connect?

iwlist scan appears to suggest it is working fine - wlan0 is searching for wifi access points (and found none).  Hardly surprising, given you don't have a wifi network.

---

### Post by Strohfeuer on 2009-02-10
> **ugm6hr said:**
> What happened when you tried to use the wifi a few days ago?  It is difficult to work out what the problem was / is without more detail.

For example, did the wifi access point appear in the Network Manager list (as in the screenshot you posted)?

Did the icon change to suggest it was trying to connect?

iwlist scan appears to suggest it is working fine - wlan0 is searching for wifi access points (and found none).  Hardly surprising, given you don't have a wifi network.

It absolutely makes sense what you wrote. Maybe I overreacted, sorry for that. I didn't have any time today and then I had some [other problems]("http://ubuntuforums.org/showthread.php?t=1065847") but I will be on a short business trip the next 3 days and I think then I will have some more opportunities to check my wifi and will provide you with more details on friday I hope.
Thanks.

---

### Post by ugm6hr on 2009-02-10
Maybe keep a file with a list of commands to run when out and about in the neighbourhood of wifi networks:

```
ifconfig
iwconfig
iwlist scan
```

These sometimes require "sudo" privileges to run.

Also:

```
dig www.google.com
ping -c 3 216.239.59.147
ping www.google.com
```

Try them, and save the output if it doesn't work.

Then post all the results back here.

---

### Post by Strohfeuer on 2009-02-19
Hello guys and thanks for all the help provided here! I'm finally in the US and my wifi is also working. :-) I tried everything posted in this thread but nothing helped.
Then I found an old post by another Lenovo user who had the idea to use another kernel in the boot menu. Instead of version 2.6.27-11-generic I changed it to 2.6.27-7-generic and it worked immediately! I'm feeling so happy now it's good to be able to stay in touch with good Old Europe. ;)
Here is what I get when using iwlist scan now:

```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:F8:EF:8C:47
/* I changed only the name of the ESSID here */
                    ESSID:"name_of_network" 
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=95/100  Signal level:-56 dBm  Noise level=-94 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000557b101188
                    Extra: Last beacon: 76ms ago

pan0      Interface doesn't support scanning.

```

If I find the time I will post the results of the above bash commands with my old kernel, but in short it couldn't set an ESSID for example when I followed the How-to recommended in the thread.

Now the little switch at my laptop works for wireless and bluetooth like it should be.

---

