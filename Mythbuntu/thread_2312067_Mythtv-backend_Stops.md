---
title: "Mythtv-backend Stops"
date: 2016-02-01
forum: Mythbuntu
---

### Post by vdi_nenna on 2016-02-01
Hi,

This is my first post here.  New to Linux, but know my way around a network and computer.

Using latest Mythbuntu as a backend server for OpenELEC Kodi (15) on a RPi2 B and HomeRun Prime tuner.
The box is a 1.2Ghz AMD with 2Gb RAM and 32-bit Mythbuntu OS.  It's not good hardware, but it's just a test platform until I build a better HTPC.

When opening the HD HomeRun app in Mythbuntu, it appears to find channels and get 100% signal.  Can open channels in VLC.  This is good, I suppose.

Problem I'm having is an error pops up in Kodi saying **not connecting to Mythtv PVR** at the bottom right of the screen, and then error goes away.

In the MythTV setup, set the server to the IP of the Mythtv backend and in the HTTP access setting as well.

The MySQL service is running, but the MythTV-Backend service is **stop/waiting.**  I start it manually, but is shuts down immediately.
Don't know why this happens.  I thought maybe it runs only when it needs to do something, but after reading post on the net, it should be running and have a service ID.

In past versions of Kodi and XBMC, the SQL password needed to be set on the Kodi side, but Kodi 15 doesn't have this setting.
So maybe the problem is in the backend only?

I don't know how to get logs or find the ones I need.  Maybe logs are shown in the terminal?  Is there a command?
Any troubleshooting steps would be helpful. 

Able to ping MythTV server from OpenElec SSH and visa-versa.  Can ping HD HomeRun Prime from server and openelec.
Can SSH to the MythTV server as well.
 
Compliments on a very easy install.  Very straight forward.  I doubt I missed anything during installation, but it's possible.

Thanks,

Vince

---

### Post by khPWXxF on 2016-02-02
That hardware should be ok if you don't do commercial flagging!
The logs for MythTV are held in /var/log/mythtv/
try:
```
cd /var/log/mythtv/
less mythtvbackend.log
```

and scroll up/down.  Quit with Q


hth
Phil

---

### Post by vdi_nenna on 2016-02-19
Phil,

Thanks for the reply.  I sort of gave up on the old hardware and built an AMD A1 4-core 2Ghz machine with 1 Tb of storage.  Runs better and not many errors.  After first Mythbuntu updates, I got a could of errors, but things are running Ok and able to record shows and watch TV off HDHR Prime cablecard unit.

One weird thing that happened was somehow the front-end was installed and I don't remember installing it.  I mean it was running just the BE, then one day it had the FE too.

I'm not sure I like the way commercial flagging works.  Most of the time it cuts off the show before going to commercial and picks up a few commercials before starting the show.
Only channel it works almost flawlessly is on Fox.

I can't complain.  It's mostly doing what I need.  will figure out the rest as time passes.

Thanks,

Vince

---

### Post by vdi_nenna on 2016-02-19
BTW- the new hardware works equally well with SD and HD.  In fact, the HD color looks better than the HD FIOS box.

Also, only using 4Gb of RAM.

Front-end is RPi 2 B with Openelec and Kodi.  The menus freeze up a bit and at times have to boot it.
Otherwise it works well.

Hope this info helps someone else.

Vince

---

