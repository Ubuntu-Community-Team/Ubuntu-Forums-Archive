---
title: "Important Help"
date: 2006-02-03
forum: Networking &amp; Wireless
---

### Post by sunnypk on 2006-02-03
Can anyone in here please guide me how to install Lucent Win Modem with I think NEC Chipset in Ubuntu Breezy Badger 5.10? I know there are lot of tutorials available but no such guide to help a real beginner one have to figure alot of things by himself. So I need a proper real step by step guide to do that. It'll not only help me but it'll support every new starter having problem in the installation of modems. So I request if anyone in here can do this job I'll really be thankful for this act of kindness. I am tired of reading 100s of articles and switching from windows to ubuntu and ubuntu to windows as my internet is not working on ubuntu so i read article and to perform it save the required things and switch over to ubuntu but errors sucks! So please do help me out and give me a real starter guide in which each step is included. Thanks in advance :mad: :-# :cry:

---

### Post by mpvano on 2006-02-03
If it's really the lucent, then the driver may be already installed.  Unfortunately there are a lot of variations on this theme, and it's quite a project tracking down what's really going on.

I got mine (which is part of an ibm t-30 wireless adapter and uses the intel sound card for part of the modem) working by just installing the "sl-modem-daemon" and then configuring the modem with "sudo pppconfig".

Note that you need to enable access to the "multiverse" repositories in synaptics to obtain the modem daemon package (which just takes care of loading, configuring and starting and stopping the modem emulation as needed).

There are so many variations on the hardware that it's impossible for any one set of "cookbook" instructions to work, so I'm afraid you're on your own.

Avoid any instructions that tell you to download and build drivers - they will just destroy the existing driver which works as well as most of the variants floating around the net. It can be very hard to recover from some of the instructions floating around.

If you can't get the existing driver loaded and working with sl-modem, you're probably doing something wrong or your modem is just not supported by the lucent driver.

If you really need to use the onboard modem and it's not a lucent modem or one of the few others compatible with the driver built in to ubuntu you'll probably need to buy a driver from the third party apparently given the right to sell them by conexant - go to [www.linuxant.com](www.linuxant.com) for more information and to find out if their drivers support your card. If you have one of the modems they support, their drivers work well and cost $20.00, I believe.

There seems to be some more information about this entire subject collected  at [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) that actually looks pretty good, but use it with caution.

They also have a "crippled" free version you can download to evaluate. The free version works too slowly to be useful, but once you've determined that your modem is one they support, it can be a good way to confirm that it will work in your machine.

If you have a USR (US Robotics, or a variant after the company was bought out), you may not be able to use any standard driver because they seem to have deliberately modified the chip sets to make them incompatible with other company's modems.

hope this info helps....

Mario

---

### Post by sunnypk on 2006-02-03
First of all mpvano thanks for ur nice reply i worked over that thanks again dude :) n Well actually it is lucent as I have windows running on another partition so windows xp is showing it as lucent win modem and in UBUNTU as well in DEVICE MANAGER its showing lucent win modem its detecting the right modem but why not running that one? Is there anything else required ? I've tried to dial but its not working at all can you again or anyone else in here help me?

---

### Post by sunnypk on 2006-02-04
[COLOR="Red"]NO RESPONSE AT ALL :([/COLOR]
Well I've done myself what was written in Wiki without error but still no modem :S ... im confused lt_modemserial gives error that FATAL: module not found i followed more steps given but to no use can anyone plz help me?

---

### Post by cjwworld on 2006-02-05
hello,

I have read and reread all post and tried different things and I can't seem to connect to internet.  I have reinstalled and the net and synastic works great.  updated all advailable updates.  BUT as soon as I reboot it doesn't connect!??

I 'sudo pppoeconf' it.  I know that ip and gateway # are correct.

I use an dsl router, SpeedStream 5100 model.  Each time I reinstall it works, but it goes dead after reboot.  The ethernet adapter light blinks on the modem as well as the card in the back of computer and the other (modem) lights (DSL, Internet) stays green, 

I am using two HD, one for Ubuntu and one for XP Pro.  I have GRUB installed. I have upgrade to (i believe) 10.9-10 kernel.

I am at lost aat this.  Trying to be patient.

can anyone pave the way for me?

Remember that I cannot copy and paste any details (I guess I can write it down) I would have to use XP to communicate

Thanks

cjwworld

---

### Post by sunnypk on 2006-02-06
**[COLOR="Red"]NO REPLY? Come on please help.[/COLOR]**

---

