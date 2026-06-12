---
title: "Albuquerque, Comcast, Hauppauge 1600, qam help?"
date: 2009-05-30
forum: Multimedia Software
---

### Post by damoek on 2009-05-30
I've been working on getting a 100% functional mythtv box for some time now, but have been running into a few issues. Namely I can't get the QAM channels from comcast albuquerque to be tunable inside the mythfrontend. 

I followed the guide over here [http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_(For_ATSC/QAM_Tuner_Cards_--_USA/Canada)]("http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_(For_ATSC/QAM_Tuner_Cards_--_USA/Canada)") 

and was able to create this channels.conf file

```
[0641]:375012500:QAM_256:94:95:1601
[0644]:375012500:QAM_256:91:92:1604
[0642]:375012500:QAM_256:98:99:1602
[0515]:375012500:QAM_256:100:104:1301
[0643]:375012500:QAM_256:0:106:1603
[0005]:573000000:QAM_256:49:52:5
[0008]:573000000:QAM_256:16:17:8
[0002]:573000000:QAM_256:80:81:2
[0007]:573000000:QAM_256:400:401:7
[000d]:573000000:QAM_256:1360:1320:13
[000f]:573000000:QAM_256:241:244:15
[0046]:585000000:QAM_256:0:74:70
[0048]:585000000:QAM_256:0:72:72
[004c]:585000000:QAM_256:0:85:76
[004a]:585000000:QAM_256:0:67:74
[0049]:585000000:QAM_256:0:79:73
[0051]:585000000:QAM_256:0:83:81
[0050]:585000000:QAM_256:0:90:80
[004d]:585000000:QAM_256:0:77:77
[0007]:585000000:QAM_256:0:97:7
[0009]:111025000:QAM_256:162:163:9
[0019]:111025000:QAM_256:173:174:25
[001e]:111025000:QAM_256:165:168:30
[0005]:111025000:QAM_256:170:171:5
[001c]:111025000:QAM_256:176:177:28
[001d]:111025000:QAM_256:179:180:29
[0006]:111025000:QAM_256:187:188:6
[000f]:111025000:QAM_256:193:194:15
[000e]:111025000:QAM_256:190:191:14
[000d]:111025000:QAM_256:184:185:13
[0008]:111025000:QAM_256:196:197:8
[0011]:111025000:QAM_256:201:202:17
[0012]:111025000:QAM_256:204:205:18
[0015]:111025000:QAM_256:207:208:21
[0007]:111025000:QAM_256:210:211:7
[0010]:111025000:QAM_256:213:216:16
[0014]:111025000:QAM_256:218:219:20
[0017]:111025000:QAM_256:224:225:23
[0018]:111025000:QAM_256:227:228:24
[002d]:111025000:QAM_256:221:222:45
[0030]:111025000:QAM_256:232:233:48
[001b]:111025000:QAM_256:238:239:27
[001f]:111025000:QAM_256:235:236:31
[001a]:111025000:QAM_256:249:250:26
[0020]:111025000:QAM_256:244:245:32
[0024]:111025000:QAM_256:255:256:36
[0025]:111025000:QAM_256:241:242:37
[0023]:111025000:QAM_256:252:253:35
[0021]:111025000:QAM_256:258:259:33
[002e]:111025000:QAM_256:261:264:46
[0028]:111025000:QAM_256:275:276:40
[000a]:111025000:QAM_256:266:267:10
[0029]:111025000:QAM_256:269:270:41
[0026]:111025000:QAM_256:272:273:38
[002c]:111025000:QAM_256:280:281:44
[002b]:111025000:QAM_256:283:284:43
[0033]:111025000:QAM_256:0:286:51
[002f]:111025000:QAM_256:288:289:47
[0004]:111025000:QAM_256:0:291:4
[0031]:111025000:QAM_256:293:296:49
[0032]:111025000:QAM_256:298:299:50
[0003]:111025000:QAM_256:0:301:3
[0016]:111025000:QAM_256:303:304:22
[0013]:111025000:QAM_256:309:312:19
[000c]:111025000:QAM_256:306:307:12
[0027]:111025000:QAM_256:323:324:39
[000b]:111025000:QAM_256:314:315:11
[002a]:111025000:QAM_256:317:318:42
[0022]:111025000:QAM_256:320:321:34
```

however when I try and import this channels.conf file It only adds two channels and neither are tunable. When I use the built in channel scanner and use the ATSC antenna i find all of the OTA channels.

I've got the guide working, I've got the remote working, and I've got the analog cable channels working, this is the farthest that I've ever come with a MYTHtv install and i'm damn proud, and actually wouldn't mind giving in and just using the antenna but I'm wondering wtf i'm missing with the QAM. I know the channels aren't encrypted because my lcdtv tunes them just fine...
If anyone can point me in the right direction i would sure appreciate it.

---

### Post by damoek on 2009-06-05
Am i looking to do something that is impossible? Does comcast send qam signals in the clear? Is my TV tuner just catching the OTA dtv channels and using my cable line as an atsc tuner?

---

