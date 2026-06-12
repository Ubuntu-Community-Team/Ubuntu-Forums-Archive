---
title: "Help! 3Com LAN PC Card"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by Brad_J on 2011-06-15
Hi. I'm trying to set up a LAMP HTTP server using Ubuntu Server 10.04 32 bit and I've run into a problem. I have a 10/100 LAN PC Card + 56K modem that I'm using to connect via ethernet to my home router and it's worked for other operating systems, including Debian, XP, and Ubuntu 10.04 desktop, but it doesn't work with Ubuntu Server apparently. It doesn't detect that anything is plugged in. 

I've tried to get linmodem to run on it in an attempt to get it to recognize that it's connected, but, since the laptop won't connect to the internet, I can't download it. I saved it to a usb stick, but I can't access the usb and I get a repeating message of "[sdb] Assuming drive cache: write through". I even tried saving it to a cd and accessing it through the disk drive and it doesn't detect that at all. 

I have no idea what to do next; I'm really new to linux/creating a server so I'm hoping that someone here has had a similar experience and found a solution.

-Brad

PS - I have no other means of connecting through the internet for this laptop, I have a few of these cards lying around somewhere that I can search for, but it was working earlier today and I'm quite sure that the card I'm using isn't faulty.

---

### Post by dandnsmith on 2011-06-15
If you can use the card in the PC which has Ubuntu Server when booting from a LiveCD, then it should be possible to look at config details when working to check aginst when booted from UServer.

---

### Post by Brad_J on 2011-06-15
I hadn't thought of booting from a live cd to access the internet, good idea. What details would I be looking for exactly and how would they be helpful to getting this resolved? Like I said, I'm pretty new to linux in general and I've barely scratched the surface on things that you are able to do in linux.

---

### Post by arrrghhh on 2011-06-15
> **Brad_J said:**
> Hi. I'm trying to set up a LAMP HTTP server using Ubuntu Server 10.04 32 bit and I've run into a problem. I have a 10/100 LAN PC Card + 56K modem that I'm using to connect via ethernet to my home router and it's worked for other operating systems, including Debian, XP, and Ubuntu 10.04 desktop, but it doesn't work with Ubuntu Server apparently. It doesn't detect that anything is plugged in. 

I've tried to get linmodem to run on it in an attempt to get it to recognize that it's connected, but, since the laptop won't connect to the internet, I can't download it. I saved it to a usb stick, but I can't access the usb and I get a repeating message of "[sdb] Assuming drive cache: write through". I even tried saving it to a cd and accessing it through the disk drive and it doesn't detect that at all. 

I have no idea what to do next; I'm really new to linux/creating a server so I'm hoping that someone here has had a similar experience and found a solution.

-Brad

PS - I have no other means of connecting through the internet for this laptop, I have a few of these cards lying around somewhere that I can search for, but it was working earlier today and I'm quite sure that the card I'm using isn't faulty.

Can you elaborate on "doesn't detect anything"?

Also, I'd like to see:```
lspci
``` and ```
ifconfig
```  Thanks!

---

### Post by Brad_J on 2011-06-15
Doesn't detect anything as in the drive spins but there is no visible response from the machine. After changing to the /root/cdrom directory I see nothing. My ifconfig, if I recall correctly, returns no ipv4 or ipv6 but does display 127.0.0.1 as the localhost and I can ping localhost but nothing else. I'll check the other command when I get access to the box later today. Thanks for your help!
 
-Brad

---

### Post by arrrghhh on 2011-06-15
> **Brad_J said:**
> Doesn't detect anything as in the drive spins but there is no visible response from the machine. After changing to the /root/cdrom directory I see nothing. My ifconfig, if I recall correctly, returns no ipv4 or ipv6 but does display 127.0.0.1 as the localhost and I can ping localhost but nothing else. I'll check the other command when I get access to the box later today. Thanks for your help!
 
-Brad

Hrm... are there any indicator lights on the card itself?  Usually if yes, there's two - one indicating a link is there (should be a solid color, green or orange are typical) and the other indicates activity, which will blink when there is Rx or Tx activity.

The color of the lights sometimes are also used to indicate speed, and perhaps sometimes duplex.  That's what I would look for as far as indication that the card is detected.

I also am making an assumption here - the card is seated when the machine is booted, you're not putting the card in after it's already up...?

---

### Post by Brad_J on 2011-06-15
Oh, I misunderstood your previous question to be about the disk drive. There are no lights on for the card, I forgot to mention that in my original post. And, when I've booted it up I've had the card seated, although I have taken it out and put it back in while running to check if it was seated properly. I'll double check when I get home and make sure that the card is in during reboot, I'll keep you posted.

---

### Post by dandnsmith on 2011-06-15
A quick place to look is System | Admin| Network Tools
which easily shows the detected interfaces, and how they're configured.

---

### Post by Brad_J on 2011-06-15
> **dandnsmith said:**
> A quick place to look is System | Admin| Network Tools
which easily shows the detected interfaces, and how they're configured.
 
Cool, I'll be sure to check it out when I get home and report back here when I do. Thanks

---

### Post by Brad_J on 2011-06-15
> **arrrghhh said:**
> 
Also, I'd like to see:```
lspci
``` and ```
ifconfig
```  Thanks!

```
lspci
``````
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:03.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:03.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
``````
ifconfig
``````
lo          Link encap:Local Loopback
            inet addr:127.0.0.1   Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING    MTU:16436    Metric:1
            RX packets:16 errors:0 dropped:0 overruns:0 frame:0
            TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:1112 (1.1 KB)   TX bytes:1112 (1.1KB)
```Hope this helps!

-Brad

---

### Post by Brad_J on 2011-06-15
> A quick place to look is System | Admin| Network Tools
which easily shows the detected interfaces, and how they're configured.     Sorry it took so long to respond, I seem to have misplaced all of my boot disks and had to burn a new copy of ubuntu. I took two pictures of the Devices window with my phone, it gives me eth0 which isn't shown in when I run ifconfig on the server. I'm not sure how this helps, but I attached the pictures anyway, sorry for the low resolution. Tell me if I'm giving you the wrong window, or if that tells you anything important that will help to solve this. Thanks.

-Brad

---

### Post by dandnsmith on 2011-06-16
Don't worry about the resolution - it's clear enough!

OK, so you have a workable eth0, since that shows it, complete with addresses, mask, and traffic.

Now the tricky bit is to establish why it doesn't get picked up by the server installation. I wonder if it shows on either of:

lspci |grep -i eth
sudo lshw |grep -i eth

we should also get a trace in /var/log/messages or /ver/log/messages.1 (look for eth in those)

---

### Post by arrrghhh on 2011-06-16
Oh... I thought you were running Ubuntu Server.  I'll step out :p.

---

### Post by Brad_J on 2011-06-16
> **dandnsmith said:**
> Now the tricky bit is to establish why it doesn't get picked up by the server installation. I wonder if it shows on either of:
 
lspci |grep -i eth
sudo lshw |grep -i eth
 
we should also get a trace in /var/log/messages or /ver/log/messages.1 (look for eth in those)
Would you like me to run those through the server or through the desktop live session?

---

### Post by Brad_J on 2011-06-16
> **arrrghhh said:**
> Oh... I thought you were running Ubuntu Server. I'll step out :p.
 I am :p

---

### Post by dandnsmith on 2011-06-17
> **Brad_J said:**
> Would you like me to run those through the server or through the desktop live session?

The server - we already know they're OK for the LiveCD session

---

### Post by Brad_J on 2011-06-18
> **dandnsmith said:**
> 
Now the tricky bit is to establish why it doesn't get picked up by the server installation. I wonder if it shows on either of:

lspci |grep -i eth
sudo lshw |grep -i eth

Nothing...:(
> **dandnsmith said:**
> 
we should also get a trace in /var/log/messages or /ver/log/messages.1 (look for eth in those)
```

[ "eth" not found ]
```In fact, there is nothing relevant to the commands that I ran, the only thing that shows up for today is the authentication for the sudo call that I made with lshw |grep -i eth.

---

### Post by dandnsmith on 2011-06-19
I'm completely at a loss now.
I think you've tried LiveCD for the same version of Ubuntu desktop as that for Ubuntu Server, and the expected network stuff just isn't showing up.
If there's one thing I do expect to find in a server it's the networking (the prime raison d'etre, after all).
The only other suggestion I have is to use the desktop version as server instead.
You might want to strip out the bits you'll never use, and add some of the networking bits, to get to the right end position.

HTH

---

### Post by Brad_J on 2011-06-19
> **dandnsmith said:**
> I'm completely at a loss now.
I think you've tried LiveCD for the same version of Ubuntu desktop as that for Ubuntu Server, and the expected network stuff just isn't showing up.
Yup, I used 10.04 LTS for both.
> **dandnsmith said:**
> The only other suggestion I have is to use the desktop version as server instead.
You might want to strip out the bits you'll never use, and add some of the networking bits, to get to the right end position.
I think I'm gonna try for a reinstall and see if that fixes anything, if it doesn't I'm gonna go for Debian minimal because the laptop can't handle running a GUI. Thanks for your help, I'm gonna leave this thread open for a bit and see if I can get things working.

---

### Post by dandnsmith on 2011-06-19
OK - hope to hear you were successful

---

### Post by Brad_J on 2011-06-20
> **dandnsmith said:**
> K - hope to hear you were successful
I reinstalled Ubuntu Server with no luck, so I went with Debian. The card works fine now, but, there are some differences with some other things that I was just getting used to with Ubuntu, oh well... I'm going to mark this thread as solved as I'm no longer having any issues with my card. Thank you very much for all your help.

-Brad

---

