---
title: "iTouch Login Fails"
date: 2008-06-25
forum: Multimedia Software
---

### Post by mastermindg on 2008-06-25
I have jailbroken my iTouch using ZiPhone. Everything is working fine as it were on the iTouch itself. 

I am able to ssh into the iTouch fine. I have not changed the initial password. 

I am NOT able to login via ipod-touch-mount. It fails at the password prompt. The IP is correct, the same as if I ssh. Not sure why it is failing.

Anydbody have any ideas?

---

### Post by mastermindg on 2008-06-26
For some reason or other, which was not properly outputted from ipod-touch-mount, it would not mount. 

I, however, have found a more direct way of accomplishing the same thing (somewhat). After looking at the ipo-touch-mount script, it looks like it is supposed to output the firewireguid necessary to access the itunes library, which would be great if it worked in the first place.

I ended up mounting the itouch using this command:
```

sshfs root@itouch:/var/mobile/Media /media/itouch -o reconnect
```

I have to play with the options, but at this point I can transfer music to the library, so I've got the basics down.

To get the firewireguid run (with iTouch/iPhone plugged into usb):
```

lsusb -v | grep -i iSerial
```

The firewiregui is the first 16 characters of the Serial. There's some extra tutorials out there to simplify the process of transferring the firewireguid to the SysInfo file, google them.

At this point, I can open gtkpod (following some errors) and transfer music to my iTouch.

Wishlist:

Automatic login (passwordless login)
Transfer Photos (error regarding photo db)
Download photos from Safari :)

---

