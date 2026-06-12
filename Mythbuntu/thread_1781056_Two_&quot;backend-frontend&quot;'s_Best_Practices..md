---
title: "Two &quot;backend-frontend&quot;'s Best Practices."
date: 2011-06-12
forum: Mythbuntu
---

### Post by gwar11d2 on 2011-06-12
Hi,
Been setting up mythbuntu the past couple of weeks and I just about have everything setup.

I've got a 'livingroom' Backend-Frontend and a 'office' backend-frontend.  Both have Hauppauge 1600's Dual-tuner (analog and HD).

For the most part things work fine.  BUT I was wondering today if there was a better way of doing this...especially in regards to being able to see stuff upstairs and downstairs so I setup the office system to connect to the livingroom IP under backend setup and told it that the livingroom as the master backend.

When I did that I lost control of the tuners on the office box and it appeared that it was just a tuner-less front end box...

So, I'm toying with the idea of setting up NFS mounts across my network and just have two independent Backend-Frontends, but I'm guessing this is an easier way to accomplish what I'm trying to do (and probably make better use of my storage across all systems).  

I've been through the wiki about 5-6 times now and I think I'm missing something.

---

### Post by klc5555 on 2011-06-13
Setting up the living room as master backend is fine. But from your description it would appear that while you've connected your office machine's frontend as a proper remote frontend, you've neglected to reconfigure your office machine's backend  as a correctly connected slave backend. Once the slave backend is correctly configured and connected, you'll be able to control all your tuners, your recording schedule, and your playback from either location.

---

### Post by gwar11d2 on 2011-06-13
Thanks.  I figured this is the case.  I'll have to spend some time today and figure it out.  Looks like under "Advanced Backend Configuration" [http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.12]("http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.12")  I need to remove all capture cards from the config except for one on the Slave and then do one at a time/ doing a mythfilldatabase inbetween each one...I think.

---

### Post by klc5555 on 2011-06-13
That's not what the document you cited is for. It describes only how to set up tuners in such a way that Mythtv's scheduler, when confronted with simultaneous recordings, will try to schedule a recording first on the master, then on the slave then the next slave ... etc. In order to prevent the usual scenario where the scheduler, when confronted with multiple simultaneous recordings, tries to schedule them all on the master's tuners, then, when they run out, on the first slave backend, etc. Since two or three or four simultaneous recordings going on on the master backend might lead to some recording corruption.

Your problem, as described, is more fundamental: you don't have a slave backend set up at all. For this, you need the following document: [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend) 

You will need to run sudo mythtv-setup (or go to the mythbuntu control center) on the machine you wish to become the slave backend. You will need to configure the General configuration page, in particular what the manual refers to as "Host Address Backend Setup" so as to connect this future slave backend properly to the master backend. All references to 127.0.0.1 or local host on the slave backend setup must be replaced with the ip of the master backend. 

You will add configure/tuners from the mythtv-setup running on this slave backend, but notice that the Video Sources used on the master are available to all the mythtv backends, and if they happen to be suitable for the slave tuners, you may use these same Video Sources on the slave backend when setting up the Input Connections on the slave tuners.

The first time you run the newly set up slave backend, the tuners on this backend will show up in mythtv's "System Information" as "unavailable". The mythbackend will have to be restarted on the master backend, then mythbackend will have to be restarted on the slave, and then all tuners should show up and be available to the scheduler. Whenever multiple-machine mythtv networks are restarted, the master backend must be running first, then the slaves (however many there are) can connect to it in no particular order.

---

