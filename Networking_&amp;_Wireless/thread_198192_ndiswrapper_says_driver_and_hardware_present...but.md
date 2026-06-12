---
title: "ndiswrapper says driver and hardware present...but nothing."
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by kewldude606 on 2006-06-16
I am using the Windows Wireless Drivers panel under the System --> Administation.  I installed the exe files on a windows machine and got the proper inf and sys files, and loaded them into that panel.  Now it is saying "Driver present, hardware present".  I still can't connect.  I was searching everywhere and this is the info I think might help:
[LIST]
[*]I have no wlan0... interfaces, only eth0 to 2.  This is some of the output of iwconfig:```
eth2      IEEE 802.11b  ESSID:"Finnie"
          Mode:Auto  Channel=10  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```I put the SSID and Channel in there by myself.
[*]Before I did the whole ndiswrapper stuff, my network settings listed my wireless card as being wireless and active.  It still didn't work when I unplugged the ethernet and rebooted, however.
[*]My WAP has no encryption
[*]I am using a Linksys WUSB54G
[*]It is connected via a hub (powered hub)..worked under Windows.
[*]I started to follow the [Installation directions from the ndis wiki]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Load_module"), but got stuck right above "Configure Interface."  "ndiswrapper: driver ''driver1'' added" and "wlan0: ndiswrapper ethernet device xx:xx:xx:xx:xx:xx" weren't in the system log (dmesg | grep ndis is the command I used).  The lights on the card did light up, but it was the power light and not the activity light.  
[/LIST]
Thanks for any help you can give.

---

### Post by Dr. Nick on 2006-06-16
You say you had a wireless in your control panel before starting ndiswrapper?

That means ubuntu had drivers for your card already, they just werent working.

To get ndiswrapper to work you have to disable the built in drivers, if you dont it will never attempt to use ndiswrapper.

Run 

**lsmod**

from a terminal and look for anyting named prism, If your card is usb and you dont have a prism entry then post all that appears on the line starting with **usbcore. **

You can remove any listed module by running

sudo modprobe -r [I]module

[/I]If you see a module for your card loaded try to remove it then run

sudo modprobe ndiswrapper

any time you reboot or unplug the card the module will get reloaded until you remove the file itself. If removing the module works ill help you remove the file if needed

---

### Post by kewldude606 on 2006-06-17
I didn't see prism anywhere.  Here is the usbcore line```
usbcore               130692  7 ndiswrapper,hci_usb,islsm_usb,usbhid,ehci_hcd,uhci_hcd
```

These are the things I saw relating to wireless: ndiswrapper, ieee80211, ieee80211softmac, ieee80211_crypt.  I did the modprobe thing to ndiswrapper, and I tried to do it to ieee80211 (and all the rest starting with ieee80211) but I got an error, "FATAL: module in use."

---

### Post by blurredbrain on 2006-06-17
YOu know, I'm having the exact same issue, only I have an internal broadcom card on my Compaq Presario v2000, and its showing up under usbcore with the ndiswrapper.  Is this my problem?

---

### Post by Cinvent on 2006-06-17
I have a Compaq Presario V2000 with an AMD64 Turion. I tried several options, but the only way it works for me was using a 64-bit driver.

On the ndiswrapper wiki 

[INDENT][http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)[/INDENT]

I used the drivers from entry number 7.

[INDENT]
Driver: bcmwl5.inf, BCMWL564.SYS, had to go for a 64 bit version from [[ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip]](ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip])
[/INDENT]

Perhaps you could try this. I hope it works.

---

### Post by kewldude606 on 2006-06-17
Cinvent, you are responding to blurredbrain, right?  Because I have a 32 bit proc.

---

### Post by Dr. Nick on 2006-06-17
If you have a built in module for you wireless card showing up on the same line as ndiswrapper it will take priority, So if you have a builtin module that doesnt work and you want to use ndiswrapper you must remove the builtin module before ndiswrapper will work

If you have a 64bit install of ubuntu and want to use ndiswrapper you will need a windows 64bit driver, You can not use a 32bit driver with ndiswrapper 64bit.

But if you have a standard 32bit ununtu (thus ndiswrapper) install you can use any 32bit driver, just not 64.


@kewldude606

I googled the islsm_usb module on your usbcore line and it appears to be the native driver you are looking to destroy ;)

Try 

**sudo modprobe -r islsm_usb**

and see if ndiswrapper starts to work. If it does you will either have to blacklist the islsm_usb file to keep it from starting on the next boot, or just delete the file entirely

---

### Post by kewldude606 on 2006-06-17
I did the sudo line you suggested.  Now the Windows Wireless Drivers still says Driver and hardware present, but in iwconfig everything is listed as "no wireless extensions."  eth2, where the wireless extensions used to be, isn't listed anymore.  I then did sudo modprobe islsm_usb everything was back to the way it was in the 1st post by me.

---

### Post by blurredbrain on 2006-06-17
Yeah, I now have the 64 bit drivers but it doesn't make any difference.  Its doing the exact same thing.

---

### Post by Dr. Nick on 2006-06-17
[quote=kewldude606]I did the sudo line you suggested.  Now the Windows Wireless Drivers still says Driver and hardware present, but in iwconfig everything is listed as "no wireless extensions."  eth2, where the wireless extensions used to be, isn't listed anymore.  I then did sudo modprobe islsm_usb everything was back to the way it was in the 1st post by me.[/quote]

I just checked that on mine and have the same situation, I just updated my kernel so my wireless driver that doesnt work that well came back.

What I did was modprobe -r the kernel driver,
then find the actual module file and remove it
then modprobe -r ndiswrapper
and finally sudo modprobe ndiswrapper

I would try that and see how it goes. You should first try without deleting the file just to be safe. Just unload ndiswrapper, and the islsm_usb and reload only the ndiwswapper and see how that goes.

---

### Post by Etoile on 2006-06-18
Hmm.  Does checking the "usbcore" line apply even if you are using a laptop with builtin wifi?  (Dell Inspiron 1150 on my case.) I'm having the same problem with ndiswrapper claiming everything is present, so I assume I also need to blacklist the bad default.  :confused:

---

### Post by Dr. Nick on 2006-06-18
if the wifi is built in then usbcore isnt what to look for, just load the ndiswrapper module then run a lsmod and see what line it appears on, then check that line for a native driver.

usb is used in the origional poster and my examples since both our cards are usb.

---

### Post by Etoile on 2006-06-18
Right, that's what I figured.  Thanks for the quick response; I've had to boot into XP to research this so I was eager for an answer before booting back into Ubuntu! :)

---

### Post by kewldude606 on 2006-06-20
OK, my wireless still isn't working.  I have done everything in this guide: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) including booting with noacpi.  I am stuck on 4.3, router connection.

This is my iwconfig output:```
eth2      IEEE 802.11b  ESSID:"Finnie"
          Mode:Auto  Channel=10  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
Then I tried to connect like this:
```
sudo iwconfig eth2 ap <MAC ADDR> commit
```
Nothing happened.

I NEED to get this wireless working!

Altho I could just buy another wireless card.  Are there are true plug and play wireless G cards for linux/ubuntu?

---

### Post by goodmaj on 2006-06-20
When you install ndiswrapper it makes a file named /etc/modprobe.d/ndiswrapper.  It probably has a single line which "alias wlan0 ndiswrapper".

If you are seeing your wireless card as eth2 or something else, change the line in the above file to match what the system is calling your wireless card instead of wlan0.

Then just try "ifup eth2"

---

### Post by kewldude606 on 2006-06-20
Ifup got the error: interface already configured.

---

### Post by goodmaj on 2006-06-20
[QUOTE=kewldude606]Ifup got the error: interface already configured.[/QUOTE]
That means it is now up and running.

---

### Post by kewldude606 on 2006-06-20
I still can't ping from that address.  This command: ping -I eth2 192.168.1.1 just gets Destination Host Unreachable messages.

---

### Post by goodmaj on 2006-06-20
Please paste in the output of ifconfig that pertains to eth2.

---

### Post by kewldude606 on 2006-06-20
There is no output for eth2 in ifconfig, but in iwconfig this is it:```
eth2      IEEE 802.11b  ESSID:"Finnie"
          Mode:Auto  Channel=1  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by goodmaj on 2006-06-20
At this point I would suggest a reboot and then check the configuration of the interface. The fact that there is no output in ifconfig for eth2 and the command sudo ifup eth2 returns that the interface is already configured is peculiar.

Let me know what happens after a reboot and rechecking things.

iwconfig is saying the Access Point is invalid.  Do you have the correct ESSID?  Are  you in any way controlling access to router by say the MAC address?

---

### Post by kewldude606 on 2006-06-20
The SSID is Finnie, is that the same as ESSID?.  I am not filtering from the AP, but in the configuration settings it asked me for a WEP key but I just left it blank.  I didn't see a way to disable all encryption in the Wireless Configuration.  Is this how I should do it?

---

### Post by goodmaj on 2006-06-20
Yes, all you are saying makes sense.  Let me think a while.  Maybe tomorrow.

---

### Post by Airjoe on 2006-06-20
I'm having a similar (same?) problem with my Linksys WUSB54G. It only started after upgrading to dapper. ndiswrapper says the driver and hardware is present, but in "iwconfig" the device is listed as eth2. When I scanned, my Access Point didn't come up. I had to manually set the channel, and then my AP came up in a scan. However, even after setting the AP with iwconfig, it just doesn't connect. 

Still though, sometimes it doesn't come up in a scan. When it does, I can't connect. I'm reading through this thread now to try and see if anything works. The problem is I only have on monitor, keyboard, and mouse, for three computers! :P

---

### Post by kewldude606 on 2006-06-20
So Breezy worked?  Do you think I should down-grade?

Edit: Did Breezy work out of the box?

---

### Post by Airjoe on 2006-06-20
I hope we won't have to downgrade :|

What do you mean by out of the box? I still had to use ndiswrapper, but it was really easy.

---

### Post by kewldude606 on 2006-06-20
Easy is good :).

Dapper is my first Linux install ever.  Is there much of a difference between Breezy and Dapper?

---

### Post by goodmaj on 2006-06-21
I did a search for "Linksys WUSB54G" in the Ubuntu Forums and found the following thread.  Evidently there are particular problem associated with USB adapters.  If you read this in it's entirety, not just the first part, I am sure you will be able to get your device working.

[http://ubuntuforums.org/showthread.php?t=106846&highlight=Linksys+WUSB54G](http://ubuntuforums.org/showthread.php?t=106846&highlight=Linksys+WUSB54G)

---

### Post by kewldude606 on 2006-06-21
Mine doesn't use that chipset, it is a Prism one.  Can I still follow the firections and not screw stuff up?

---

### Post by stephenrhall on 2006-06-22
I have the Linksys adapter with the Prism chipset.  I finally got it working by removing the islsm_usb module, re-loading ndiswrapper, and unplugging and reconnecting the network adapter.  Everything then worked fine until I was told there were upgrades.  I downloaded and installed them, and networking is again broken, and nothing I can do fixes it.  I presume it it the kernel upgrade that has broken things.  

Incidently, I had no networking problems with Breezy.  Set up ndiswrapper and it worked perfectly.  Upgrade to Dapper and nothing but problems.

---

### Post by Dr. Nick on 2006-06-22
[quote=stephenrhall]I have the Linksys adapter with the Prism chipset.  I finally got it working by removing the islsm_usb module, re-loading ndiswrapper, and unplugging and reconnecting the network adapter.  Everything then worked fine until I was told there were upgrades.  I downloaded and installed them, and networking is again broken, and nothing I can do fixes it.  I presume it it the kernel upgrade that has broken things.  

Incidently, I had no networking problems with Breezy.  Set up ndiswrapper and it worked perfectly.  Upgrade to Dapper and nothing but problems.[/quote]

I assume you removed the module again once updated? What I would reccomend doing is getting ndiswrapper then going into synaptic and locking the version to the working one to avoid trouble with updates. Every new kernel will reload the native drivers for you so watch for that.

---

### Post by kewldude606 on 2006-06-22
[QUOTE=stephenrhall]I have the Linksys adapter with the Prism chipset.  I finally got it working by removing the islsm_usb module, re-loading ndiswrapper, and unplugging and reconnecting the network adapter.  Everything then worked fine until I was told there were upgrades.  I downloaded and installed them, and networking is again broken, and nothing I can do fixes it.  I presume it it the kernel upgrade that has broken things.  

Incidently, I had no networking problems with Breezy.  Set up ndiswrapper and it worked perfectly.  Upgrade to Dapper and nothing but problems.[/QUOTE]
This didn't work for me :(.

I have the newest kernel that came out a few days ago I think.  Anyway, here's what I did (maybe I did something wrong).
```
sudo modprobe -r lslsm_usb
sudo ndiswrapper -e wusb54g
cd to directory with INF files
sudo ndiswrapper -i WUSB54G.inf
<unplug>
<go to the bathroom>
<replug>
ndiswrapper --> driver and hardware present
iwconfig --> same as before.
```

---

### Post by Dr. Nick on 2006-06-22
[quote=kewldude606]This didn't work for me :(.

I have the newest kernel that came out a few days ago I think.  Anyway, here's what I did (maybe I did something wrong).
```
sudo modprobe -r lslsm_usb
sudo ndiswrapper -e wusb54g
cd to directory with INF files
sudo ndiswrapper -i WUSB54G.inf
<unplug>
<go to the bathroom>
<replug>
ndiswrapper --> driver and hardware present
iwconfig --> same as before.
```[/quote]

OK, That **MAY** help lol

When you do modprobe -r islsm_usb it is only temporarily removed until next reboot OR Next unplug/replug of the card itself I believe. 

Here is what I would try
Set up ndiswrapper so when you run ndiswrapper -l it says driver/hardware present.

Now do the **sudo modproe -r islsm_usb**
and finally [B]sudo modprobe ndiswrapper

[/B]then try the **iwconfig**

Hopefully that helps, If you do the steps like you have them then add one more to make sure you can do it that way.

Do like you have above and end with a **lsmod** and make sure the islsm_usb module isnt still hanging around on the usbcore line next to ndiswrapper. If you were to have errors in your steps above I would think it was to unplug/replug the card. I am not 100% sure on that but its a idea.

---

### Post by mshirey8 on 2006-06-22
[QUOTE=blurredbrain]YOu know, I'm having the exact same issue, only I have an internal broadcom card on my Compaq Presario v2000, and its showing up under usbcore with the ndiswrapper.  Is this my problem?[/QUOTE]

I have the exact same setup. Here's what I did:

1. clean install of dapper.
2. Made sure Network Manager was NOT installed
3. Used ndiswrapper to install the drivers that came with the machine.
4. Rebooted.

The only thing I noticed is that my wireless connection status button only lights up when there is traffic across the connection. It doesn't stay lit all the time like it did in Breezy.

But it works!

---

### Post by kewldude606 on 2006-06-23
[QUOTE=Dr. Nick]OK, That **MAY** help lol

When you do modprobe -r islsm_usb it is only temporarily removed until next reboot OR Next unplug/replug of the card itself I believe. 

Here is what I would try
Set up ndiswrapper so when you run ndiswrapper -l it says driver/hardware present.

Now do the **sudo modproe -r islsm_usb**
and finally [B]sudo modprobe ndiswrapper

[/B]then try the **iwconfig**

Hopefully that helps, If you do the steps like you have them then add one more to make sure you can do it that way.

Do like you have above and end with a **lsmod** and make sure the islsm_usb module isnt still hanging around on the usbcore line next to ndiswrapper. If you were to have errors in your steps above I would think it was to unplug/replug the card. I am not 100% sure on that but its a idea.[/QUOTE]
:D :D :D 
I think we are getting somewhere!  [Update: you don't have to read this, pls skip to the end]
This is the output of iwconfig (some of it):
```
eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:2 Mb/s
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

But then I go to set my AP and I get this error:```
daniel@daniel-desktop:~$ sudo iwconfig eth1 ap Finnie
Interface eth1 doesn't support IP addresses
eth1      Interface doesn't support IP addresses
Error for wireless request "Set AP Address" (8B14) :
    invalid argument "Finnie".
```
I went into Windows Wireless Drivers and I was able to set the SSID in there.  Oh crap I'm retarded.  I put a SSID where it wanted a MAC.  OK forget that last part.

I can ping my router over the wireless. (ping 192.168.1.1 -I eth1)
I can ping google.com over the wireless. (^^ w/ google.com)

Update...:
I cut the cable, and now I can ping my router over the wireless.  But I can't ping google.com.  I can surf the web.  I think it is DNS troubles.  New update: forgive me, I can ping google but with 101ms latency instead of 30ms and it freezes up the Network Tools as it works.  Update: its back down to 30ms.  I guess it was a momentary glitch.

New question: what can I do to make this permanent?

---

### Post by Dr. Nick on 2006-06-23
ok, i think I understand where your at.

So after running the above code you can surf the inernet fine over your wireless, you just have to run the code on every boot?

What I would do is go into your network settings and open up you wired ethernet card and uncheck the box that says "enable this connection"

Then make sure the word "ndiswrapper" appears in the file /etc/modules

And then I would look into blacklisting the islsm_usb module, I am not sure how to do that so you may have to search for it. I tried blacklisting mine but wasnt successfull so I just deleted the file


You can run from a terminal

locate islsm_usb


or just use the find files program to search islsm_usb to find the file. It should be something like /drivers/network/wireless/... You can just move the file out of that folder or delete the islsm file and it wont load then, You will just have to do that every time you get a new kernel

---

### Post by kewldude606 on 2006-06-23
i think I found how to blacklist something.  You add it to /etc/default/linux-restricted-modules-common.  I'm rebooting now...

Update: Strange things just happened.  It didn't work at boot.  I did iwconfig and everything said no wireless extensions.  It took a lok of removing isls.. and adding ndis to get it to work.

I guess I will just delete the file.

It works on boot know. *HUGS TO ALL*

---

### Post by Dr. Nick on 2006-06-23
glad you got it all working, If anyone knows how to blacklist please share. Deleteing the file, or just moving the file, is not a big deal ;you just have to remember thats what you did to get it working since every new kernel will reload the module and you will have to delete it again

---

### Post by kewldude606 on 2006-06-23
I'm scarred from my Windows experience about deleting files.  Delete Windows/audio.txt and suddenly your mouse stops working...

---

### Post by cydec on 2006-06-24
I had similar problems getting my wireless online.

First of all i did a 'lsmod' and there was 'prism2_usb' in the usbcore.
I removed it with '$ modprobe -r prism2_usb'
And i loaded 'ndiswrapper' with '$ modprobe ndiswrapper'
What i did next is just enabeling & activating the network interface 'wlan1'

Everything seems to work now but when i reboot i always have to do this over again...

prism driver is back and ndiswrapper is even not loading from start...
(i did a ndiswrapper -m but it won't boot from the start as module)

can somebody help me out here ?

---

### Post by cydec on 2006-06-24
[QUOTE=cydec]I had similar problems getting my wireless online.

First of all i did a 'lsmod' and there was 'prism2_usb' in the usbcore.
I removed it with '$ modprobe -r prism2_usb'
And i loaded 'ndiswrapper' with '$ modprobe ndiswrapper'
What i did next is just enabeling & activating the network interface 'wlan1'

Everything seems to work now but when i reboot i always have to do this over again...

prism driver is back and ndiswrapper is even not loading from start...
(i did a ndiswrapper -m but it won't boot from the start as module)

can somebody help me out here ?[/QUOTE]

OOooopps, got it to work.

Blacklisted 'prism2_usb' in /etc/modprobe.d/blacklist
Went to /etc/modules and added 'ndiswrapper'.

The only weird thing i have now is that my modprobe alias says "wlan0".
But if- and iwconfig tell me "wlan1"

---

### Post by Dr. Nick on 2006-06-24
OK So maybe adding the module to /etc/modprobe.d/blackist is the correct way to blacklist, Ill remember that in the future instead  of just deleting my prism2_usb file.

If you want to change the alias then have a look at the file /etc/network/interfaces and see if it looks correct.

---

### Post by boxxxx117 on 2006-07-01
I have a similar problem to this post but my card is a PCMCIA instead of usb but in lsmod i get

```
usbcore               130692  3 ndiswrapper,uhci_hcd

```

and under the PCMCIA line i get this

```
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic

```

should ndiswrapper be in pcmcia_core and not usbcore. if so how do i do this?
thanx

---

### Post by Dr. Nick on 2006-07-01
I would think it should be under pcmcia, Are you sure you have ndiswrapper set up properly? does runnig **ndiswrapper -l** say **driver present, hardware present**?

---

### Post by jazzwhistle on 2006-11-24
THANK YOU :)

I lost all wireless connectivity on my WUSB54 after upgrading Breezy > Dapper, spent about 6 hours booting back and forth to XP (ahh... it can be good too!) trying to sort it out, and finally hit this thread.

I got soooo close to connecting (Connecting...testing connection... FAILED) by changing all references to wlan0 into eth1 in my config files, but the answer was indeed a conflict between my previous working ndiswrapper and Dappers new islsm_usb. Blacklisted islsm_usb, changed everything back to wlan0, rebooted, and here I am on Opera and Kubuntu Dapper :)  Next step Edgy...

---

### Post by Dr. Nick on 2006-11-24
glad you got it, if its blacklisted then edgy shouldnt be as hard a upgrade

---

