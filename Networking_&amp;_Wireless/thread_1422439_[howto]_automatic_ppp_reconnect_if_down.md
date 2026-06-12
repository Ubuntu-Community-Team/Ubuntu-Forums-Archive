---
title: "[howto] automatic ppp reconnect if down"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by Pauligrinder on 2010-03-05
Hey there.

I didn't find a solution to making my 3G/GPRS "modem" reconnect automatically when the connection fails, so I made a solution of my own. It's very annoying when you're downloading a file overnight, only to find that the connection has failed 5 min after you went to sleep. 
Restarting the NetworkManager daemon makes it automatically connect to all configured interfaces, including 3G/GPRS, so I made a simple script to do that.

First, we check if the modem is even connected. Replace Huawei with the brand you're using. Any unique word on the line in lsusb will do fine as well. 
Then we check if the connection is up, and if it is, we simply exit. Otherwise, the NM daemon is restarted, which causes the 3g/gprs to reconnect. Simple as that :)

```
#!/bin/bash

MCHECK=`lsusb | grep Huawei`

if ! [ -n "$MCHECK" ]; then
echo "3G/GPRS modem not in use, ignoring..."
exit 0
fi

NCHECK=`ifconfig ppp`
NCHECK1=`echo $NCHECK | cut -d " " -f 1`

if [ "$NCHECK1" = "ppp0" ]; then
echo "Connection up, reconnect not required..."
exit 0
else
echo "Connection down, reconnecting..."
/etc/init.d/NetworkManager restart
fi

```

Save the file, and then
```
sudo chmod a+x /path/to/script
```
(I'm not really sure what the a in the chmod does, apparently +x would be enough. Some people instruct to use a+x and some +x, I haven't checked myself [and to be honest I don't give a rats ***...])

Then, I made a cronjob to make it check once an hour, which should be enough. (I figured once a minute would be a waste of resources.)

```
sudo crontab -e
```
(Using sudo, because a normal user isn't allowed to restart the daemon.)
then add
```
0 * * * * /path/to/script
```
save the file, exit the editor (simply crtl+x, y to choose yes and then enter to save the file in nano), and that's it :) 
Feel free to correct me if something's not right, I'm not a super scripting-guru or anything :)
Might also be a good idea not to restart everything, only the ppp. (ifconfig doesn't seem to be able to do that, because it doesn't show ppp0 when not connected...)
EDIT:
Can someone help me find what I'm doing wrong here? The script works just fine when I execute it manually, but the cronjob _always_ restarts the NM once an hour :I What's wrong here?

---

### Post by Pauligrinder on 2010-03-05
> **Pauligrinder said:**
> the cronjob _always_ restarts the NM once an hour :I What's wrong here?

I'm starting to feel like this is a bug in cron! anyone else having similiar problems?

---

### Post by Pauligrinder on 2010-03-05
Sorry for bumping this thread again, but now it seems I've found a better solution for this :)

```

sudo nano /etc/NetworkManager/dispatcher.d/3G

```

and paste this :

```

#!/bin/bash

MCHECK=`lsusb | grep Huawei`

if [ $1 == "ppp0" ] && [ $2 == "down" ] && [ -n MCHECK ]; then
/etc/init.d/NetworkManager restart
fi

```

then

```
chmod +x /etc/NetworkManager/dispatcher.d/3G
```

Now, what this does:

It checks if ppp0 is down, and a line which contains Huawei exists in lsusb. If this is true, then NetworManager restarts -> 3G reconnects! :)

---

