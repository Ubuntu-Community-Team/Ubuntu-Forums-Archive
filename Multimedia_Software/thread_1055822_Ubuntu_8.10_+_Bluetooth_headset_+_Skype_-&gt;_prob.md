---
title: "Ubuntu 8.10 + Bluetooth headset + Skype -&gt; problems"
date: 2009-01-31
forum: Multimedia Software
---

### Post by yesyes on 2009-01-31
Hi!
This is my first post. Well, second post because I had posted this issue in the Absolute Beginner Talk section a few days ago but didn't get a reply there. So I'm trying here...

I'm new to Ubuntu and Linux in general. I've been running XP and predecessors but have decided to move to Ubuntu 8.10 on my main machine.
So far most things work fine... There are a few other issues but this one is the "most pressing". I'll start new threads for the other ones.

What I'm trying to do is to get my Logitech Bluetooth headset working in Skype. Skype itself works great already when I use a corded headset connected to the on-board sound card. Even my webcam worked straight after plugging it in.

The headset is a Logitech. On the headset itself it's printed "Model# F-0228A" and when I let Bluetooth Applet 1.8 discover the headset it says "Logitech HS02-V07".
The Bluetooth dongle I use is the one that came with the Logitech Wireless Desktop 5000. The keyboard and mouse work fine with this (after reading some of the posts here...)

The current situation is that I can pair the headset in the Bluetooth tool. I have an option to select "headset" in the Skype audio settings. But I can't hear the Skype test sound and when making a test call it says audio problems.

I have found a few posts on here related to the subject but none of them have the same issue and I couldn't find a solution.

Has anyone got this working?
I doubt that it has something to do with the model of headset as the pairing works. So if someone has got this working with another headset, I'd be interested too.

Ah, and it was working fine on XP, so I know this combination can work...

Thanks !
Chris

---

### Post by yesyes on 2009-02-02
Hm, no replies at all?

Anyone ANY ideas? 
Is there some info missing? I'm happy to provide anything you need to resolve this... ;)

---

### Post by cbaron0185 on 2009-02-16
I know its a little late, but I found that this solution did work for me. Its still a little buggy at times but it allows skype to see my LG headset. 

[http://gablog.eu/online/node/80](http://gablog.eu/online/node/80)

Good Luck!

---

### Post by yesyes on 2009-02-16
Thanks for that! I had almost given up on a reply.. ;-)

I've tried that but "$ sudo hcitool scan" doesn't list anything although my mouse and keyboard are also connected via bluetooth and are working. Hm, I will have to look into this in a bit more detail.
I do also see some strange audio and bluetooth related errors and warnings in my /var/log/syslog which I need to google. On board audio works fine though.

It's good to know that someone has got this working. And your link is a good place to start... ;-)

---

### Post by tonymaro on 2009-03-20
> **yesyes said:**
> I've tried that but "$ sudo hcitool scan" doesn't list anything

From what I've seen it may not show devices that are currently paired.  

Could it be you're running a 64 bit install of 8.10?  You're probably just missing the 32 bit libraries.  Here's my notes from just going through this same thing, getting a bluetooth headset working in 64 bit Intrepid with Skype:  ** [http://www.ossramblings.com/skype_bluetooth_headset_64_bit_ubuntu](http://www.ossramblings.com/skype_bluetooth_headset_64_bit_ubuntu) **

---

### Post by yesyes on 2009-03-22
Hi tonymaro. Thanks a lot for that. Indeed I'm running 64bit Intrepid ;)
I will give that a try what you described on your website and post the results here.

And sorry about the late reply. I've been moving house this weekend. Not much time for any experiments... I'm lucky to have an Internet connection already ;)

---

