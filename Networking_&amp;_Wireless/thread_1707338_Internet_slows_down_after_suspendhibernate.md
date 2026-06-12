---
title: "Internet slows down after suspend/hibernate"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by sicco1 on 2011-03-15
My wireless internet speed slows down after starting my Asus K52F laptop from suspend or hibernate. When I shut down or restart my laptop my internet speed (as tested on speedtest.net) will be something like: 30-40 ping, 4 Mbps download, 0.5 Mbps upload. After the suspend or hibernate my ping and download speeds become worse: 50-60 ping, 2 Mbps download, but still 0.5 Mbps upload.

The problem arises on other networks as well, so it is not caused by my home wireless network. I haven't tried any wired connections (which is not easy to try in my current situation). I tried restarting my network using "sudo /etc/init.d/networking restart", but that doesn't work, neither thus reconnecting to the wireless modem or disabling/enabling my wireless hardware. The only thing I can do to regain full speed is restarting my laptop. How can I fix this?

Some system information.
OS: Ubuntu 10.10 64 bit
Laptop: Asus K52F

Wireless hardware:
```
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network
Adapter (PCI-Express) (rev 01)
        Subsystem: Device 1a3b:1089
        Physical Slot: 1
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d2c00000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k
```If more information is needed please let me know.

---

### Post by sicco1 on 2011-03-16
[COLOR=RoyalBlue]small bump[/COLOR]

---

### Post by sicco1 on 2011-03-17
[COLOR=Purple]little bump[/COLOR]

---

### Post by sicco1 on 2011-03-21
[COLOR=DarkRed]bumpzz[/COLOR]

---

### Post by sicco1 on 2011-03-22
[COLOR=MediumTurquoise]boink[/COLOR]

---

### Post by sicco1 on 2011-03-23
[COLOR=DarkOrange]bumper[/COLOR]

---

### Post by sicco1 on 2011-03-25
[COLOR=Olive]b0mp
[/COLOR]

---

### Post by sicco1 on 2011-03-26
[COLOR=Indigo]bonkers[/COLOR]

---

### Post by sicco1 on 2011-03-28
[COLOR=Green]bmpz[/COLOR]

---

### Post by matt_symes on 2011-03-28
Hi

Not sure if i can help as i have never come across this but after all your colourful bumps...

Post the output of

```
iwconfig
```

before and after you hibernate after a fresh reboot.

Kind regards

---

### Post by sicco1 on 2011-03-28
Thanks for the reply :D

I did a reboot and then iwconfig which gave me:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"my_wireless_network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:EB:AD:FC:72   
          Bit Rate=58.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Then I closed my laptop lid, which puts it into suspend.
I opened the lid again and entered my password to log in.
Then I ran iwconfig again and it gave me:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"my_wireless_network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:EB:AD:FC:72   
          Bit Rate=39 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missedood beacon:0

```The only thing I notice is the drop in the Bit Rate (***update: I just noticed that Bit Rate goes up again when I access data intensive websites (after suspend), so I probably misinterpreted the meaning of Bit Rate. While the Bit Rate goes up, my actual download speed is thus still lower than before the reboot as described in my start post), which is exactly my problem :) What could cause this?

---

### Post by sicco1 on 2011-03-30
[COLOR=Olive]bump[/COLOR]

---

### Post by matt_symes on 2011-03-30
Hi

Your iwconfig looks alright. Power management is off and that is good as that has been known to cause issues with speed.

Lets try to track this down. After coming out of suspend, open a terminal and type

```
sudo /etc/init.d/networking restart
``` 

Enter your password. It will not be echoed to the screen. This is normal.

What kind of speed do you get after networking is restarted ?

If that does not work we will try to reload your driver. In preparation for this, please post the output of (case sensitive)

```
lspci -nnk | grep -A3 Network
```

Kind regards

---

### Post by sicco1 on 2011-03-31
Thanks again for the reply. I have already been tried to restart the network with the command you gave that didn't and still doesn't work. My download speed is still way lower after suspend/hibernate than after rebooting. I am also kind of suspecting the network drivers. Here is the info from lspci:
```

02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Device [1a3b:1089]
    Kernel driver in use: ath9k
    Kernel modules: ath9k

    Subsystem: Device [1a3b:1089]
    Kernel driver in use: ath9k
    Kernel modules: ath9k

```

Thanks in advance

---

### Post by matt_symes on 2011-03-31
Hi

Alright. Lets try to unload and reload the kernel drivers. Same as before. After suspend.. hibernate...

```
sudo rmmod ath9k
sudo modprobe ath9k
```

Usual routine with the password.

Please tell me that makes a difference :confused:

Kind regards

---

### Post by sicco1 on 2011-04-03
Hi,

I finally got to test your suggestion and it works! Thanks a lot! My download speed and ping restore to their normal values after removing and adding the ath9k module with the commands you gave. I am wondering though why this happens? Any ideas on how to figure this out? Is this a bug that needs to be reported (where?)?

Thanks

---

### Post by matt_symes on 2011-04-03
Hi

> **AgamemnonZ said:**
> Hi,

I finally got to test your suggestion and it works! Thanks a lot! My download speed and ping restore to their normal values after removing and adding the ath9k module with the commands you gave. I am wondering though why this happens? Any ideas on how to figure this out? Is this a bug that needs to be reported (where?)?

Thanks

I'm not sure why it happens. I have never had it happen to me so i have never really investigated it. If you want to investigate have a look at the logs and dmesg.

If you want to make it happen (unload and reload the module at suspend, hibernate, resume and thaw) automatically you will need to make a script to do this. If you need directions on how to do that post back.

Kind regards

---

### Post by sicco1 on 2011-04-03
Hi,

Thanks for offering to help me with automating these commands after suspend/hibernate. How do I do this?

Regards

---

### Post by matt_symes on 2011-04-03
Hi

Try this. If it does not work we can try something else.

Open a terminal and type

```
sudo nano /etc/pm/sleep.d/10_wireless_sleep
```

Add this to the file

```
#!/bin/sh

case "$1" in
        suspend|hibernate)
               rmmod ath9k
                ;;
        resume|thaw)
               modprobe ath9k 
                ;;
esac
```

Ctrl + o to save the file and ctrl + x to exit.

Make it executable

```
sudo chmod 751 /etc/pm/sleep.d/10_wireless_sleep
```

Suspend and resume. 

Does that fix it for you ?

Kind regards

---

### Post by sicco1 on 2011-04-03
Hi,

After removing the stray '#' in front of the 'modprobe' line the script works like a charm! Thanks! I appreciate the time and effort you have put into solving my issue a lot, so thank you again :D!

Cheers

---

### Post by matt_symes on 2011-04-03
Hi

> After removing the stray '#' in front of the 'modprobe

Opps. That was part of my testing :D I'm glad it's fixed and will update my earlier post to remove the offending #. Please mark thread as solved.

Kind regards

---

### Post by AndyJR on 2011-05-16
I have the same issue with my Asus U50F, which also uses the ath9k module. After resuming from suspend/hibernate, the wireless performance is terrible. The solution presented here fixes the issue, but there's an easier way: create a file in /etc/pm/config.d, called whatever you want (for instance, "config") with the following line:
```
SUSPEND_MODULES="ath9k"
```That will unload the module on suspend/hibernate and reload it on resume.

---

### Post by bacchusmarsh on 2011-06-10
hello good people,

i have a similar problem, same laptop.

my speed is half as fast on this laptop as it is on older asus, both running 10.10. 

(also dual boot windows 7 new machine, the speedtest is same as old laptop, twice as fast)

it does not seem to matter about the suspend/hibernate vs restart/shutdown factor. it is half pace regardless.

just thought i would try you in case you were still listening...

---

### Post by bacchusmarsh on 2011-06-10
actually your right, it is slower after suspend.
i will try your work around...

.... awesome that worked a treat :)
 now my girlfriends computer isn't faster than mine.

---

### Post by Ken Kaniff on 2012-02-02
Thanks for this thread, and thanks AndyJR for the work-around. Worked for my IBM ThinkPad notebook like a charm.

---

