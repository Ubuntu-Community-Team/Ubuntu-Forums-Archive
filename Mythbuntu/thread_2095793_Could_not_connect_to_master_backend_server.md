---
title: "Could not connect to master backend server"
date: 2012-12-18
forum: Mythbuntu
---

### Post by cjgump720 on 2012-12-18
I started with a post like this over in the Absolute Beginners section, and after some stumbling around I managed to solve some of my problems.  The one that remains is one I get whenever I try to configure my HDhomerun tuners in the backend setup.

I'm running a single machine with front and backend, Mythbuntu 12.04.  I can use Mythbuntu to watch videos, but whenever I try to configure the tuners I get a

> Could not connect to the master backend server.  Is it running? Is the IP address set for it in mythtv-setup correct?I set the machine and the HDHomerun up with static IPs on my network, and I'm able to use mythmote to communicate and control MythTV, so I know that the MythTV box is able to get some data through the network.  If I select "Watch TV" I get the "could not connect" error, and then an "All tuners are currently busy." message.  As soon as I delete the tuners from the backend setup, the "could not connect" error goes away in the frontend. 

I've tried manually entering the tuner IPs, as well as using the automatic settings in the backend.  When I use the HDHomerun config, I can see the tuners, and watch TV.

I have no idea what to try next.  Does anyone have a suggestion?

chris

---

### Post by NautiusMaximus on 2012-12-19
This rings a vague bell with me: I think I had some similar problems a while back.

I'm not sure I can be very helpful, but I seem to remember that there is more than one place where you need to specify IP addresses. Have you been through all the settings to make sure you've set the IP address everywhere you need to?

---

### Post by Erik-NA on 2012-12-20
Do you use 127.0.0.1 as the backend IP-adress?

I believe it can be related to mysql, which normally is configured to only listening on localhost. 

If you use the Static IP-adress, Mysql may reject the connetion attempt.

Try to use 127.0.0.1 in the backend generall and frontend config. 

If not, edit /etc/mysql/my.cnf and change the bind-address parameter to your static IP adress. And then restart mysql.

---

### Post by cjgump720 on 2012-12-21
Switching my IP addresses back to 127.0.0.1 seems to have worked.  I'm thinking that was the last piece of the puzzle.  

Just in case some finds this in a search in the future, using dynamic IPs on my network and 127.0.0.1 in the backend setup gave me the error, and using static IPs on my network and the static IP address in the backend setup also gave the error.  But going to static IPs on the network and 127.0.0.1 in the backend setup fixed the problem.

Thanks Erik!

---

