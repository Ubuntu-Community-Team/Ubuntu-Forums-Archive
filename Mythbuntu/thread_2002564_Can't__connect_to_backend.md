---
title: "Can't  connect to backend"
date: 2012-06-12
forum: Mythbuntu
---

### Post by Salbono on 2012-06-12
I have spent some time trying to work this out. If I wipe the hard drive and do a new install of mythbuntu will the backend communication problem be resolved? It is frustrating that the front and back don't work together when the are installed at the same time on the same machine. What gives?

---

### Post by klc5555 on 2012-06-12
You haven't provided any information to go on. Such information might or might not include some or all of the following, or might include other things depending on where your debugging efforts get hung up. For instance:

Is this a new or an old installation? Has it ever worked? If it worked at one time and now fails, what was the last change made before it failed? What do the frontend/backend logs look like from around the time of the failure?

If this is a new installation, has the backend ever been set up? (As per chapter 3 of [http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index) ) If set up, is the backend actually running, so that the frontend can connect to it? If the backend has been set up, but won't run at boot, can it be started and run from a terminal with ```
sudo mythbackend
``` ? If it won't start, what does the end of mythbackend.log say? An incorrectly set up tuner or Video Source will prevent the backend from starting.

If the backend is correctly configured and actually running but the frontend can't connect to it, has the frontend been configured as per [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend) ? What errors to you get if you try to start the frontend in a terminal with ```
mythfrontend
``` Do you get error messages in the terminal along with the dreaded two-page frontend config screen? What do the errors say? 

These are the sorts of things to be looking for.

---

### Post by tgm4883 on 2012-06-12
> **Salbono said:**
> I have spent some time trying to work this out. If I wipe the hard drive and do a new install of mythbuntu will the backend communication problem be resolved? It is frustrating that the front and back don't work together when the are installed at the same time on the same machine. What gives?

Just a sec, let me grab my crystal ball.

---

### Post by Salbono on 2012-06-13
OMG!    What does it say??


Lol  Just kidding I know you don't have a crystal ball.

---

### Post by tgm4883 on 2012-06-13
> **Salbono said:**
> OMG!    What does it say??


Lol  Just kidding I know you don't have a crystal ball.

I'll assume that yes it will since it works correctly out of the box, but I don't know what you did nor why it isn't working now (and haven't seen any logs).

---

### Post by Salbono on 2012-06-13
Thanks
Ok another question. If I don't have the capture card set correctly, should the backend still start, and communicate with the frontend? Or does it error out on the database?

---

### Post by nickrout on 2012-06-13
I believe that the backend will not start without a capture card being defined (if you are just testing then you can define one of the "dummy" ones.

---

### Post by klc5555 on 2012-06-13
> **Salbono said:**
> Thanks
Ok another question. If I don't have the capture card set correctly, should the backend still start, and communicate with the frontend? Or does it error out on the database?

If the backend can open the card at all, then the backend should run even if the card's output is trash. If, however, the backend can't open a card because of incomplete or misconfiguration, then normally the backend will fail to start and error out. The problem should end up being echoed in the mythbackend.log, under /var/log/mythtv/ Misconfigurations can include things like the card being set up on the wrong /dev node, being set up as the wrong type of encoder, not having a valid Video Source bound to the tuner's Input Connection, or a range of others. 

Or, of course, MySQL might not have been set up properly to allow the mythtv account to login.

So confirm whether or not the backend's running. If not, check the log. If the backend can actually be started and run, then the rest of it becomes much easier.

---

