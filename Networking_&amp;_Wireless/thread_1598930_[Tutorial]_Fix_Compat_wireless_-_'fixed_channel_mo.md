---
title: "[Tutorial] Fix: Compat wireless - 'fixed channel mon0: -1'"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by SquirrelScript on 2010-10-17
After upgrading to Ubuntu 10.10, I found that airodump-ng and aireplay-ng didn't want to work:
> 
airodump-ng: Fixed channel to -1 = [B]fixed channel mon0: -1
[/B]aireplay-ng: Wouldn't false authenticate OR deauth = **mon0 is on channel -1, but the AP uses channel 9**
**Setup**
OS: Ubuntu 10.10 
Kernel: 2.6.35-22-generic-pae
WiFi Card: Intel iwlwifi iwlagn Intel Corporation WiFi Link 5100

**How?** 
```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2
tar -jxf compat-wireless-2010-10-16.tar.bz2
cd compat-wireless-2010-10-16
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo reboot
```Hope it helps someone[/I]

---

### Post by hallucynogenyc on 2010-10-17
Your code fails if copy pasted on the terminal. Wget can't interpret the shortened version of the links and will give a 404 error on all the links. Then, even fixing that still gives one error. You're not uncompressing the first file before entering it's folder, which, as the code is, doesn't exist at all.

Thanks for the help anyway, but try to test your own code before uploading it ;)

---

### Post by SquirrelScript on 2010-10-17
> **hallucynogenyc said:**
> Your code fails if copy pasted on the terminal. Wget can't interpret the shortened version of the links and will give a 404 error on all the links. Then, even fixing that still gives one error. You're not uncompressing the first file before entering it's folder, which, as the code is, doesn't exist at all.

Thanks for the help anyway, but try to test your own code before uploading it ;)
Sorry, the forum auto added the URL tags - I didnt add them!
Yes, I did skip out un-compressing stage. *now added in*
For the record, I did test it. I just added the "wget, tar, and cd" by hand afterwards.

---

### Post by hallucynogenyc on 2010-10-17
Great, no problem mate. I was just trying to help hehe ;)

Btw, the code worked for me, at least the one based on the initial one that I executed.

---

### Post by SriNarayanan on 2010-10-17
Just running make , will check and post :-)

---

### Post by SriNarayanan on 2010-10-17
Just one question , may sound silly , Are we rebuilding the kernel here ?

---

### Post by SriNarayanan on 2010-10-17
The Fix works :-) Thanks .
But I am not sure , if an injection is succeeding .
That is airodump doesnt show in an increase in packets . 


root@narayant-VPCEB16FG:~# aireplay-ng --arpreplay  -b D8:5D:4C:C1:64:01  mon0
No source MAC (-h) specified. Using the device MAC (78:DD:08:CC:1C:FE)
00:14:11  Waiting for beacon frame (BSSID: D8:5D:4C:C1:64:01) on channel 1
Saving ARP requests in replay_arp-1018-001411.cap
You should also start airodump-ng to capture replies.
Notice: got a deauth/disassoc packet. Is the source MAC associated ?
Notice: got a deauth/disassoc packet. Is the source MAC associated ?
^Cad 5868 packets (got 0 ARP requests and 642 ACKs), sent 0 packets...(0 pps)
--------------------------------------------------------------------------------------------------------------
 CH  1 ][ Elapsed: 8 mins ][ 2010-10-18 00:19 ][ Decloak: D8:5D:4C:C1:64:01    
                                                                               
 BSSID              PWR  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID
                                                                               
 D8:5D:4C:C1:64:01  -50     4938      784    0   1  54   WEP  WEP    OPN  Binat
                                                                               
 BSSID              STATION            PWR   Rate    Lost  Packets  Probes     
                                                                               
 D8:5D:4C:C1:64:01  78:DD:08:CC:1C:FE    0   54 -54      0     1436  Binatone 


Of course this is my wifi that I am trying to hack wep:-)

---

### Post by xorman2k7 on 2010-10-17
thanks man!

worked like a charm :)

---

### Post by SquirrelScript on 2010-10-18
> **hallucynogenyc said:**
> Great, no problem mate. I was just trying to help hehe ;)

Btw, the code worked for me, at least the one based on the initial one that I executed.
Good good!
Its great to hear its working!



> **SriNarayanan said:**
> Just one question , may sound silly , Are we rebuilding the kernel here ?
I dont think we are! Just editing the drivers. :)



> **SriNarayanan said:**
> The Fix works :-) Thanks .
But I am not sure , if an injection is succeeding .
That is airodump doesnt show in an increase in packets . 

Ive tested airodump-ng myself, was going on what someone else said they are injection working. Ill try and find my old WiFi router, and give WEP ago later tonight. (=



> **xorman2k7 said:**
> thanks man!

worked like a charm :)
Im glad its working for you!

---

### Post by SriNarayanan on 2010-10-18
> **SquirrelScript said:**
> Good good!
Its great to hear its working!




I dont think we are! Just editing the drivers. :)




Ive tested airodump-ng myself, was going on what someone else said they are injection working. Ill try and find my old WiFi router, and give WEP ago later tonight. (=




Im glad its working for you!

Thanks for the reply buddy,
Few educational questions :-)

1. If we are editing drivers ,can a faulty edited driver damage the hardware.
In other words , is it OK to play with the drivers .

2. Initially I dint find the chan.c anywhere , I guess the patch is applied to this file .
Which means , does the compat-wireless driver package contain this file?
In that case what is the wireless driver currently active and what has compat wireless have to do with the fix

----
Machine details :
Sony Vaio EB15FG / Atheros AR9285

---

### Post by SquirrelScript on 2010-10-19
> **SriNarayanan said:**
> Thanks for the reply buddy,
Few educational questions :-)

1. If we are editing drivers ,can a faulty edited driver damage the hardware.
In other words , is it OK to play with the drivers .

2. Initially I dint find the chan.c anywhere , I guess the patch is applied to this file .
Which means , does the compat-wireless driver package contain this file?
In that case what is the wireless driver currently active and what has compat wireless have to do with the fix

----
Machine details :
Sony Vaio EB15FG / Atheros AR9285
1.) I don't think it can. I belive it would just make your system unstable...HOWEVER. IF it does kill something - dont sue/blame me... ;)

2.) Did you use "compat-wireless-2010-10-16.tar.bz2"? 
I've found that these WOULDN'T patch correctly (with the method at the top):
compat-wireless-2.6.32.16.tar.bz2
compat-wireless-2.6.33.6.tar.bz2
compat-wireless-2.6.34.1.tar.bz2

However, these PATCH successfully:
[compat-wireless-2.6.35-1.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.35/compat-wireless-2.6.35-1.tar.bz2")
[compat-wireless-2010-10-16.tar.bz2]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2") *<--- The one in the method*
*If you follow the method at the top, doing each command - it shouldn't have a problem.*

---

### Post by SriNarayanan on 2010-10-19
> **SquirrelScript said:**
> 1.) I don't think it can. I belive it would just make your system unstable...HOWEVER. IF it does kill something - dont sue/blame me... ;)

2.) Did you use "compat-wireless-2010-10-16.tar.bz2"? 
I've found that these WOULDN'T patch correctly (with the method at the top):
compat-wireless-2.6.32.16.tar.bz2
compat-wireless-2.6.33.6.tar.bz2
compat-wireless-2.6.34.1.tar.bz2

However, these PATCH successfully:
[compat-wireless-2.6.35-1.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.35/compat-wireless-2.6.35-1.tar.bz2")
[compat-wireless-2010-10-16.tar.bz2]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2") *<--- The one in the method*
*If you follow the method at the top, doing each command - it shouldn't have a problem.*
I just copied each and every line from the above for that matter :-)
did use   compat-wireless-2010-10-16.tar.bz2 - so it should have patched correctly.

Thing is none of the aircrack command through any error , but they don't seem to produce result either.

It is said that the #/s in the aerodump will dramatically increase after a 
deauth with aireplay , but that dont seem to happen.Am i missing something here.

Basically what I do is ,
1. Run airodump to find my routers BSSID and my friends client ESSID
2. Capture a dump file listening for my routers BSSID and run injections -deauthentication my frnd's client.So technically there should be an increase in the #s when my frnd's client try to authenticate again.

But the rate of the BEACON frames from my router remains the same .
Just wondering if there is something wrong in my approach or is the library not working properly.Since there r no errors I could nt  decide whats wrong :-k

---

### Post by SquirrelScript on 2010-10-19
I've tired it on my home network which runs WPA2. Work fine. I'm unable to change it to WEP as my house mates are using it.

Then it may be working correctly - the problem MAY be your router.
I can remember trying it on our old router a few months back, then on our new one when we got an upgrade.
The old router wouldn't work with chopchop or fragment attacks, but the basic ARPreplay would. Then on the new one, none of the attacks would work.
Is there a connect client? WEP 64 bit? Open/Shared?

---

### Post by soad6 on 2010-10-21
Your post is really helpful. I posted your fix to the bug forum for the negative-one channel bug. Seems this issue affects quite a few ppl. Thanx for this fix. You are the man!

---

### Post by soad6 on 2010-10-21
Oh and can some please tell me if you can get a WPA handshake using this fix or not?? cuz i tried to and couldn't. It maybe that my router is a G+N router dualband and my wireless AP is only a G card. If this is my issue then no problem, if not then compat still has some issues.

---

### Post by SriNarayanan on 2010-10-21
> **SquirrelScript said:**
> I've tired it on my home network which runs WPA2. Work fine. I'm unable to change it to WEP as my house mates are using it.

Then it may be working correctly - the problem MAY be your router.
I can remember trying it on our old router a few months back, then on our new one when we got an upgrade.
The old router wouldn't work with chopchop or fragment attacks, but the basic ARPreplay would. Then on the new one, none of the attacks would work.
Is there a connect client? WEP 64 bit? Open/Shared?


I just want to know this . 
Is it able to inject frames or deauth .
As far as I see there is no increase in the #s value nor the number of beacon frames.
Correct me if I am wrong , my assumption is the #S and the number of beacon frames have to increase when the injection succeed.

[-(


My Router is a Binatone one 
and the wifi card is Ar9285 Atheros

---

### Post by sagaci on 2010-10-22
Hi,

I just patched and it all works fine now.

Used a alfa AWUS036H and a thomson router.

Cracked WEP (open systems) and WPA & WPA2 via handshake. Works normal now.

---

### Post by SriNarayanan on 2010-10-22
> **sagaci said:**
> Hi,

I just patched and it all works fine now.

Used a alfa AWUS036H and a thomson router.

Cracked WEP (open systems) and WPA & WPA2 via handshake. Works normal now.

Educate me here , 
WPA with TKIP is supposed to be cracked via handshake capture .


Let me read and try 8)

---

### Post by comrobo on 2010-10-22
hello.

I have a card with a broadcom chip and working with b43 driver.

so this patch work with b43?
this change b43 for compat-wireless?

so thanks for your help.

greetings jo.

---

### Post by jfekendall on 2010-10-24
Mr. Squirrel,
  I would like to say that I actually registered for this forum just to thank you for this complicated, yet effective fix. You sir, rock.
  Tested and working with Atheros AR5001 Chipset.

-jfekendall

---

### Post by comrobo on 2010-10-24
OK, it works, in this difficult card:  Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315]  (some people will know about I'm talking)  Thank you very much!

---

### Post by SquirrelScript on 2010-10-25
> **soad6 said:**
> Your post is really helpful. I posted your fix to the bug forum for the negative-one channel bug. Seems this issue affects quite a few ppl. Thanx for this fix. You are the man!
Thanks (=
Great to know its working for you, thanks for reporting that it is too!



> **soad6 said:**
> Oh and can some please tell me if you can get a WPA handshake using this fix or not?? cuz i tried to and couldn't. It maybe that my router is a G+N router dualband and my wireless AP is only a G card. If this is my issue then no problem, if not then compat still has some issues.
Yes. Its working for me. (=
Got my WPA2 handshake (unable to test WEP - too many people use our WiFi for my to change its settings)



> **SriNarayanan said:**
> I just want to know this . 
Is it able to inject frames or deauth .
As far as I see there is no increase in the #s value nor the number of beacon frames.
Correct me if I am wrong , my assumption is the #S and the number of beacon frames have to increase when the injection succeed.

[-(


My Router is a Binatone one 
and the wifi card is Ar9285 Atheros
DeAuth is working for me, I haven't been able to test injection. Other users have reported it working!



> **sagaci said:**
> Hi,

I just patched and it all works fine now.

Used a alfa AWUS036H and a thomson router.

Cracked WEP (open systems) and WPA & WPA2 via handshake. Works normal now.
Thanks for the feedback & testing. Big thanks for testing out both types of networks (WEP and WPA) as I'm unable to do so!



> **SriNarayanan said:**
> Educate me here , 
WPA with TKIP is supposed to be cracked via handshake capture .


Let me read and try 8)
Yep. Its the only "known" method of cracking WPA/WPA2. You need a connected client - so you can DeAuth them to get the handshake.



> **comrobo said:**
> hello.

I have a card with a broadcom chip and working with b43 driver.

so this patch work with b43?
this change b43 for compat-wireless?

so thanks for your help.

greetings jo.
I dunno. Try?
Are you having the same issue now?



> **jfekendall said:**
> Mr. Squirrel,
  I would like to say that I actually registered for this forum just to thank you for this complicated, yet effective fix. You sir, rock.
  Tested and working with Atheros AR5001 Chipset.

-jfekendall
Thank you. That means alot to me that you took the time & effort do sign up. :)


> **comrobo said:**
> OK, it works, in this difficult card:  Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315]  (some people will know about I'm talking)  Thank you very much!
Your welcome! Glad its working for you

---

### Post by Bent Axle on 2010-10-25
Hi folks.

I just wanted to let you know this HOWTO worked for me. I'm using 10.10 and the 'ar9170' driver. I followed the OP's instructions to the letter.

Thanks again for the fix. 

BA

---

### Post by charlie_brownie on 2010-10-25
HEYYYYYY!!

I just wanted to say THANK YOU VERY MUCH for these codes. It solved the problem, which was killing me...

+100 for you!!!!!!!                                 

PS: i registered just to say thanks a lot :)

:)

---

### Post by SquirrelScript on 2010-10-25
> **Bent Axle said:**
> Hi folks.

I just wanted to let you know this HOWTO worked for me. I'm using 10.10 and the 'ar9170' driver. I followed the OP's instructions to the letter.

Thanks again for the fix. 

BA
That's great to hear! (=

> **charlie_brownie said:**
> HEYYYYYY!!

I just wanted to say THANK YOU VERY MUCH for these codes. It solved the problem, which was killing me...

+100 for you!!!!!!!                                 

PS: i registered just to say thanks a lot :)

:)
Thanks for the feedback and the time sign up! (=

---

### Post by theecho on 2010-10-26
I wish I could have the joyous response, however I am still having the issue.  I ran the code verbatum how I am still getting mon0 is on channel -1.  My chipset is atheros ar9285 and I am using the ath9k driver.  Any help is greatly appreciated and I am still new to linux.

---

### Post by tenbartek on 2010-10-27
Hi,
I was trying to play with aircrack, and got that issue with mon0 channel and found your solution to the problem.
I am new one with Ubuntu so hope my problem is just simple to resolved:
I followed step by step (every stage seems to be worked perfect)
After rebooting my wifi networks dissapeared.
I can see the driver but it is swithced off and can not be installed through system->drivers method (message: SystemError: installArchives() failed)
I used terminal with compat-wireless-2010-10-16/script/driver-select b43
but still not working.
I have now two directories: compat-wireless-2.6.32.16, compat-wireless-2010-10-16
any help?

hope my language clear enough.

---

### Post by Hack.The.Pow. on 2010-10-28
Thanks it worked perfectly!

Only problem now is that the compat-wireless folder is in my home directory.  Is it safe to move it to a lesser used directory?  And if so what directory would be most appropriate?

---

### Post by nathanhillinbl on 2010-10-28
I believe that (and please correct me if I'm wrong) because you ran make install, that folder is irrelevant, and you can delete it.

---

### Post by Hack.The.Pow. on 2010-10-29
> **nathanhillinbl said:**
> I believe that (and please correct me if I'm wrong) because you ran make install, that folder is irrelevant, and you can delete it.

really?  before I do this can somebody confirm this?

it seems to sort of make sense but i would like confirmation before doing this.

Edit: Nevermind I finally just deleted it anyway and it still works.  Thanks again.

---

### Post by Newbie789 on 2010-10-29
I would like to thank you for the great fix, however, now for some reason when I open terminals and use airmon-ng commands, my computer locks up and I have to hold the power button to shut it off every time... is there something that can fix this?

Any idea what's wrong?
I have an Atheros AR5009 (ath9k) wireless driver, and followed the instructions exactly... are these instructions not compatible with my system?

*Edit*
Sorry, I figured out what I was doing wrong!

Great fix!!!! hahah

---

### Post by SweetzDesigns on 2010-11-01
Need help,

I've followed the instructions given but I keep getting errors after doing the "make" commands. To assist anyone further here are my specs:

description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.

driverversion=2.6.35-22-generic-pae

And this is my output.




> daniel@Daniel-Aspire-5741:~$ wget [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2)
--2010-11-01 17:57:14--  [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2)
Resolving wireless.kernel.org... 78.46.109.217, 2a01:4f8:121:1401:1::2
Connecting to wireless.kernel.org|78.46.109.217|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3873551 (3.7M) [application/octet-stream]
Saving to: `compat-wireless-2010-10-16.tar.bz2.2'

100%[======================================>] 3,873,551    156K/s   in 27s     

2010-11-01 17:57:43 (140 KB/s) - `compat-wireless-2010-10-16.tar.bz2.2' saved [3873551/3873551]

daniel@Daniel-Aspire-5741:~$ sudo tar -jxf compat-wireless-2010-10-16.tar.bz2
[sudo] password for daniel: 
daniel@Daniel-Aspire-5741:~$ cd compat-wireless-2010-10-16
daniel@Daniel-Aspire-5741:~/compat-wireless-2010-10-16$ wget [http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch](http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch)
--2010-11-01 17:58:20--  [http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch](http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch)
Resolving patches.aircrack-ng.org... 213.186.33.2
Connecting to patches.aircrack-ng.org|213.186.33.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1049 (1.0K) [text/plain]
mac80211.compat08082009.wl_frag+ack_v1.patch.3: Permission denied

Cannot write to `mac80211.compat08082009.wl_frag+ack_v1.patch.3' (Permission denied).
daniel@Daniel-Aspire-5741:~/compat-wireless-2010-10-16$ sudo su
root@Daniel-Aspire-5741:/home/daniel/compat-wireless-2010-10-16# wget [http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch](http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch)
--2010-11-01 17:58:34--  [http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch](http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch)
Resolving patches.aircrack-ng.org... 213.186.33.2
Connecting to patches.aircrack-ng.org|213.186.33.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1049 (1.0K) [text/plain]
Saving to: `mac80211.compat08082009.wl_frag+ack_v1.patch.3'

100%[======================================>] 1,049       --.-K/s   in 0s      

2010-11-01 17:58:38 (60.7 MB/s) - `mac80211.compat08082009.wl_frag+ack_v1.patch.3' saved [1049/1049]

root@Daniel-Aspire-5741:/home/daniel/compat-wireless-2010-10-16# patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
patching file net/mac80211/tx.c
Hunk #1 succeeded at 777 (offset 100 lines).
root@Daniel-Aspire-5741:/home/daniel/compat-wireless-2010-10-16# wget [http://patches.aircrack-ng.org/channel-negative-one-maxim.patch](http://patches.aircrack-ng.org/channel-negative-one-maxim.patch)
--2010-11-01 17:59:04--  [http://patches.aircrack-ng.org/channel-negative-one-maxim.patch](http://patches.aircrack-ng.org/channel-negative-one-maxim.patch)
Resolving patches.aircrack-ng.org... 213.186.33.2
Connecting to patches.aircrack-ng.org|213.186.33.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1021 [text/plain]
Saving to: `channel-negative-one-maxim.patch.3'

100%[======================================>] 1,021       --.-K/s   in 0s      

2010-11-01 17:59:06 (114 MB/s) - `channel-negative-one-maxim.patch.3' saved [1021/1021]

root@Daniel-Aspire-5741:/home/daniel/compat-wireless-2010-10-16# patch ./net/wireless/chan.c channel-negative-one-maxim.patch
patching file ./net/wireless/chan.c
Hunk #1 succeeded at 50 (offset 1 line).
Hunk #2 succeeded at 80 (offset 1 line).
root@Daniel-Aspire-5741:/home/daniel/compat-wireless-2010-10-16# gedit scripts/update-initramfs

(gedit:4584): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
root@Daniel-Aspire-5741:/home/daniel/compat-wireless-2010-10-16# make
/home/daniel/compat-wireless-2010-10-16/config.mk:196: "WARNING: CONFIG_CFG80211_WEXT will be deactivated or not working because kernel was compiled with CONFIG_WIRELESS_EXT=n. Tools using wext interface like iwconfig will not work. To activate it build your kernel e.g. with CONFIG_LIBIPW=m."
make -C /lib/modules/2.6.35-22-generic-pae/build M=/home/daniel/compat-wireless-2010-10-16 modules
make: *** /lib/modules/2.6.35-22-generic-pae/build: No such file or directory. Stop.
make: *** [modules] Error 2
root@Daniel-Aspire-5741:/home/daniel/compat-wireless-2010-10-16# sudo make install
/home/daniel/compat-wireless-2010-10-16/config.mk:196: "WARNING: CONFIG_CFG80211_WEXT will be deactivated or not working because kernel was compiled with CONFIG_WIRELESS_EXT=n. Tools using wext interface like iwconfig will not work. To activate it build your kernel e.g. with CONFIG_LIBIPW=m."

Your old wireless subsystem modules were left intact:

kernel/net/mac80211/mac80211.ko
kernel/net/wireless/cfg80211.ko
kernel/net/wireless/lib80211.ko
kernel/drivers/net/wireless/adm8211.ko
kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
kernel/drivers/net/wireless/at76c50x-usb.ko
kernel/drivers/net/wireless/ath/ath.ko
kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/b44.ko
kernel/drivers/net/usb/cdc_ether.ko
kernel/drivers/misc/eeprom/eeprom_93cx6.ko
kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
kernel/net/wireless/lib80211_crypt_ccmp.ko
kernel/net/wireless/lib80211_crypt_tkip.ko
kernel/net/wireless/lib80211_crypt_wep.ko
kernel/drivers/net/wireless/libertas/libertas.ko
kernel/drivers/net/wireless/libertas/libertas_cs.ko
kernel/drivers/net/wireless/libertas/libertas_sdio.ko
kernel/drivers/net/wireless/libertas/libertas_spi.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/ipw2x00/libipw.ko
kernel/drivers/net/wireless/mac80211_hwsim.ko
kernel/drivers/net/wireless/mwl8k.ko
kernel/drivers/net/wireless/p54/p54common.ko
kernel/drivers/net/wireless/p54/p54pci.ko
kernel/drivers/net/wireless/p54/p54spi.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/usb/rndis_host.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rtl818x/rtl8180.ko
kernel/drivers/net/wireless/rtl818x/rtl8187.ko
kernel/drivers/ssb/ssb.ko
kernel/drivers/net/wireless/libertas/usb8xxx.ko
kernel/drivers/net/usb/usbnet.ko
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko

Your old bluetooth subsystem modules were left intact:

kernel/net/bluetooth/sco.ko
kernel/net/bluetooth/l2cap.ko
kernel/net/bluetooth/hidp/hidp.ko
kernel/net/bluetooth/rfcomm/rfcomm.ko
kernel/net/bluetooth/bnep/bnep.ko
kernel/drivers/bluetooth/btusb.ko
kernel/net/bluetooth/bluetooth.ko

make -C /lib/modules/2.6.35-22-generic-pae/build M=/home/daniel/compat-wireless-2010-10-16 modules
make: *** /lib/modules/2.6.35-22-generic-pae/build: No such file or directory. Stop.
make: *** [modules] Error 2
root@Daniel-Aspire-5741:/home/daniel/compat-wireless-2010-10-16# sudo make unload
/home/daniel/compat-wireless-2010-10-16/config.mk:196: "WARNING: CONFIG_CFG80211_WEXT will be deactivated or not working because kernel was compiled with CONFIG_WIRELESS_EXT=n. Tools using wext interface like iwconfig will not work. To activate it build your kernel e.g. with CONFIG_LIBIPW=m."
Stoping bluetooth service..
 * bluetooth is not running
Unloading ath9k...
root@Daniel-Aspire-5741:/home/daniel/compat-wireless-2010-10-16# 



Honestly any help with this would greatly be appreciated I've been searching countless forums and non have worked. If you need further information please just ask. :)

---

### Post by vicmate on 2010-11-03
> **Newbie789 said:**
> I would like to thank you for the great fix, however, now for some reason when I open terminals and use airmon-ng commands, my computer locks up and I have to hold the power button to shut it off every time... is there something that can fix this?

Any idea what's wrong?
I have an Atheros AR5009 (ath9k) wireless driver, and followed the instructions exactly... are these instructions not compatible with my system?

*Edit*
Sorry, I figured out what I was doing wrong!

Great fix!!!! hahah

What did yo do to fix it? 

I'm having a similar problem now. 
I'm using wepcrackgui with aircrack in ubuntu netbook edition, before I used the updates provided on page 1, I was getting the -1 error. Now after the updates on page 1, I don't get the -1 error any more although every time I go to authenticate, my computer locks up and I need to pull the plug to turn it off. 

Does anyone have any idea's? I don't want to give up yet...

---

### Post by almark on 2010-11-03
> **SquirrelScript said:**
> After upgrading to Ubuntu 10.10, I found that airodump-ng and aireplay-ng didn't want to work:
**Setup**
OS: Ubuntu 10.10 
Kernel: 2.6.35-22-generic-pae
WiFi Card: Intel iwlwifi iwlagn Intel Corporation WiFi Link 5100

**How?** 
```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2
tar -jxf compat-wireless-2010-10-16.tar.bz2
cd compat-wireless-2010-10-16
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo reboot
```Hope it helps someone[/I]
Excellent this fixed my problem aircrack problem too. Thanks a lot!

Regards
Mark

---

### Post by Acme22 on 2010-11-05
First thanks for all and second if the kernel is updated we have to redo this?
Thanks

---

### Post by seth_rutland01 on 2010-11-07
firstly thanks for the fix this has taken away the -1 error the only problem i have now is when i run the 
sudo airmon-ng start wlan0 (channel) 
it does not appear to be fixed on the set channel and i get like nine people connected to router which is not correct as there is only one other laptop connected will this still get a wpa handshake have tried disconnecting from the router on other laptop and reconnecting but it will not pick up the handshake 

any help much appreciated

---

### Post by laaraj11 on 2010-11-07
Thank you very much !
it work's for me :P

---

### Post by castruita on 2010-11-09
> **vicmate said:**
> What did yo do to fix it? 

I'm having a similar problem now. 
I'm using wepcrackgui with aircrack in ubuntu netbook edition, before I used the updates provided on page 1, I was getting the -1 error. Now after the updates on page 1, I don't get the -1 error any more although every time I go to authenticate, my computer locks up and I need to pull the plug to turn it off. 

Does anyone have any idea's? I don't want to give up yet...
I have the same problem too... did you solved it?

---

### Post by path0s on 2010-11-10
First off, big thanks on the -1 fix, worked like a champ! I did initially try to patch yesterday's source for compat-wireless and even though it patched fine, it wouldn't compile. The source linked in the tutorial does patch and compile fine though.
 
Any idea when this might get pulled into the official compat-wireless tree?
 
If it appears that radio isn't locking onto a channel in airodump, you might try starting the monitor interface locked onto a channel as well as the --channel switch with airodump. You can do that by using 'airmon-ng start <interface> <channel>' so for me to lock onto channel 6 with my setup, I use 'airmon-ng start wlan0 6'
 
I too am having issues with my wifi dongle and/or system locking up sometimes. I'm pretty sure it comes from having stuff like wpa-supplicant and avahi and the other apps running that airmon-ng complains about when you start the monitor interface. I tried killing those processes but the system immediately restarts them. I'm trying to find the correct non-permanent way to disable and enable those apps at will without rebooting (maybe using the 'service' cli interface?). Any ideas?
 
Again, thanks a ton for the patches and tutorial. Good stuff!

---

### Post by soulseek on 2010-11-11
I used the above instructions and the fix does no survive a reboot.

If I want wireless after reboot I have to make unload first and then modprobe b43. If not I get an error on b43.so


Anyone knows how to fix it?


Thanks

---

### Post by jrvasquezb on 2010-11-12
> **soulseek said:**
> I used the above instructions and the fix does no survive a reboot.

If I want wireless after reboot I have to make unload first and then modprobe b43. If not I get an error on b43.so


Anyone knows how to fix it?


Thanks

update-initramfs -u

---

### Post by putrid on 2010-11-13
Got a problem..

```

**:~$ patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patchpatching file net/mac80211/tx.c**

Hunk #1 FAILED at 677.
1 out of 1 hunk FAILED -- saving rejects to file net/mac80211/tx.c.rej
```
```

[B]:~$ patch ./net/wireless/chan.c channel-negative-one-maxim.patchpatching file ./net/wireless/chan.c
[/B]
Hunk #1 FAILED at 49.
Hunk #2 FAILED at 76.
2 out of 2 hunks FAILED -- saving rejects to file ./net/wireless/chan.c.rej

```

[SIZE="2"]Wireless Hardware:
product: AR5001 Wireless Network 
vendor: Atheros Communications Inc.

Ubuntu: 10.10
emachines E725[/SIZE]

Thanks for the how-to! Cant wait to get this fixed!

-putrid

---

### Post by path0s on 2010-11-13
If it's  failing the patch, you didn't grab the proper source tarball from the first post. Either the patch files would of had to of changed or the source tarball since I recompiled and I believe neither is the case.

---

### Post by phazed on 2010-11-13
Woot Woot!

Upgraded to 10.10 and had the fixed channel -1 problem... THIS FIXED IT RIGHT UP!

You... are.... awesome!

Using Asus 1005HA Netbook with Ath9k Drivers, WICD. Confirmed 100% GO, no lockups here!

Sincerely,
Aaron

---

### Post by Vfire on 2010-11-15
Hey gang, exciting work you're all doing here. .  Question - anyone have any success w/ the intel 3945 , or is there no love for this chip.

After the first attempt, I lost the whole OS, and that sucked. I'm to blame b/c I deleted all the packages after install - don't do that.  so reinstalled now have one lame OS and the newest fresh install.

Did the patch, and no more -1 ty tu - but now when I say airmon-ng start wlan0 10,  .. airodump says it's on 11!! This is like the game of golf. It will drive u insane but must play

Also as I am noob, does any concern exist for the compat-wireless version. . I seem to recall concern about the bleeding edge stuff.     ,  or will the patch always work with the latest version of the compat-wireless family? 

Someone please tell me some good news about the Intel 3945 :) :)

muchos gracias


**EDIT***  got everything working . .  I was doing a classic mistake.   the wireless connection kept re-connecting to my default..   needed to make sure everything was OFF..   then worked like a champ.  make sure all connections are off before starting anything.. my 2 cents

---

### Post by jacky.alcine on 2010-11-16
Just making sure, this collection of Bash corrects the channel error found in **airodump-ng** and allows channel hopping in **aireplay-ng**?

Because that's my problem.
Do you know any possible side effects?

---

### Post by jensbodal on 2010-11-17
I was stupid and enabled the pre-release updates in the Synaptic package manager while trying to figure out how to solve this problem, assuming this is going to cause problems in fixing this.

The 10-16-2010 drivers did not work, currently trying with the 11-16 drivers but not very hopeful.  Wondering if I now just need to reinstall 10.10...

Using a Broadcom Chipset BCM4311

---

### Post by SquirrelScript on 2010-11-17
@Everyone,
I'm glad that your WiFi cards are working once more! (=
And to the people that are saying "will this work with xxxx", why don't you try it first & see if it does work! :)
*Sorry I haven't been keeping up-to-date with everyones replys as well*



> **jacky.alcine said:**
> Just making sure, this collection of Bash corrects the channel error found in **airodump-ng** and allows channel hopping in **aireplay-ng**?

Because that's my problem.
Do you know any possible side effects?
Yep.
Other than it working, no (= *No-one has reported anything as far as I know*



> **jensbodal said:**
> I was stupid and enabled the pre-release  updates in the Synaptic package manager while trying to figure out how  to solve this problem, assuming this is going to cause problems in  fixing this.

The 10-16-2010 drivers did not work, currently trying with the 11-16  drivers but not very hopeful.  Wondering if I now just need to reinstall  10.10...

Using a Broadcom Chipset BCM4311

When you say its "not working". What not working, what happens, whats on the screen?

---

### Post by jacky.alcine on 2010-11-17
So I attempted to use the bash shown at the start of this thread. and this appeared.

```
"WARNING: CONFIG_CFG80211_WEXT will be deactivated or not working because kernel was compiled with CONFIG_WIRELESS_EXT=n. Tools using wext interface like iwconfig will not work. To activate it build your kernel e.g. with CONFIG_LIBIPW=m."
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h

make -C /lib/modules/2.6.35-22-generic/build M=/home/jacky/Desktop/compat-wireless-2010-10-16 modules
make: *** /lib/modules/2.6.35-22-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2

```

What should I do?

---

### Post by jacky.alcine on 2010-11-17
So I was looking through Synaptic and I found two packages that were related to wireless-compat.:lolflag:

---

### Post by jensbodal on 2010-11-17
> **SquirrelScript said:**
> When you say its "not working". What not working, what happens, whats on the screen?

I followed your instructions as best I could, and I'm pretty sure everything installed/patched just fine.  What I mean by it is "not working" I mean I was still receiving the: 'AP is on channel X by card is on channel Y error.'

I was able to use Wireless just fine, so aside from the card continuing to have issues in monitor mode I guess the patch worked.

I have now reformatted twice because I tried some other methods.  I am back to square 1 with a fresh 10.10 install and all the generic updates from Synaptic Package manager.  I need to first figure out how I can do a basic system backup so that I can tinker with this more and not have to spend an hour reformatting by screwing something up.

---

### Post by Vfire on 2010-11-17
> **jensbodal said:**
> I followed your instructions as best I could, and I'm pretty sure everything installed/patched just fine.  What I mean by it is "not working" I mean I was still receiving the: 'AP is on channel X by card is on channel Y error.'
p.

Is the Y the -1 error?   Sounds very much like your wlan is still in managed mode, everything is off before u go to monitor right?   check 
```
 iwconfig 
```

---

### Post by jensbodal on 2010-11-17
> **Vfire said:**
> Is the Y the -1 error?   Sounds very much like your wlan is still in managed mode, everything is off before u go to monitor right?   check 
```
 iwconfig 
```

As far as I know, what am I looking for in iwconfig?

I've tried doing
```

sudo ifconfig wlan0 down
sudo airmon-ng start wlan0
sudo ifconfig wlan0 up

```

Then using the mon0 interface for aireplay:
```

sudo aireplay-ng -1 0 -e SSID -h APMAC -a MYMAC mon0
mon0 is on channel -1, but the AP uses channel 6

```

---

### Post by jensbodal on 2010-11-18
How do I check for sure I installed the Compat Wireless drivers correctly?

---

### Post by Rizado on 2010-11-20
There's a problem with atleast the kernels in phc-linux ppa. For some reason modules install to /lib/modules/2.6.35.4 which is not correct, hence they do not get loaded. Have not tried to compile compat-wireless on the regular kernel yet...

---

### Post by ssc351 on 2010-11-20
Hey guys,

I was having a similar problem but I am running lucid.  I have an atheros ar9287 card and using ath9k drivers via stock install.  

I ran this tutorial to fix the same issue, but now my whole system freezes up after about 2 mins of running.  If I turn the wireless off, it runs no problem, so I assume it has to do with the patching with the compat-wireless stuff.

Is there a way I can get rid of it to get my wireless working again?  Or better yet, a way to use the patched driver so it doesn't freeze up my system?

---

### Post by SquirrelScript on 2010-11-21
> **jensbodal said:**
> I followed your instructions as best I could,  and I'm pretty sure everything installed/patched just fine.  What I mean  by it is "not working" I mean I was still receiving the: 'AP is on  channel X by card is on channel Y error.'

I was able to use Wireless just fine, so aside from the card continuing to have issues in monitor mode I guess the patch worked.

I have now reformatted twice because I tried some other methods.  I am  back to square 1 with a fresh 10.10 install and all the generic updates  from Synaptic Package manager.  I need to first figure out how I can do a  basic system backup so that I can tinker with this more and not have to  spend an hour reformatting by screwing something up.
Try this:
```

sudo ifconfig wlan0 up
sudo airmon-ng start wlan0 6
sudo airodump-ng -c 6 --bssid APMAC mon0
sudo aireplay-ng -1 0 -h APMAC -e SSID -a MYMAC mon0

```If that doesn't work, what is the output when you try:
```

iwconfig

```



> **jensbodal said:**
> How do I check for sure I installed the Compat Wireless drivers correctly?
Are you connected to the network afterwords? Are you able to surf the internet using your WiFi?



> **Rizado said:**
> There's a problem with atleast the kernels in  phc-linux ppa. For some reason modules install to /lib/modules/2.6.35.4  which is not correct, hence they do not get loaded. Have not tried to  compile compat-wireless on the regular kernel yet...
I don't have/use that kernel - and Im out of my depth on that issue. Sorry! Best of luck with it though



> **ssc351 said:**
> Hey guys,

I was having a similar problem but I am running lucid.  I have an  atheros ar9287 card and using ath9k drivers via stock install.  

I ran this tutorial to fix the same issue, but now my whole system  freezes up after about 2 mins of running.  If I turn the wireless off,  it runs no problem, so I assume it has to do with the patching with the  compat-wireless stuff.

Is there a way I can get rid of it to get my wireless working again?  Or  better yet, a way to use the patched driver so it doesn't freeze up my  system?
Does the caps lock key blink? (Then its a kernel failure)

---

### Post by ssc351 on 2010-11-21
> **SquirrelScript said:**
> 
Does the caps lock key blink? (Then its a kernel failure)

The Caps lock key DOES NOT blink...anything I can try?

---

### Post by Hamzouzz on 2010-11-21
Many thanks to you SquirrelScript, many sleepless nights to get this problem sorted and searching the web for an answer and finally fell on your thread. Everything now works like a charm :), I can't thank you enough! 

I registered on this forum just to thank you. :)

---

### Post by jensbodal on 2010-11-22
> **SquirrelScript said:**
> Try this:
```

sudo ifconfig wlan0 up
sudo airmon-ng start wlan0 6
sudo airodump-ng -c 6 --bssid APMAC mon0
sudo aireplay-ng -1 0 -h APMAC -e SSID -a MYMAC mon0

```If that doesn't work, what is the output when you try:
```

iwconfig

```

OK I gave this another shot and did not have any luck.  I have tried with 2 different compat drivers as well as the B43 driver.  

iwconfig gives:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"CONVICTED SEX OFFENDERS"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:24:A5:42:AA:42   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mon0      IEEE 802.11bg  Mode:Monitor  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

This is with stock drivers now however.  

[QUOTE=SquirrelScript]
Are you connected to the network afterwords? Are you able to surf the internet using your WiFi?[/quote]

I was able to surf the internet afterwards yes.  I am following the directions verbatim.

---

### Post by jensbodal on 2010-11-22
OK I just tried again and this time I was not able to connect to the internet.  Everything in the install went fine without error, I changed line 13 of the scripts/update-initramfs file as directed.  After reboot the wireless indicator just shows a red exclamation work in it.  Only way I've figured out to get things working again is to go into the compat directory and do a sudo make uninstall then reboot.

---

### Post by jensbodal on 2010-11-23
I just added Backtrack 4 as a triple boot option and tried running aircrack from there and it worked perfectly.  I think this is because BT4 loads up with my wireless cards fully down, and simply doing ifconfig wlan0 down is not doing the job here.

---

### Post by AdamSiEva on 2010-11-27
> **jensbodal said:**
> OK I just tried again and this time I was not able to connect to the internet.  Everything in the install went fine without error, I changed line 13 of the scripts/update-initramfs file as directed.  After reboot the wireless indicator just shows a red exclamation work in it.  Only way I've figured out to get things working again is to go into the compat directory and do a sudo make uninstall then reboot.

Same problem here. I have a Broadcom wireless card and when i install the compat driver everything f*cks up.

---

### Post by Starter Rager on 2010-12-02
> [QUOTE]Quote:
Originally Posted by jensbodal  
OK I just tried again and this time I was not able to connect to the internet. Everything in the install went fine without error, I changed line 13 of the scripts/update-initramfs file as directed. After reboot the wireless indicator just shows a red exclamation work in it. Only way I've figured out to get things working again is to go into the compat directory and do a sudo make uninstall then reboot.
Same problem here. I have a Broadcom wireless card and when i install the compat driver everything f*cks up.[/QUOTE]

I also have a Broadcom wireless card 
lspci output:
Network Controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

This happens to me, my wireless gets disabled after I follow everything you posted initially. /edit: tried it again, wireless gets disabled directly after sudo make unload
i.e.
Unloading b43...
*disconnected from 'wireless network'*

I had to manually change '2.6.31-wl' on line 13 to 'uname -r' which in my case is '2.6.35-22-generic'

Everything else seemed to work, 'make' took a long time but that's probably normal.
 
So, it 'works' but my wireless gets disabled...

---

### Post by Korsakoff on 2010-12-06
thanks man

---

### Post by mampe on 2010-12-09
Hi.
I'm new to using ubuntu so pleace bear with me.
I have had problems running aireplay-ng since my wireless card was lock on different channel than my network. I had hoped that this script would have helped but now I'm totally f.... since bothe my wireless card and my wired internet connections are gone.
iwconfig result in:
lo no wireless extension
eth0 no wireless extensions

I got no errors when running the script. Can anyone please help.

Regards

---

### Post by mbossard on 2010-12-15
> **SquirrelScript said:**
> After upgrading to Ubuntu 10.10, I found that airodump-ng and aireplay-ng didn't want to work:
**Setup**
OS: Ubuntu 10.10 
Kernel: 2.6.35-22-generic-pae
WiFi Card: Intel iwlwifi iwlagn Intel Corporation WiFi Link 5100

**How?** 
```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2
tar -jxf compat-wireless-2010-10-16.tar.bz2
cd compat-wireless-2010-10-16
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo reboot
```Hope it helps someone[/I]

I have ath5k, and I just implemented this patch on the 'bleeding-edge' compat-wireless package (2010-12-14), and it worked swimmingly!
**[COLOR="Red"]NOTE:[/COLOR]** the patch files are not compatible with the current package, so manual editing/patching is required.  Sorry, I don't have time to update the patch files, but PM me if you want my patched files for the 2010-12-14 [compat-wireless]("http://linuxwireless.org/en/users/Download") package.

Thanks **SquirrelScript**! :P

---

### Post by briml3y on 2010-12-16
As previously mentioned there are some compat-wireless related packages available through synaptic. 

```
linux-backports-modules-compat-wireless-2.6.36-generic
linux-backports-modules-compat-wireless-2.6.36-generic-pae

You likely do not want to install this package directly. Instead, install
the linux-backports-modules-compat-wireless-2.6.36-generic meta-package, which will ensure
that upgrades work correctly, and that supporting packages are also installed.
```

Does anyone know what the pae stands for?

Also can these packages be used? I would like to keep my drivers updated as time goes on.

---

### Post by thatllmovethechains on 2010-12-16
Hi I just installed the patches that were outlined but now my system freezes occasionally when the wireless get left on. It seems to be the same problem explained in [http://ubuntuforums.org/showthread.php?t=1629129](http://ubuntuforums.org/showthread.php?t=1629129). Has anybody else experienced this?

Thanks a lot

---

### Post by Erik500002 on 2010-12-16
Wow, finally solved my problem but i had to use the [compat-wireless-2.6.35-1.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.35/compat-wireless-2.6.35-1.tar.bz2") in order to work since the one squirrel had would make my AR5008 crash everytime, Thanks for everything man :D

---

### Post by thatllmovethechains on 2010-12-16
> **Erik500002 said:**
> Wow, finally solved my problem but i had to use the [compat-wireless-2.6.35-1.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.35/compat-wireless-2.6.35-1.tar.bz2") in order to work since the one squirrel had would make my AR5008 crash everytime, Thanks for everything man :D
Hey Erik500002,
When you said your AR5008 crashed everytime, was that during installation or afterwards?

---

### Post by omnomnom1 on 2010-12-20
I'm having errors at the "make" commands... Didn't work for me :/.

---

### Post by bstep on 2010-12-25
SquirrelScript, great job in fixing the problem. Just curious, how many times have you tried with diferent drivers until success.

I have a problem now,and not shure how to fix it. There is alfa  awus036h wich is working now thanks to the "-1" fix. But I have an mini pci card bcm4318,wich is not working after the patch install.
Does anyone knows how to make this card work without messing with the other driver? No injection necessary for this card.

Again, thanks for the "-1" man.

---

### Post by ekjsim on 2010-12-30
kernel: 2.6.35-24 generic
wireless card: Intel 4965 AGN

The codes given to update did not cause any problems with the wireless. But it doesn't seem to have worked? 

14:26:49  Waiting for beacon frame (BSSID: 00:25:5E:26:FF:FF) on channel -1
14:26:49  mon0 is on channel -1, but the AP uses channel 11
It is still stuck at -1

*Sorry, I am new linux user (2 days old). This is my first linux personal computer!*

iwconfig shows:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Hello world"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:25:5E:26:FF:FF  
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:67   Missed beacon:0

mon0      IEEE 802.11abg  Mode:Monitor  Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

What could I have done wrong? Can anybody point me to the right direction?

codes I used for aircrack are

Terminal #1
airmon-ng start wlan0
airodump-ng mon0
airodump-ng -c 11 -w 'Hello world' --bssid  00:25:5E:26:FF:FF  mon0

Terminal #2
aireplay-ng -1 0 -a   00:25:5E:26:FF:FF -h 00:11:22:33:44:55 mon0  <- after this line I get the -1 error

Any help would be appreciated :)

EDIT: I try installing it twice, doesn't seem to be working still

---

### Post by inzhagiz on 2010-12-30
yeah, it's works. finally solved my problem. Thanks for everything man

---

### Post by rom3lol on 2010-12-31
Is their a way to uninstall these? This worked for me but then my desktop freezes and my desktop goes black.

When I restart The caps lock button blinks? How can I fix these?
Can I undo these? Thanks in Advanced

---

### Post by ekjsim on 2011-01-02
Ubuntu10.10
Kernel: 2.6.35-24
Aircrack-ng 1.0 
Intel 4965 AGN [ Iwlagn ]
last tested 10/1/2011

Below are steps required if you still get fixed channel issues after installing "squirrel's patch". Note that this is a workaround in case the patch didn't work too well... 


Step1: Firstly uninstall aircrack 1.1

Step2: Go to[ http://www.brothersoft.com/aircrack-download-326409.html]("http://www.brothersoft.com/aircrack-download-326409.html")
to get Aircrack-ng 1.0 - (C) 2006, 2007, 2008, 2009 Thomas d'Otreppe

Step3: install these files
**apt-get install libssl-dev**
**apt-get install iw**

Step4: Put the tar ballzz in your home folder.

Step5: extract and install aircrack 1.0
[B]tar -jxf aircrack-ng-1.0.tar.gz
cd aircrack-ng-1.0
make install [/B]

You should be on your way! :)

REMINDER, if you still get -1 error, you still need the "squirrel's patch" codes...

---

### Post by ekjsim on 2011-01-04
> **rom3lol said:**
> Is their a way to uninstall these? This worked for me but then my desktop freezes and my desktop goes black.

When I restart The caps lock button blinks? How can I fix these?
Can I undo these? Thanks in Advanced

In terminal
Go to compat wireless folder. run command
sudo make uninstall
sudo reboot

---

### Post by xvilar on 2011-01-04
Hiya My friends, I'm triyng to patch the aircrack-ng 1.1 that I'm running in my laptop SD Card Permanent Ubuntu 10.10 ... and I get an error doing "make install":


[I]make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
Updating Ubuntu's initramfs for 2.6.35-22-generic under /boot/ ...
Will now run update-grub to ensure grub will find the new initramfs ...
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
make: *** [install-modules] Error 1
[/I]

I think I'm not using Grub... I boot from my SD card with Ubuntu 10.10 installed into, with " Universal USB Installer" and as PERMANENT 1gb.

N1 here could help me please? thnx in advance, cheers!

---

### Post by xvilar on 2011-01-04
> **ekjsim said:**
> Ubuntu10.10
Kernel: 2.6.35-24
Aircrack-ng 1.0 
Intel 4965 AGN [ Iwlagn ]
last tested 3/1/2011

For those who has problem with this fixed channel on Ubuntu 10.10 (and still have them after this compat-wireless patch update)

Firstly uninstall aircrack 1.1

Go to
[http://www.brothersoft.com/aircrack-download-326409.html](http://www.brothersoft.com/aircrack-download-326409.html)
to get Aircrack-ng 1.0 - (C) 2006, 2007, 2008, 2009 Thomas d'Otreppe

Put the tar ballzz in your home folder.

[B]tar -jxf aircrack-ng-1.0.tar.gz
cd aircrack-ng-1.0
make install [/B]

OOPS, there's an error. To fix the error, run the command below, then run **make install** again
**apt-get install libssl-dev**
when you try to start airmon if an error comes out regarding to iw or libl-devel, then run the following command
**apt-get install iw**

You should be on your way! :)

It doesnt work for me ... :-( and still cannot apply the patches (grub error on Make install)... anyway thnx

---

### Post by ekjsim on 2011-01-05
> **xvilar said:**
> It doesnt work for me ... :-( and still cannot apply the patches (grub error on Make install)... anyway thnx

Can you install anything at all?

---

### Post by mikejonesey on 2011-01-06
after running the;

sudo make unload

I lost my wireless in the nm-applet and my wlan0

I then ran;

sudo make wlload

which restores wlan0 among others, but I still have nothing in nm-applet (can't connect to any wireless).

Is there somthing i'm missing, if not how do i revert,

many thanks

------------------------

wierd, nm-applet just picked up... I now have wirless again... but i'm stuck on channel -1 again...

------------------------

sorry for long post:

mike@mike-laptop:~/Downloads/compat-wireless-2010-10-16$ sudo make wlload
[sudo] password for mike: 
Unloading b43...
Loading ipw2100...
Loading ipw2200...
Loading libertas_cs...
Loading usb8xxx...
Loading p54pci...
Loading p54usb...
Loading adm8211...
Loading zd1211rw...
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
Loading p54usb...
Loading iwl3945...
Loading iwlagn...
Loading ath...
Loading ar9170usb...
Loading rtl8180...
Loading rtl8187...
Loading rt2400pci...
Loading rt2500pci...
Loading rt61pci...
Loading rt2500usb...
Loading rt73usb...
Loading rndis_wlan...
Loading at76_usb...
FATAL: Module at76_usb not found.
Loading mwl8k...
Loading mac80211_hwsim...
Loading at76c50x_usb...
Module ath_pci not detected -- this is fine
ath5k loaded successfully
ath9k loaded successfully
Module bcm43xx not detected -- this is fine
Module wl not detected -- this is fine
b43 loaded successfully
b43legacy loaded successfully
mike@mike-laptop:~/Downloads/compat-wireless-2010-10-16$ 

mean I am loading too many... right? how do i tell it to just load the new b43 module?

----------------------------------

Iv'e tested all wlan's after doing the load (wlan0,wlan1 and wlan2-wlan0) all work with airodump but are all stuck on channel -1 still, so I can't see the fix has worked? any advice to help me?

---

### Post by xvilar on 2011-01-06
> **ekjsim said:**
> Can you install anything at all?


Yes, but with aircrack-ng 1.0 (it is what is installed with your workaruond) I'm still getting channel -1 errors... ¿?

Do you know how to bypass Grub make install errors I have? (it's explained in a post before my ones you have quoted...)

thnx!

---

### Post by mikejonesey on 2011-01-07
I've now added to my problems.... I installed compat-wireless from the  repos (synaptic package manager), which installed packages without the  build folder so I can't use the make command on my patched version now  even after removing the extra installed packages...

how can I revert?

...

many thanks for any help...

---------------------------

the reason i can't make is i get the following;

```
mike@mike-laptop:~/Downloads/compat-wireless-2010-10-16$ make
/home/mike/Downloads/compat-wireless-2010-10-16/config.mk:196: "WARNING: CONFIG_CFG80211_WEXT will be deactivated or not working because kernel was compiled with CONFIG_WIRELESS_EXT=n. Tools using wext interface like iwconfig will not work. To activate it build your kernel e.g. with CONFIG_LIBIPW=m."
make -C /lib/modules/2.6.35-24-generic-pae/build M=/home/mike/Downloads/compat-wireless-2010-10-16 modules
make: *** /lib/modules/2.6.35-24-generic-pae/build: No such file or directory. Stop.
make: *** [modules] Error 2
```This means somewhere there is a command to tell the compiler which lib module to use, if I can switch this back to one with a build folder it should work again, to find this I need a grep command, can anyone help me with this?

(I asume i can find a file with /lib/modules/2.6.35-24-generic-pae to change to /lib/modules/2.6.35-24-generic)

------------------------------

further reading leads me to believe I need to revert my selected kernel...

----------------------------

lol real messy, prob cause problems later... but...
```
cd /lib/modules/2.6.35-24-generic-pae
sudo ln -s ../2.6.35-24-generic/build build
```

-------------------

the proper fix; I searched synaptic for pae, found that kernel and marked for complete removal, rebooted and i'm now back on 2.6.35-24-generic which has it's own build folder... I can now build compat-wireless again :)

---

### Post by mikejonesey on 2011-01-07
made again...

now no wlan0 again...

can anyone help with this?

```
mike@mike-laptop:~$ sudo modprobe b43
[sudo] password for mike: 
FATAL: Error inserting b43 (/lib/modules/2.6.35-24-generic/updates/compat-wireless-2.6.36/b43.ko): Invalid argument

```

---------------------

worked out the prob, before it loaded b43, after install and it does the interim update it loads;
ssb... and mac80211...

...no good for me... how do i get it to install the b43 only?

---

### Post by mikejonesey on 2011-01-07
YEY YEY YEY :) :) :), it works!!!

I just deleted all the newly installed stuff, started again but this time I only patched with the -1 patch and missed the other one out.

thanks for all the info in this thread... :D

---

### Post by rom3lol on 2011-01-08
> **ekjsim said:**
> In terminal
Go to compat wireless folder. run command
sudo make uninstall
sudo reboot

Thank's this fixed the issue. Now that I removed it I get the fixed channel again.
The problem is when I install the patch on this tutorial my computer freezes and goes black every time I connect too the internet? Any ideas as too getting around this?

---

### Post by UlyssesTheBarbarian on 2011-01-08
> **SquirrelScript said:**
> After upgrading to Ubuntu 10.10, I found that airodump-ng and aireplay-ng didn't want to work:
**Setup**
OS: Ubuntu 10.10 
Kernel: 2.6.35-22-generic-pae
WiFi Card: Intel iwlwifi iwlagn Intel Corporation WiFi Link 5100

**How?** 
```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2
tar -jxf compat-wireless-2010-10-16.tar.bz2
cd compat-wireless-2010-10-16
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo reboot
```Hope it helps someone[/I]

Hi - thanks for this, it got rid of the channel -1 issue. As a newbie, I am still trying to figure out how to do the above patches as well as the wifi driver packet injection patches.

Ubuntu 10.10 (64 bit)
kernel 2.6.35-24-generic
Intel Wireless WiFi Link 4965AGN

Within the compat-wireless-2010-10-16 directory as above, I follow the commands on [http://airodump.net/packet-injection-wifi-intel-4965/](http://airodump.net/packet-injection-wifi-intel-4965/)

i.e.

wget [http://pastebin.com/pastebin.php?dl=f7bc96631](http://pastebin.com/pastebin.php?dl=f7bc96631) -O iwl4965-injection.patch
wget [http://patches.aircrack-ng.org/mac80211_2.6.26-wl_frag.patch](http://patches.aircrack-ng.org/mac80211_2.6.26-wl_frag.patch)
patch -p1 < iwl4965-injection.patch

but get the following error on the 3rd command:

(Stripping trailing CRs from patch.)
patching file drivers/net/wireless/iwlwifi/iwl-sta.c
Hunk #1 FAILED at 968.
1 out of 1 hunk FAILED -- saving rejects to file drivers/net/wireless/iwlwifi/iwl-sta.c.rej
(Stripping trailing CRs from patch.)
patching file drivers/net/wireless/iwlwifi/iwl-tx.c
Hunk #1 FAILED at 783.
Hunk #2 FAILED at 810.
Hunk #3 FAILED at 822.
3 out of 3 hunks FAILED -- saving rejects to file drivers/net/wireless/iwlwifi/iwl-tx.c.rej
(Stripping trailing CRs from patch.)
patching file drivers/net/wireless/iwlwifi/iwl4965-base.c
Hunk #1 FAILED at 2680.
patch unexpectedly ends in middle of line
1 out of 1 hunk FAILED -- saving rejects to file drivers/net/wireless/iwlwifi/iwl4965-base.c.rej
patch unexpectedly ends in middle of line

Would be grateful if someone could point me in the right direction please?

---

### Post by hauk142 on 2011-01-09
huh, this is strange. 

I did as the tutorial said, and it worked XD.

But now i have a slight problem....
I can not connect to access points.
When i connect to an access point and start firefox, the whole kernel panics after a few seconds:
The whole system freezes, and caps lock starts blinking.

A little later I found that it appeared to be having problems to connect only on open networks.... 

What can i do to fix it without reverting back to mon0 channel -1??

-hauk

---

### Post by ekjsim on 2011-01-10
> **xvilar said:**
> Yes, but with aircrack-ng 1.0 (it is what is installed with your workaruond) I'm still getting channel -1 errors... ¿?

Do you know how to bypass Grub make install errors I have? (it's explained in a post before my ones you have quoted...)

thnx!

You still need the patch... As in, you will still need the patch in this thread. With the patch in this thread, and aircrack 1.0, it will WORK.

Sorry, I have no idea how to solve the grub error.

---

### Post by ekjsim on 2011-01-10
Oops...  Posted twice

<- Post deleted ->

---

### Post by ekjsim on 2011-01-10
UPDATED for better clarification!

> **ekjsim said:**
> Ubuntu10.10
Kernel: 2.6.35-24
Aircrack-ng 1.0 
Intel 4965 AGN [ Iwlagn ]
last tested 10/1/2011

Below are steps required if you still get fixed channel issues after  installing "squirrel's patch". Note that this is a workaround in case  the patch didn't work too well... 


Step1: Firstly uninstall aircrack 1.1

Step2: Go to[ http://www.brothersoft.com/aircrack-download-326409.html]("http://www.brothersoft.com/aircrack-download-326409.html")
to get Aircrack-ng 1.0 - (C) 2006, 2007, 2008, 2009 Thomas d'Otreppe

Step3: install these files
**apt-get install libssl-dev**
**apt-get install iw**

Step4: Put the tar ballzz in your home folder.

Step5: extract and install aircrack 1.0
[B]tar -jxf aircrack-ng-1.0.tar.gz
cd aircrack-ng-1.0
make install [/B]

You should be on your way! :smile:

REMINDER, if you still get -1 error, you still need the "squirrel's patch" codes...

---

### Post by xvilar on 2011-01-10
> **xvilar said:**
> Hiya My friends, I'm triyng to patch the aircrack-ng 1.1 that I'm running in my laptop SD Card Permanent Ubuntu 10.10 ... and I get an error doing "make install":


[I]make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
Updating Ubuntu's initramfs for 2.6.35-22-generic under /boot/ ...
Will now run update-grub to ensure grub will find the new initramfs ...
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
make: *** [install-modules] Error 1
[/I]

I think I'm not using Grub... I boot from my SD card with Ubuntu 10.10 installed into, with " Universal USB Installer" and as PERMANENT 1gb.

N1 here could help me please? thnx in advance, cheers!

I had a /boot/ folder in my Windows 7 partition that causes the grub error (impossible to update-grub). Deleted and "/boot" ones NOT "/Boot"... and now I can compile... cheers!

---

### Post by Name User on 2011-01-11
Hi everyone :D
First thanks squirrel! YMMD !
Ok just wanted pass on the info that i used the 
[compat-wireless-2011-01-10.tar.bz2]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2011-01-10.tar.bz2") (the newest i found)
and it worked fine. Injection etc.
No problems applying the patches.
You don't have to edit "update-initramfs" anymore though.
Running:
Ubuntu 10.10 with kernel:
2.6.35-24-generic with wifi card:
Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
You all have a good day!

---

### Post by MR2Quick on 2011-01-12
I basically copied and pasted these directions and now I don't have wireless... The adaptor disappeared completely. Any ideas?

---

### Post by Ravendark on 2011-01-15
> **MR2Quick said:**
> I basically copied and pasted these directions and now I don't have wireless... The adaptor disappeared completely. Any ideas?

same problem here.
I am using the ath9k driver and the module has disapeared.
How can I instal it back?

---

### Post by jpmorelli on 2011-01-16
Squirrellscript does a very good Job !!! Work perfect for me in my Acer Aspire One A150 with Ubuntu 10.10. Thank you  !!!

---

### Post by rom3lol on 2011-01-21
> **hauk142 said:**
> huh, this is strange. 

I did as the tutorial said, and it worked XD.

But now i have a slight problem....
I can not connect to access points.
When i connect to an access point and start firefox, the whole kernel panics after a few seconds:
The whole system freezes, and caps lock starts blinking.

A little later I found that it appeared to be having problems to connect only on open networks.... 

What can i do to fix it without reverting back to mon0 channel -1??

-hauk

Hello Hauk it seems we are having the same problem well I had the same problem.
What you need too do is uninstall the patches and drivers you installed.
If you the patches are in your home directory then use
```
$ ls
```
this will show the files that are their once you see them use
```
sudo make uninstall "name of the file"
```
use that for all the files you installed :D

---

### Post by mlkovacs on 2011-01-24
Thank you very much this solved my problem with -1 channel issue. I used the most recent compat-wireless available along with the two patches and everything worked fine. I am using ath9k driver with an AR9285.

---

### Post by jsevi83 on 2011-01-27
Did anyone check if kernel 2.6.35-25 and linux-backports-modules-compat-wireless fix this problem? Or we still need to fix it manually?

---

### Post by hodginsa on 2011-01-28
I too have lost all sightings of wlan0, on my broadcom BCM4318...

I had it for awhile but I reinstalled this patch and now its gone completely.

---

### Post by hodginsa on 2011-01-28
I have it working now. What I had to do was uninstall everything, get rid of aircrack 1.1 and install 1.0. reinstall compat with the patch described here except I did this instead.
(Notice the date change, shouldn't matter but its the latest one.) **<driver-name> is the driver you use for you wireless card.**

```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2011-01-27.tar.bz2
tar -jxf compat-wireless-2011-01-27.tar.bz2
cd compat-wireless-2011-01-27
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
./script/driver-select <driver-name>
make
sudo make install
sudo make wlunload
sudo modprobe <driver-name>
```

but now everytime I restart my computer I have to do 

```
cd compat-wireless-11.01.27
sudo make wlunload
sudo modprobe b43
```

Anyway to have the b43 driving start up automatically?

---

### Post by elfandereth on 2011-01-29
I am not an expert but maybe you can load b43 adding 'b43' without commas at the end of /etc/modules.

regards

---

### Post by hodginsa on 2011-01-29
Hmm, I thought that might work too and changed it before you mentioned it, but still nothing. 

It still loads 'ssb' and 'mac80211' on start up and not b43, because when I do 'sudo make wlunload' it says those two things are unloading.

What should be in my /etc/modprobe.d/options?

I have 'options b43 nohwcrypt=1' I'm not sure why I put that in there.

Whats telling my computer to load ssb and mac80211 and not b43?

---

### Post by hodginsa on 2011-01-29
Okay so I think I got it working. Hopefully this helps someone else.

This works for my case cause I have mac80211 and ssb running on start up. So it may not work for you if mac80211 or ssb isn't on your machine/interfering. 

You're going to edit /etc/rc.local (boot up commands)


```
Sudo gedit /etc/rc.local
```

add lines before 'exit 0'

```
rmmod mac80211
rmmod ssb
sleep 3
modprobe b43
```

the 'rmmod' removes those modules upon startup and the 'modprobe b43' is what I had to enter in manually before but now it waits and enters it automatically.

My wifi starts automatically now.

---

### Post by jd2012 on 2011-01-29
Hi all, 

Working with:
ASUS K50IJ Best buy Edition
Atheros AR9285 
Basic kernel drivers, SqurrelScript's Compat-Wireless driver patch.


When i run command:
```

sudo aireplay-ng -1 0 -a BS:SS:ID -h MY:MA:CA:DD:Y0 mon0

```I get "Association successful" with the smiley :-)

But after running:
```

sudo aireplay-ng -3 -b BS:SS:ID -h MY:MA:CA:DD:Y0 wlan0

```I get "wlan0 on channel 14 but AP is on channel 1"

**Side note** when i start airmon i do it like this:

```

sudo airmon-ng start wlan0 **1** 

```My AP being on channel 1, if i dont start airmon like that, I dont get the "Successful" Notif. instead I
get channel error.

Anyone shed some light?

Thanx,

---

### Post by jd2012 on 2011-01-29
To any and all it may help, after playing and searching around I found a somewhat solution.

Using:

```

sudo airodump-ng wlan0 --channel X

```Channel X being your AP's channel.
and:

```

sudo aireplay-ng -1 0 -e SSID -a BSSID -h FAKEMAC mon0

```This helped TREMENDOUSLY with staying connected to the AP.
And finally, using aircrack:

```

aircrack-ng -b BSSID filename*.cap

```Instead of:

```

aircrack-ng -b BSSID filename-01.cap

```Worked flawlessly, cracked my NETGEAR in under 5 minutes.

Hoped this helped someone.

---

### Post by hodginsa on 2011-01-30
I was going to mention you were using mon0 you have to use mon0 for aireplay and airodump as well.

I find you should reset the mon0 with the channel you want to use like 
```
sudo airmon-ng wlan0 <channel>
``` 

also you can try switching the channel by using

```
sudo ifconfig mon0 <channel>
```

But I can't recall

---

### Post by soad6 on 2011-01-31
please BUMP... fixed in kernel 2.6.35-25.

---

### Post by crownclown on 2011-02-02
> **SquirrelScript said:**
> After upgrading to Ubuntu 10.10, I found that airodump-ng and aireplay-ng didn't want to work:
**Setup**
OS: Ubuntu 10.10 
Kernel: 2.6.35-22-generic-pae
WiFi Card: Intel iwlwifi iwlagn Intel Corporation WiFi Link 5100

**How?** 
```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2
tar -jxf compat-wireless-2010-10-16.tar.bz2
cd compat-wireless-2010-10-16
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo reboot
```Hope it helps someone[/I]





thx to u man...i've solve my problem that have been 5 month waiting for solution...:guitar:

---

### Post by cirkomortale on 2011-02-03
> **SquirrelScript said:**
> After upgrading to Ubuntu 10.10, I found that airodump-ng and aireplay-ng didn't want to work:
**Setup**
OS: Ubuntu 10.10 
Kernel: 2.6.35-22-generic-pae
WiFi Card: Intel iwlwifi iwlagn Intel Corporation WiFi Link 5100

**How?** 
```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2
tar -jxf compat-wireless-2010-10-16.tar.bz2
cd compat-wireless-2010-10-16
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo reboot
```Hope it helps someone[/I]

not works in my case, 
how I can make all this change back now, so i can try some other instruction?

---

### Post by goyonavarro on 2011-02-04
I had the same problem as hauk142... I couldn't fix it, so i had to reinstall my system, but i still need to get rid of the fixed channel issue... Has anyone tried to patch compat-wireless on a live cd? Would that work?

---

### Post by kpappa on 2011-02-06
The problem has to do with Ubuntu Desktop v10.10 
I downgraded to 10.04LTS and no problems any more !
No system halt, no patch needed, no channel lock to -1, no madwifi to install, both aircrack v1.0 and v1.1 operate fine !
I'm using ath9K driver for my Atheros AR9285 embedded card.

---

### Post by Sc00by22 on 2011-02-06
I tried the fix but it disabled pretty much all the functionality of my laptop, I had no mouse, keyboard or networking. I uninstalled it and and everything is back to normal however I really do want to use this fix, anybody?

EDIT: Compiled and installed some different mac80211 drivers, working all good now!

---

### Post by stevomanu on 2011-02-10
> **soad6 said:**
> please BUMP... fixed in kernel 2.6.35-25.

i have updated to this kernal but i am still stuck on channel -1  anybody any ideas please , have tryed tut on first page but noting !! 

many thanks

---

### Post by PeteLong on 2011-02-15
Same running 2.6.35.25

With Intel 4695 (iwlagn driver) Patched as previously posted with compat-wireless-2011-02-14 Still I get

mon0 is on channel -1, but the AP uses channel 11
or
wlan0 is on channel -1, but the AP used channel 11

Ive spent ages searching (I am very new to Linux, and Quite why eveything has to be so difficult I do not know).

Pete
[PeteNetLive]("http://www.petenetlive.com")

---

### Post by sahilganguly on 2011-02-17
I patched everything as explained in this thread. And I got it to work. I remember mon0: 11 came up. But after a restart, its gone back to mon0: -1. 

Any ideas?

---

### Post by soad6 on 2011-02-25
Hi, I running ubuntu 10.10 with kernel 2.6.35-27-generic-pae. The problem is that I tried to use the directions from page 1 however, if I use them then my wifi card doesn't work and I have to recompile it from scratch, and then no usb wireless APs plugged in are recongized, this is from kernel 2.6.35-25 thru 27 so far as found for me. The card is realtek 8191VseB or A, depending on if I recompiled or if by default on system. The other card is a atheros ar9170usb. Not sure why this happens to those two cards. I'm going to look into other ways to change the channel from -1 to whatever I'd like to select.

---

### Post by asmaridis on 2011-02-27
For those who are having problems after the patch, try the following before you use airmon-ng start:

[B]service network-manager stop

[/B]This did the trick for me.

---

### Post by crownclown on 2011-03-01
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch

i dint make at this state.but it says that use the sudo apt-get install patch

so i type sudo apt-get install patch.it does install some patch.
or there are any solution for it ?

---

### Post by M8R-i22ji6@mailinator.com on 2011-03-03
> **hodginsa said:**
> I have it working now. What I had to do was uninstall everything, get rid of aircrack 1.1 and install 1.0. reinstall compat with the patch described here except I did this instead.
(Notice the date change, shouldn't matter but its the latest one.) **<driver-name> is the driver you use for you wireless card.**

```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2011-01-27.tar.bz2
tar -jxf compat-wireless-2011-01-27.tar.bz2
cd compat-wireless-2011-01-27
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
./script/driver-select <driver-name>
make
sudo make install
sudo make wlunload
sudo modprobe <driver-name>
```but now everytime I restart my computer I have to do 

```
cd compat-wireless-11.01.27
sudo make wlunload
sudo modprobe b43
```Anyway to have the b43 driving start up automatically?
ok i have an intel 5100 agn.  injection now works (fixes '**mon0 is on channel -1**').  driver name i used is **iwlagn**.  after running `make` i just followed the on screen directions.

this was with aircrack 1.1

thanks

---

### Post by hodginsa on 2011-03-03
Glad I could help, it would be cool is people understood one thing, since it took me a while to realize it myself.

If you go here. 
[http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)

It has all the patch files, and there is literally one uploaded every single day, with a different date. 

so for 

wget [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-)**2011-01-27**.tar.bz2
tar -jxf compat-wireless-**2011-01-27**.tar.bz2
cd compat-wireless-**2011-01-27**

You can change that to the latest release.which since its the 3rd of march would be 2011-03-03. If you look at the list it will be there(check first) This is what fixed an issue of mine the other day too.

---

### Post by complience on 2011-03-06
Tried to apply this patch because I was getting the channel error in airmon.

upon restarting I get a Loading Operation system then "segmentation fault" then "init: plymouth main process (341) killed by SEGV signal"

The only way I can boot my system is too select one of my unmodified legacy kernals... wtf is going on?

---

### Post by fabianr2 on 2011-03-09
Thx a lot!!! I worked fine in a Toshiba Satellite L305D, Atheros AR5BXB72 2.4 +5Ghz 11n

---

### Post by needlez6 on 2011-03-11
Hi, I have a better solution for everyone trying to use this patch that isn't able to get it working. You should go and download the svn package from aircrack-ng. first download the package for svn by running this in terminal.  [FONT=monospace]
[/FONT]svn co [http://trac.aircrack-ng.org/svn/trunk/](http://trac.aircrack-ng.org/svn/trunk/) aircrack-ng
then browse to that folder with cd and sudo make && make install
...
then when you want to use this version of aircrack-ng use the --ignore-negative-one option with aireplay-ng.
Any information you have please msg me

---

### Post by Mohsen_cia on 2011-03-17
You`re solution works fantastic ... 10/10

Thanks a lot.

---

### Post by zacorbul on 2011-04-03
Thank you soo much.

---

### Post by bitbomb on 2011-04-06
What exactly does this do?   

```
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build 
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
```Why is it necessary?

---

### Post by steveone on 2011-05-11
> **needlez6 said:**
> Hi, I have a better solution for everyone trying to use this patch that isn't able to get it working. You should go and download the svn package from aircrack-ng. first download the package for svn by running this in terminal.  [FONT=monospace]
[/FONT]svn co [http://trac.aircrack-ng.org/svn/trunk/](http://trac.aircrack-ng.org/svn/trunk/) aircrack-ng
then browse to that folder with cd and sudo make && make install
...
then when you want to use this version of aircrack-ng use the --ignore-negative-one option with aireplay-ng.
Any information you have please msg me
 
I get the following when I run the sudo make && make install command:

mkdir -p -- //usr/local/share/airoscript-ng/ //usr/local/share/doc/airoscript-ng/html/images //usr/local/etc //usr/local/share/man/man1 //usr/local/share/locale //usr/local/share/airoscript-ng//themes //usr/local/share/airoscript-ng//plugins //usr/local/share/airoscript-ng//airosperl //usr/local/share/doc/airoscript-ng/tools
Installing airoscript
Installing themes
Installing plugins
Installing documentation
     Installing standard documentation
     Installing html documentation
     Installing manpages
     Installing artwork
Installing locales
     Not installing locale es_ES (Not yet translated)

Installing airoscript
install: cannot remove `//usr/local/sbin//airoscript-ng': Permission denied
make: *** [install-binary] Error 1 

Any suggestions? Thank you in advance.

---

### Post by s0ysauce on 2011-05-15
Once you get the initial patch and everything that is needed, you will need to download and install the newer patches that are made available on the website. Once its too old, the issue will reoccur again. 

Does anyone know how to somehow place this as a source in the update manager?
That would be nice!

---

### Post by minglis on 2011-05-24
After I attempted to fix this with the patch listed, I no longer have any wireless working at all. If I check the additional drives, I'm told that the drivers are active, but not in use. I now see 2 drivers for the broadcom. Is there a way of undoing this fix so that I can go back to having a working wireless network again?

things I've tried:
reapply the patch
re-activate the drivers
remove, reinstall the drivers
remove any package I could find using synaptic (broadcom, bcmwl, b43) 

In dmesg, I see the following 2 lines:
wl: disagrees about version of symbol lib80211_get_crypto_ops
wl: Unknown symbol lib80211_get_crypto_ops (err -22)

I'm a noob, and completely lost. Can anyone help at all?

---

### Post by lostmuted on 2011-05-26
[minglis]("http://ubuntuforums.org/member.php?u=228418") ive been trying to work threw the same problem with two computers both running 11.04 different wireless cards.

i uninstalled compat-wireless and things went back to normal. try that out.

ive tried to use different ver. of compat-wireless and im not getting anywhere everytime it locks out my network-manager.

installing ubuntu 11.04 with this labtop i pop'd up with the ath5 drivers and i thought i was in the clear without even changing drivers or anything but then i get the fixed channel error.  >.< 

my desktop is another story, but in the same boat soon as i patch/install compat-wireless network manager no longer functions till i uninstall it.

when i first started trying to get this all working i thought i read somewhere that with current network manager compact wireless doesnt work....can anyone confirm?...... i think i might try and download a new network manager today just throwing out more info that ive been reading.

---

### Post by complience on 2011-06-10
attempted this 'fix' now my adapter is not detected at all

I think updating & patching compat deleted the module

LSUSB shows nothing 
LSMOD does not show the expected driver either

when I attach the usb the kernal logs show this

Jun 10 13:07:33 ubuntu-laptop kernel: [ 1305.242448] usb 2-1.2: new full speed USB device using ehci_hcd and address 10
Jun 10 13:07:33 ubuntu-laptop kernel: [ 1305.649573] usb 2-1.2: device not accepting address 10, error -32
Jun 10 13:07:33 ubuntu-laptop kernel: [ 1305.649753] hub 2-1:1.0: unable to enumerate USB device on port 2


please help me sort out this mess.. just having wifi would be great now never mind this negative one business

---

### Post by needlez6 on 2011-06-25
> **steveone said:**
> I get the following when I run the sudo make && make install command:

mkdir -p -- //usr/local/share/airoscript-ng/ //usr/local/share/doc/airoscript-ng/html/images //usr/local/etc //usr/local/share/man/man1 //usr/local/share/locale //usr/local/share/airoscript-ng//themes //usr/local/share/airoscript-ng//plugins //usr/local/share/airoscript-ng//airosperl //usr/local/share/doc/airoscript-ng/tools
Installing airoscript
Installing themes
Installing plugins
Installing documentation
     Installing standard documentation
     Installing html documentation
     Installing manpages
     Installing artwork
Installing locales
     Not installing locale es_ES (Not yet translated)

Installing airoscript
install: cannot remove `//usr/local/sbin//airoscript-ng': Permission denied
make: *** [install-binary] Error 1 

Any suggestions? Thank you in advance.

make && sudo make install... sorry not sudo make && make install... my bad... did that kinda in a rush, and didnt check til now...mate

---

### Post by needlez6 on 2011-06-25
BTW, just wondering if anyone has a permanent solution for this that doesnt require us to rebuild the package everytime a new kernel update is released. I'm currently using the SVN of aircrack-ng as my work around, but I find this not helpful as I would like to run gerix-wifi-cracker-ng... Any ideas of a script or something that can fix this issue 100% so that it get resolved for all kernels upstream like a PPA that checks and installs the newest patched wifi drivers?? just wondering if anyone has any ideas about how to do this, ill look into it myself, but don't have much free time here. Thank you

---

### Post by jensbodal on 2011-06-25
I might have mentioned this earlier but FYI my wireless card works fine in Backtrack.  I spent way too much time messing around with Ubuntu trying to get it to work, so whenever I need to use the aircrack tools I just boot into BT4.

---

### Post by needlez6 on 2011-06-28
[COLOR=Blue][SIZE=4]FIX BELOW. ------------v [SIZE=2]

[COLOR=Black]Below is a script I wrote which you need to run from the desktop with permissions. Follow the scripts instructions and it should install the latest svn version of aircrack-ng with a patch to override -1 issue. Thank you for all the work going on to permanetly fix this issue. [/COLOR]

[SIZE=4]MAKE SURE TO RUN THIS IN DESKTOP AS NORMAL USER! THANK YOU! [SIZE=1]

[COLOR=Black]anyone that needs help please get at me on AIM or Yahoo. Screenname : needlez6, or on IRC: channel #ubuntu nick: needlez, needlez1

thanks goes to zerochaos, and all other mods and helpers from the aircrack-ng channel.
[/COLOR][/SIZE][/SIZE][/SIZE][/SIZE][/COLOR]

---

### Post by Erik500002 on 2011-07-01
> **thatllmovethechains said:**
> Hey Erik500002,
When you said your AR5008 crashed everytime, was that during installation or afterwards?

Nah it would crash afterwards, but now I'm running natty and not such a nice experience with my AR5008 can't even connect to any network I fixed the -1 channel problem but still, seems to be like a kernel regression who knows, had to downgrade back to 10.10, much better ;)

---

### Post by oyejorge on 2011-07-02
> **needlez6 said:**
> 
Below is a script I wrote...

I Just tried it and I got this:
```
aircrack-ng: unrecognized option '--ignore-negative-one'
```

---

### Post by djpalmer88 on 2011-07-03
I've been trying to get aircrack-ng to work with my intel centrino advanced 6200 agn card but nothing seems to work. Has anyone got it working with this card running 11.04? cheers.

---

### Post by muyaad on 2011-07-23
Thank God,
i finally found a way out after trying a couple of weeks to make my usb adapter (TL-WN722N) work as it should.  now, fixed channel mon0 has been resolved, Chipset has been identified as Atheros from unknown  and Driver is ath9k from usb
here is what i did :-

wget [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2011-07-22.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2011-07-22.tar.bz2)
tar -jxf compat-wireless-2011-07-22.tar.bz2
cd compat-wireless-2011-07-22
wget [http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch](http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch)
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget [http://patches.aircrack-ng.org/channel-negative-one-maxim.patch](http://patches.aircrack-ng.org/channel-negative-one-maxim.patch)
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make wlunload
sudo make load ath9k_htc
sudo make modprobe ath9k_htc

---

### Post by rk_pr0t0c0l on 2011-08-01
> **muyaad said:**
> Thank God,
i finally found a way out after trying a couple of weeks to make my usb adapter (TL-WN722N) work as it should.  now, fixed channel mon0 has been resolved, Chipset has been identified as Atheros from unknown  and Driver is ath9k from usb
here is what i did :-

wget [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2011-07-22.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2011-07-22.tar.bz2)
tar -jxf compat-wireless-2011-07-22.tar.bz2
cd compat-wireless-2011-07-22
wget [http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch](http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch)
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget [http://patches.aircrack-ng.org/channel-negative-one-maxim.patch](http://patches.aircrack-ng.org/channel-negative-one-maxim.patch)
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make wlunload
sudo make load ath9k_htc
sudo make modprobe ath9k_htc

Thanks man, this works!!

---

### Post by onur.keser on 2011-08-02
how can i do it , with my Asus n53jq ?
Help me plz  ! :S

---

### Post by Muster Mark on 2011-08-11
Thanks so much!  Your patch worked perfectly on the Centrino Advanced-N 6200 too (it also uses the iwlagn driver, so I thought it might).

---

### Post by poke708 on 2011-08-24
This fix works just fine no more -1 
THANKS AGAIN

remember you have to have it on your desktop, and give permission "executable"

FIX BELOW. ------------v

Below is a script I wrote which you need to run from the desktop with permissions. Follow the scripts instructions and it should install the latest svn version of aircrack-ng with a patch to override -1 issue. Thank you for all the work going on to permanetly fix this issue.

MAKE SURE TO RUN THIS IN DESKTOP AS NORMAL USER! THANK YOU!

anyone that needs help please get at me on AIM or Yahoo. Screenname : needlez6, or on IRC: channel #ubuntu nick: needlez, needlez1

thanks goes to zerochaos, and all other mods and helpers from the aircrack-ng channel.
Attached Files
File Type: sh 	air.sh (675 Bytes, 179 views)

---

### Post by needlez6 on 2011-08-28
its sudo aireplay-ng --ignore-negative-one --fakeauth 0 -e "ESSID" -b BSSID -h STATION mon0
also sudo aireplay-ng --ignore-negative-one --arpreplay -b BSSID -h STATION mon0

sorry if that wasn't clear.

---

### Post by jago25_98 on 2011-08-30
gave up searching on the aircrack forum through thousands of posts with replies saying to search the forum for "-1"... but if you search all you find are the posts in the `I didn't search` forum!

So I was glad to find this. 

 Still, I had a make error:

```

  CC [M]  /home/j/src/wifi-fix/compat-wireless-2010-10-16/drivers/net/wireless/rt2x00/rt2x00pci.o
/home/j/src/wifi-fix/compat-wireless-2010-10-16/drivers/net/wireless/rt2x00/rt2x00pci.c: In function ‘rt2x00pci_resume’:
/home/j/src/wifi-fix/compat-wireless-2010-10-16/drivers/net/wireless/rt2x00/rt2x00pci.c:375:6: error: void value not ignored as it ought to be
make[4]: *** [/home/j/src/wifi-fix/compat-wireless-2010-10-16/drivers/net/wireless/rt2x00/rt2x00pci.o] Error 1
make[3]: *** [/home/j/src/wifi-fix/compat-wireless-2010-10-16/drivers/net/wireless/rt2x00] Error 2
make[2]: *** [/home/j/src/wifi-fix/compat-wireless-2010-10-16/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/j/src/wifi-fix/compat-wireless-2010-10-16] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-10-generic'
make: *** [modules] Error 2
j@laptop:~/src/wifi-fix/compat-wireless-2010-10-16$ 

```

Perhaps I could use Virtualbox? But that doesn't seem to allow raw enough access to the network device does it?

It's a shame. I'd prefer a Kernel 3.0 but I can't get virtualbox to work with 3.0+...

---

### Post by sarahfacecopter on 2011-09-26
> **needlez6 said:**
> [COLOR=Blue][SIZE=4]FIX BELOW. ------------v [SIZE=2]

[COLOR=Black]Below is a script I wrote which you need to run from the desktop with permissions. Follow the scripts instructions and it should install the latest svn version of aircrack-ng with a patch to override -1 issue. Thank you for all the work going on to permanetly fix this issue. [/COLOR]

[SIZE=4]MAKE SURE TO RUN THIS IN DESKTOP AS NORMAL USER! THANK YOU! [SIZE=1]

[COLOR=Black]anyone that needs help please get at me on AIM or Yahoo. Screenname : needlez6, or on IRC: channel #ubuntu nick: needlez, needlez1

thanks goes to zerochaos, and all other mods and helpers from the aircrack-ng channel.
[/COLOR][/SIZE][/SIZE][/SIZE][/SIZE][/COLOR]

Hi,

I ran this, everything installed fine, but now I can't use airmon-ng to put wlan0 in to monitor mode. Using Intel Centrino Advanced N 6205 AGN, so I would assume iwalgn driver.

Any ideas? :)

---

### Post by grafted_scion on 2011-09-29
Thank you this works perfectly with   --ignore-negative-one :D

> **needlez6 said:**
> [COLOR=Blue][SIZE=4]FIX BELOW. ------------v [SIZE=2]

[COLOR=Black]Below is a script I wrote which you need to run from the desktop with permissions. Follow the scripts instructions and it should install the latest svn version of aircrack-ng with a patch to override -1 issue. Thank you for all the work going on to permanetly fix this issue. [/COLOR]

[SIZE=4]MAKE SURE TO RUN THIS IN DESKTOP AS NORMAL USER! THANK YOU! [SIZE=1]

[COLOR=Black]anyone that needs help please get at me on AIM or Yahoo. Screenname : needlez6, or on IRC: channel #ubuntu nick: needlez, needlez1

thanks goes to zerochaos, and all other mods and helpers from the aircrack-ng channel.
[/COLOR][/SIZE][/SIZE][/SIZE][/SIZE][/COLOR]

---

### Post by truta9 on 2011-10-17
the script doest work for me. any sugestion?

the message  sucess appear but de aircrack doest installed.

any suggestion?

---

### Post by mym2f on 2011-10-22
Hi everyone ......

I have recently updated to Ubuntu 11.10 64-bit and my kernel is 3.0.0-12-generic ......

I can not change the channel for mon0 to anything but channel -1 .......

My ath9k_htc was working great with 2.6.39 kernel and compat-wireless-2011-08-27 after patching.

Which version of compat-wireless do I need to install ? and are the old patches works with that ?

Please tell me that I do not need to go back to an older version to make my wireless works !!!!

Thank you

---

### Post by Backtrackin on 2011-10-22
Hello everyone, 
I have a problem that appears similar to this, but is a little different.
What is happening is when I run airmon-ng -c 1 -w filename --bssid 00:11:22:33:44:55 instead of saying 'fixed channel mon0: -1' it is saying 'fixed channel mon0: number' and the number is rotating between five or six channels. It hits 3, 5, 6, 12, and maybe one other. After a minute of this, I get an error message saying 
'read failed: Network is down
ioctl(SI0CSIFFLAGS) failed: Unkown error 132
Can't reopen mon0'
I'm a newbie to linux so any insight at all would be greatly appreciated.

Thanks.

---

### Post by mafi127 on 2011-11-10
> **mym2f said:**
> Hi everyone ......

I have recently updated to Ubuntu 11.10 64-bit and my kernel is 3.0.0-12-generic ......

I can not change the channel for mon0 to anything but channel -1 .......

My ath9k_htc was working great with 2.6.39 kernel and compat-wireless-2011-08-27 after patching.

Which version of compat-wireless do I need to install ? and are the old patches works with that ?

Please tell me that I do not need to go back to an older version to make my wireless works !!!!

Thank you

same here I'm using ubuntu 11.10 and I cant use thows patches

---

### Post by Elfy on 2011-11-10
Not supported here.

Closed

---

