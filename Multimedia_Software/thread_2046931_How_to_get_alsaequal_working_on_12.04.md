---
title: "How to get alsaequal working on 12.04"
date: 2012-08-23
forum: Multimedia Software
---

### Post by aless3466 on 2012-08-23
Hello! I upgraded my computer from 10.10 to 12.04 and after this I'm having trouble with alsaequal. I can't get alsaequal to work, Not matter what config I use on '.asoundrc' , the alsaequal do not have any effect on my audio.

Actually, I'm trying to use the same '.asoundrc' that worked on my 10.10, it looks like this:

> pcm.plugequal{
 type equal
 slave.pcm "plug:dmix"
}

ctl.equal{
 type equal
}
pcm.equal{
 type plug
 slave.pcm "plug:dmix"
}
pcm.!default {
 type plug
 slave.pcm "plugequal"
}

I tried to install alsaequal through the 'libasound2-plugin-equal' and compiling from source but the result is the same, I tried to use the configuration found on the website of alsaequal, but not worked.

My actual system is made of Ubuntu 12.04 x86_64 built from the mini.iso running on ECS A785GM-AD3 motherboard with Realtek ALC888 sound card. It looks strange because on Ubuntu 10.10 it worked like a charm.

Anybody have some idea of what i'm doing wrong?

---

