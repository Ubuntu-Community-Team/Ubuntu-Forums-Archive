---
title: "Making injection work in intel 4965 with Intrepid"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by ztrange on 2008-12-11
UPDATE: There is this tutorial in the aircrack-ng site that tells everything you need. Im almost sure that you can skip the kernel preparing part:

[http://www.aircrack-ng.org/doku.php?id=iwlagn]("http://www.aircrack-ng.org/doku.php?id=iwlagn")


UPDATE: The info has been gathered form several sites but the above one is the best one.

I (originally) translated this from [here]("http://weblogs.inf.udp.cl/nboettcher/07/11/2008/inyectar-paquetes-con-intel-pro-wireless-4965-abgn-mac80211-en-ubuntu-intrepid-ibex-810/"). Im just trying to put it here so averybody can use it. There is [this]("http://ubuntuforums.org/showthread.php?t=493095&highlight=driver+update+4965") other guide but due to recent changes in the iwlwifi driver, it no loger works.

We need to download the firmware and the compat-wireless driver from:

[http://intellinuxwireless.org/?n=downloads]("http://intellinuxwireless.org/?n=downloads")
and
[http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers]("http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers")

or with wget:

```
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-228.57.2.23.tgz
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
```

then, copy the firmware to your /lib/firmware:
```
tar zxvf iwlwifi-4965-ucode-228.57.2.21.tgz
cd iwlwifi-4965-ucode-228.57.2.21
sudo cp * /lib/firmware/
```

extract the compat-wireless driver:
```
tar xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless-*
```

Inside, download the patchet and apply them:
```
wget http://patches.aircrack-ng.org/mac80211_2.6.27_frag+ack_v2.patch
patch -p1 < mac80211_2.6.27_frag+ack_v2.patch
wget http://pastebin.com/pastebin.php?dl=f7bc96631 -O iwl4965-injection.patch
patch -p1 < iwl4965-injection.patch
```

Finally, compile.
```
make
sudo make install
sudo make unload
sudo make load
```

If you had trouble with make unload and make load, you have to reboot your pc in order to load the necessary modules.

Now you have to enable your card monitor mode:

```

sudo airmon-ng start wlan0
```

And finally, we just need to test the interface (from now on we will use mon0 due to the way the mac80211 module is built) to start injecting packages

```
sudo aireplay-ng mon0 -9
```

You should get something like this, note that it says that injection is working:
[IMG]http://weblogs.inf.udp.cl/nboettcher/files/2008/11/aireplay.png[/IMG]

UPDATE: Note that the patch doesn't still support fakeauth so, you have to use the wpa_supplicant method. Thanks to Sebix

Hope this helps some of you and any suggestion will be appreciated

---

### Post by Jamezracer on 2008-12-15
thank you so much for this! i was ripping my hair out trying to get the old patches for the 2.6.26 kernel to work. you are my hero lol.

---

### Post by Sebix on 2009-01-09
Hi "ztrange"... I have come to the same point as you did. I ve compiled the drivers in ubuntu intrepid..and also got the injection test working (sudo aireplay-ng -9 mon0). 

The problem in my case is althought the injection test is working..I cannot manage to inject traffic in any AP. As you maybe know its not possible to assosiate with the AP via the aireplay-ng tool... there is a workaround using the wpa_supplicant. I ve used this but still... I do not get any injected packages.

Did you tried this??.. any suggestion would be really helpfull .. I m starting to loose my mind with this card.

Thankx
Sebix

---

### Post by Sebix on 2009-01-15
Auto-Answer (maybe it will be usefull for somebody). The injection works perfect but the order of execution is important. First you should autheticate via the wpa_supplicant method, then airmon-ng to start mon0, then airodump-ng directed to the desired network and finally the aireplay -3 for the injection itself. If you change that order the wpa_supplicant lock the aircrack-ng pack for any reason I cannot explain (bug maybe). Hope its usefull for someone.

Sebix

---

### Post by ztrange on 2009-01-24
Hello, everyone,

UPDATE: Sebix is right, fake association is still not working, see the link i put in the top of the first post. As for injection, I have done it but with existing client, I will have to try the wpa_supplicant (in the link there are 3 links that tell you how to do it). For now,i use my linksys to do the cracking thing. However I still want the agn4965 to work because my linksys only supports g networks.

As I said before, Im no guru of this matter and I only translated the guide I found in the internet.

Unfortunately my agn4965 is not working fine now and I'm not sure what happened, so for now I'm using a Lynksys WUSB54G (not GC) and injection works out of the box.

But now, today, my agn4965 started working again (it logged into my wlan before i plugged in my linksys, so I'm using it.

And yesterday I found some fresh instructions in a blog that says that you should patch the compat wireless driver:

Download and extract driver:
```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless-*
```

Inside, download and patch (and another patch...):
```
wget http://patches.aircrack-ng.org/mac80211_2.6.27_frag+ack_v2.patch
patch -p1 < mac80211_2.6.27_frag+ack_v2.patch
wget http://pastebin.com/pastebin.php?dl=f7bc96631 -O iwl4965-injection.patch
patch -p1 < iwl4965-injection.patch
```

Finally, compile.
```
make
make install
sudo make unload
sudo make load
```

Also, Im updating the first post to make it up-to date.

---

### Post by skit on 2009-01-24
Hi the patch part isn't quite working. What file should the patch be applied to ?

Btw, i don't have wireless using the default driver provided by ubuntu intrepid on a fresh install. Would this solve it ?

---

### Post by Gun_Smoke on 2009-01-24
First patch seems to fail. 


```
$ patch -p1 < mac80211_2.6.27_frag+ack_v2.patch
patching file net/mac80211/tx.c
Hunk #1 FAILED at 630.
1 out of 1 hunk FAILED -- saving rejects to file net/mac80211/tx.c.rej

```

---

### Post by tylerdurd on 2009-01-25
> **Gun_Smoke said:**
> First patch seems to fail. 


```
$ patch -p1 < mac80211_2.6.27_frag+ack_v2.patch
patching file net/mac80211/tx.c
Hunk #1 FAILED at 630.
1 out of 1 hunk FAILED -- saving rejects to file net/mac80211/tx.c.rej

```

Hi all !

Same mistake ... :(

---

### Post by nhasian on 2009-01-26
Hunk #1 FAILED

same here, looking for solution

---

### Post by Gun_Smoke on 2009-01-26
Forget about all the above instructions.  

```
tar -jxf compat-wireless-2.6.tar.bz2
cd compat-wireless-2009-01-08/
make
make install
```

[http://rhosted.blogspot.com/2009/01/making-packet-injection-work-on-ubuntu.html](http://rhosted.blogspot.com/2009/01/making-packet-injection-work-on-ubuntu.html)

---

### Post by ztrange on 2009-01-26
yes, it fails, but that is the right way... (we'll have to wait for it to be fixed) as I posted earlier, this place has the best info for agn4965 with aircrack.

[http://www.aircrack-ng.org/doku.php?id=iwlagn]("http://www.aircrack-ng.org/doku.php?id=iwlagn")

By the way, the driver without patching is supposed to work fine but is not the best result possible this far with the 4965 card.

---

### Post by macabro22 on 2009-03-21
> **ztrange said:**
> yes, it fails, but that is the right way... 
By the way, the driver without patching is supposed to work fine but is not the best result possible this far with the 4965 card.

So you are saying that packet injection works but does not increase packet transmission* and that is the "right way"?

I´m baffled. What do you mean?


===============
*(thus fails)

---

### Post by ztrange on 2009-03-24
The driver shipped with Ubuntu, can do injection since some time ago. But, the latest release from the intel wireless webpage with some patches mentioned in the aircrack web, make the best configuration possible this far for the 4965.

The instructions for the 4965 in the aircrack page are outdated a long ago. Anyway, I haven't tried to find new instructions because I got a new adapted that can inject without problem.

As for the "it fails..."

Im sorry, the instructions in the aircrack page havent been updated and the patches didn't worked the last time I tried them. However, I'm saying that the instructions in that page are the best ones I've found in the net but right now they fail to do the patching.

---

### Post by Gun_Smoke on 2009-03-24
2.6.28 should work out of the box

---

### Post by superkato on 2009-03-25
I patched the 8.10 Kernel with an injection patch for AGN Cards!

Downloads for 64bit and 32bit:

[http://www.superkato.net/2009/03/23/intel-injection-kernel-patch-download/](http://www.superkato.net/2009/03/23/intel-injection-kernel-patch-download/)

---

### Post by eekfonky on 2009-03-30
I cannot copy the firmware to lib/firmware. I don't have permission. How do i do it from  a rterminal?

---

### Post by superkato on 2009-04-11
type in sudo <command> 

or 

sudo nautilus to open the root file browser

---

### Post by eekfonky on 2009-04-11
Thank you

---

