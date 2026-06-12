---
title: "Java Sound Audio Engine missing on server"
date: 2008-06-23
forum: Multimedia Software
---

### Post by hal9037 on 2008-06-23
Help me please.

I'm writing a streaming audio application in Java to run on a server edition of Ubuntu with no UI.

On my development machine (Hardy Heron with Desktop), running the following Java code:

Mixer.Info[] mixerInfo = AudioSystem.getMixerInfo();
for(int j=0;j<mixerInfo.length;j++)
{System.out.println(mixerInfo[j].getName());}

Outputs:
Intel [plughw:0,0]
Intel [plughw:0,1]
Java Sound Audio Engine
Port Intel [hw:0]

If I run it on the server which has sun java installed I get:
V8237 [plughw:0,0]
V8237 [plughw:0,1]
Port V8237 [hw:0]

I desperately need the Java Sound Audio Engine on this machine - I installed the latest jre - why is it not there?

This is driving me nuts - TIA.

---

