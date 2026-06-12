---
title: "Secrets to getting your video card or USB to reset, reload drivers"
date: 2012-07-14
forum: Multimedia Software
---

### Post by fixitdude on 2012-07-14
I was getting tired of un-plugging and re-plugging the USB TV tuner and found that resetting it works just the same. This may or may not work on your card or device but you can try it.

You need to know the driver it uses, look with "dmesg" and find out what it's name is. Mine is called "au0828", so as root I do this:

```

/sbin/modprobe -r au0828
/sbin/modprobe au0828

```

Now go look at dmesg, it shows the same thing as if I did a re-plug.

To get more advanced, I wanted to do this as a normal user, so I wrote this little script and put it in /root and created a cron job that starts it every minute.

```

#! /bin/sh

# started every minute by cron
# then every 10 seconds we check to see if the reset file exists
# if it does we do the reset and then remove the file
# we only do this till the minute is up and cron starts another one
# I checked this and it checks at exactly 50 seconds but then sits for 10

for i in 1 2 3 4 5 6
do
echo "check" $i

if [ -f /home/USERNAME/reset-au0828.txt ]
then
echo "reset file exists, resetting USB au0828"
killall mencoder
killall atsc_epg
sleep 5
/sbin/modprobe -r au0828
/sbin/modprobe au0828
rm -f /home/USERNAME/reset-au0828.txt
break
fi
sleep 10

done


```

The cron line looks like this:
* * * * * /root/cron-tv-check-reset-usb.sh >/dev/null 2>&1

Now if I do this in a terminal as the normal user "USERNAME":

echo "lala" > /home/USERNAME/reset-au0828.txt

It will reset it within about 10 seconds. (I also have it kill any running TV access programs just in case, you can take that out)

This is also great for a script, like my "tivo" or "mythtv" like script below. By creating that file I can reset the TV stick if I detect it isn't recording a show.

[http://ubuntuforums.org/showthread.php?t=2009778](http://ubuntuforums.org/showthread.php?t=2009778)

---

### Post by OM55 on 2012-07-14
In case of a USB device, you can also try:

```
sudo usb_modeswitch -R -v <usb device code> -p <usb product code>
```for example, for a Prolific USB-Serial adapter, you can do:

```
sudo usb_modeswitch -R -v 067b -p 2303
```However, I noticed that it doesn't always work as expected.

---

