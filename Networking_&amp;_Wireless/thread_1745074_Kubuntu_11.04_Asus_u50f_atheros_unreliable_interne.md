---
title: "Kubuntu 11.04/ Asus u50f/ atheros/ unreliable internet"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by WyzeGye on 2011-04-30
```
Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

wlan0     IEEE 802.11bgn  ESSID:"DUSTINSEE"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:22:2D:A2:D9:48   
          Bit Rate=150 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:31   Missed beacon:0

```
it takes 3-4 refreshes to make a page load, when i apt-get something, my speed is an average of 400 bytes per second. Making it impossible to get anything done.

its been like this for a while, i figured it was a bug in 10.10 and ignored it since 11.04 was coming soon. And with windows everything is fine. 

I'm getting very sick of this. Can somebody please help me? If you need more info, just let me know.

---

### Post by Sillywombat on 2011-04-30
A few people have been reporting this recently, especially since they switched to 11.04. 
I'd suggest taking a look at this thread: [http://ubuntuforums.org/showthread.p...hlight=wmp54gs](http://ubuntuforums.org/showthread.p...hlight=wmp54gs)

Also, have you checked to see if your card is compatible? And if not, is there a workaround.

---

### Post by WyzeGye on 2011-04-30
That is for broadcom cards. If you'd read my post you'd see that it does not apply to my card. According to the compatibility chart my ar9285 is supported and compatible

---

### Post by WyzeGye on 2011-04-30
Is there anybody out there that can help? Preferably somebody who can read posts, not just topic titles. I don't mean to be hard on the guy, but nothing good comes from the  blind leading the blind.

---

### Post by teachop on 2011-04-30
if you run dmesg, do you see a bunch of messages like this:
wlan0: deauthenticating from xxxxxxxxx by local choice (reason=3)

---

### Post by WyzeGye on 2011-04-30
```
[   92.572118] wlan0: authenticate with 00:22:2d:a2:d9:48 (try 1)
[   92.574187] wlan0: authenticated
[   92.574213] wlan0: associate with 00:22:2d:a2:d9:48 (try 1)
[   92.583411] wlan0: RX AssocResp from 00:22:2d:a2:d9:48 (capab=0x411 status=0 aid=1)
[   92.583420] wlan0: associated

```


that's what i'm seeing

---

### Post by WyzeGye on 2011-04-30
[http://bayimg.com/jahImAaDn](http://bayimg.com/jahImAaDn)

just an idea of what i'm dealing with. I can't even install firefox

---

### Post by el_koraco on 2011-04-30
Do a ```
lspci -k | grep Network
```

I do believe that this card should be using ath9 kernel driver. I have ath9 and have been running Kubuntu without problems. If the issue persists, you might try apt-getting wicd or gnome network manager.

---

### Post by teachop on 2011-04-30
Ok.  Took a stab, I have the same atheros wireless chip and the same symptoms.  This bug report matches what happens on this laptop to a tee, thought you may be seeing the same thing (it isn't specific to atheros).
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992")

---

### Post by WyzeGye on 2011-04-30
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


that's the output for the grep.

---

### Post by el_koraco on 2011-04-30
Sorry, my bad, just the lspci -k and look for the network controller and kernel driver in use. 

You guys need to file a bug on this asap, there's no question. But perhaps something can be done in the meantime.

---

### Post by WyzeGye on 2011-04-30
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: AzureWave Device 1089
        Kernel driver in use: ath9k
        Kernel modules: ath9k


looks to me like i'm using ath9... unless the k makes it different.

---

### Post by WyzeGye on 2011-04-30
well. i'm posting this from fedora 14, maybe i'll come back to ubuntu when my wireless works. Farewell for now. Thanks for trying to help guys

---

### Post by el_koraco on 2011-05-01
There seems to be a problem with some Aetheros card and the ath9 driver in the 2.6.38 kernel. It is especially true on KDE. I suggest you try this out even though you're on Fedora, because it seems like the move to the new kernel when you decide upon it might give you further headaches. 

[http://www.jlacroix.me/?p=1999]("http://www.jlacroix.me/?p=1999")

"*Even with Kubuntu being as great as it is, I have a few complaints. The first is the wireless speed. With my Atheros card, it&#8217;s so slow it can take up to five minutes for a page to load, if it loads at all. However, this is not a Kubuntu problem, it&#8217;s a bug with the 2.6.38 Linux kernel and has already been reported, and is being worked on. It&#8217;s easily fixed by adding &#8220;options ath9k nohwcrypt=1&#8243; to the /etc/modprobe.d/ath9k.conf file (that file didn&#8217;t already exist on my system, so I had to create it) and then after a reboot, it was fine. I found that solution here (in post #3). I&#8217;m not sure what all that effects, but it does make things work. Since this bug isn&#8217;t Kubuntu&#8217;s fault, I won&#8217;t hold it against the score, but it was worth mentioning.*"

Hope this helps.

---

### Post by jepong on 2011-05-02
> **WyzeGye said:**
> well. i'm posting this from fedora 14, maybe i'll come back to ubuntu when my wireless works. Farewell for now. Thanks for trying to help guys

by the way... how did you make AR9285 work in Fedora 14? i'm having the same issue too in fedora.

regarding the topic... in maverick i used to install linux-backports-modules-wireless-maverick-generic and wireless is fixed. In natty, no such package exist but there is linux-backports-modules-net-natty-generic but still a broken wireless card.

---

### Post by WyzeGye on 2011-05-02
> **jepong said:**
> by the way... how did you make AR9285 work in Fedora 14? i'm having the same issue too in fedora.

regarding the topic... in maverick i used to install linux-backports-modules-wireless-maverick-generic and wireless is fixed. In natty, no such package exist but there is linux-backports-modules-net-natty-generic but still a broken wireless card.


It worked right "out of the box", i didn't do anything special. Though after a night of fiddling with fedora and the whole yum/rpm thing, i decided to go to linux mint debian. 

So far so good, even got burg installed. and my apt-get is going at a consistent 750kb/s

---

### Post by jepong on 2011-05-02
someone from the other thread think he found the solution for this one... i can't check it right now but I just want to share it.

[http://ubuntuforums.org/showpost.php?p=10757804&postcount=25](http://ubuntuforums.org/showpost.php?p=10757804&postcount=25)

---

