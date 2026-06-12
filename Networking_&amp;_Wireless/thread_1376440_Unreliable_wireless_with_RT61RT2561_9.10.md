---
title: "Unreliable wireless with RT61/RT2561 9.10"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by ushills on 2010-01-09
Karmic 9.10 seems to have real stability issues with RT61/RT2561 wireless cards.  9.04 was really stable but for some reason 9.10 has poor signal strength and frequently drops the connection.

Has the driver changed with 9.10?

I am willing to test and bug report but I have had to downgrade to 9.04 to use PC.

---

### Post by popaclay on 2010-01-12
> **ushills said:**
> Karmic 9.10 seems to have real stability issues with RT61/RT2561 wireless cards.  9.04 was really stable but for some reason 9.10 has poor signal strength and frequently drops the connection.

Has the driver changed with 9.10?

I am willing to test and bug report but I have had to downgrade to 9.04 to use PC.



I am having the same problem. I am running other distros with no issues (Lenny - sidux).

---

### Post by XanTrax on 2010-01-13
I'm having the same problem...I just wrote this for now.  Its not the best thing to do but its a band-aid until a real fix comes along.


```

#!/bin/bash

sleep 1 && ifconfig wlan0 down
if [ $? -ne 0 ]; then
	exit 100
fi
sleep 1 && dhclient -r wlan0
if [ $? -ne 0 ]; then
	exit 200
fi
sleep 1 && ifconfig wlan0 up
if [ $? -ne 0 ]; then
	exit 300
fi
sleep 1 && iwconfig wlan0 essid "Kozler_wireless"
if [ $? -ne 0 ]; then
	exit 400
fi
sleep 1 && iwconfig wlan0 mode Managed
if [ $? -ne 0 ]; then
	exit 500
fi
sleep 1 && dhclient wlan0
if [ $? -ne 0 ]; then
	exit 600
fi

sleep 1

exit 0

```

Just execute that and it will restart the network from releasing the DCHP lease and renewing it.  I wrote a second part to work as a cronjob and check the network connection every minute and to execute the above script when it was down.

```

#!/bin/bash

date=`date +%Y-%m-%d`
time=`date +%r`
netstamp="[network.log][ $date | $time ]"
appstamp="[application.log][ $date | $time ]"
netlog="/root/applogs/netchecker/network.log"
applog="/root/applogs/netchecker/application.log"

get_assoc=`iwconfig wlan0 | grep -i "access point" | cut -d ':' -f4 | cut -d ' ' -f2`

#assoc=`iwconfig wlan0 | grep -i "access point"`


if [ $get_assoc == "Not-Associated" ]; then
	echo $netstamp "The network is down" >> $netlog
	echo $appstamp "Executing network restart" >> $applog
	retval=`/usr/local/bin/netrestart`
	if [ $? -eq 0 ];
	then
		echo $appstamp "Network restart successful" >> $applog
		#echo $netstamp "Network association post restart: $get_assoc" >> $netlog
	else
		if [ $? -eq 100 ];
		then
			echo $appstamp "Failed at stage 1" >> $applog
		fi
		if [ $? -eq 200 ]; then
			echo $appstamp "Failed at stage 2" >> $applog
		fi
		if [ $? -eq 300 ]; then
			echo $appstamp "Failed at stage 3" >> $applog
		fi
		if [ $? -eq 400 ]; then
			echo $appstamp "Failed at stage 4" >> $applog
		fi
		if [ $? -eq 500 ]; then
			echo $appstamp "Failed at stage 5" >> $applog
		fi
	fi
#else
#	echo $netstamp "The network is up (Association=$get_assoc)" >> $netlog
#	echo $netstamp "Assoc var = $assoc" >> $netlog
fi

```

And in the crontab:

```

*       *       *       *       *       test -x /usr/local/bin/netcheck && ( sudo /usr/local/bin/netcheck )

```

Like I said, its not the best thing because the signal still really sucks but at least I can keep a (somewhat) steady connection now.

---

### Post by popaclay on 2010-02-07
Well, I tried different things, but no luck.  I upgraded to lucid, and wireless is working like a charm.
cheers

---

### Post by iClouseau88 on 2010-02-07
I found the Ralink driver to be unstable, difficult to install and difficult to maintain a steady connection.  When you first installed the Ralink driver, did you download the source file from Ralink's web site, compile and build it, or was it automatically installed for you (plug and play)from Ubuntu?

---

### Post by jackwhite on 2010-03-03
> **popaclay said:**
> Well, I tried different things, but no luck.  I upgraded to lucid, and wireless is working like a charm.
cheers

Is it possible to somehow just upgrade the drivers so that you get the benefit from Lucid for this but don't risk your noob *** in an aplha release?

---

### Post by popaclay on 2010-03-14
> **jackwhite said:**
> Is it possible to somehow just upgrade the drivers so that you get the benefit from Lucid for this but don't risk your noob *** in an aplha release?

well, the card has gone back to acting up.  so recent updates may have resulted in the unstable operation.

---

### Post by jackwhite on 2010-03-18
hmm, thats interesting but obviously unfortunate. I was hoping to update and that that would solve my problems...

---

