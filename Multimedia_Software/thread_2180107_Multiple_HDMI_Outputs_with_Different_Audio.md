---
title: "Multiple HDMI Outputs with Different Audio"
date: 2013-10-11
forum: Multimedia Software
---

### Post by Ethan_Goldstein on 2013-10-11
I'm currently attempting to build an HTPC that can feed multiple TVs in different rooms, so that each can show something different simultaneously.  I found a really spiffy looking Mini-ITX motherboard that has two HDMI ports:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128567](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128567)

And was wondering if this could work.  Getting two different video files to play from a computer's two HDMI ports is easy; what I was wondering is how I could make it so the audio isn't pooled between the two HDMI ports, which is the case in a traditional multiple-monitor style setup.  Since HDMI carries audio this should be doable, but I have no idea how.  If I launch two instances of streaming programs, is there something I can type so each HDMI port's audio is dedicated to that instance?  Thanks!

---

### Post by gravysteak on 2013-10-12
Here are the specs from realtek

> 
[LIST]
[*]Primary 16/20/24-bit SPDIF-OUT supports 32k/44.1k/48k/88.2k/96k/192kHz sample rate
[*]Secondary 16/20/24-bit SPDIF-OUT supports 32k/44.1k/48k/88.2k/96k/192kHz sample rate
[*]16/20/24-bit SPDIF-IN supports 44.1k/48k/96k/192kHz sample rate
[/LIST]


So it looks like you are out of luck. There are only 2 channels. One for the spdif connector and one for the hdmi.

But I can't seem to find any info on wether those 2 channels can be used independantly so even if you were to use the spdif connector with an extra cable or splice it into the hdmi I'm not shure it would work.

---

### Post by Sinixstar on 2013-10-13
> **gravysteak said:**
> Here are the specs from realtek



So it looks like you are out of luck. There are only 2 channels. One for the spdif connector and one for the hdmi.

But I can't seem to find any info on wether those 2 channels can be used independantly so even if you were to use the spdif connector with an extra cable or splice it into the hdmi I'm not shure it would work.

It's kinda tough to find onboard hardware with multiple independent output channels. 
Your best bet would probably be external cards like this : [http://www.newegg.com/Product/Product.aspx?Item=N82E16815136006](http://www.newegg.com/Product/Product.aspx?Item=N82E16815136006)

---

