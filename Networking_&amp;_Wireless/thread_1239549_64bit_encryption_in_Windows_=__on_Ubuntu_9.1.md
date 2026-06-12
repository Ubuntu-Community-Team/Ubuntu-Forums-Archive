---
title: "64bit encryption in Windows = ?? on Ubuntu 9.1?"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by bowie101 on 2009-08-13
My IT guy (who actually does the networking and hardware in this place) told me the router is 64bit encryption WEP, shared authentication. But what does that translate into on Ubuntu 9.1?

The options on Ubuntu 9.1 are: 

WEP 40/128-bit key   (wep index  is 1 , 2 ,3 , or 4)  (authentication is Open System or Shared Key)
WEP 128-bit passphrase (wep index is  1 , 2 ,3 , or 4) (authentication is Open System or Shared Key)
LEAP
Dynamic WEP (802.1x)  with either TLS, LEAP, Tunneled TLS, PEAP (protected EAP) for authentication

Also, the password is 5 numbers and 5 letters. The letters on a Mac have to be in all caps. In Windows, it's all lower-case. So, in linux, would it be safe to assume caps?

---

### Post by t0mppa on 2009-08-13
[Here]("http://ubuntuforums.org/showthread.php?t=974272")'s a thread about it, apparently 64 bit WEP was left out of 8.10 already. And [here]("http://www.wirelessdefence.org/Contents/LinuxWirelessCommands.htm")'s a page displaying how you can enter the 64 bit key manually, if none of the ideas in the above thread help. 1st & 2nd hit on Google BTW.

What you should ask your IT guy about is why you're still using WEP though, the web is full of pages elaborating how to break it in ~3 minutes with a few simple programs.

---

### Post by chili555 on 2009-08-13
I believe you want WEP 40/128-bit key, wep index 1 and authentication is Shared Key. My computer likes the letters in my key in lower case, i.e.```
096c7f280e etc.
```Let us know.

A 40 bit key is really the same as 64-bit WEP: [http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy](http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy) See especially:> Standard 64-bit WEP uses a 40 bit key (also known as WEP-40), which is concatenated with a 24-bit initialization vector (IV) to form the RC4 traffic key.

---

### Post by bowie101 on 2009-08-13
ok, I'll let you know after i try tomorrow. thanks !

---

### Post by bowie101 on 2009-08-14
Well, I after reading a bit (but maybe not enough?) I uninstalled network manager-gnome and whatever else was attached to it, and installed wicd. 

At home, it was good enough to easily pick up the home comcast signal that seems to elude my computer when in windows. (very finicky in windows.) But that is an unsecure /unencryped signal.

At work now, I see the wireless network to which I want to connect. I put in the correct password or I put in an incorrect password. Regardless, the message says validating authentication, then goes right on to Obtaining IP address. It hangs there. Eventually it quits and says "connection failed: unable to get ip address".


in the wicd interface though, it does give me a bit more info. It says that the signal is indeed WEP and channel is 6. Whatever that means.

---

### Post by bowie101 on 2009-08-14
actually, it will have to wait until Monday, as our IT guy is coming in to change the routers anyway. 

Today, it isn't even working in windows.

---

