---
title: "wicd won't remember hidden network name"
date: 2011-08-09
forum: Networking &amp; Wireless
---

### Post by jtwdyp on 2011-08-09
I've got a fairpoint communications supplied DSL modem/router set to use wpa2 with a preshared key, SSID broadcast off, and set to only accept connections from the one usb wireless adaptors mac address. It does work.

For more info on what I had to do to get it working please see:

[http://ubuntuforums.org/showthread.php?t=1807799](http://ubuntuforums.org/showthread.php?t=1807799)

What wicd isn't doing is to remember the SSTD after a reboot. At least not  in ubuntu (actualy installed as xubuntu but the desktop environment in use is E17) When I run Arch with the same wicd settings, it automatically & successfully connects if the usb wireless adapter is plugged in durring the boot process. But for some reason with ubuntu I have to wait till after I login. start the wicd user interface, click on network->"find a hidden network". manually enter the ssid, and finally click on connect...

When I first start the wicd gui the place where it should say something like: NetworkName  100%  WPA2  Channel 6

says instead:

\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00  85%  WPA2

What could cause this???

---

### Post by thefasterblueone on 2011-08-09
Try [this solution](http://kubuntuforums.net/forums/index.php?topic=3110265.new), it looks promising.

---

### Post by jtwdyp on 2011-08-10
> **thefasterblueone said:**
> Try [this solution](http://kubuntuforums.net/forums/index.php?topic=3110265.new), it looks promising.

I suppose I could experiment with that wicd script to see If I can get it to work for wlan1... if done this way im thinking I could put it in:
 /root/bin/wicd-auto-init
and source it in:
 /etc/rc.locsl
even though on my system X don't start till I run startx...

But as it is wicd comes up so close... the only part it doesn't remember is the ssid. Do I need the whole script? or just something to tell it the network name?

---

### Post by jtwdyp on 2011-08-12
OK so I tried adapting "wizard10000"'s wpa_supplicant script. 
(see [http://kubuntuforums.net/forums/index.php?topic=3110265](http://kubuntuforums.net/forums/index.php?topic=3110265) )
And after many tries it appeared to work except that the connection failed... At least with wicd all I had to do was:
Network->find hidden... enter the correct essid and click on a couple of connect buttons... 

This wouldn't be an issue if I didn't like the slight security advantage of hiding my ESSID. I mean at least wicd was able to auto-connect using wpa2-psk with AES encryption. (Just as long as I kept broadcasting my network name...) With network-manager, I couldn't even get wep working...

Thing is there isn't much point in hiding the ESSID if I'm going to make it simple to remember & type...{and therefore easy to guess.} So what I did was to use a long string of random mixed case characters. And it was a pain to manually open a file containing said string with something from which I could use the clipboard to paste the ESSID string into wicd's Network->find hidden... input box.

But since some more testing found an wicd-cli solution that {mostly} works, I guess I will be marking this thread solved...

Once I figured out a simple wicd-cli script that corrected the Essid and made the connection, I tried to source it in rc.local but for some reason even though it worked on the command line, when sourced from rc.local something said the listed network was invalid... So I moved the script to usr/local/bin, added test logic to ensure that neither the wired nor wireless interface was already up before "connecting", and called the script from my ~/.bash_profile. Which is close enough to the function of the buggy "automatically connect" option that I should have been able to use for me.

The /usr/local/bin/wicd.sh script contains:
```

#!/bin/bash
iSeth0uP=$(ifconfig eth0|grep "inet addr:")
if [ "$iSeth0uP" != "" ] 
then
	echo "eth0 appears to be up: ABORTing"
	exit 1
else
	iSwlan1uP=$(ifconfig wlan1|grep "inet addr:")
	if [ "$iSwlan1uP" != "" ]
	then
		echo "wlan1 appears to be up: ABORTing"
		exit 1
	else
		echo "ok wlan1 appears down as well... attempting to bring it up"
		# wicd-cli -y -n 0 -p Essid -s "HiddenNetworkName" -c
 		wicd-cli --wireless --network=0 --network-property=Essid --set-to="HiddenNetworkName" --connect
	fi

fi
exit 0


```

To those of you who tried to help I say "thanks!"

---

