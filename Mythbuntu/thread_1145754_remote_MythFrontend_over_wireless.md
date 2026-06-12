---
title: "remote MythFrontend over wireless"
date: 2009-05-01
forum: Mythbuntu
---

### Post by dotnick on 2009-05-01
Most threads I find talk about bandwidth issues with mythfrontend over a wireless network, but I never see a post where the setup is talked about.

I have most everything working, except that my wireless card is not activated until after the X session is going.  And because it takes a few seconds for it to proceed through the protocols and connect, the automatic instance of mythfrontend does not find the backend because the wireless card is not ready.

If someone has done a second frontend over wireless where one of the wireless wrappers is used, I'd love to see the script you've used to get everything working.

I would be interested in 1. waiting for the network connection to come up, 2. sending a 'wakeonlan' packet over the network followed by another pause, and 3. starting mythfrontend

---

### Post by ian dobson on 2009-05-02
Hi,

Couldn't you just write a small script that delays the start of X until you can ping another computer, something like:-

```

loop
  sleep 5
until  ping backend OK
sleep 5
startX

```

If I get the time today I'll sit down and see if I can write a real script for this.

Are you using a fixed IP address or DHCP for your frontend?


Regards
Ian Dobson

---

### Post by dotnick on 2009-05-02
The wireless is DHCP.  I also believe that the network connection takes place during the Xsession.  I lose my ssh session when I restart the Xserver on that computer and regain it once the automatic login is initiated.  I'm not too familiar with the ndiswrapper? or whichever method is used for the wireless.  It's a belkin 802.11b/g card which is a couple of years old at this point.

If there is a way to enable the wireless card outside of the Xsession so that root had the instance instead of user, that would also be helpful I think.

Maybe the loop script would work if it was added to by .bashrc file to check for the backend and then start the frontend once detected?

---

### Post by ian dobson on 2009-05-02
Hi,

If thats the case then just write a script that:-

1) Reads the backend IP address from mysql.txt
2) Try ping the backend until you get an answer
3) Start the frontend

Note the script  /usr/bin/mythfrontend actually starts the frontend binary.

Regards
Ian Dobson

---

### Post by ian dobson on 2009-05-02
Hi,

I've banged a small script together that waits unit the backend is pingable. Here it is:-

```

#!/bin/sh
Backend=`cat /etc/mythtv/mysql.txt | grep DBHostName | sed 's/DBHostName=//'`
Answer=""
until [ "$Answer" = "5" ]; do
  Answer=`ping $Backend -c 5 | grep received | awk '{print $4 }'`
done

```

Just add the code to /usr/bin/mythfrontend just before frontend.real is called. 
What the script does is:-
1) Read the IP address from the backend
2) Cleanup the line read so that only the IP address is left
3) Sit in a loop trying to ping the backend until it can be pinged 5 times out of 5 attempts.

Regards
Ian Dobson

---

### Post by williammanda on 2009-05-02
> **dotnick said:**
> Most threads I find talk about bandwidth issues with mythfrontend over a wireless network, but I never see a post where the setup is talked about.

I have most everything working, except that my wireless card is not activated until after the X session is going.  And because it takes a few seconds for it to proceed through the protocols and connect, the automatic instance of mythfrontend does not find the backend because the wireless card is not ready.

If someone has done a second frontend over wireless where one of the wireless wrappers is used, I'd love to see the script you've used to get everything working.

I would be interested in 1. waiting for the network connection to come up, 2. sending a 'wakeonlan' packet over the network followed by another pause, and 3. starting mythfrontend

Can you watch HDTV over your wireless setup?

---

### Post by dotnick on 2009-05-02
My HD is a little jumpy, but the SD is fine.  This is a rather old pc too.  1.8 GHz celeron with a geforce 3 graphics card.  Even with a local copy of HD content, there's a little jumpiness in the video playback.

The HD, though, is noticebly worse when streamed than it is local.  My signal level seems to be near 90% when visually guaging the XFCE network manager signal bar.

---

### Post by dotnick on 2009-05-04
This method works fairly well.  I added your script section to the mythfrontend in a couple of different places, so that every if statement had that code piece plus the wakeonlan command.  I am curious though.  The backend starts to wake up and as soon as the network interface on the backend is in place, the script continues regardless is the mythbackend server is up or not.  Is there another call that would check for mythbackend being up?  Maybe a parsed mythtv-status (though the output seems to change based on the build of mythtv).

The reason I ask, is that even though the 2nd MythFrontend waited to run until the backend network connection was up and running, Mythbackend did not have enough time to start and so the 2nd MythFrontend went to the blue screen about not finding a uPnP device.  Is that something that is easily checked for?  Maybe a loop until a uPnP device is found instead of the ping?

---

### Post by ian dobson on 2009-05-04
Hi,

If you want to wait for the myth backend software to be up and running, maybe you could ue nc (netcat) to attempt to get the status page from mythtv. If the backend isn't running then NC will timeout and return no data.

Give me afew days and I'll have a look at it.

Regards
Ian Dobson

---

### Post by ian dobson on 2009-05-05
Hi,

maybe this will do it for you

```

#!/bin/sh

BackendStatus=0
Backend=`cat /etc/mythtv/mysql.txt | grep DBHostName | sed 's/DBHostName=//'`  #Get backend IP address

until [ "$BackendStatus" > "5" ]; do 
  BackendStatus=´echo GET /   | nc -w 10 $Backend 6544 | wc -l | awk '{print $1}'`#Try and grab XML status page
done

echo Status from backend $BackendStatus

```

This code is tolally untested, I've written it off the top of my head. When I get home I'll try it out on my system.

Regards
Ian Dobson

---

### Post by TheHolm on 2009-05-05
> **dotnick said:**
> Most threads I find talk about bandwidth issues with mythfrontend over a wireless network, but I never see a post where the setup is talked about.

I have most everything working, except that my wireless card is not activated until after the X session is going.  And because it takes a few seconds for it to proceed through the protocols and connect, the automatic instance of mythfrontend does not find the backend because the wireless card is not ready.


Fist, start your network before X kick in. Do not use DHCP. /etc/network/interfaces is way to go. 
It still not guaranty that you will have network at moment when you FrontEnd starts.

---

### Post by dotnick on 2009-05-05
I realize now that I may have been unclear about my network setup.  My backend is has a static IP and has a ethernet connection.  My remote frontend is DHCP over 802.11g.  The remote frontend, I believe, is not capable of being static because the Linksys router I have only does DHCP wireless clients.

ian dobson:  Thank you. I will try this tonight.

---

### Post by ian dobson on 2009-05-05
Hi,

The top of my head isn't a perfect programmer. Here's a working version of the code

```

#!/bin/sh

BS="0"
Backend=`cat /etc/mythtv/mysql.txt | grep DBHostName | sed 's/DBHostName=//'`  #Get backend IP address
until [ "$BS" != "0" ]; do
 BS=`echo -e "GET / HTTP/1.1\n\r" | nc -w 5  $Backend 6544 | wc -l` 
 sleep 5
done

echo Status from backend $BS

```

Now to get back to my screwed up munin plugin for md devices.

Regards
Ian Dobson

---

### Post by dotnick on 2009-05-05
This works fantastically.  Thank you so much.

FYI.  I added :

/usr/bin/wakeonlan xx:xx:xx:xx:xx:xx

to the loop so that if the first packet didn't take, it would try again.  Though, this would probably only need to be called once at the beginning of the script.

---

### Post by dotnick on 2009-05-06
does anyone know if this type of functionality is going to be included in either mythbuntu-control-centre or the mythtv 0.22 setup options?  I would think this type of setup to be activated by a checkbox (for a second or third frontend) would be rather useful.  Just my 2 cents.

---

### Post by nickrout on 2009-05-06
this would be completely fixed if mythbuntu wasn't so stupid as to only start networking on login to X. Using /etc/network/interfaces so it all starts up on boot would be so much better.

Surely ubuntu server edition must start networking on boot, as often there wouldn't ever be an X login, and a server without a network interface would be a door stop. Can't the mythbuntu guys take a leaf from that book?

---

### Post by dotnick on 2009-05-06
I believe, for whatever reason, this is only the case for wireless connections, not wired.  My backend is a wired connection and I'm quite certain networking comes up long before X is started.

Is it possible that the wireless connections cannot be started simply because it hasn't yet been told which access point to connect to?  There is a possibility of having several wireless access points, I can see 2 (mine and my neighbors).  The utility 'remembers' which access point I prefer, which may be why wlan connections aren't established before X, as the utility is a gui application and requires X to run.  (I know I use a lot of hypotheticals, mostly because I don't know, nor do I really care to, the progression of things).

If it were possible for the utility to make the changes to /etc/network/interfaces in a usable format for wlan connections, that would be preferrable, but the network utility doesn't require sudo or root privelages to change connections, so it doesn't automatically have write privelages to that file.

I'm not entirely sure it's mythbuntu's fault.

---

### Post by nickrout on 2009-05-06
rethinking this it is possibly because the wep/wpa key is stored in the logged in users settings, ie it is a per user setting. Therefore wireless doesn't get started until $USER logs in.

Be that as it may, it is possible to set up wep or wpa to run from boot via /etc/netweork/interfaces. If you want it to run properly from boot, that is the best solution. 

Its unlikely that a frontend will ever be using more than one AP, so the slight lack of flexibility in not using network manager is probably not significant.

---

### Post by ian dobson on 2009-05-07
Hi,

It should be possible to get a wlan up and running without X, you just need to edit /etc/netword/interfaces and add 

```

iface eth2 inet dhcp
  pre-up ifconfig eth2 up
  pre-up iwconfig eth2 essid whatever
  pre-up iwconfig eth2 channel 11
  pre-up iwpriv eth2 set AuthMode=WPAPSK
  pre-up iwpriv eth2 set EncrypType=TKIP
  pre-up iwpriv eth2 set WPAPSK='password!'

```

ethX, essid channel and AuthMode/EncrypType need to be changed to match you network. 

I also hate network manager, all my boxes have a fixed IP address and use the /etc/network configuration options, so much cleaner.

Regards
Ian Dobson

---

