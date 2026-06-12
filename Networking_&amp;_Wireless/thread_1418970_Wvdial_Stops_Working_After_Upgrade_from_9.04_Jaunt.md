---
title: "Wvdial Stops Working After Upgrade from 9.04 Jaunty to 9.10 Karmic"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by DustStuff on 2010-03-01
**Background:** On a fully updated Ubuntu 9.04 system, I had successfully configured wvdial to connect using a USB modem ("Update" brand) with an ID of 067b:0611 (uses the pl2303 driver module). In considering an upgrade to Ubuntu 9.10, I tried a LiveCD and was unable to connect using wvdial. However, because I had made the CD a couple months before, I went ahead with the upgrade (via the internet; not a fresh install) in the hopes that it would end up working or I would be able to find a solution for it.

**The Problem:** The upgrade was a success as far as I could tell, but when I tried to connect to the internet with wvdial, I was not able to. I checked the wvdial.conf settings to make sure they were the same as before, added some new ones I thought it might need, unplugged the modem and replugged it, restarted my system, etc., but all to no avail. Whenever I would try to run wvdial to connect, I would get the following output:

```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","gpinternet"
AT+CGDCONT=1,"IP","gpinternet"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
~[7f]}#@!}!$} }<}!}$}&@}#}$@#}%}&_8^G}"}&} } } } }'}"}(}"63~~~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Mar  1 19:32:08 2010
--> Pid of pppd: 3321
```

So, it appears to have some sort of communication with the 'carrier' and possibly establish some sort of connection, but it stalls out with its starting of ppp, pppd, etc., rather than continuing on with its usual lines of some more 'gibberish', with an IP address and a couple DNS addresses thrown in. And a quick check with a browser confirms that there is no data being transferred back and forth. Now, to tell you the truth, I don't know that much about the inner workings of wvdial, so I don't really know what the problem is here, and why it won't work in 9.10. I did some searching in the forums here and on Google, entered *info wvdial* at the terminal, and tried a few extra lines in my wvdial.conf file, but nothing did the trick. So, I'm not sure if this is a bug in wvdial or in Ubuntu, or just a problem with settings somewhere.

**Note: **The following workaround solution is not recommended unless you are already quite sure about the settings that you need for your particular modem and internet provider. In my case, I was able to use my wvdial.conf file (which I knew had worked in 9.04) as a reference for the settings that I needed.

**Workaround Solution:** In my searches on this forum I ran across [this post]("http://ubuntuforums.org/showthread.php?t=1238954&highlight=pppd+terminal&page=2") (Post #19) by GeorgeVita on 14 Aug 2009, where he mentions how he figured out how to start pppd with one command in the terminal (in 9.10). After scanning the command, I thought it looked an awful lot like some of the settings I had been putting in my wvdial.conf file, so I thought I'd give it a shot, not really expecting it to work for what I needed it for. :) Of course, I first checked out the pppd command by entering *info pppd* in the terminal to make sure I had a bit of an idea of what all I was getting ready to tell my system to do. After correcting a typo or two, I changed the setting of the provider name to 'gpinternet' and ended up with the following revised command:

  	 	 	 	 	```
sudo pppd ttyUSB0 460800 nodetach defaultroute noipdefault noauth lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','gpinternet'" "OK" "atdt*99***1#" CONNECT' user web password web
 
```

In my case, this gave the following output (with x's representing numbers):

```
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
Remote message: TTP Com PPP - Password Verified OK
PAP authentication succeeded
Cannot determine ethernet address for proxy ARP
local  IP address xx.xxx.x.xxx
remote IP address xx.x.x.x
primary   DNS address xxx.xx.x.xxx
secondary DNS address xxx.xx.x.xxx
```

This was different than the output I used to get with wvdial, but when I went over to my browser (Firefox) the internet worked fine. I'm assuming my email client and other things will work okay as well, but have not tested them as of yet.

A final touch I did to make connecting a bit less 'painful' was to right-click on the panel (at the top of the default Ubuntu screen), and click on 'Add to Panel'. Then I selected 'Custom Application Launcher', chose 'Application in Terminal' for 'Type', gave the launcher a name, pasted in that 'horrifically' long command line above, gave a brief description in the 'comment' box, then pressed 'OK'. Voila! I now have a launcher on my panel that with a single-click will bring up a terminal screen where I enter my sudo password and it connects. Then when I want to disconnect I just go back to that terminal, press Ctrl+C, which promptly disconnects me and causes the terminal to vanish into thin air.

Now, I don't know enough about this stuff to know why this command worked and wvdial didn't, but if you know, feel free to post a reply. Or if you'd like to see what settings I had for wvdial that worked in 9.04 but not in 9.10, let me know. Or if you think it's worth checking to see if this should be posted as a bug in either wvdial or Ubuntu, you can mention that as well. The main thing is, I found something that worked, and I thought I'd put it out there for anyone else that might be having trouble with this.

---

### Post by DustStuff on 2010-03-02
**Update:** Well, the workaround solution I mentioned has some issues. Sometimes it just disconnects, especially if downloading continuously for awhile, as with torrents (an issue others have noted with ppp), and sometimes it will give a vague error that basically means my provider terminated the connection. So, at best, this is (barely) a half-solution. I've been going back and forth between trying to get this to work and trying to get wvdial to work, and thought I'd put some wvdial info here in case anyone has any ideas for me.

Here's the wvdial.conf that worked no problem in 9.04 (Jaunty):

  	 	 	 	 	```
[Dialer Defaults]
 Modem = /dev/ttyUSB0
 Init1 = ATZ
 Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
 Init3 = AT+CGDCONT=1,"IP","gpinternet"
 Phone = *99***1#
 ISDN = 0
 Username = blah
 Password = bleh
 Baud = 460800
 Stupid Mode = On

```

Here's the output I get when I try to run it in 9.10 (Karmic):

```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","gpinternet"
AT+CGDCONT=1,"IP","gpinternet"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
~[7f]}#@!}!}1} }<}!}$}&@}#}$@#}%}&_8^G}"}&} } } } }'}"}(}"05~~~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Mar  2 11:06:31 2010
--> Pid of pppd: 2350
```

As mentioned in my previous post, normally the output would continue on with a bunch more stuff and you'd be able to connect to the internet. But that last line is where it stops and there's no internet. The message logs simply report that pppd has been started. But when I can successfully run the workaround mentioned above, then the message logs go on to mention other lines beyond that, including IP addresses, DNS addresses, etc. So whatever is supposed to be happening after that last line above doesn't seem to be happening, and I'm not seeing an obvious error reported anywhere either.

If you have any ideas about how I can get wvdial to work with Karmic, I'd be glad to hear them, and can also provide more information if you need it and can tell me how to get it, etc. I'm interested to see if the connection will still drop when downloading if I'm using wvdial, since it didn't do that for me in 9.04.

All for now! :)

---

### Post by GeorgeVita on 2010-03-02
Hi **DustStuff**, can you test the following:

Boot without modem, issue:
```
sudo stop network-manager
sudo killall modem-manager
```
Then attach your modem and try wvdial.
Post output of '**uname -a**' and '**sudo cat /etc/ppp/peers/wvdial**'

Regards,
George

---

### Post by DustStuff on 2010-03-02
George, here's the results:

Background: Turned off connection, unplugged modem, did a restart.
Comment: The 'modem-manager' command you gave returned 'no such process' as I expected, since I had removed that earlier today to see if it was interfering with wvdial, etc.

Trying wvdial (*sudo wvdial* in the terminal, the way I normally do it and the way I did it in 9.04) gave the same behavior -- the only really different thing I see each time is that the number of the pppd pid is different. The other (possibly) interesting thing is that when I tried to do the commandline workaround (based on yours) for an internet connection, the message it gave was something like the device being locked by pid number xxxx, where the number was one less than the number on the last line of wvdial output. Not sure if that's helpful, or just expected.

Output of *uname -a*:
```
 Linux dustin-desktop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux
```Output of *sudo cat /etc/ppp/peers/wvdial*:
```

noauth 
name wvdial 
usepeerdns

```Comment: I had earlier tried various edits to the above file using some of the pppd setting names from your commandline, but wasn't able to find anything that made wvdial work.

Let me know if you'd like me to try anything else. Thanks!

---

### Post by GeorgeVita on 2010-03-02
Hi **DustStuff**, seems to be difficult to 'investigate'!

a. file /etc/ppp/peers/wvdial has the 'usual' contents

b. you can find any running process using '**ps**' command:
```
ps -A | grep ppp
ps -A | grep -i manager
ps -A | grep -i wvdial

``` and then 'sudo kill 1234' to remove unwanted processes (1234 is the PID# shown at ps)
**-i** makes search string NOT case sensitive (manager=Manager)

c. add 'debug' parameter to pppd commaaaand for more info while connecting
(sudo pppd ttyUSB0 460800 **debug** nodetach default...)

Regards,
George

---

