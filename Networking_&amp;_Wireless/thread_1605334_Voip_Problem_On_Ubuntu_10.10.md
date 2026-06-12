---
title: "Voip Problem On Ubuntu 10.10"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by arynet on 2010-10-25
Hi, i got some problem on ubuntu 10.10. Im running SFLphone client for [Smartvoip]("http://www.smartvoip.com") i can make a call but just about 10-15 seconds and call dropped, silent and i talk with myself.

I have tried on Ekiga, Twinkle, and more. They are same.

Problem on ubuntu network setting? I dont know how to fix this problem. can someone help me?

When i on Microsoft windows (my friend's PC) in the same internet network. The voip work fine.

I have no problem on ubuntu 10.04. Running smoothly. Its happen when using new ubuntu 10.10 - Clean Install.

thanks in advance. sorry for bad english.

---

### Post by kalou on 2010-12-12
Up!

I have tried ZOIPEr, but there are no version for maverick, works with OSS or Alsa.
Ekiga doesn't even propose VOIP in the account configuration.
Can anybody help on this issue?
iS IT POSSIBLE TO GET eKIGA TO DO  VOIP  with OVH for example?

thanks a lot

---

### Post by fcigoi on 2010-12-12
Kalou,

It's not nice to hijack threads like that, however Ekiga can do VOIP if your provider is SIP compatible. Don't know if OVH is.

As regards the main subject of the thread all I can suggest is to take a look to the log files. Normally there's a sign of why it works like it does

---

### Post by kalou on 2010-12-13
Sorry, i thought I was contributing somehow too; Ekiga in the maverick distribution, does not offer SIP in "create new account", unless it is something like SILC...
OVH does SIP, how can i use my ovh account on ubuntu 10.10?

thanks a lot again

---

### Post by fcigoi on 2010-12-13
Ekiga 3.2.7 offers the possibility to configure SIP accounts. Not sure when I installed it but I think it was with 10.04.

---

### Post by rookcifer on 2010-12-23
I am also trying to get SFLphone working.  I cannot even place a call with it.  I just get the red X and a 404 error when I try.  Does anyone know how to configure it?

---

### Post by kalou on 2010-12-24
I have a mini10v (dell) and installed maverick a few weeks ago. I use a phone line from OVH (sip)

I have tried twinkle, softphone (ekiga) or zoiper, i get problems with all of them with the sound card. There are bugs in the sound drivers, sometimes the mike doesn't work and sometimes it is the sound. drivers HDA INTEL
any bug fixes of versions for 10.10 that work?

---

### Post by Boondoklife on 2010-12-24
Have you tried just using empathy? [LINK]("http://ubuntuforums.org/showthread.php?t=998411")

I use it for my sip account and I get calls all day. I don't make any calls though so couldn't tell on that side of it.

---

### Post by svaens on 2011-02-06
I just re-tried getting SIP to work reliably on ubuntu.

Twinkle works, almost flawlessly, as it did since at least 9.04
Only problem now with twinkle is that it doesn't seem to support pulseaudio natively, and is rather ugly (sorry). 

Empathy now, since Maverick for me, seems to work. I needed to uncheck the option to discover STUN server automatically) .. and then I was able to connect. 

I have tried SFLphone too, and honestly, since it is the prettiest of the bunch, was dearly hoping I could get it to work. 
But while I could get it to register.... I could not get it to connect me to another phone. As soon as it would (theoretically) start to dial, I just get silence.... 
I am also able to dial in (from another phone, for example my skype-out account) but as soon as I accept the call, silence again. 

This 404 error I was also receiving until I changed the advanced 'account settings' to:
* (yes) Using STUN
STUN server URL: stun.sflphone.org

Perhaps that is just plain wrong,...
Perhaps I need to read up on just what the hell a STUN server is? I don't think it is provided by my SIP account provider is it?
Is that why it doesn't work?

---

