---
title: "Mobile Broadband working in liveCD but not installed Ubuntu"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by GGleroutier on 2011-04-11
Greetings all,

I have a funny problem...
I've used Ubuntu 9.04 on my laptop for a long time. I uninstalled Network Manager early on, and replaced it with WiCD to get wifi.

I recently lost access to this wifi connection and got a mobile broadband USB stick device (Huawei E169u) to replace it. I thought it might be a good occasion to get a more up-to-date distribution.
I tried the 10.04 live CD, everything worked fine, the USB stick modem appeared directly in Network Manager under "Mobile Broadband" and I could connect without any problem.

I then upgraded my 9.04 to 9.10 and 10.04 (through wifi connection, not here at my place), and reinstalled Network Manager (v0.8, apparently same as in the liveCD).

Problem : my USB stick does not appear in Network Manager. No Mobile Broadband devices. Funny, isn't it ? :D

It's one of those dual mode USB sticks, both modem and small storage device for the windows drivers. I have a hunch this may be the problem... The USB stick appears on my desktop as a storage device. It does not in the live CD version (I see it in "Places", ready to be mounted, that's all).
I know there are some mode switching tricks to get around this, but I'd like to avoid this kind of thing if possible, as it seems that everything should be working out of the box.
There's probably an easy solution... isn't there ? :D

Any ideas ?

Thanks in advance !

---

### Post by spiky001 on 2011-04-11
Have you added it in network manager select mobile broadband then follow instructions

---

### Post by GGleroutier on 2011-04-11
Thanks for the input !

Yes, I've tried that, sorry I forgot to mention it.

To add a broadband mobile connection,  I have to specify for which device I am creating it for.
The list is blank, ie Network Manager sees no device that could be used.

I still think the problem comes from the modem/storage duality.
A 'virgin' Ubuntu 10.04 recognizes the device instantly for what it is. My upgraded 10.04 seems to see it as a memory stick. So I think there is something somewhere left from my 9.04 that says "this is a storage device !" ; if I could correct that... Or am I completely wrong... :D

---

### Post by GGleroutier on 2011-04-11
Well ! I had been using the live CD all day (which is not so bad, by the way) and just rebooted five minutes ago to switch to the installed Lucid Lynx.
What do you know. This time the USB modem appeared under the Mobile Broadband list in Network Manager. Everything works fine, perfect connection. And it stills appears as a storage device on the desktop.

I suppose my problem is solved :D but still would like a few words of explanation if possible.

Anyway, thanks all !

---

### Post by GGleroutier on 2011-04-12
Well I'm back :D

Seems like it's not working after all.
Or rather, it works only if I boot with the live CD, restart the computer and use the installed 10.04.

Any idea ?

---

