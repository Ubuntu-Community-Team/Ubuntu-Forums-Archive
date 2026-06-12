---
title: "Huawei modem frequent disconnects"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by didac on 2011-06-15
I have a Huawei EC226 modem, running now on 11.04. The problem is frequent disconnects. The connection icon still shows connected, but there is no internet activity. A 'ping [www.google.com](www.google.com)' show network as unreachable, though there is domain name resolution.

It usually happens when there is voltage fluctuation. Yes, electricity supply is hell here. I have UPS, stabilizer, power surge protector, the works. And yet fluctuations can get through. Curiously, this is not a problem with Fedora, I don't know why. Mysterious mysteries. It does happen with Ubuntu, no matter the version: 11.04 -- the present one -- 10.10, 10.04 . . . I'm at a loss on how to diagnose it.

So, at times I get disconnected. For instance: I cannot leave a file downloading overnight -- supposing there will be electricity all night long, which isn't usually the case.

More problems: reconnect doesn't work. I have to unplug the modem, plug it back and try again to reconnect. Which doesn't work all the times. The best solution so far is unplugging, do 

```

sudo rmmod ppp_deflate
sudo rmmod option
sudo rmmod usb_wwan
sudo rmmod usbserial
sudo rmmod usb_storage
sudo rmmod ppp_async

```

and then I can reconnect again.

Finally, after all this long poem-tragedy-novel, the question:

Any idea how can I write a script running in the background, pinging, when it doesn't get a response disconnects, removes modules, loads modules again and dials the connection again?

Sorry about the incredible length. It doesn't matter if I cannot diagnose the cause of this problem. So far, I'll be happy with a script to redial.

---

