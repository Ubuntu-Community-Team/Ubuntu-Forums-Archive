---
title: "D-Link DSB-C120 Webcam"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by schweini on 2008-02-27
I just wanted to reiterate that the D-Link DSB-C120 webcam, which seems to be a popular and cheap model at least in latin america (a lot of Brazilian results on google?), isn't working AT ALL with linux, and thus ubuntu. What i found weird is that i couldn't even find any mention of an experimental driver on the 'net. Anybody know anthing more than i do regarding this?

dmesg & /var/log/messages just report a plugged in USB device, and nothing more. no /dev/video* thus no xawtv or anyhting else.

Thanks,

M.

---

### Post by linuxwizard on 2008-02-27
Post results of the command > lsusb

---

### Post by scriptfighter on 2008-02-28
This should be interesting.

I have a D-Link CSB-C100, not the same, but similar, perhaps same driver to be used ?

My lsusb spits:

```

Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 05a9:a511 OmniVision Technologies, Inc. OV511+ WebCam
Bus 004 Device 002: ID 0764:0501 Cyber Power System, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 0458:0003 KYE Systems Corp. (Mouse Systems) Genius NetScroll+
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by schweini on 2008-02-28
my lsusb output:

```
Bus 001 Device 004: ID 2001:f115 D-Link Corp. [hex]

```

besides, is there anyway to actually see which sensor is being used, so that i could contact the maintainer of a similar webcam?

---

### Post by linuxwizard on 2008-02-28
schweini
I can not find anything on your webcam, which driver you may need. Looked everywhere I can think of. Seen other D-Link models but not yours. Try using Ekiga see if the cam works/detected. I would not count on it but worth a try. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.

---

### Post by scriptfighter on 2008-03-04
Strangely,

after a reboot the webcam is recognized but the Skype test mode shows a black square only :( 

Still digging.

---

### Post by linuxwizard on 2008-03-04
Hello scriptfighter
I didn't realize that you were asking for help in your first post. What do you need help with ?

---

### Post by scriptfighter on 2008-03-04
Hi,

my problem was the same as "schweini". However, now the webcam is recognized, I think I installed some drivers, cannot remeber which tool I used to do that, I found it on some post. So that is step forward, now in Skype test I get a black screen / square, so it is obviously not working, however I saw some posts about this around here, so I'm gonna try those before I bug you again.

Thanks.

---

### Post by linuxwizard on 2008-03-04
I don't use Skype so I don't know much about its configurations. Look over these there maybe something that will help, notes & troubleshooting

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

