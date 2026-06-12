---
title: "Issues with new build"
date: 2009-01-29
forum: Mythbuntu
---

### Post by rschapman on 2009-01-29
Last night I put together a new mythbox. The build went pretty well but there are some issues I want to try and resolve. 
[B]
HDHomerun[/B]: I configured the HDHomerun in the backend and scanned for channels. However when I go to the frontend and select the tuner the screen goes blank and eventually just kicks me back to the menu page. I've read the documentation on the wiki and followed it with no success. I've tested the tuners with VLC and they are working fine. Any suggestions or ideas? Does anyone have a good guide for setting up and using the HDHomerun?

**RAM**: I put 4GB of RAM in the box but the system only recognizes it as 2.2. Now I'm using an integrated nvidia 9400 chip that's taking part of it but certainly not 1.8 GB. Any ideas? Do I need to go 64bit?
[B]
HD Playback[/B]: When watching HD content from my cable box one of the cores will peg out at a full 100%. I put a Intel Core 2 8400 3.0Ghz processor in there and that seems a little much to me. Should I expect this or do I need to do something else. My playback profile is set at CPU+ should I lower that? I would expect that with that kind of processor it shouldn't be a problem. 

Thanks for the help.

---

### Post by movieman on 2009-01-29
> **rschapman said:**
> I put 4GB of RAM in the box but the system only recognizes it as 2.2. Now I'm using an integrated nvidia 9400 chip that's taking part of it but certainly not 1.8 GB. Any ideas? Do I need to go 64bit?

All kinds of things will affect how much memory is visible below 4GB, and a non-PAE 32-bit kernel can't see anything above that address. If you have 4GB of RAM I'd definitely install a 64-bit OS; all of my Linux machines run 64-bit and now that 64-bit Flash is available there's no good reason not to.

---

### Post by rschapman on 2009-01-29
Well I will try going that route tonight after work. I had considered it but hadn't really done the homework to know if I would run into any trouble or not. I'm assuming that I won't have any troubles with nvidia drivers either right?

---

### Post by movieman on 2009-01-29
> **rschapman said:**
> I'm assuming that I won't have any troubles with nvidia drivers either right?

Not that I'm aware of; this machine is 64-bit with an Nvidia card and fairly recent drivers (I don't run MythTV on it though).

---

### Post by rschapman on 2009-01-29
Okay that sounds good. Now I just need to figure out why it's pegging the cpu so hard and why I can't get the HDhomerun to display now. Any thoughts?

---

### Post by rschapman on 2009-01-29
I have tried without success to use the HDHomerun. I have a Hauppauge 150, a Firewire connection to the cable box, and an HDHomerun. I want to use them all. When I add he HDHomerun it can't tune a station. Do I need to configure my box to change what channel the HDHR listens on or does it do it automatically? Any help would be great. Thanks.

---

### Post by joho500 on 2009-01-30
HDHomerun problem:
Check your backend log. Look for "ivtv driver not responding". If that is the problem you can solve it by installing the latest driver. There is a post on this subject in the forum.

Cheers,
Joost

---

### Post by rschapman on 2009-01-30
Thanks for the reply. I'll check it out. Thanks. Another question. When setting up the HDHomerun for digital cable what is the best method for setting it up to work with the guide data from schedules direct? When I scan for channels is messes up my data. Do I just leave it as it is and use the digital cable lineup from Scheduels Direct or something else?

---

### Post by rschapman on 2009-01-30
When I ran the log grabber for to see what happened when I use the hdhomerun this is what I got.
```


2009-01-30 18:19:56.819 Finished recording Shop Latino Network: channel 1880
2009-01-30 18:19:58.119 AFD Error: Could not find codec parameters. file was "/var/lib/mythtv/recordings/1910_20090130181929.mpg".
2009-01-30 18:20:02.381 Couldn't open decoder for: /var/lib/mythtv/recordings/1910_20090130181929.mpg
2009-01-30 18:20:02.382 NVP, Error: Could not open file for preview.
2009-01-30 18:20:02.383 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1910_20090130181929.mpg'
2009-01-30 18:20:01.912 Finished recording Shop Latino Network: channel 1880
2009-01-30 18:20:02.388 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/1910_20090130181929.mpg.png) exists: 0 readable: 0 size: 0
```

is this is ivtv issue you mentioned? Thanks. The link to the rest of the log is below.

[http://mythbuntu.pastebin.com/f14c192d7](http://mythbuntu.pastebin.com/f14c192d7)

---

### Post by rschapman on 2009-01-31
What I don't understand is the log comment about decoding. Does the IVTV stuff have anything to do with that. I've made sure that I was on a clearQAM channel.

---

### Post by joho500 on 2009-02-01
Looking at your logs I don't think your problem has to do with the ivtv driver. I'm no expert but I see two things that don't look OK. Your backend seems to miss a codec for playing mpg files. And it looks like your frontend can't connect to your backend. Something with the IP-address. Do you get a message when you exit the frontend or when starting Live TV?

Joost

---

