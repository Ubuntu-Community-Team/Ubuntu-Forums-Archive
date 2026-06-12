---
title: "Eee 1000HE wifi only works from Live USB"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by slthytove on 2009-03-20
***UPDATE:** My original hypothesis that the problem was related to whether or not I was booting from a Live USB image or the hard disk has proven to be incorrect. See the 2nd post for more info.*


Hello, all. I am running into the strangest issue with my new Asus Eee PC 1000HE netbook. Here's the narrative:

I'd like to install Ubuntu on this machine. I first decided to try out the Jaunty Netbook Remix (now in alpha6), which I put on a USB flash drive and ran. Everything seemed to work great from the LiveUSB, including wifi and the integrated webcam, so I decided to install it and give it a shot.

Strangely enough, when I booted it up after installing it, wifi no longer works. All of the access points show up when I click on the network icon in the top panel, but I am unable to connect to any of them. I am prompted for my WPA password like usual, but it doesn't connect.

Thinking perhaps it was an issue caused by the alpha status of Jaunty, I decided to try it with Intrepid. I ran into the exact same issue. I'm posting this now from the Live USB version of Intrepid (created using UNetbootin).

Here's what I get when I run the following commands from the Live USB on Intrepid:
```

$ **lspci -nn |grep 'Wireless'**
01:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```
```
$ **iwconfig wlan0**
wlan0     IEEE 802.11bgn  ESSID:"Gemini"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:21:91:D9:CB:A1   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=85/100  Signal level:-40 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
```
$ **lsmod | grep 'ath'**
ath9k                 274232  0 
mac80211              216820  1 ath9k

```
```
$ **dmesg |grep -e ath -e wlan0**
[   54.107547] ath9k: 0.1
[   54.109928] ath9k 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   54.109952] ath9k 0000:01:00.0: setting latency timer to 64
[   54.624551] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   75.128377] wlan0: authenticate with AP 00:14:bf:7c:48:8a
[   75.130626] wlan0: authenticated
[   75.130652] wlan0: associate with AP 00:14:bf:7c:48:8a
[   75.132923] wlan0: RX AssocResp from 00:14:bf:7c:48:8a (capab=0x401 status=0 aid=1)
[   75.132934] wlan0: associated
[   75.145487] wlan0: disassociating by local choice (reason=3)
[  231.771786] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  231.773297] wlan0: authenticated
[  231.773315] wlan0: associate with AP 00:21:91:d9:cb:a1
[  231.776244] wlan0: RX AssocResp from 00:21:91:d9:cb:a1 (capab=0x431 status=0 aid=4)
[  231.776259] wlan0: associated
[  320.212103] wlan0: no IPv6 routers present

```
```
$ **uname -mr**
2.6.27-7-generic i686

```

Running from the installed version of Intrepid gives very different results. I can't easily copy and paste the output from the installed version, but the gist of things is this:
It still uses the same ath9k module, but instead of authenticating in the dmesg output as above, it tries 3 times, then gives a "timed out" message. At this point, the Network Manager also prompts me to re-enter the password, which I do, and receive the same issue.

On the jaunty alpha, after a couple times entering the password, the dmesg logs started showing something about "directly associating," but I still had 3 tries followed by a timeout, repeatedly.

Thanks in advance for any and all help!

---

### Post by slthytove on 2009-03-20
Some updates... it seems that the problem is unrelated to whether or not Ubuntu is run from a LiveCD, so my original subject was a bit of a misnomer. I am now booting off of the LiveUSB (non-persistent) version of Intrepid, and the same issues that I was having with wifi are present. I've connected via wired LAN so I can paste the results of the same commands as before.

Now I'm pretty stumped. I'm in the same room as the access point, and as you can see from the first post, the signal quality is pretty good. I've tried changing the router to support N only, G only, and G/N, and all of them had the same flaky results.

```
$ **lspci -nn |grep 'Wireless'**
01:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

```
```
$ **iwconfig wlan0**
wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
```
$ **lsmod | grep 'ath'**
ath9k                 274232  0 
mac80211              216820  1 ath9k
```
```
$ **dmesg |grep -e ath -e wlan0**
[   56.030898] ath9k: 0.1
[   56.030976] ath9k 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   56.030999] ath9k 0000:01:00.0: setting latency timer to 64
[   56.805172] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   74.499433] wlan0: authenticate with AP 00:22:75:31:e6:c1
[   74.528178] wlan0: authenticated
[   74.528205] wlan0: associate with AP 00:22:75:31:e6:c1
[   74.531652] wlan0: RX AssocResp from 00:22:75:31:e6:c1 (capab=0x401 status=0 aid=1)
[   74.531676] wlan0: associated
[   74.532429] wlan0 (WE) : Wireless Event too big (338)
[   74.544950] wlan0: disassociating by local choice (reason=3)
[  140.120787] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  140.316145] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  140.516112] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  140.716158] wlan0: authentication with AP 00:21:91:d9:cb:a1 timed out
[  152.582724] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  152.582819] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  152.780180] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  152.980141] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  153.180141] wlan0: authentication with AP 00:21:91:d9:cb:a1 timed out
[  293.163689] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  293.360135] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  293.561082] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  293.760124] wlan0: authentication with AP 00:21:91:d9:cb:a1 timed out
[  303.341611] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  303.341745] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  303.540135] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  303.740119] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  303.941120] wlan0: authentication with AP 00:21:91:d9:cb:a1 timed out
[  511.205043] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  511.404148] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  511.604153] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  511.804094] wlan0: authentication with AP 00:21:91:d9:cb:a1 timed out
[  521.180010] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  521.188638] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  521.389134] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  521.588116] wlan0: authenticate with AP 00:21:91:d9:cb:a1
[  521.788147] wlan0: authentication with AP 00:21:91:d9:cb:a1 timed out
[  621.171261] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  819.268733] wlan0: deauthenticated

```
```
$ **uname -mr**
2.6.27-7-generic i686

```

---

### Post by Hauke on 2009-03-21
Hi

Have you tried updating the kernel to the newest version. There are some fixes for the wireless driver included.

If this does not help try out the backported drivers out of the linux-backports-modules-intrepid package or the newest version directly from [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) .

PS: I also like to buy an Asus Eee PC 1000HE. Is everything else working with Ubuntu? Is suspend/resume working?

---

### Post by slthytove on 2009-03-22
I tried out the backports package for Intrepid, and had much more consistent results with the wireless. First of all, I was able to connect most of the time (hooray!), but my connection also consistently dropped out at seemingly random intervals (boo!). Running a ping for a few minutes showed packet loss at around 20-30%, with the packet loss generally occurring in isolated segments of 20-30 packets dropped in a row.

In a fit of something approaching desperation, I decided to do an apt-get dist-upgrade to the jaunty alpha, to see if anything worked better. Unfortunately, I still ran into the same issues.

I then tried setting up ndiswrapper using the ASUS-supplied driver for the wireless card, but ran into some issues with the driver. ndiswrapper seemed to think the hardware was detected, but a peek into dmesg revealed lines like the following:
```
DLL initialize failed for athw.sys
```

Since ndiswrapper was an utter failure, I removed it and tried putting things back the way they were... and I couldn't even get them into that state any more!

Finally, I was preparing to try the newest version of the Linux wireless drivers as you suggested. On that page, I noticed a reference to the backports package for jaunty. Thinking it couldn't hurt, I decided to install those...

```
sudo apt-get install linux-backports-modules-jaunty
```

Well, wireless seems to be quite a bit better, although the connection still randomly drops out every now and then. I'm down from 30% packet loss to around 5%, although there has been at least one instance where I had to restart the computer before I could get the wireless card to reconnect. If the issues become frequent, then I think I'll try the latest version from wireless.kernel.org to see if it does any better. Thanks for the pointers!


To answer your questions about the 1000HE - it seems to work well with Linux other than the wifi issues. I haven't really put it through its paces yet, but I can report that the following work as expected:
[LIST]
[*]Suspend via Fn hotkey or closing the lid (if set up in Power Management)
[*]Display brightness Fn keys
[*]Volume Fn keys
[*]The external monitor Fn key seems to flash the display at the very least. I don't have an external monitor to test it with at the moment.
[*]Only the leftmost of the top softkeys does anything, although the others may generate X events.
[*]Sound works - the volume is initially quite low, fixable by adjusting all the different mixers in sound preferences to their max.
[*]Certain multitouch gestures work on the trackpad: two finger vertical scroll and three-finger tap for right-click I know for sure. I wish this was more configurable, though...
[*]The built-in camera and microphone both work with Cheese.
[*]Over/underclocking works - I'm using two instances of the CPU Frequency Scaling Monitor applet to set both of the cores to Ondemand mode for some excellent powersaving.
[*]The battery is quite amazing. I haven't actually timed a complete discharge of the battery, but I have used it on battery for more than 4 hours straight.
[*]The SD slot works as expected.
[/LIST]

That said, there are a couple things that don't work (aside from the wifi issues):
[LIST]
[*]The wireless enable/disable Fn key. I'm also not sure that the power to the wireless adapter gets cut off if I use the network applet to disable it.
[*]Other Fn/soft keys not mentioned above, including the trackpad enable/disable key.
[*]I haven't tested bluetooth.
[/LIST]

All-in-all, it's a great machine - it seems a shame that you can't buy it with Linux preinstalled!

---

### Post by thexcat on 2009-03-23
I'm having similar issues with wifi.  

I did notice that when logging onto a network with no password, wifi stays connected without any issues.  

It's only networks with passwords that stop working after some time (prompt for password pops up, etc...).   

Hopefully somebody will get this resolved soon :(

---

### Post by IanW on 2009-03-24
> **slthytove said:**
> All-in-all, it's a great machine - it seems a shame that you can't buy it with Linux preinstalled!

True, but I'm currently talking to Asus about getting a partial refund for the unwanted WindowsXP installation (see [Wikipedia](http://en.wikipedia.org/wiki/Windows_refund)).

---

### Post by slthytove on 2009-03-24
> **IanW said:**
> True, but I'm currently talking to Asus about getting a partial refund for the unwanted WindowsXP installation (see [Wikipedia](http://en.wikipedia.org/wiki/Windows_refund)).

Can you let us know how that goes, and if you have any insights to offer others who might like this refund? I'm very interested in doing the same, since I never agreed to the original EULA when I first booted up the machine.

---

### Post by scottro on 2009-03-28
I'm having the same issue with Jaunty and wireless dropping after a few minutes.  It seems to work better with CrunchBang's eee version (as well as Mint's version 6, Fluxbox release candidate.

So far, it's worked best in Fedora 11 (Alpha) where it is consistently reliable.  

How much of this is due to each distribution's kernel, I have no idea, I haven't done any real troubleshooting.  In Fedora, for what it's worth, I connect through command line with wpa_supplicant and dhclient.  With Cruncheee (the EEE version) I found that I had much better results removing NetworkManager and installing wicd, however this hasn't fixed the problem in Jaunty.

As for the refund of the MS tax, yes, please keep us posted.  Although I think it's something all of us who immediately wipe Windows should do, I fear that I never have the time or energy to try to pursue it.

---

### Post by crispeto on 2009-03-31
I woke up this morning and had a reply from a different thread and someone told me to install "linux-backports-modules-jaunty". I did that this morning and so far it's been connecting every time. Hope this helps.

---

### Post by scottro on 2009-03-31
I see they've removed the thank you thingies that they used to have (and also see their quite reasonable explanation.)

However, I do want to thank you.  I've installed the backports as suggested and it seems to fix the constantly dropped connection.

---

### Post by azdavef on 2009-04-02
I installed eeebuntu standard on my daughter's 1000HE two weeks ago as a dual boot.  Used Wicd and Blueman as the only modifications and I haven't heard from her since.  I am taking this as a positive.... I have used Wicd since Feisty without headaches...

---

