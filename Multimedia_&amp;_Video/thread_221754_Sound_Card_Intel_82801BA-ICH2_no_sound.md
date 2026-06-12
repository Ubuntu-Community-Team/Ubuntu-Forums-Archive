---
title: "Sound Card Intel 82801BA-ICH2 no sound"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by SadaraX on 2006-07-24
I just installed Dapper Kubuntu and I cannot get any sound to work. In KDE, it the program 'kmix' reports the the built in soundcard on the motherboard as "Intel 82801BA-ICH2". 

I have tried a couple of different cards, including a Sound Blaster Live 5.1 (which shows up in kmix as SB Live 5.1). However no sound comes out of the system. I have verified that the sound cards do actually function (tested them in windows), so they work. I just don't have any audio output. 

I know this card does work under Linux. I tested it under Mepis 3.4 live-boot and it played just fine. Can someone help me? I really want to get audio working on my system...

---

### Post by wieman01 on 2006-07-24
I think sound is disabled by default in Dapper... it's really silly and a lot of people fall into the same trap over and over again. So did I.

You need to fire up "alsamixer" in a terminal and "unmute" the sound. I am not in front of my Linux machine so I cannot guide you through it. But it's fairly simple, just search for it in this forum.

The sound card itself should be fine. It's just this annoying step that you have to do.

---

### Post by dgrafix on 2006-09-11
Ive got the same problem, did that, but still no sound. It seems to be working as im not getting any problems with sound hardware messages.

Just cant hear anythuing

---

### Post by TwoWordz on 2006-10-20
I've just put together a computer from spare parts I had around. 

My audio wasn't working on the back panel because the motherboard was a pull from another case which had front audio connectors. 

It was missing the jumpers on the connector which was preventing the sound from being routed to the back plane. 

see intel [article]("http://support.intel.com/support/motherboards/desktop/d850emv2/sb/cs-010586.htm")

I hope it helps some of you.

TW

---

