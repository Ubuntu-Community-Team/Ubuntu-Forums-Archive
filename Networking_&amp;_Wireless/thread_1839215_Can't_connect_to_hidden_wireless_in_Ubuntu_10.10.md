---
title: "Can't connect to hidden wireless in Ubuntu 10.10"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by veroslav on 2011-09-05
Hi,

I am using Ubuntu 10.10 and I am experiencing some issues while trying to connect to my hidden wireless network.
While the wireless connection was NOT hidden, the Ubuntu was connecting to it without any issues. Just as an
experiment, and in order to slightly improve the wireless security, I changed the set-up to a hidden one and also
changed the SSID to something else.

Then I tried connecting to the hidden network by choosing "Connect to the hidden network.."
from the network manager, and entering the new connection details and tried to connect. The connection icon was
spinning round and round and finally it threw an error and said it could not connect.

I then tried disabling/enabling wireless, restarting the computer, creating a new connection, searching for similar
threads on this forum, but could not find the root cause for not being able to connect. It seems to be a common
issue though, with no solution.

The interesting thing is that Kubuntu 11.04, that I am running on the other partition, picks up the same hidden wireless
network straight away without any issues.

I am using WPA Personal for my wireless connection.

What could be the issue and why does it work in Kubuntu 11.04 but not in Ubuntu 10.10?

P.S. I know that my hidden wireless can be detected even though it is hidden, but I did this because I am curious and wanted
to find out how it would work, which it does not.

Thank you in advance.

Kind regards,
Veroslav

---

### Post by veroslav on 2011-09-06
Bump

---

### Post by wildmanne39 on 2011-09-06
Hi, here is a link for connecting to hidden networks but these is really no added security having a hidden network.
[https://help.ubuntu.com/11.04/ubuntu-help/net-wireless-hidden.html](https://help.ubuntu.com/11.04/ubuntu-help/net-wireless-hidden.html)
Thank you

---

### Post by veroslav on 2011-09-07
Thank you for your reply. I looked at the pointed document before I started configuring the wireless, however, I did it just as described there but to no effect. It just does not work, which is disappointing because it works in Kubuntu 11.04.

I've now reverted back to a non-hidden wireless network unfortunately.

Thanks again.

Kind Regards,
Veroslav

---

### Post by wildmanne39 on 2011-09-07
Hi, I am sorry to hear that, there are a lot of issues connecting to a hidden network for some reason, I am glad you can connect to unhidden though instead of not at all.
Thank you

---

### Post by veroslav on 2011-09-09
No problem, I appreciate your help however :)

Kind Regards,
Veroslav

---

### Post by haqking on 2011-09-09
I have 10.10 and 2 wireless networks which are both hidden.

Mine works fine.

I preserve the router MAC within the connection if that helps ?

i use WPA also and never had any issue.  I login if disconnected takes aboutr 30 seconds to connect, if i dont want to wait i choose connect to hidden and it connects straight away.

maybe adapter - router device related  often are incompatabilities.

I use intel inbuilt and netgear router though.

all good in the hood here ;-)

---

### Post by nowifi on 2012-02-04
same problem again: 
[http://ubuntuforums.org/showthread.php?t=1919987](http://ubuntuforums.org/showthread.php?t=1919987)

can anyone explain why connections to hidden SSID routers fail with some hardware? and even better provide information to provide a fix?

This is NOT a fix, because it is manually labour intensive (which is anathema to the whole concept of computing and automation), but Ubuntu can be coerced to make Network Manager connect my Ralink wireless hardware to a router that does not broadcast it's SSID by executing in a terminal window the following:

 (replacing [COLOR=Blue]**<...>**[/COLOR] appropriately):

     ```

  [COLOR=Blue]**sudo iwconfig wlan0 essid <Router's non-broadcast SSID> key s:<ASCII passcode string>**[/COLOR]     
```

(It also helps to Dis/En-able Wireless in Network Manager to register the connection protocol.)

---

