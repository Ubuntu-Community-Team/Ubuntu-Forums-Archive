---
title: "Transport endpoint is not connected"
date: 2009-12-31
forum: Multimedia Software
---

### Post by Jordanwb on 2009-12-31
I don't know what Gphoto2 is doing behind the scenes but when I copy an MP3 onto my Creative ZEN, the songs don't show up. I managed to get mtpfs to work with a udev rule but it won't work on 9.10 or 10.04. This is what I did on 9.04 that worked:

```
mkdir /media/Zen
chown -R jordanwb /media/Zen
chmod -R 0777 /media/Zen
echo "allow_user_other" >> /etc/fuse.conf
chmod 0744 /etc/fuse.conf
echo "mtpfs /media/Zen fuse allow_other,noauto,user 0 0" >> /etc/fstab
apt-get -y install mtpfs
echo "ATTR{idVendor}==\"041e\", ATTR{idProduct}==\"4157\", RUN=\"/usr/bin/sudo -u jordanwb /bin/mount /media/Zen\"" >> /etc/udev/rules.d/45-mtpfs.rules
```

I plug in my ZEN, gphoto2 mounts it (this did not happen on 9.04 when mtpfs worked), the udev rule runs, but when I go to /media/Zen on Nautilus it says "Unexpected error: Error opening file: Transport endpoint is not connected"

---

