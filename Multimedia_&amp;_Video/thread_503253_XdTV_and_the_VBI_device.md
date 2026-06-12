---
title: "XdTV and the VBI device"
date: 2007-07-17
forum: Multimedia &amp; Video
---

### Post by gray-squirrel on 2007-07-17
I have a Pinnacle PCTV HD Pro television tuner, and currently I'm trying to get a couple of programs, especially XdTV, to do a channel scan.  I'm using this to watch analog cable ([FONT="Courier New"]us-cable-hrc[/FONT]).

The reason the channel scan fails is because the computer claims to be unable to open the VBI device.

So far, I have been able to do the following:

```
sudo mknod /dev/vbi0 c 81 224
sudo chmod 666 /dev/vbi0
ln -s /dev/vbi0 /dev/vbi
```


I've tried this in Edgy, rebooted, and XdTV was not able to open the device.  When I upgraded to Feisty recently (for reasons unrelated to this matter), I lost the VBI device for some reason, so I recreated it, and even after rebooting XdTV still can not get access to the device.

Interestingly, there is this as a result of [FONT="Courier New"]dmesg | tail[/FONT]:

```
squirrel@kubuntu:~ $ dmesg | tail
[51027.696000] ANALOG TV REQUEST
[51030.920000] ANALOG TV REQUEST
[51031.556000] ANALOG TV REQUEST
[51032.124000] ANALOG TV REQUEST
[51032.748000] ANALOG TV REQUEST
[51033.364000] ANALOG TV REQUEST
[51034.036000] ANALOG TV REQUEST
[51077.032000] ANALOG TV REQUEST
[57989.844000] em28xx-video.c: there's a reader but that's not us!
[57989.844000] em28xx-video.c: there's a reader but that's not us!
```


The VBI feature works fine in Windows (when the TV tuner is working, that is).  A few minutes ago I suspected there might be a permissions issue, but I don't know what group [FONT="Courier New"]/dev/vbi[/FONT] is supposed to be in.  I do know that running XdTV as root in Edgy gave me the same complaint about not being able to open the VBI device.

Please let me know if there is anything else I should check out.  Thanks.

---

