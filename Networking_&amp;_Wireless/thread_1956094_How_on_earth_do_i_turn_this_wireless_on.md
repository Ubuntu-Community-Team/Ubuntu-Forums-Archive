---
title: "How on earth do i turn this wireless on??"
date: 2012-04-10
forum: Networking &amp; Wireless
---

### Post by bangemudha on 2012-04-10
I'm running Xubuntu 11.10 on Dell Studio 1555 and my wireless is working fine with the broadcom driver. I've been using Xubuntu/Ubuntu for years but i've had the same problem over and over and over again - once i disable wireless either by the button on my keyboard or by clicking on the icon, i'm not able to enable it again. Its not that i haven't gone through numerous posts and tried out what worked for other but for me it doesn't work at all. My only solution is to boot to windows every time, start the wireless interface from there and then reboot to linux. This gets really annoying at times - especially when you've got tonnes of assignments and papers piling up and you're wasting time rebooting. Any of you faced this?

---

### Post by josephmills on 2012-04-10
Hello there 

there are a couple of was to enable and disable wireless. On dells it is the fn+f4 keys. Here is how you test 

1) open terminal (ctrl+alt+t) and enter 

```
rfkill list all 
```
this is going to give you a list like 
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

So **Soft blocked** means that there is some sorta software blocking yout wireless and or bluetooth 
to fix this we use command 
```
rfkill unblock all 
```

**Hard Blocked** means that there is a HARDware switch that is blocking you meaning that the external switch or the key combos are looking it and you need to turn on.

so what you can do it do rfkill list all then try key combo the do rfkill list all again to see if anything has changed. If not go under setting~~>keyboard~~>shortcuts    and make sure that nothing is assigned to fn+f2 


I hope this help 
cheers


ps there are alot ways to skin a cat

---

