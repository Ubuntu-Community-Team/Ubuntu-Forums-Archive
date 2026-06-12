---
title: "Help getting wireless working"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by matthejl8 on 2010-09-13
I just put Xubuntu on my HP ze4800 laptop.  Everything works fine I believe, but the wireless connection.  When I right click it just says "dissabled".  The little button that usually turns the wireless adapter on and off just stays lit, no matter if I push it.

Basically I need to know how to get the wireless connection going.  Try to use it in the most rookie terms possible.

thanks

---

### Post by matthejl8 on 2010-09-14
I have tried using a command installing and using the windows driver and nothing works.

Its nuts how just getting a simple driver to install to have wireless internet could be so difficult.  

Any help or tutorial would be hugely appreciated as I am pulling out hair as we speak.

I am new to Linux by the way.

---

### Post by PRC09 on 2010-09-14
Hope this helps,usually its hardwire into your router,do all updates and then check for the hardware drivers in System> Admin >Hardware Drivers and you should see the Broadcom drivers there(b43) I think for that card and click activate and away you go.....


[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by MaindotC on 2010-09-14
> **matthejl8 said:**
> I am new to Linux by the way.

Really?  In the future please consult the [sticky on a list of supported hardware and how to post a request in this forum]("http://ubuntuforums.org/showthread.php?t=370108").  We want your wireless card to work, and we want you to enjoy the benefits of using Ubuntu after you clear this one small hurdle, so we will help you as best we can.

> **PRC09 said:**
> Hope this helps,usually its hardwire into your router,do all updates and then check for the hardware drivers in System> Admin >Hardware Drivers and you should see the Broadcom drivers there(b43) I think for that card and click activate and away you go.....

PRC09 - those directions are only a fraction of what needs to be done.  Please stop advising other users in this fashion, and always try to consult official documentation as I have done below.  

matthejl8 please consult the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and let us know if you have any difficulty and precisely where so we can better help you.

---

### Post by PRC09 on 2010-09-14
I just quoted what has worked for me in the past and present........

---

### Post by PRC09 on 2010-09-14
> Really? In the future please consult the sticky on a list of supported hardware and how to post a request in this forum. We want your wireless card to work, and we want you to enjoy the benefits of using Ubuntu after you clear this one small hurdle, so we will help you as best we can.

TO:strAlan

I see thats how to welcome a new user....Send him a little note on how to post his question.Great help......

---

### Post by grahammechanical on 2010-09-14
The best I can offer is too look through the Ubuntu Wireless Trouble Shooting Guide at
[https://help.ubuntu.com/community/WifDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifDocs/WirelessTroubleShootingGuide)

Do the tests listed there collect the information it will help others give you advice if you are not able to correct it yourself

Regards

---

### Post by matthejl8 on 2010-09-14
StrAlan, is it necessary to actually take the time to quote the text that I am new to Linux and then comment "really?"  I dont appreciate that much.
 
Ok, I appreciate greatly the technical help...because this issue is driving me crazy and I think its nuts there is a huge technical article on getting wireless working.  Is it not simple as you have a hardware device, you need a driver,  you match the two and it works?
 
Is there another distro thats more user friendly out of the box for getting wireless to work, I would think something as common as wireless internet on a laptop would be easier to deal with.
 
And yes, some of it is my stupidity and rookieness, but I do pick up pretty fast.
 
and to be honest I would rather deal with direct question and answer than reading an entire manual trying to sort out my specific problem.
 
I thought that was what forums are for.  I do know I can read through that thing and eventually probably figure it out, but my profession limits my time and I am trying to get help as quick as I can.
 
If you arent willing to help and only want to point to a wireless connecting troublshooting guide, thats fine, just say "I dont want to help you, read the guide" and I will, and in the mean time I will see if someone is genrous enough to help me individually.

---

### Post by utilitytrack on 2010-09-14
> **matthejl8 said:**
> Is there another distro thats more user friendly out of the box for getting wireless to work... 

Does not matter what kind of distribution, because it does not determine the degree of support equipment. This is determined by the development of the Linux kernel.

> **matthejl8 said:**
> ...and to be honest I would rather deal with direct question and answer than reading an entire manual trying to sort out my specific problem.

No, is not a correct view of things. If you consider yourself capable to learn Linux, you should be able to read and understand the documentation first. Only after this if something is unclear you can to ask for help from more experienced people.

**matthejl8**, 

Iowan gave you very good advice. Unfortunately, if you don't wish help yourself by reading the documentation, we on this forum can't help you anyway.

---

### Post by utilitytrack on 2010-09-14
Here the answer to your questions: [http://linuxwireless.org/en/users/Drivers/b43/faq]("http://linuxwireless.org/en/users/Drivers/b43/faq")

---

### Post by cariboo on 2010-09-14
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by matthejl8 on 2010-09-14
Sorry, I only did this because I initially posted it in the wrong section and didnt realize it at first.

---

### Post by matthejl8 on 2010-09-14
> **utilitytrack said:**
> Does not matter what kind of distribution, because it does not determine the degree of support equipment. This is determined by the development of the Linux kernel.
 
 
 
No, is not a correct view of things. If you consider yourself capable to learn Linux, you should be able to read and understand the documentation first. Only after this if something is unclear you can to ask for help from more experienced people.
 
**matthejl8**, 
 
Iowan gave you very good advice. Unfortunately, if you don't wish help yourself by reading the documentation, we on this forum can't help you anyway.
 
for the past two days all I have been doing is reading...my lack of experience and understanding of linux is limiting me of being successful here so I posted the question hoping to get the answer from a different point of view, or different angle.  Sometiems, for me, thats all it takes for me to understand what has been previously written or previously figured out.

---

### Post by perspectoff on 2010-09-14
(Redacted)

---

### Post by matthejl8 on 2010-09-14
What would be the main commands I would need to run and post the results to where you guys could see if my driver / hardware is configured...or how it would need to be configured.
 
I will do this tonight when I get home and post the results.
 
thanks

---

### Post by MaindotC on 2010-09-14
> **matthejl8 said:**
> What would be the main commands I would need to run and post the results to where you guys could see if my driver / hardware is configured...or how it would need to be configured.

In the troubleshooting guide that has been posted twice...

---

### Post by matthejl8 on 2010-09-15
I formatted and reinstalled, and it worked out of the box this time.  The difference was that I had it hooked to the internet upon installation this time with an ethernet cable.
 
When I booted, the hardware drivers screen popped up and asked if I wanted to enable the broadcom legacy driver, I clicked enable and it worked.
 
Is this solely due to the internet access it has upon installation.

---

