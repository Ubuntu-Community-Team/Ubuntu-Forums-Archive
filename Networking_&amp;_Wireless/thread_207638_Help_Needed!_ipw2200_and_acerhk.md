---
title: "Help Needed! ipw2200 and acerhk"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by AlexBryan on 2006-07-02
I'm trying to get my Acer Aspire 3023 WLMi WLAN working. It has an Intel 2200BG wireless card and I'm following this guide under build in wireless card: [http://folk.uio.no/krisvh/linux/cl56.html#wireless](http://folk.uio.no/krisvh/linux/cl56.html#wireless)
I've done this much

$ sudo apt-get install linux-headers-`uname -a|awk '{ print $3 }'` build-essential 
$ wget [http://heanet.dl.sourceforge.net/sourceforge/ipw2200/ipw2200-1.0.3.tgz](http://heanet.dl.sourceforge.net/sourceforge/ipw2200/ipw2200-1.0.3.tgz) 
$ tar xvzf ipw2200-1.0.3.tgz $ 
cd ipw2200-1.0.3

But typing make brings up this error:
 ERROR: ieee80211.h not found in '/lib/modules/2.6.15-25-386/include'.

You need to install the ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net)
and point this build to the location where you installed those sources, eg.:

% make IEEE80211_INC=/usr/src/ieee80211/

will look for ieee80211.h in /usr/src/ieee80211/net/

make: *** [check_inc] Error 1

Also with the next part, the acerhk, I followed the guide exactly and it dosn't work, I received no errors. All I can think of is that 'sudo modprobe acerhk' just returned me to the promp without giving any info.

Any ideas whats going wrong?

---

### Post by wofritz on 2006-07-03
Hi,
you don't have to compile the ipw2200 module from source. It's already included in the Kernel:

find /lib/modules/`uname -r` -name "ipw2200.*"
/lib/modules/2.6.15-25-386/kernel/drivers/net/wireless/ipw2200.ko


If you didn't get error messages for acerhk during
make
sudo make install
all should be fine.
sudo modprobe acerhk
gives console output only if something went wrong ;-)

You should see the acerhk module with
lsmod
(with loads of other modules)
The output of  the acerhk module goes to /var/log/messages
If you open a shell window and type
tail -f /var/log/messages
and
sudo modprobe acerhh
in an other shell window, you'll see the output of acerhk (if it is not already loaded, of course).

Regards,
Wolfgang
(typing this on an Acer Travelmate 292LMi running Dapper with ipw2200 and acerhk)

---

