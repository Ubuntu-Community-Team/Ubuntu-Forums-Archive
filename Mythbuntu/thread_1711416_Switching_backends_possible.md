---
title: "Switching backends possible?"
date: 2011-03-21
forum: Mythbuntu
---

### Post by bcg30506 on 2011-03-21
I hope this makes sense, but here is what I'd like to be able to do and have no idea if I can or if so, how.

I have a travel netbook with mythbuntu frontend only installed to use on trips.  I've set it up to use an ssh tunnel to reach my home backend which seems to work well, as long as I have a network connection.

My problem was this past weekend we were cut off my any type of signal so I had no network connection of any kind while on the road.  However, I did have some mythtv recordings I had copied from my backend to the netbook before traveling just in case I couldn't get on a network.  However, when I try to start mythfrontend on the netbook to try and watch the local mpg files via mythvideo, the frontend exits with a failure to start due to not finding the backend.

So it seems I'd have to setup and start a backend on the netbook for this case.  Fine, except if I do have a network signal somewhere, I'd like it to use my home's mythbackend and not the local one on the netbook itself.

Is there any way to accomplish this without too much headache?  Is there any additional info I need to provide?

---

### Post by klc5555 on 2011-03-21
It's not clear why you'd want to use mythtv at all in this case. 

For the mythtv files copied locally onto your netbook, mplayer, vlc, xine or whatever can just play them directly. No additional stuff or configuring at all. This has got to be simpler than installing/configuring a dummy backend on the netbook just for the purpose of using mythvideo when you have no networking access.

---

### Post by bcg30506 on 2011-03-21
Hi, and thanks for the reply.

There are 2 reasons for doing this in my case:

1. vlc crashes part way through the files for some reason which I do not have the time or know how to figure out why, so the alternative is mplayer which plays them fine, and is what I did this weekend, but requires command line which is not wife-friendly.

2. We use it as a "portable" TV in cabins that have no TV for catching up on stuff or watching a show while going to sleep.  So, with mythfrontend I can control the system with my ipod touch using network control (which rocks btw!), and I can make use of the sleep timer in mythtv to have the machine sleep after a given time, similar to what you might do in a hotel room with the TV timer.

---

### Post by LowSky on 2011-03-22
Make the netbook a secondary backend. it can be done from mythbuntu control center. copy the files over and copy the database too so the files are readable.

Open the backend on the netbook. go to general, setup the local backend IP, the machine's normal IP... then setup the master backends IP.. go to third page and check the box for master backend override.

that should do it.

---

### Post by klc5555 on 2011-03-22
> **bcg30506 said:**
> Hi, and thanks for the reply.

There are 2 reasons for doing this in my case:

1. vlc crashes part way through the files for some reason which I do not have the time or know how to figure out why, so the alternative is mplayer which plays them fine, and is what I did this weekend, but requires command line which is not wife-friendly.

2. We use it as a "portable" TV in cabins that have no TV for catching up on stuff or watching a show while going to sleep.  So, with mythfrontend I can control the system with my ipod touch using network control (which rocks btw!), and I can make use of the sleep timer in mythtv to have the machine sleep after a given time, similar to what you might do in a hotel room with the TV timer.

If LowSky's recommendation works for you, then it will address both 1. and 2., and you're set.

If it doesn't, then while I have nothing additional to recommend for 2., you may eliminate the command line for mplayer by installing an interface/skins for it. Then run it point-and-click from the multimedia menu like any other player app. Likewise with an installation of Xine/gxine.

---

### Post by bcg30506 on 2011-03-22
Okay, I think I was making it too complex, realizing this while trying to setup the secondary backend.  I figured out I don't need a slave, but rather, EITHER the netbook OR my home backend will be the master, depending on whether or not the ssh tunnel is started or not.

The problem I ran into trying to setup a slave backend on the netbook was I am using ssh tunnels to reroute the mythtv ports from home to localhost on the netbook so I don't have to expose the home backend to the world through my router.  So the IP address for both ends up being the same.  Also, with the backend running locally, the tunnels fail to create.

So, here is my solution that seems to work in my initial testing:

1. Installed mysql-server, mythtv-database, and mythtv-backend on the netbook and setup the backend as a master with no capture cards and a video storage directory to my user's videos folder.

2. Created a BASH script and an application launcher icon for it to run as a frontend-only to my home backend.
```
#!/bin/bash
sudo service mythtv-backend stop
sudo service mysql stop
# att is in /etc/hosts as my home's static IP from my ISP
xterm -title Close_me_after_Myth -e "ssh -CN -L 6543:localhost:6543 att" &
xterm -title Close_me_after_Myth -e "ssh -CN -L 3306:localhost:3306 att" &
echo Press ENTER when tunnels are ready.
read junk
mythfrontend --service
sudo service mysql start
sudo service mythtv-backend start
```
3. If I want to run it with no network connection as a dummy combined FE/BE to watch videos with myth's UI, I run the frontend with the default app icon in Sound/Video menu instead of my script launcher.

So is it optimal?  I don't know, but it works for my case.  Thanks for all the advice that pointed me in the right direction.  I hope these steps may help someone else with a similar need.

---

