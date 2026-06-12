---
title: "Ipw2200 - Power:off! Why?"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by jollyr0ger on 2006-06-07
Hi! I've installed Kubuntu 6.06, some days ago and the wireless (centrino integrated module, the ipw2200 type) were working so good.
But now i don't know why, but it stops working.
When i try to find some wireless lan, it find nothing, and ask me every times to turn on the wireless module. I do it, but it find nothing again...

These are the result of a little search in the shell:
```
# iwlist eth1 scan
eth1      No scan results

# iwlist eth1 power
eth1      Current mode:off

# iwconfig
eth1      radio off  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# dmesg
[...]
[4294690.345000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[4294690.345000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[4294690.345000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[4294690.345000] ACPI: PCI Interrupt 0000:06:03.0[A] -> GSI 17 (level, low) -> IRQ 177
[4294690.345000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294690.546000] ipw2200: Radio Frequency Kill Switch is On:
[4294690.546000] Kill switch must be turned off for wireless networking to work.
[4294690.546000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[4294690.619000] cs: IO port probe 0x100-0x3af: clean.
[4294690.621000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294690.622000] cs: IO port probe 0x820-0x8ff: clean.
[4294690.622000] cs: IO port probe 0xc00-0xcf7: clean.
[4294690.623000] cs: IO port probe 0xa00-0xaff: clean.
[...]
[4300176.470000] ipw2200: Failed to send TX_POWER: Command timed out.
[4300181.952000] ipw2200: Failed to send TX_POWER: Command timed out.
[4300270.381000] device eth1 entered promiscuous mode
[4300363.787000] device eth1 left promiscuous mode
[4300377.701000] device eth1 entered promiscuous mode
[4300383.122000] device eth1 left promiscuous mode
```

What i have to do?

---

### Post by noneofthem on 2006-06-08
I have got the exact same problem. There must be more people with that problem. I hope this will be fixed soon. Any help on this one is highly appreciated...

None Of Them

---

### Post by chambjon on 2006-06-09
I am having the same problem,
did you find any answers.
My info looks exactly the same.
I have a dell 700m with an intell centrino](*,)

---

### Post by noneofthem on 2006-06-09
Unfortunately not. Still looking. I will post the answer here once I know how to fix that.

Good luck!

Amir

---

### Post by wofritz on 2006-06-09
Hi all,

I had the same problem with my Acer Travelmate 292LMi. If you have Windows on your machine, you could do this test: boot to Windows, enable the Wireless, then reboot to Ubuntu wtihout power off. If the radio kill button message is now gone, your radio switch button is not recognized in Ubuntu. Too bad. You can try the "acerhk" driver to enable the radio button. Go to
[http://www2.informatik.hu-berlin.de/~tauber/acerhk/](http://www2.informatik.hu-berlin.de/~tauber/acerhk/)
to find out if your laptop is supported.

Wolfgang

---

### Post by pnael on 2006-06-09
Yes it means that your radio is off. Usually you have an off/on switch to enable
the wireless card but be carefull. It can be on with the wireless led off.
So to be sure run iwconfig and check if it is off. Switch on the wireless card
with your button and check with iwconfig that it is on.

It works like that on my hp nc6120 with an ipw 2200 card.

Hope it helps.
Philippe

---

### Post by dachandr on 2006-06-15
try to toggle promiscuous:
ifconfig eth0 promisc

---

### Post by manubreizh on 2006-06-15
hi,
i have the same problem, and promisc doesn't seem to do anything to solve it (or i used it badly ?) ;
acerhk neither ; and google search just make me feel less alone with this trouble...
just to be more precise : i have a nec versa m500 laptop, dapper drake (kubuntu), speedtouch.ng installed and network manager ;the wifi interface is active (in system settings), but nothing happens when i'm in a place with wifi running (my laptop doesn't even recognize and find a network !) ; i haven't windows on this machine (only kubuntu), and have never used wifi with windows (migration as soon as i recieved the machine...).
i even cannot write in the document named : /sys/bus/pci/drivers/ipw2200/0000:01:01.0/rf_kill , in which there is only "2" written (which means radio is off if i remember well...) : it says : ""/sys/devices/pci0000:00/0000:00:1e.0/0000:01:01.0/rf_kill" E667: Fsync failed."
so, anyone can help ?

---

### Post by gm__ on 2006-06-17
Same problem here with ,acer aspire/ dapper drake , first it seemed to work now it 
wont work anymore.

manubreizh if you wanna write in a document type:

sudo gedit /path to your document

---

### Post by wofritz on 2006-06-18
[QUOTE=gm__]Same problem here with ,acer aspire/ dapper drake , first it seemed to work now it 
wont work anymore.
[/QUOTE]

Maybe you should give acerhk a try (see my post above). It made the radio switch work on my Acer Travelmate 292LMi. The Website lists a bunch of acer aspire as supported.

If you have a Windows partition on your laptop (with working Wirelesss, of course), you could do the following test:

1. Boot to windows, start wireless.
2. Reboot to Linux **without power down**

If your radio is now working, acerhk is definitely worth a try.

Wolfgang

(Just sitting in the garden with my Acer and Wireless)

---

### Post by mrk_0 on 2006-06-21
Hi, 

i have an acer travelmate 290 laptop, and my ipw2200 was working well with ubuntu breezy. I only had to install acerhk driiver to be able to switch the radio button on. It was working perfectly!

Now, with ubuntu dapper, i installed the acerhk to solve the same problem, but it isn't able to switch the radio on! 

The ipw220 wireless card is working well, but to switch the radio on, first i have to boot windows, switch the radio button on, and then reboot with ubuntu. It's the only way i'm be able to use my ipw2200 in Dapper! This is not a confortable option... Can someone help? Maybe there is something different with the new kernel (dapper kernel)...

If i can't find a solution i will have to install breezy again...

---

### Post by mrk_0 on 2006-06-27
Hi,

my ipw2200 radio switch it's working now...

After acerhk driver installation i wasn't able to use the driver... I was missing something. I had to modprobe the driver with the following parameters:

$ modprobe acerhk force_series=290 usedritek=1
$ echo 1 > /proc/driver/acerhk/wirelessled

---

### Post by mcadoar on 2006-09-17
I have a compaq presario R3430US with a very similar issue.  It has a broadcom wireless card and as with most others, it doesn't work unless I boot into windows, fix it, then reboot into linux.  With that said, this may help someone else fix this problem:

In windows, if I go into device manager and edit the properties of the card, there's a property I can set (yes, in software, without physically pressing the switch) that will toggle the radio on and off.  In fact, sometimes in windows the hardware switch fails but this toggle in device manager works every time.  Therefore, if there was a way that iwconfig or such could do this same toggle, I believe it would fix this problem.  It appears to me this acerhk is doing the same thing, so prhaps whoever wrote it could let us know their secret?

---

### Post by rossman on 2006-09-20
I was having the same problem and this "fix" worked for me.  :cool:  Thanks Wolfgang!  I wonder *why* this works?

> **wofritz said:**
> 
1. Boot to windows, start wireless.
2. Reboot to Linux **without power down**


---

### Post by mrlarone on 2006-09-23
i've managed to get my ipw2200 working by installing the latest driver and firmware and the using the following cmd to turn the card on.

$sudo iwconfig eth1 power 1

use this to turn it off

$sudo iwconfig eth1 power 0

eth1 is the name of my wifi card so you may need to change this for your card.

---

### Post by happy-and-lost on 2006-09-23
I had that problem on my Dell Inspiron 6000.

I found the solution in the wifi card BIOS settings.

---

### Post by r3fuG4d0 on 2006-09-26
I have the same exact problem with my laptop an AOpen 1557. In windows I have a Launch Manager to detect the radio buttons, but that software isn't available for Linux distros ](*,) 

I've tried to turn it on in Windows and restart in Ubuntu but still has no effect... will now see if in bios is an otpion to allways turn it on when computer starts... if anyone has got nay idea to do it simplier in Linux please tell me :mrgreen: 

Greetz :)

---

### Post by Early Uiniverse on 2006-09-27
Although I'm a complete newbie to Linux, after 3 days of fighting with wireless I might have something to say...

First, as was said above - no light on a button doesn't necessarily mean it is not on to turn on the LED with ipw2200 one should create a file in

/etc/modprobe.d/

called ipw2200 with the line

options ipw2200 led=1

Second, during the last 3 days my button didn't work from time to time and it always could be helped by

iwconfig eth1 txpower auto

i.e. eth1 is my wireless interface and the setting auto overrides any script bolcking the radio power. One can perhaps try also "on" instead of auto.

It might not help but anyway at least a try, I can understand how desprate one is :-k

---

### Post by siiib on 2006-09-27
yeah i just got the disease  on my acer 1680.. just upgraded to 2.6.18 and now the wireless is as dead as a dodo.. worked flawlessly before in 2.6.15 .. tried acerhk and reboot fix but none of them work for me..
dmesg reports a -2 error which i assume means card switched off.. interesting](*,)

---

### Post by siiib on 2006-09-28
i fixed my problem which was a kernel update problem.. it may not be relevant any more but i'll post the solution.. it may help someone

under my circumstances if i did a dmesg | grep ipw2200 i got a -2 error.. this was because the firmware files were missing from /lib/firmware.. there were only entries for the old kernel.. so i created a new directory whose name coincided with the new kernel and copied the fw files across (actually i copied the lot) ..i also noticed that some of the files from /usr/src/kermel headers../include/config/ipw2200 were also missing.. so i copied them across as well..

i'm sure that the same result would come about if you downloaded the intel drivers and remade and installed them.. probably a cleaner option.. oh well its working anyway.. 

hth simon

---

### Post by n3Cre0 on 2006-10-02
Try looking in your BIOS.

I also got an ipw2200 and if I accidently switch off my wifi by pressing a button I reboot and enable it again in the BIOS.

---

### Post by Nopius on 2006-10-10
I had the same problem in my HP nc6120 laptop. Now it's fixed. 

I did install multiple drivers (related to WiFi) from Compaq site on my Windows, after that my wireless key become working even in Linux and after reboot. This key is located on the right side after Power button and "i" button (on this model). Now pressing that key turns on and off a blue LED. Bluetooth become On. But WiFi Kill switch still was ON (even when you this blue LED was lighting).

Now I read that in this laptop we have restricted ethernet controller, that works only with EITHER 100-base-T OR with WiFi, but not simultaneously.

So, to get WiFi working you should pull out your ethernet cable. It seems to be that magic 'Kill Switch'. And also you should press WiFi button (the light is On).

---

### Post by curumbao on 2007-11-21
OK, I've been googling an diving through forums a lot of days, If they paid me for this I would be very rich.

I have an Acer Travelmate 4000 with the hated ipw2200. I had edgy, upgraded to fiesty and no problem. But I made a clean installation of kubuntu gutsy, and another of fluxbuntu, and in both of them I had this problem with kill switch.

Another problem I had was the wifi-led, that didn't work.

And I found the final answer here [http://www.duskzone.it/works/linux/c300howto/debianLinux_on_acer_travelmateC300.php]("http://www.duskzone.it/works/linux/c300howto/debianLinux_on_acer_travelmateC300.php")

The basic is installing the ieee80211 subsystem, and the ipw2200 driver and firmware, as we all knew. Having acerhk configured and loaded, we also knew.

 But what I hadn't seen before was the final step: 

# echo on > /proc/driver/acerhk/wirelessled


(now I checked other webs I saw, and they put echo 1, not echo on)

And AFTER that load the module ipw2200

# modprobe ipw2200


As for the led I found it somewhere else here at ubuntu forums, and consist on creating a file in
 
 /etc/modprobe.d/
 
 called ipw2200 with the line
 
 options ipw2200 led=1


So when the card is enabled the light would light :p

---

### Post by ola-x on 2007-11-24
For the HP tablet PC (Compaq tc4200) it was quite simple: Theres an on/off button on the left side on the machine, near the power switch. By the way, the pen function on the tablet PC works great with 7.04. Havent testetd Gutsy yet...

---

