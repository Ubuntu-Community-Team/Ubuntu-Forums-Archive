---
title: "How to activate a wlan stick"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by Bigjge on 2009-06-04
I need help please.
My daughter has own computer with a avm wlan stick.  With windows, just plug wlan into router, then plug wlan into other computer and in minutes works and can get on line.
Has anyone any idea how to activate this wlan stick with ubuntu, if not my daughter will not use ubuntu as would not be interesting not getting on line.
I will say that ubuntu is not user friendly ie point and click.

---

### Post by chili555 on 2009-06-04
> I will say that ubuntu is not user friendly ie point and click.You could get a lot of pointless debate there, but rather than start a pointing and clicking contest, let's just attack the problem directly. First, 'avm wlan stick' is not enough information for us to know what driver to use. Please insert the device and open a terminal and do:```
lsusb -v
```Post the output and we'll be very happy to help.

---

### Post by Bigjge on 2009-06-05
I have read and will say that the sudo command does not work.
I have tried several sudo commands in terminal that people give and none work.
I think that either the people who reply forget they were once new and abrieviate answers,this is hard for new people, or they are not correct.   I do not know I will say that no linux program will be a great success until lots of settings are made a lot easier as most people can not take the time to try and type a lot of cammands that most do not remember anyway.

---

### Post by chili555 on 2009-06-05
> sudo command does not work.It works perfectly. If you have a citation, I will be fascinated to read it. I have read quite a few posts where the command didn't work because the person mis-typed the command such as *sudo lshw -c network* when it should be *sudo lshw -C network*; that is a capital C.> I think that either the people who reply forget they were once new and abrieviate answers,this is hard for new people, or they are not correct.I agree fully. Some here do not take the time or have the empathy to try to see if a person is pretty experienced and understands the jargon, or if they are new and need a bit of friendly hand-holding. I try and sometimes I fail.

If this is all about pointing out the frailties of Ubuntu and Linux, I want no further part of it. We could debate for weeks and, I suspect, neither of us will win over the other.

If this is about getting your wlan stick going, may we please see:```
lsusb -v
```Thanks.

---

### Post by 3rdalbum on 2009-06-05
Most wireless devices don't require any terminal commands or "sudo" - they work on Ubuntu without you even needing to point and click. You're just unlucky to have one that is maybe a bit more obscure. I haven't heard of this "AVM" brand before so I suspect this may be the case.

You might find it easier to copy and paste the suggested commands into the terminal, then there's no possibility of mistyping.

---

### Post by Bigjge on 2009-06-05
I thankyou for help but will stop here as is my daughters computer and she found that ububtu does not load anymore widows has removed the boot start for ubuntu.
I have had this before.
I have a problem with ubuntu and I have xp pro.   Ubuntu will get on line but not how I wish it to.
I have a german avm router but english version and works perfect in windows.   This router has its own program which when running gives me control over what can and cannot
go on line and also gives a visual guide as to what comes down and goes out.
If I can get to work in ubuntu then will at a later date get my daughters wlan to work.
This router uses pppoe but adds own drivers for ppp/dsl.
If you have any ideas on this one I can make a new thread.
I do understand that the avm program will run in wine but only goes in a file is not installed.

---

### Post by Jsmooth622 on 2009-06-05
I do not mean to hijack another person's thread, this is merely the only way I know of to recieve immediate help with my problem. I am also having a similar problem connecting to the internet on my gateway desktop pc. I have installed Linux ubuntu 9.04 on it as the only os. My wireless stick is a netgear router. Under the network icon, No networks are visible leaving me no options to access the internet. Internet worked fine on windows, and connection is otherwise fine. Please help!!!

---

