---
title: "Anyone get a Hauppauge HVR-900 working?"
date: 2010-05-18
forum: Mythbuntu
---

### Post by asprinwizard on 2010-05-18
Hi there,

I have installed Mythbuntu 10.04. I'm planning on using it as a media center with XBMC as the interface. However first I need to setup the myth TV backend. I have a Hauppauge HVR-900 usb stick. It's an analogue and digital card and I know Hauppauge installation is not exactly seemless with MythTV.

I am having problems setting it up. I have setup two capture cards - one analog and one DVB. The analogue scan works but finds no channels. I have tried with EIT and Radio Times downloaded listings but it makes no difference. I have set location to europe-west as that is the nearest available location. I'm in the UK so assume that is ok. With DVB I get the message 'failed to open card' so can't even get to the channel scan.

I would really appreciate anyone's experiences with this card or one from the same family, Has anyone got this card working? I have trawled through various posts and am still none the wiser. I'm not a Linux noob but I'm not far beyond that. It's like a second language that I'm learning. If this card does not work with MythTV it's not the end of the world but it would be helpful to know so I can stop wasting hour after hour trying to find a way top get it going! Also any recommendations for a replacement with similar spec (must be usb) would be helpful.

Thanks in advance.

---

### Post by gdbutcher on 2010-06-03
Does it say HVR-900 H on the USB stick itself?

If so it is not supported, just made this mistake myself. The box says HVR-900 (which is supported) but the device states that it is HVR-900 H (which isn't). If you can, take it back, it doesn't work with linux.

See this page for confirmation:

[http://www.hauppauge.com/site/support/linux.html]("http://www.hauppauge.com/site/support/linux.html")

---

### Post by bods on 2010-10-16
Sadly this happened to me this morning.  Thought it was a 900, got a 900H.  Ho hum.  i'm sure we'll get support one day but for the meantime I guess I'll need to use Windows.

---

### Post by smaug42 on 2010-10-23
The 900H does work in Linux... you need a 2.6.35 or higher kernel, load the tm6000 kernel module (modprobe tm6000), and copy xc3028L-v36.fw (search for/download it from the net) into /lib/firmware.

See here: [http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices/Full]("http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices/Full") last entry in the table.

---

### Post by marmiteOlz on 2011-02-27
sorry for dragging up an old post but i read the linuxtv.org list and it says the 900h is supported
i got one today for my daughters pc..
i copied the above firmware  like is said   but how do i load the tm6000 kernel module?

i have ubuntu 10.10  64bit... does the 64bit hurt  at all?

---

### Post by smaug42 on 2011-03-28
Assuming everything is in place, you would open a Terminal and type:

```
sudo modprobe tm6000
```

---

