---
title: "Wifi Deauthenticated - Intel PRO/Wireless 4965 - Ubuntu 13.04 - HP Compaq 2510p"
date: 2013-08-21
forum: Networking &amp; Wireless
---

### Post by midhunjackson on 2013-08-21
Hi,

Since I installed ubuntu on my compaq 2510p laptop wifi is not working. I've put the outputs of the commands I ran on pastebin [http://pastebin.com/J0xzwnwx](http://pastebin.com/J0xzwnwx).

Could you please tell me what is wrong and how I can fix this.

Thanks in advance.

---

### Post by chili555 on 2013-08-22
I suggest these steps. First, right-click the Network Manager icon and edit wireless, IPv6 to ignore IPv6 settings, like this: [https://access.redhat.com/site/documentation/resources/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](https://access.redhat.com/site/documentation/resources/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png) Save and close.

Second, try this:```
sudo -i
echo "options iwl4965 11n_disable=1" > /etc/modprobe.d/iwl4965.conf
echo "options mac80211 probe_wait_ms=5000" > /etc/modprobe.d/mac80211.conf
exit
```Reboot and let us have your report.

---

### Post by midhunjackson on 2013-08-28
Thanks a ton chili555!!
Working perfectly now. Sorry for the late reply :)

---

### Post by chili555 on 2013-08-29
> **midhunjackson said:**
> Thanks a ton chili555!!
Working perfectly now. Sorry for the late reply :)No worries! Glad it's working.

Please mark the thread Solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

