---
title: "Mobile Broadband?"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by UncleMonty on 2009-06-03
I want to use mobile broadband in ubuntu jaunty. What options are there? Do any companies provide mobile broadband for this linux distro?

---

### Post by peterroots on 2009-06-03
T-mobile works (so presumably so will vodacom and others that use the same usb stick).
Just buy it, credit the account and plug it in - network manager will detect the usb stick and prompt you for the country and operator and does all the hard work for you.
What you can not do is anything other than connect to the internet so you can not send texts for example.  sending texts is essential if you want to change from daily to weekly or monthly price plans.  You can take the sim card out of the usb stick and put in in a phone (must be a matching one or unblocked) to send the text to change plan.  Well it worked for me anyway in the UK (not tried this yet in Tanzania)
Unfortunatly this does not work in Kubuntu for some reason but here you can use kppp to get on line (help available on Tux radar)

---

### Post by stoney_sjl on 2009-06-25
Hi there UncleMonty, I'm running Jaunty (not UNR) on a Lenovo S10E and have just bought a Vodafone K3565 USB Modem Stick Lite from Maplins (£39 with a free £15 topup) Bought it because there's no 30-day expiry on the account, you have to log in once every 180 days to keep the credit going, which even I can manage !
Plugged the USB stick in, answered 2 questions (I think) and that was it, I was up and running. Very, VERY impressed - setting up 3G on my Asus EEE was much harder :) My only "hardship" was that the built-in software needs Windows for initial account creation, but I was able to use my daughter's Windoes laptop to do the registration/account creation, 'though I'm pretty sure that I could have done it by going to [www.vodafone.co.uk](www.vodafone.co.uk) and working it out from there. However, Vodafone do send an "activation code" (only valid for 20 mins) to the device's "phone number" via SMS, and the feature for receiving SMS is only available on Windows. Once this is done however, everything else is available via normal on-line web interface.
The only other limitation (so far) that I can see with the device, is that you have to topup in £15 increments only, but given that the credit doesn't run out at the end of a month, whether you've used it or not, this one really doesn't concern me too much.
Good luck
Simon

---

### Post by billmania on 2009-07-04
I have a Nokia E61i with a USB cable and T-Mobile USA data service. I cannot make this combination work with ubuntu desktop 9.04. I get past the PAP step and then LCP is terminated.
I've given up completely trying to use network-manager for this because it doesn't work at all. I'm trying to get confirmation from T-Mobile USA about PAP or CHAP or some PPP credentials. It was almost trivial to get the phone working with 8.04 but now I don't know if the problem is with 9.04 or with something at T-Mobile.

---

### Post by kellyhardinguk on 2009-07-04
I use a T-Mobile USB stick (Huawei E160). Works flawlessly with Ubuntu NBR 9.04 on my Aspire One.

Network Manager pops up a dialog when its inserted asks a few questions, and it just works. All the needed settings are already pre-defined.

---

### Post by JAwuku on 2009-07-05
I currently use the 3 service, with the Huawei E3220 device.

Works well on Jaunty (using eeepc 1000HE).

---

### Post by londonbabs on 2009-08-02
I use the huawei e160 with O2 pay as you go on ubuntu 9.04 and it worked straight away, I had to put the necessary O2 settings during the setup and rebooted a couple of times to get it together but it eventually worked and has been fine since
only thing I need to figure out now is how to block it on 3G connection only, it keeps jumping from GPRS to 3G and can be somewhat annoying, any suggestion ?

---

### Post by IanMoff on 2009-08-03
Hi

I'm in UK and use Orange (think it's a Huwaei) dongle. £15.00 pcm and 3GB limit(?). Only use it now and again. When travelling. When BT network goes down ;-) Not downloading torrents etc. so never been over limit. HTH. Ian

---

### Post by lisati on 2009-08-03
I use a [ZTE R6]("http://www.zte.co.nz/main/R6.htm") 3g phone from [Telecom NZ]("http://telecom.co.nz") which can be used for mobile broadband . The copy of Ubuntu I use (9.04) currently only lists Vodafone as a provider, but the settings are easily changed to try to connect through Telecom - changing Ubuntu's settings aren't too hard, I based the ones I use on some information that was preprogammed into the phone/SIM.

(BTW, I normally use a wired connection and have only used mobile broadband when I've been "having a play")

---

