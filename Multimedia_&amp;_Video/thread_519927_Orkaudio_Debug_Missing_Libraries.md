---
title: "Orkaudio Debug Missing Libraries"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by haden9 on 2007-08-07
Good afternoon everyone,

 I was wondering if there could be someone who could help me with this issue. I have been trying to configure an application called Orkaudio, which is a program the sniffs out packets and decodes them into .wav files for a high school project but here comes the problem.

root@voip:/# orkaudio debug
Unable to open file: /var/log/orkaudio/orkaudio.log

Unable to open file: /var/log/orkaudio/messages.log

Unable to open file: /var/log/orkaudio/tapelist.log

2007-08-07 20:06:32,665  INFO root:117 - 

OrkAudio service starting

2007-08-07 20:06:32,670  INFO root:93 - Loaded plugin: /usr/lib/orkaudio/plugins/librtpmixer.so
2007-08-07 20:06:32,672  INFO root:87 - Loaded plugin: /usr/lib/libvoip.so
2007-08-07 20:06:32,673  INFO immediateProcessing:53 - thread starting - queue size:10000
2007-08-07 20:06:32,673  INFO batchProcessing:129 - thread Th0 starting - queue size:20000
2007-08-07 20:06:32,675  INFO packet:835 - Initializing VoIP plugin
2007-08-07 20:06:33,082  INFO packet:753 - Available pcap devices:
2007-08-07 20:06:33,083  INFO packet:760 - * eth0 - 
2007-08-07 20:06:33,083  INFO packet:760 - * any - Pseudo-device that captures on all interfaces
2007-08-07 20:06:33,083  INFO packet:760 - * lo - 
2007-08-07 20:06:33,118  INFO packet:806 - Successfully opened default device:eth0 pcap handle:80d7a90
2007-08-07 20:06:33,120  INFO packet:617 - Start Capturing: pcap handle:80d7a90

It won't load those log files and when I look for them they are simply not there. Any ideas as to what debs I need to install to get them. Please help and thanks in advanced.

---

### Post by haden9 on 2007-08-10
I found my solution, all I had to do was to create the log directory in /var/log/ and label it orkaudio like this:


 # mkdir /var/log/orkaudio 

And it loaded fine now, thanks again!

---

