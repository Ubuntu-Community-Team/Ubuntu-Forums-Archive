---
title: "Ndiswrapper Issues."
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by angelam on 2011-09-26
Hi,

I'm totally new to Ubuntu and I really want to get this working. I install Ubuntu on an older Compaq Presario laptop. Turns out the wireless firmware is not compatible.

I have been trying to get this to work for the last several hours. So far I managed to figure out how to get Ndiswrapper set up. I found the driver .inf I added in the Windows Network Drivers gui thing and it says its ok and "Hardware Present: Yes". But even after restarting my computer I can't get wireless working.

I have no idea what to try now. I'm totally at a loss and would really appreciate some help.

----

UPDATE: 
I have gone through all the checks on the general troubleshooting thread. Everything passes the checks. I'm a little at a loss for step 3.

network:0 says driver=8139too 

I think that is the correct driver. The wireless in the compaq is a realtek 8139 so that makes sense, that's the driver I downloaded. 

I should add at the end of that output *-network says DISABLED

step 5 doesn't work "dmesg | grep -e ndis -e wlan" it has no output and goes straight to the next line.

Other than that everything from the checks shows the info it's supposed to.

---

### Post by chili555 on 2011-09-26
> The wireless in the compaq is a realtek 8139Realtek 8139 is a wired ethernet device, not wireless. Let's check a few things. Please open a terminal and run and post:```
lspci -nn | grep 0280
ndiswrapper -l
```Thanks.

---

### Post by collisionystm on 2011-09-26
Did you check to see if there is a physical 'On / Off ' switch for the wireless on the computer? I had an older presario, silver and black. There was a physical switch on the front of the computer.

---

### Post by angelam on 2011-09-27
> **chili555 said:**
> Realtek 8139 is a wired ethernet device, not wireless. Let's check a few things. Please open a terminal and run and post:```
lspci -nn | grep 0280
ndiswrapper -l
```Thanks.

Thanks so much for the reply. That's useful to know. OK so I guess now it's a matter of finding out what is the correct driver?

The first command outputted:

Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN controller [14e:4318]

The second one said:
```

bcmwl5: driver installed
device (14E4: 4318) present (alternate driver: ssb)
netrtl32: driver installed
device (10EC:8139) present (alternate driver: 8139cp)

```
I'm wondering is there any command to output what hardware is in the laptop?

---

### Post by angelam on 2011-09-27
There is a physical button on the computer but I've confirmed it's pressed out several times throughout the process.

---

### Post by chili555 on 2011-09-27
> I'm wondering is there any command to output what hardware is in the laptop?Absolutely. Please do:```
sudo lshw
```We don't need to see it. We have what we need already.> bcmwl5: driver installed
device (14E4: 4318) present (alternate driver: ssb)
netrtl32: driver installed
device (10EC:8139) present (alternate driver: 8139cp)First, the native driver will run the ethernet just fine. Let's remove netrtl32. Please do:```
sudo ndiswrapper -e netrtl32
```Next, let's see what kernel messages there are about ndiswrapper; maybe we can find out why it doesn't drive your wireless.

If we can't get ndiswrapper going, it's pretty easy to get the native b43 and ssb driver going. Is your wired ethernet working?

---

### Post by angelam on 2011-09-27
Thanks so much for your help.

I removed the netrtl32 driver. It didn't have any output when I did it but now when I type ndiswrapper -l it only shows the one first driver. 

I'm not sure how to get the kernel messages? 

My wired ethernet is working. Wirless is not working. Do I need to restart to see if this effected it or is there another step I should take next first.

---

### Post by chili555 on 2011-09-27
> I'm not sure how to get the kernel messages? Oops! More coffee, Chili! Wake up!!!

I didn't give you the command; sorry about that!```
dmesg | grep ndis
```> is there another step I should take next first. Probably several; which they are depends on the result from kernel messages above.

---

### Post by angelam on 2011-09-27
Thanks so much, ok the output is:
```

ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
usbcore: registered new interface driver ndiswrapper

```

---

### Post by chili555 on 2011-09-27
> [COLOR="Red"]usb[/COLOR]core: registered new interface driver ndiswrapperThis just get's more interesting by the minute!! I am actually shocked that there is no complaint or other message about ndiswrapper. Let's see:```
iwconfig
sudo modprobe ndiswrapper
```There may be a warning or error; the exact nature is helpful, so please note and post it.

---

### Post by angelam on 2011-09-27
> **chili555 said:**
> This just get's more interesting by the minute!! I am actually shocked that there is no complaint or other message about ndiswrapper. Let's see:```
iwconfig
sudo modprobe ndiswrapper
```There may be a warning or error; the exact nature is helpful, so please note and post it.


Ok so the first command says: 
```

lo            no wireless extensions.
eth0        no wireless extensions.
wlan0     IEEE 802.11bg ESSID:off/any
              Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm
              Retry long limit:7 RTS thr:off Fragment thr:off
              Power Management: off

```

And the second command  doesn't seem to have any output it just jumps to the next line?

---

### Post by chili555 on 2011-09-27
You seem to have a wireless interface wlan0. Does it scan?```
sudo iwlist wlan0 scan
```When you click the Network Manager icon, does it see networks? As always, any errors or warnings are helpful.> And the second command doesn't seem to have any output it just jumps to the next line? That's good news because there is no error or warning.

---

### Post by angelam on 2011-09-27
> **chili555 said:**
> You seem to have a wireless interface wlan0. Does it scan?```
sudo iwlist wlan0 scan
```When you click the Network Manager icon, does it see networks? As always, any errors or warnings are helpful.That's good news because there is no error or warning.

It doesn't look like it scans the message I get is:

```

wlan0 Interface doesn't support scanning : Network is down

```

---

### Post by chili555 on 2011-09-27
I wonder why the 'network is down.' Let's see:```
dmesg | grep wlan
```Ordinarily, I'd suggest we bail out on ndiswrapper but we see no errors or warnings.

Is the ethernet cable detached? Network Manager will disallow wireless if wired is available.

---

### Post by angelam on 2011-09-27
Thanks again for coming back and helping.

It looks like "dmesg | grep wlan" doesn't output anything. It just jumps to the next line. 

I didn't have the ethernet plugged in at the moment when I ran that test. I've been plugging and unplugging it to share between that computer and another.  

Any other thoughts or did we hit a roadblock? I can always go back to the old OS and try out ubuntu on some other computer.

---

