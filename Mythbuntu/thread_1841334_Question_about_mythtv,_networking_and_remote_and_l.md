---
title: "Question about mythtv, networking and remote and local frontends."
date: 2011-09-09
forum: Mythbuntu
---

### Post by chipsugar on 2011-09-09
I'm hoping you can help me out.

I've been running mythbuntu for years now with and local frontend and am quite knowledgeable about linux however I know very little about networking.

I'm now interested in having access from more than one machine. I could try to set up my router to give me a static ip but I won't be using the remote frontends that often and would rather not depend on having the router connected all the time just to get the local frontend to work.

Thanks

---

### Post by klc5555 on 2011-09-09
By "the router" I understand you mean the ethernet device that connects your whole network of machines to each other and to the internet. I'll also assume that your remote frontends are to be attached by ethernet, since a wireless access point would be its own router anyway.

If you don't want this internet router to run all the time, the following method should work: first set up the router to reserve a specific address for your mythtv backend (which you should be already having it do) and also reserve an address for each of the remote frontends that may be connecting to this backend.

On each of the backend and frontend machines, Network Manager should be edited so that each machine is using an actual static IP; make these static IPs the same ones that you reserved for these machines in the router. You will need to fill in the correct netmask for your network (probably 255.255.255.0) and the gateway address (the router's address for when it happens to be online and the myth machines will connect to the internet. The router's address will also likely be what you use for your DNS server on the DNS page of the network settings. A reasonable illustrated tutorial for these sorts of Network Mangler operations is here: [http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html) 

Now the thing is, when your main internet router is turned off, a frontend will still have to be connected to the backend in order to function. Just a straight ethernet cable between the two won't work, as the output from the one machine ends up being the mirror image of what the input to the other machine needs to be. 15 years ago one might have used a specialized "crossover cable" to network two machines without intermediation. But nowadays a simple fast-ethernet or gigabit ethernet switch (not router [because there's no address translation going on], not hub [because a hub can't normally do full duplex]) would sit between these two machines.

A four port fast-ethernet or gigabit-ethernet switch can cost as little as $18-$20 from someplace like Amazon. The uplink from this switch would connect to one of the ports of your router. The Mythtv backend and frontend machines would be connected to the ports of the switch. When the main internet router is offline, the backend and frontends can still talk to one another because their ethernet switch is still powered up and they are all set up on self-sufficient static IPs. When the internet  router is, in fact online, the switch gets treated as just an extra four connection ports on the router --it's transparent.

---

### Post by chipsugar on 2011-09-10
I'll explain what I need a little bit clearer. I've several computers connected to the same router but there is no internet connection. The router also isn't going to be on all the time (possibly just when the remote frontend is on) and I don't want the local backend/frontend connection to depend on external routers/switches/devices anyway.

If MythTV's backend allowed connection from a variety of ip's that would be a lot easier but it seems to just allows one.

---

### Post by klc5555 on 2011-09-10
> **chipsugar said:**
> I'll explain what I need a little bit clearer. I've several computers connected to the same router but there is no internet connection. The router also isn't going to be on all the time (possibly just when the remote frontend is on) and I don't want the local backend/frontend connection to depend on external routers/switches/devices anyway.

If MythTV's backend allowed connection from a variety of ip's that would be a lot easier but it seems to just allows one.

If you have a backend and a frontend on separate machines, their connection to one another will necessarily depend on a "router/switch/device" unless you wire them directly together with an old-fashioned crossover ethernet cable and set the two machines up on static IPs.

---

### Post by chipsugar on 2011-09-10
I think my terminology may be a bit out.

By "local backend/frontend" I meant the backend/frontend on the same machine that will be on all the time. I want this to be a self contained setup that doesn't rely on any external access points/routers to work.

By "remote frontend" I meant a laptop that will connect via wi-fi to the router which will be turned on only when it is needed (ie only when we want to watch mythtv on the laptop).

The MythTV backend setup only seems to allow connection via one ip (i.e. 127.0.0.1 meaning the localhost frontend will work but no network connections OR a static ip which means remote connections work but an external box is needed).

Thanks for your help so far.

---

### Post by klc5555 on 2011-09-10
Ah. This turns out to be much simpler than what you seemed to be describing.

Your backend is set for localhost -- 127.0.0.1 This will need to be changed in the backend setup General menu to your backend machine's actual IP address, in the two places on that page where 127.0.0.1 occurs. This will of course need to be a static IP. If your backend machine has not been configured for a static IP thus far, now will be the time you need to do it. You may wish to use whatever address your router has currently assigned you as your static IP, which is fine. You'll then need to go into your router's setup and permanently reserve that IP address for your backend machine, so that the router doesn't later reassign that address to some other computer and neither one can connect because of IP address conflict.

One method for finding the current IP address(es), the netmask, and the hardware (MAC) address of the network devices on your backend machine is from a terminal to type: sudo ifconfig

In the backend setup General menu you will also need to set the backend access Pin number to 0000. And, most easily from the Mythbuntu Control Centre (unless you really like mucking around in MySQL configuration files) set the MySQL service to accept remote connections. The backend should be now be ready to accept any number of local and/or remote frontend connections. The mythtv manual briefly overviews the necessary settings here: [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend)


Your local frontend may still be able to connect without incident (it's still trying for localhost 127.0.0.1). But if it can't, on the frontend's configuration screen, the 127.0.0.1 will need to be changed to the real IP that you just set the backend to. As mentioned here: [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend#Database_Configuration_1.2F2](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend#Database_Configuration_1.2F2)

Any remote frontend on your network should be able to connect to your backend by configuring mythfrontend on that remote frontend machine with the backend's IP, the database name (mythconverg), the user (mythtv) and the MySQL password on the backend, which will be found in the mysql.txt file in the .mythtv directory in your main users account on the backend machine.

And that's all there is to it.

---

