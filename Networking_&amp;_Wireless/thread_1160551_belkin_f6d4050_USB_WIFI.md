---
title: "belkin f6d4050 USB WIFI"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by Adam25 on 2009-05-15
Hello,

I just picked up a belkin f6d4050, this is the only USB wifi stick wal-mart had in stock. I checked the list and can only find older supported models such as the f5xxxxx and see no f6 models. Can anyone help me get this going? We got it to where its saying its connected to the laptop but have yet to get any internet. Thanks.

---

### Post by albinootje on 2009-05-15
> **Adam25 said:**
> We got it to where its saying its connected to the laptop but have yet to get any internet. Thanks.

Can you ping a public ip address successfully ? Please post the output of the following :
```

ping -c5 194.109.21.51

```

Can you also post the output of the following :
```

lsusb
lsmod
dmesg|tail

```

---

### Post by Adam25 on 2009-05-15
Im pretty new to ubuntu, I just figured out how to ping on here and no i cannot. I went to network connections and added my mac addy and such so thats there. Im really not sure what do do here can you help?

---

### Post by albinootje on 2009-05-15
> **Adam25 said:**
> Im pretty new to ubuntu, I just figured out how to ping on here and no i cannot. I went to network connections and added my mac addy and such so thats there. Im really not sure what do do here can you help?

Okay, if you can't ping that ip address that I gave in my previous comment, then that means that you are likely to have no internet through that usb wifi card.
If you could have pinged that specific ip address, then it was likely that the problem was a DNS problem.

I've searched for the type of the usb device you have, in combination with the word "ubuntu" in a search engine, and that gave almost no hits as result.

It could be very useful if you start a terminal and post the output of the following (with the usb device attached) :
```

lsusb

```
With that information it can be easier to get more search results 
while searching for information if and how to get that device working properly.

---

### Post by Adam25 on 2009-05-15
bus 002 ID 1d6b:0001 linux ffoundation 1.1 root hub
bus 001 ID 050d:935a Belkin Components
bus 002 ID 1d6b:0001 linux ffoundation 1.1 root hub


So i guess it knows what it is since it says belkin? Anything else you need to know?

Is there a way to get ubuntu to search for my wifi??

---

### Post by Adam25 on 2009-05-16
Can anyone help me here?

FYI if you need 2 know, Dell insperion 2650, running ubuntu 8.10

---

### Post by albinootje on 2009-05-16
> **Adam25 said:**
>  bus 001 ID 050d:935a Belkin Components

Good, thanks. That gives a little bit more hits after searching, see here :
[http://groups.google.com/group/it.comp.os.linux.iniziare/msg/5167783d1d05245f](http://groups.google.com/group/it.comp.os.linux.iniziare/msg/5167783d1d05245f)
Which translates as :
> 
Thanks for the answer. The numbers are 050d: 935a. Googlata has not given some result. However, spulciando the file.inf for windows, me it seems to have understood that they are the rt2870. When I have a time P2o I try to compile them and we see if I have guessed to us. 

So.. can you try the Ralink 2870 driver in 8.10 ?
Here's a howto :
[http://www.apfelkraut.org/2009/02/howto-wlan-ralink-rt2870-usb-stick-kubuntu-810/](http://www.apfelkraut.org/2009/02/howto-wlan-ralink-rt2870-usb-stick-kubuntu-810/)
And here too :
[http://ubuntuforums.org/showthread.php?t=919044&highlight=rt2870](http://ubuntuforums.org/showthread.php?t=919044&highlight=rt2870)

Let us know how it goes. Good luck!

---

### Post by hackerb9 on 2010-07-12
Solution is here [http://ubuntuforums.org/showthread.php?t=1509403](http://ubuntuforums.org/showthread.php?t=1509403)

---

