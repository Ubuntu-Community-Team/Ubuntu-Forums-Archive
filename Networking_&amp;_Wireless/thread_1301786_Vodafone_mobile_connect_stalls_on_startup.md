---
title: "Vodafone mobile connect stalls on startup"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by Sandertje on 2009-10-26
Hello,

Since I don't have a regular internet connection, I'm bount to use an USB modem. I'm using Vodafone Mobile Connect, and I succesfully installed the drivers for this. It worked for a few weeks, but now the application just stalls on startup. I'm getting the startup screen, but the program doesnt progress any further. The only thing working is the "cancel" button ;-)

So I tried
```
vodafone-mobile-connect-card-driver-for-linux-debug
```

It gives me this output:

```
sander@sander-laptop:~$ vodafone-mobile-connect-card-driver-for-linux-debug
get_plugin_by_vendor_product_id called with 0x19D2 and 0x0055
data port is /dev/ttyUSB1
ctrl port is /dev/ttyUSB3
Efective user id: 1000
2009-10-26 18:36:15+0100 [-] Log opened.
2009-10-26 18:36:15+0100 [-] twistd 8.2.0 (/usr/bin/python 2.6.2) starting up.
2009-10-26 18:36:15+0100 [-] reactor class: twisted.internet.gtk2reactor.Gtk2Reactor.
2009-10-26 18:36:18+0100 [-] AT+CGMM response: []
2009-10-26 18:36:18+0100 [-] Unhandled error in Deferred:
2009-10-26 18:36:18+0100 [-] Unhandled Error
	Traceback (most recent call last):
	Failure: twisted.internet.defer.FirstError: FirstError[#0, [Failure instance: Traceback: <type 'exceptions.AssertionError'>: Modem didn't reply anything meaningful
	/usr/lib/python2.6/threading.py:497:__bootstrap
	/usr/lib/python2.6/threading.py:525:__bootstrap_inner
	/usr/lib/python2.6/threading.py:477:run
	--- <exception caught here> ---
	/usr/lib/python2.6/dist-packages/twisted/python/threadpool.py:210:_worker
	/usr/lib/python2.6/dist-packages/twisted/python/context.py:59:callWithContext
	/usr/lib/python2.6/dist-packages/twisted/python/context.py:37:callWithContext
	/usr/share/vodafone-mobile-connect/vmc/common/hardware/base.py:87:_identify_device
	]]
	
2009-10-26 18:36:56+0100 [-] Shutting down...
2009-10-26 18:36:58+0100 [-] Unhandled error in Deferred:
2009-10-26 18:36:58+0100 [-] Unhandled Error
	Traceback (most recent call last):
	  File "/usr/lib/python2.6/threading.py", line 497, in __bootstrap
	    self.__bootstrap_inner()
	  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
	    self.run()
	  File "/usr/lib/python2.6/threading.py", line 477, in run
	    self.__target(*self.__args, **self.__kwargs)
	--- <exception caught here> ---
	  File "/usr/lib/python2.6/dist-packages/twisted/python/threadpool.py", line 210, in _worker
	    result = context.call(ctx, function, *args, **kwargs)
	  File "/usr/lib/python2.6/dist-packages/twisted/python/context.py", line 59, in callWithContext
	    return self.currentContext().callWithContext(ctx, func, *args, **kw)
	  File "/usr/lib/python2.6/dist-packages/twisted/python/context.py", line 37, in callWithContext
	    return func(*args,**kw)
	  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/base.py", line 87, in _identify_device
	    assert len(response), "Modem didn't reply anything meaningful"
	exceptions.AssertionError: Modem didn't reply anything meaningful
	
2009-10-26 18:36:58+0100 [-] Server Shut Down.

```

(those last bits are *after* I pressed the "cancel" button)

So, any ideas how to fix this? 
Thanks :-)

---

### Post by pdc on 2009-10-27
here is the help forum

[http://www.betavine.net/bvportal/forums/index.html?forumId=51](http://www.betavine.net/bvportal/forums/index.html?forumId=51)

 ofthose whose have developed, and maintain, the VMC software; 

they are freely available and can help you; 

what about talking to them? .. join their community ...

why don't you tell us the results if they can help you?

---

### Post by Sandertje on 2009-11-15
I never got any answer to my question from the vodafone people, but the solution to this is really silly. It's actually a "I didn't safely remove devices"-problem. I still use windows besides Ubuntu, amd when shutting down windows or it crashes, the vodafone dongle isnt removed as it should. After reboot, Ubuntu can't recognize it. So, apparent solution: go back to windows and click the "Safely remove devices"-button. Seems I was just being stupid :P

---

### Post by pdc on 2009-11-15
maybe not;

maybe windows was switching it back to being seen as a zeroCD device; and not as a USB modem;

if you type 

> lsusb

when it is working in linux; and note the vendor ID: product ID numbers;

and if by chance windows crashes;

and you again do

> lsusb you *may* get a different product ID (vendor ID should stay the same)

---

### Post by John Read on 2009-11-16
Assuming you have installed your Vodaphone (Australia) wireless broadband modem via the Network Manager and are able to get it to "connect" but are still unable to actually connect to any Web sites, etc. then chances are you still have one small step to go. Right-click the Network Manager icon, choose Edit Connections, click the Mobile Broadband tab, click your Vodaphone service (e.g. Vodafone Postpaid), click the Edit button on the right, leave Number set to *99#, set the Username to vodafone, set the password to vodafone, leave APN set to vfinternet, and click the Apply button. You will be asked if it's OK to store some keys on a keyring, choose "At any time" (or somesuch), then you're set.

I find the connection speed I can achieve in Ubuntu 9.10 is several times faster than I could achieve in Ubuntu 9.04 which is just great.

The only hassle I have is that Ubuntu boots so fast that the modem does not have time to find the Vodafone connection and then it won't appear in the Network Manager list. You then have to cold boot again and hope for better luck next time.

Hope this helps.

Regards,

John

---

### Post by ibates on 2010-02-08
I am running the latest updated Karmic and have a similar problem with Vodafone Mobile Connect (Betavine).

The program seems to install OK - all components are installed exactly as described on the Betavine for Ubuntu pages.

The appplication shows in Accessories->Internet OK, but selecting the app results in the system (and HDD) running for about ten seconds then nothing.  No error message, no dialogue box, no Betavine screen, just the blank desktop screen.

Any suggestions as to what is going on and how to overcome it?

I am using an ACER Aspire 5310 laptop, almost new, all bells and whistles, running Ubuntu 9.10 only.

---

### Post by alexfish on 2010-02-08
hi

I have never been a fan of this software , for the very reasons been listed on these threads, also the lack of support and help from Betavine:

you could have a look here

[http://www.pcurtis.com/ubuntu-mobile.htm#vmc](http://www.pcurtis.com/ubuntu-mobile.htm#vmc)

if you are just wanting to Monitor what is happen etc ,you could install  pppstatus

having looked at the pppstatus.cfg  { config file} you should be able to monitor costs and check user emails

---

### Post by ibates on 2010-02-09
Further to my post above, installing the latest version of VMC solved that problem.  At least I can now get VMC loaded and running.  Still unable to connect, but with Ubuntu, it is always one very slow step then the next very slow step.

The latest version is available at this site:

[https://forge.betavine.net/frs/download.php/583/vodafone-mobile-connect_2.15.01-2_all.deb](https://forge.betavine.net/frs/download.php/583/vodafone-mobile-connect_2.15.01-2_all.deb)

The update will download and install as soon as you select it.  If you want to take a peek first, use this link

[https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12)

(I installed this over the older version simply because I can find no way to uninstall any program/app unless it was completely installed from the Ubuntu Software Centre or the Synaptic repo.  Perhaps someone can straighten me out on that one as well).

---

