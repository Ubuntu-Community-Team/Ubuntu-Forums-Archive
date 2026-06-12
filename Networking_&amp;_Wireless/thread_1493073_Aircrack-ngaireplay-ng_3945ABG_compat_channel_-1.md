---
title: "Aircrack-ng/aireplay-ng 3945ABG compat channel -1"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by benthegreat on 2010-05-25
All of this is done to my own wireless network, before anyone starts whining.

After a fair bit of work finding the correct wireless drivers for 10.04 to let me use packet injection with an intel 3945abg chip I've encountered another problem. When trying to use aireplay-ng for anything other than the test (-9), it complains about the AP being on a different channel to my wireless interface (mon0, created from wlan0). It says my interface is on channel -1, which I presume is hypothetical channel, I've only heard of wireless channels above 0! and that the AP is on channel 1 (or any conventional channel). I've checked, and there isn't an option for setting a channel in aireplay, so this has me stumped.

```
sudo aireplay-ng -1 0 -a 00:18:4D:B8:31:24  mon0
No source MAC (-h) specified. Using the device MAC (00:13:02:99:9F:1B)
18:06:25  Waiting for beacon frame (BSSID: 00:18:4D:B8:31:24) on channel -1
18:06:26  mon0 is on channel -1, but the AP uses channel 11
```

Airodump-ng has no problem, when a channel isn't specified it hops between channels without a problem; and can be forced onto only one without hitch. However when I do force it onto only one channel it does tell me it's on channel -1 as well as my desired channel, although this does not appear to effect performance.

```
CH 11 ][ BAT: 1 hour 30 mins ][ Elapsed: 16 s ][ 2010-05-25 18:08 ][ fixed channel mon0: -1                
                                                                                                            
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID                         
                                                                                                            
 00:18:4D:B8:31:24  -78 100      184        0    0  11  54e. WEP  WEP         MyNetwork
```

So I'm asking, what is this strange, presumably hypothetical channel -1, what channel is my card actually in, and can I get aireplay-ng to work?

---

### Post by jenovanomusuko on 2010-05-26
I'm also only doing this on my own router.
Before anyone says "fix the channel with airodump-ng," please listen to what I have to say. 

I've been working on this for quite some time.  I too run the intel iwl3945 driver and have been having this same problem.  I've found a way to fix the channel: 

```
airodump-ng -c X,X
```where X is the channel number.  A comma and a repetition fixes it, so instead of getting something like this: 

> **benthegreat said:**
> 
```
CH 11 ][ BAT: 1 hour 30 mins ][ Elapsed: 16 s ][ 2010-05-25 18:08 ][ fixed channel mon0: -1           
```


You get something like this: 
```
CH  6 ][ Elapsed: 2 mins ][ 2010-05-26 20:01                                         
                                                                                                                                                            
 BSSID              PWR  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID
```I have tried killing all processes that show up with airmon-ng check, and still get the error: ```
mon0 is on channel -1, but the AP uses channel 6
```About a year ago I was able to use the iwl3945 driver just fine for packet injection.  Between then and now I hopped OS's a few times, thus losing whatever magic configuration I once had.  Anyone know what the deal is?

---

### Post by benthegreat on 2010-05-27
Thanks for the reply, it's nice to know someone else is in the same boat.

I have realised that the channel number is simply calculated form the frequency, so the -1 is either a low frequency, or a mistake somewhere. Not the hypothetical setting I was hoping for.

I'm in windows at the moment, but I'll try that airodump-ng syntax later, thank you.

I'm still confused as to how a card can be supposedly locked to a channel, yet connect fine, and channel hop in airodump-ng without a problem. Interesting...

---

### Post by jenovanomusuko on 2010-05-27
Dug up my old configuration.  I had compat-wireless from 2009-06-20 and aircrack-ng 1.0 rc3.  See what that does for you. 

Now that I'm posting a configuration that I know works, I would like to reiterate that the software should be used for your own legal SECURITY and EDUCATION purposes ONLY.  This software is NOT distributed for illegal purposes and should NOT be used for illegal purposes.

---

### Post by DomInat3 on 2010-07-05
Same problem here only I'm using an Atheros AR9285 (Rev:2) chip. Its not supported in the current kernel (even though it was said to be supported in >= 2.6.29 its not but it is in the development kernel - I can't remember which one) and I didn't want to upgrade to a development kernel for the ath9k drivers so I used bleeding edge compat-wireless. All works well only I suffer from the exact same problem. Mine gets stuck on either -1 (which isn't possible??) or very rarely channel 6. I have gone ahead and killed everything. Stopped NetworkManger and wpa_supplicant and still I run into the same problem.

> **jenovanomusuko said:**
> 
```
airodump-ng -c X,X
```where X is the channel number.  A comma and a repetition fixes it

I tried this. Airodump no longer tells me I am fixed to a channel which is good but then I tried to test:
> airodump-ng -c 8,8 mon0

It still picked up a network broadcasting on channel 6. Airodump doesn't show that it's scanning other channels though. It shows as if it were fixed and all were well. I then tried:

> airodump-ng -c 10,10 mon0

This didn't pick it up. The X,X thing might lack in accuracy when choosing a band of frequency's. I havn't tried to specify a bssid and channel yet though. I'll do that tonight and see if I can catch a handshake.

Thanks

---

### Post by sensay on 2010-07-06
I'm getting the same problem here too. Using a Zydas 1211 chipset with patched compat drivers. Using the comma trick as posted above simply changes the output to not display -1 but aireplay still gives the error.

I found this patch which is supposedly a fix for the problem (temporarily) but i cant seem to get it working.

[https://patchwork.kernel.org/patch/103589/](https://patchwork.kernel.org/patch/103589/)

It patches the chan.c file, i found this in my compat directory and placed the patch there (and in all possible subdirectorys) but it fails everytime. Id be very grateful if someone can explain exactly how to use this as it seems like just what i/we need.

---

### Post by DomInat3 on 2010-07-07
> **sensay said:**
> Using the comma trick as posted above simply changes the output to not display -1 but aireplay still gives the error.

Same :(

> **sensay said:**
> 
I found this patch which is supposedly a fix for the problem (temporarily) but i cant seem to get it working.

[https://patchwork.kernel.org/patch/103589/](https://patchwork.kernel.org/patch/103589/)

It patches the chan.c file, i found this in my compat directory and placed the patch there (and in all possible subdirectorys) but it fails everytime. Id be very grateful if someone can explain exactly how to use this as it seems like just what i/we need.

Ill give it ago sometime today when I'm on my netbook. Did you save the code on the page u linked above as somthing like chan.patch in your home directory and then run somthing like
> sudo patch -p0 < chan.patch
That should do the trick?

---

### Post by DomInat3 on 2010-07-07
Ok.... so far it seems as if I have it working. It functions better than before anyway. It does a couple of weird things every now and then but it is locking into a channel and I no longer receive the error. Heres what I did:

I had to edit a few lines of the patch that sensay linked too. I attached the new version below but here's the new contents anyway:

```

--- chan.c.orig
+++ chan.c
@@ -49,9 +49,12 @@ int cfg80211_set_freq(struct cfg80211_registered_device *rdev,
 {
 	struct ieee80211_channel *chan;
 	int result;
+	struct wireless_dev *mon_dev = NULL;
 
-	if (wdev && wdev->iftype == NL80211_IFTYPE_MONITOR)
+	if (wdev && wdev->iftype == NL80211_IFTYPE_MONITOR) {
+		mon_dev = wdev;
 		wdev = NULL;
+	}
 
 	if (wdev) {
 		ASSERT_WDEV_LOCK(wdev);
@@ -76,5 +79,8 @@ int cfg80211_set_freq(struct cfg80211_registered_device *rdev,
 	if (wdev)
 		wdev->channel = chan;
 
+	if (mon_dev)
+		mon_dev->channel = chan;
+
 	return 0;
 }

```

Save it and copy it into the same directory as the chan.c file. Mine was is ~/compat*/net/wireless but you can do a search with somthing like the below to find it. ```
sudo find / -name chan.c -print
```

Now open a terminal and navigate to the directory where chan.c and the patch are located. Run (I had to use sudo because the owner was root as i had already edited the file as root but don't if you haven't already been screwing around):
```
sudo patch -p0 -i < watevaucalledthepatch.patch
```

Now if you had to run the above command with root privileges (like me) then run the below to restore the file permissions. Replace userhere in the first line below with your user name:
```

sudo chown userhere:userhere chan.c
sudo chmod 777 chan.c

```

It should now be patched successfully with the right permissions. All you need to do now is recompile and unload the old drivers. Navigate into the base directory of compat wireless (mine was ~/compat*). I ran the below to select the ath9k drivers but you may have to do different depending on your chipset:
```
./scripts/driver-select ath9k
```

Now run the below to build:
```

make
sudo make install

```
And unload the old drivers:
```

sudo make unload
sudo make wlunload

```
You may or may not have to run the below, it won't hurt if you do
```

sudo make btunload

```

Now reboot or alternatively run:
```
sudo modprobe <drivergoeshere>
```
Everything should be in working order and the problem semi-fixed ;)

Hope this helps.

---

### Post by sensay on 2010-07-08
Hi. Tried your new version of the patch, unfortunately when i now run it i simply get a hang in the terminal... Ive left it for half hour and nothing happens..

This is frustrating, im glad its working for you though..

I thought perhaps my compat may be borked (ive messed around with it a bit) so im gonna download a new version and try patching and compiling with that... Any tips though would be appreciated.

EDIT:                               sudo patch -p0 < watevaucalledthepatch.patch is incorrect.                               sudo patch -p0 -i < watevaucalledthepatch.patchis the correct string. I am patched now, just about to recompile and test..

EDIT2: Working! Thanks a lot mate. Little FYI, you can skip rebooting by using sudo modprobe <drivergoeshere> after you have unloaded the wireless and bluetooth, For me it was sudo modprobe zd1211rw but will be dependant on your driver name obviously

---

### Post by DomInat3 on 2010-07-08
> **sensay said:**
> 
EDIT: sudo patch -p0 < watevaucalledthepatch.patch is incorrect.                               sudo patch -p0 -i < watevaucalledthepatch.patchis the correct string. I am patched now, just about to recompile and test..

EDIT2: Working! Thanks a lot mate. Little FYI, you can skip rebooting by using sudo modprobe <drivergoeshere> after you have unloaded the wireless and bluetooth, For me it was sudo modprobe zd1211rw but will be dependant on your driver name obviously

Fixed :D no worries buddy. Glad to help.

---

### Post by sensay on 2010-07-08
Noticed a bug still..

Connecting to an AP on channel 8 and my monitor interface fixes to channel 10 and i get the same initial error only telling me its on channel 10 not -1 obviously. It works fine on the more common AP channels (11,6). I will fiddle with my router later and try other non standard AP channels to see if the error happens on channels aside from 8..

---

### Post by 98cwitr on 2010-08-05
im in the same boat...no matter what I seem to do, still says mon0 or mon1 is on channel -1. I haven't tried the patch yet though.

edit: chan.c was not found on my system :?

---

### Post by DomInat3 on 2010-08-06
> **98cwitr said:**
> im in the same boat...no matter what I seem to do, still says mon0 or mon1 is on channel -1. I haven't tried the patch yet though.

edit: chan.c was not found on my system :?

The patch works successfully for me although sometimes I have to reboot to get out of a channel I'm fixed into.

The chan.c file should be included in the bleeding edge drivers. I extracted to my home directory so it was in ~/compat*/net/wireless for me. Provided you have extracted the driver archive u can search for it by using:
```
sudo find / -name chan.c -print
```

If you still can't find it, try downloading the archive again and starting from scratch. If you are still without luck, I will upload the archive I have on my computer for you. Good Luck :D

---

### Post by 98cwitr on 2010-08-10
still cant find it...you mind posting it?

---

### Post by akn320 on 2010-08-16
I'm having the same problem as the OP.
I'm also a total linux n00b btw.
I think my problem is that wpa_supplicant and network manager don't shut down, or start back up immediately after being killed:

admin@ubuntu:~$ sudo airmon-ng check kill
Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID    Name
23958    NetworkManager
24218    avahi-daemon
24219    avahi-daemon
24242    wpa_supplicant
Killing all those processes...
admin@ubuntu:~$ sudo airmon-ng check


Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID    Name
24468    avahi-daemon
24469    avahi-daemon
24478    NetworkManager
24483    wpa_supplicant

I know injection works on my card:
admin@ubuntu:~$ sudo aireplay-ng -9 mon0
12:07:55  Trying broadcast probe requests...
12:07:55  Injection is working!
12:07:56  Found 3 APs

but when I try the patch recommended in this thread I get:
admin@ubuntu:~/Downloads/compat-wireless-2.6.35-1/net/wireless$ sudo patch -p0 -i < chan.patch
patch: option requires an argument -- 'i'
patch: Try `patch --help' for more information.
admin@ubuntu:~/Downloads/compat-wireless-2.6.35-1/net/wireless$ sudo patch -p0 -i chan.patch  < chan.patch
patching file b/net/wireless/chan.c
Hunk #1 FAILED at 49.
Hunk #2 FAILED at 76.
2 out of 2 hunks FAILED -- saving rejects to file b/net/wireless/chan.c.rej

I think I'm doing something wrong, perhaps my syntax or something.
thanks in advance.

---

### Post by DomInat3 on 2010-08-17
> **98cwitr said:**
> still cant find it...you mind posting it?
The below archive has the file. It's the build I'm using.... Worth a try i guess.

[DOWNLOAD HERE]("http://www.ezikialsoftware.com/files/comp/compat-wireless-2.6.tar.bz2")

> **akn320 said:**
> I'm having the same problem as the OP.
I'm also a total linux n00b btw.
I think my problem is that wpa_supplicant and network manager don't shut down, or start back up immediately after being killed:


Hahaha don't worry I'm n00b too.... I'm pretty sure wpa_supplicant is running in the background as root... off the top off my head, I'm not exactly sure how to kill it but none of those processes have effected me so long as i disable networking.

> **akn320 said:**
> 

but when I try the patch recommended in this thread I get:
admin@ubuntu:~/Downloads/compat-wireless-2.6.35-1/net/wireless$ sudo patch -p0 -i < chan.patch
patch: option requires an argument -- 'i'
patch: Try `patch --help' for more information.
admin@ubuntu:~/Downloads/compat-wireless-2.6.35-1/net/wireless$ sudo patch -p0 -i chan.patch  < chan.patch
patching file b/net/wireless/chan.c
Hunk #1 FAILED at 49.
Hunk #2 FAILED at 76.
2 out of 2 hunks FAILED -- saving rejects to file b/net/wireless/chan.c.rej

I think I'm doing something wrong, perhaps my syntax or something.
thanks in advance.

Are you using the patch downloaded from this post? It's attached at bottom of the post....

[http://ubuntuforums.org/showpost.php?p=9558176&postcount=8]("http://ubuntuforums.org/showpost.php?p=9558176&postcount=8")

The patch you are using seems to be the original patch and not the one that I edited. It is looking for the chan.c file in /b/net/wireless... I think this patch was originally developed for bt3 or 4. Try using the patch from that post... it should work if u follow the directions otherwise I may have made a stuff up.

---

### Post by 98cwitr on 2010-08-18
cant use the patch if I dont have the archive right...per the instructions that's a step? Or it that the whole file?

---

### Post by Trinity33 on 2010-08-18
> **benthegreat said:**
> All of this is done to my own wireless network, before anyone starts whining.

After a fair bit of work finding the correct wireless drivers for 10.04 to let me use packet injection with an intel 3945abg chip I've encountered another problem. When trying to use aireplay-ng for anything other than the test (-9), it complains about the AP being on a different channel to my wireless interface (mon0, created from wlan0). It says my interface is on channel -1, which I presume is hypothetical channel, I've only heard of wireless channels above 0! and that the AP is on channel 1 (or any conventional channel). I've checked, and there isn't an option for setting a channel in aireplay, so this has me stumped.

```
sudo aireplay-ng -1 0 -a 00:18:4D:B8:31:24  mon0
No source MAC (-h) specified. Using the device MAC (00:13:02:99:9F:1B)
18:06:25  Waiting for beacon frame (BSSID: 00:18:4D:B8:31:24) on channel -1
18:06:26  mon0 is on channel -1, but the AP uses channel 11
```Airodump-ng has no problem, when a channel isn't specified it hops between channels without a problem; and can be forced onto only one without hitch. However when I do force it onto only one channel it does tell me it's on channel -1 as well as my desired channel, although this does not appear to effect performance.

```
CH 11 ][ BAT: 1 hour 30 mins ][ Elapsed: 16 s ][ 2010-05-25 18:08 ][ fixed channel mon0: -1                
                                                                                                            
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID                         
                                                                                                            
 00:18:4D:B8:31:24  -78 100      184        0    0  11  54e. WEP  WEP         MyNetwork
```So I'm asking, what is this strange, presumably hypothetical channel -1, what channel is my card actually in, and can I get aireplay-ng to work?


WLAN0 AND MON0 BLOCKED ON CHANNEL ONE ?? AND THERE IS NO SOLUTION ? 

WOOW THERE IS IF YOURE USING COMPAT WIRELESS I HAVE BAD INFO FOR YA ALMOST ALL COMPAT WIRELESS FROM 2010 ARE BROKEN THEY DONT WORK PROPERLY WITH DEVICES. 

NOW IF YOU GOT ZD1211 OR ANY OTHER DEVICE THAT IS USING COMPAT U NEED TO GET COMPAT WIRELESS FROM [compat-wireless-2010-02-22.tar.bz2]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-02-22.tar.bz2")2010-Feb-22 21:05:362.2M

THE LINK [http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/) JUST VERSION FROM 22/JAN/2010 DOESNT BLOCK WLAN NOR MON0 ON CHANNEL 1 

AFTER U DOWNLOADED IT UNTAR AND IF YOU HAVE ZD1211 CHIP U NEED TO GET PATCHES AND THE  RIGHT PATCHES ARE THOSE ONE 

[http://www.zlaten.biz/tmp/zd1211rw-inject+dbi-fix-2.6.26.patch](http://www.zlaten.biz/tmp/zd1211rw-inject+dbi-fix-2.6.26.patch)

AND

[http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch](http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch)

U GOT EVERYTHING ONE PATCH FOR MAC ONE FOR ZD1211 OTHER PATCHES WORK BADLY.

COPY YOU PATCHES TO COMPAT DIRECTORY
CD COMPAT AND [B]patch -Np0 -i zd1211rw-inject+dbi-fix-2.6.26.patch
than 
[/B][B]patch -Np1 -i mac80211.compat08082009.wl_frag+ack_v1.patch

patching is done 

next easy make 

after finished sudo make install

dont leave compat directory type sudo make wlunload 

than modprobe zd1211rw or just disconnect and connect again your zd1211

thats all try if injection is working by typing airmon-ng to see what device you have 

probably it will be name wlan0

so airmon-ng start wlan0

u'll see mon0 and if there are any processes running kill it esp wpa suplicant 

than aireplay-ng -9 mon0 

u should see info injection is working

type iwconfig mon0 rate 1m  

than airodump-ng mon0 

pick your AP mac xxxxx 

airodump-ng -w wep -c a --bssid xxxx mon0

a- mean AP channel
bssid mac address of your  AP

and u'll see your mon0 isnt blocked anymore on channel one like with other compat wireless.

than in a new window aireplay-ng -1 0 -a xxxx mon0

a- mac of the AP 

when u see youre associated 

type aireplay-ng -2 -p 0841 -c ff:ff:ff:ff:ff:ff -b xxx mon0

b- mac adress of the AP
c- fake mac just type as i typed

then in few sec you should see info asking you YES or NOT say yes

and u will see on the first window there where you typed airodump-ng -w wep -c x --bssid xxxxx mon0 that data is speeding 

wait till when you see 10000 dont stop anything after that open new window and type aircrack-ng -b xxxx cap

-b max adress of the AP

and cap is the file in your home directory so it will be aircrack-ng -b xxxx /home/replay.cap 

aircrack will start and in few min you should get your key thats all



and remember what i said all compats from 2010 are broken just version from 22/feb/2010 is working and ver from december 2009 is working !!!!!!!!

and to people who has other chipset and your your card is supported by compat you have to download the same ver of compat mean 22/feb/2010 other wont work also u need the right patch from aircrack for your card to get injection working most of patches u'll find over here [http://patches.aircrack-ng.org/](http://patches.aircrack-ng.org/)
[/B]

---

### Post by DomInat3 on 2010-08-18
> **Trinity33 said:**
> WLAN0 AND MON0 BLOCKED ON CHANNEL ONE ?? AND THERE IS NO SOLUTION ? 

WOOW THERE IS IF YOURE USING COMPAT WIRELESS I HAVE BAD INFO FOR YA ALMOST ALL COMPAT WIRELESS FROM 2010 ARE BROKEN THEY DONT WORK PROPERLY WITH DEVICES. 

JUST VERSION FROM 22/JAN/2010 DOESNT BLOCK WLAN NOR MON0 ON CHANNEL 1 

AFTER U DOWNLOADED IT UNTAR AND IF YOU HAVE ZD1211 CHIP U NEED TO GET PATCHES AND THE  RIGHT PATCHES ARE THOSE ONE 

[http://www.zlaten.biz/tmp/zd1211rw-inject+dbi-fix-2.6.26.patch](http://www.zlaten.biz/tmp/zd1211rw-inject+dbi-fix-2.6.26.patch)

AND

[http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch](http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch)

U GOT EVERYTHING ONE PATCH FOR MAC ONE FOR ZD1211 OTHER PATCHES WORK BADLY.


Ok,

1.) Format you're post... No one wants to read a post in capitals and boldface.... its rude and annoying  ](*,)

2.) Im using a june 2010 build with an Atheros AR9285 chip, yet mine works fine using the patch I posted.... Below is the output from the injection test. You may want to fix that sentence.

```
benny@benny-laptop:~$ sudo aireplay-ng -9 mon0
12:38:39  Trying broadcast probe requests...
12:38:39  Injection is working!
12:38:41  Found 1 AP 

12:38:41  Trying directed probe requests...
12:38:41  xx:xx:xx:xx:xx:xx - channel: 6 - 'home'
12:38:42  Ping (min/avg/max): 1.065ms/13.037ms/37.663ms Power: -74.23
12:38:42  30/30: 100%

```

3.) The OP, nor any of us for that matter, asked how to use aircrack-ng.... so why have u given us a run through? hahaha :confused:

Thanks for the info anyway, it may help some people.

---

### Post by Pabx on 2010-10-22
> **DomInat3 said:**
> Ok.... so far it seems as if I have it working. It functions better than before anyway. It does a couple of weird things every now and then but it is locking into a channel and I no longer receive the error. Heres what I did:

I had to edit a few lines of the patch that sensay linked too. I attached the new version below but here's the new contents anyway:

```

--- chan.c.orig
+++ chan.c
@@ -49,9 +49,12 @@ int cfg80211_set_freq(struct cfg80211_registered_device *rdev,
 {
 	struct ieee80211_channel *chan;
 	int result;
+	struct wireless_dev *mon_dev = NULL;
 
-	if (wdev && wdev->iftype == NL80211_IFTYPE_MONITOR)
+	if (wdev && wdev->iftype == NL80211_IFTYPE_MONITOR) {
+		mon_dev = wdev;
 		wdev = NULL;
+	}
 
 	if (wdev) {
 		ASSERT_WDEV_LOCK(wdev);
@@ -76,5 +79,8 @@ int cfg80211_set_freq(struct cfg80211_registered_device *rdev,
 	if (wdev)
 		wdev->channel = chan;
 
+	if (mon_dev)
+		mon_dev->channel = chan;
+
 	return 0;
 }

```

Save it and copy it into the same directory as the chan.c file. Mine was is ~/compat*/net/wireless but you can do a search with somthing like the below to find it. ```
sudo find / -name chan.c -print
```

Now open a terminal and navigate to the directory where chan.c and the patch are located. Run (I had to use sudo because the owner was root as i had already edited the file as root but don't if you haven't already been screwing around):
```
sudo patch -p0 -i < watevaucalledthepatch.patch
```

Now if you had to run the above command with root privileges (like me) then run the below to restore the file permissions. Replace userhere in the first line below with your user name:
```

sudo chown userhere:userhere chan.c
sudo chmod 777 chan.c

```

It should now be patched successfully with the right permissions. All you need to do now is recompile and unload the old drivers. Navigate into the base directory of compat wireless (mine was ~/compat*). I ran the below to select the ath9k drivers but you may have to do different depending on your chipset:
```
./scripts/driver-select ath9k
```

Now run the below to build:
```

make
sudo make install

```
And unload the old drivers:
```

sudo make unload
sudo make wlunload

```
You may or may not have to run the below, it won't hurt if you do
```

sudo make btunload

```

Now reboot or alternatively run:
```
sudo modprobe <drivergoeshere>
```
Everything should be in working order and the problem semi-fixed ;)

Hope this helps.

I cant find the chan.c file. . .

---

### Post by DomInat3 on 2010-10-23
> **Pabx said:**
> I cant find the chan.c file. . .

Try reading up a bit.... Download the file in post 16. It might help. I've linked the post for you.

[http://ubuntuforums.org/showpost.php?p=9729494&postcount=16]("http://ubuntuforums.org/showpost.php?p=9729494&postcount=16")

Can a mod please edit the OP with the link to this file and the patch...

---

### Post by SriNarayanan on 2010-10-23
[http://ubuntuforums.org/showthread.php?t=1598930](http://ubuntuforums.org/showthread.php?t=1598930)

Check this ,there is a solution , Let me know if it works

---

### Post by Pabx on 2010-10-23
> **SriNarayanan said:**
> [http://ubuntuforums.org/showthread.php?t=1598930](http://ubuntuforums.org/showthread.php?t=1598930)

Check this ,there is a solution , Let me know if it works

This one Works great!!

the one DomInat3  posted is buggy. But thanks anyway.

---

### Post by SriNarayanan on 2010-10-24
> **Pabx said:**
> This one Works great!!

the one DomInat3  posted is buggy. But thanks anyway.
Glad ,that it works .

---

### Post by DomInat3 on 2010-10-24
> **Pabx said:**
> This one Works great!!

the one DomInat3  posted is buggy. But thanks anyway.

Good to know you got it working. I wouldn't call this buggy however :confused: I have used this patch on multiple systems and it has works 100% /w injection on my atheros chipset. It may be a bit harder and require a bit more reading and learning (which isnt a bad thing) then SriNarayanan's method but it is definitely not buggy and I cant see how it wouldnt work so long as you are using the correct drivers and have the correct chipset.

:popcorn:

---

### Post by kad78 on 2010-12-07
This may not be a long term solution, but the command ```
iwconfig
```can also change a wireless card's channel. E.g.:

```
iwconfig wlan0 channel 11
```This switches the wlan0 interface to channel 11. It may work for mon0 too. It seems more elegant than patching drivers/code etc.

---

