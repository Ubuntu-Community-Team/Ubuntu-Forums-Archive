---
title: "Tuner problem with bttv chipset"
date: 2008-07-25
forum: Multimedia Software
---

### Post by lindanux on 2008-07-25
Hello:

I have a Avermedia TV card with a bttv878 chip on it. About the tuner, I'm not sure, but I think it is a Phillips for NTSC (type=2). I allready readed almost all tutos in the web and didn't find out how to solve my problem. Ubuntu recognizes the card perfetly and load bttv modules (bttv and tuner) correctly. When I see in TvTime or XawTV or whatever program I only see channels 60 to 66 but it should start at 3 and end on 87. I tried all different combinations of the command:

```
modprobe bttv card=XX; tuner=XX; pll=XX
```

And nothing seems to work. What I find strange is that whatever cardnumer I assign to the card parameter, I always see channels 60 to 66 (I thought that with wrong cardnumber I should see nothing). I also tried to edit the xml channel file of TvTime, but I'm pretty sure, that the solution does not go in this direction.

¿Anyone with this problem? If someone needs some info about my system I would be glad to share it.

Thanks

PS: I have Ubuntu 8.04 on a PIV computer. Kernel version 2.6.24-19

---

### Post by cariboo on 2008-07-25
Is there any content in the lower channels, I beleive the programs scan for tv signals on all channels and then drop the channels that they find no signal on. One other thing to check, in /etc/tvtime/tvtime.xml that you have the frequencies set eg:

```
 <option name="Frequencies" value="us-cable"/>
```

This works for me even though I live in Canada.

---

### Post by lindanux on 2008-07-28
Yeah, I checked this out and it's configured in this way. 
Over the internet I found one guy asking for the same question, but he got no answer. Please help!

---

### Post by lindanux on 2008-08-03
So, nobody knows?
I've been searching around and it may be a ubuntu bug, on mandriva it seems to work well and better documented. Please help, I don't want to change distro....

---

