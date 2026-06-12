---
title: "blueman, network manager and gprs"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by ElGatoFlojo on 2009-03-23
So, I'm a little perplexed. Like many others on here I've discovered the joy's of blueman. Yes, I realize it breaks somethings but for the most part its worked great for me. But my issue is this.

I set everything up, I click on 'Device -> Serial Ports -> Dialup'. I see my phone light up as the DUN service is started and I see in my log files that rfcomm has been found

Mar 22 21:29:36 raptor NetworkManager: <info>  Found new Modem device 'rfcomm0'. 

So, I head to my Network manager and click on my AT&T dialup setting that its so helpfully provided for me. I click on it, network manager spins for a milli second and then dies. I see this in the logs

Mar 22 21:30:25 raptor NetworkManager: <debug> [1237782625.846705] nm_serial_device_open(): (rfcomm0) opening device... 
Mar 22 21:30:25 raptor NetworkManager: <info>  Activation (rfcomm0) Stage 1 of 5 (Device Prepare) complete. 
Mar 22 21:30:26 raptor NetworkManager: <WARN>  init_done(): Modem initialization failed 

I've paired the phone, everything else is working. But for some reason this connection refuses to work. Am I doing something wrong that is very simple that I'm missing? I want this to work with Network manager to make everything simple. But its like I missing some very tiny step. Anyone?

Thanks so much

---

### Post by ir0nman on 2009-03-28
I am having a very similar problem, I'm assuming that network manager isn't issuing the proper AT commands to my phone. It's a blackberry so I don't have very good usb support yet, and I've had it work with ppp before, but since ppp doesn't automatically fix dns, I thought it would be nice to use network manager when I came across blueman. does anyone know if this works in Jaunty yet? OP have you had any luck yet?

Thanks,
-Rick

---

### Post by ElGatoFlojo on 2009-03-28
Yep, thats my same thoughts exactly. Its trying to send a AT command via the rfcomm interface just like it does when its on via USB. I have no idea where those files are located at either otherwise I'd try and get in there and fix it.

Its so painfully close though! I'm even trying out jaunty right now and the bluetooth is back to being broken as it was before. I'll be installing blueman as soon as its available for jaunty. Hopefully they'll make it the new default manager

---

