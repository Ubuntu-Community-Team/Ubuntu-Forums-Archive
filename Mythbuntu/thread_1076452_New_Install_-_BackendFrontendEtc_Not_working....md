---
title: "New Install - Backend/Frontend/Etc? Not working..."
date: 2009-02-21
forum: Mythbuntu
---

### Post by fudnet on 2009-02-21
Greetings fellow Mythbuntu'ers-

I'm returning to the world of MythTV after putting it down for a couple of years. I've just installed fresh server as a 'Primary Backend' as selected from the Mythbuntu installation disc. My understanding is that now I can install multiple 'Frontend' machines and have them connect to the backend server for scheduling, content, etc. Correct?

Assuming yes, I've tried this. When prompted for the MySQL database information, the frontend unit is able to connect with no problems. However, after getting the frontend unit installed and running MythTV, I'm constantly 'greeted' with errors about not being able to connect to the backend. The log files show that the mythfrontend instance is connecting to the database on the backend server but *STILL* using 127.0.0.1 to connect to the mythtv *backend* daemon. I've looked high and low and cannot find a place to change this value.

Where do I specify the backend IP address for mythtv to connect? Am I just completely wrong in my assumptions of relationship between the backend and frontend systems? Did I miss some important step in the installation process? I've reinstalled the frontend quite a few times...

All help and pointers welcome!

---

### Post by fudnet on 2009-02-23
Nobody has any ideas? Is it safe to assume that everyone installing a new server(backend role) and installing one or more client units (frontend role) has them working flawlessly? All of the discussions I'm seeing here as well as information on the wiki seem to point that configuration of the MySQL connection is what causes problems. Mine is fine... however it's the actual mythtvfrontend trying to connect to the backend daemon that's causing problems on my setup. Do I really just have to install the fronted as a fronted+slave backend setup? That seems quite unnecessary...

Help!

---

### Post by klc5555 on 2009-02-23
> **fudnet said:**
> Nobody has any ideas? Is it safe to assume that everyone installing a new server(backend role) and installing one or more client units (frontend role) has them working flawlessly? All of the discussions I'm seeing here as well as information on the wiki seem to point that configuration of the MySQL connection is what causes problems. Mine is fine... however it's the actual mythtvfrontend trying to connect to the backend daemon that's causing problems on my setup. Do I really just have to install the fronted as a fronted+slave backend setup? That seems quite unnecessary...

Help!

IP addresses are handled in the General setup screen. In the backend General screen, both references to 127.0.0.1 need to be changed to the actual IP address, as described here: [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend)

Likewise, the remote frontend needs to have this real IP address entered (instead of 127.0.0.1) in its general setup screen and the MySQL password of the database on the master backend. As described here: [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend#General](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend#General)

The remote frontend does not need a slave backend (and basically should not have a slave backend installed or configured) unless it also has a tuner. The first time you run "mythfrontend" on the remote machine, the General config screen should pop up when it doesn't immediately find a backend to connect to, and you may then enter the appropriate information.

Cheers! :)

---

### Post by pjbgravely on 2009-02-23
Don't forget to set the pin in the backend to 0000. The links above seem to be broken. [ Try this one.](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend#Host_Address_Backend_Setup)

Paul

---

### Post by klc5555 on 2009-02-23
> **pjbgravely said:**
>  The links above seem to be broken. [ Try this one.](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend#Host_Address_Backend_Setup)

Paul

Sorry about that. I didn't notice that the stupid forum editing software interprets the sequence ":" plus "D" as though it were the emoticon "grin", even when it's autoparsing the html address for a URL. Argh!

The URLs for backend and frontend configuration were:

[http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend)
and 
[http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend)

Cheers!

---

### Post by fudnet on 2009-02-25
When I go into the general settings, I only see configuration for the database. There is no place to change the values of the myth backend connection. Ideas?

---

### Post by klc5555 on 2009-02-25
> **fudnet said:**
> When I go into the general settings, I only see configuration for the database. There is no place to change the values of the myth backend connection. Ideas?

Very first page of the "General" screen in the backend setup on your primary backend machine itself. If you are running mythbuntu on this backend, you can get there from the mythbuntu control center on this machine. If you are running mythtv just as an app over some Linux distro on this backend machine, kill the backend process ("killall mythbackend"), and run "mythtv-setup" from a terminal on this backend machine. 

Then as the previously quoted documents say. The user manual on the mythtv wiki is surprisingly good on what you find in which boxes in the backend General setup, and is worth reading. It explains the information box-by-box on this page, and tells you the three boxes that need be altered for a remote frontend to access this master backend machine. You will need to change the 2 IP address boxes on this page, and probably add 0000 as your PIN. 

Then setup the frontend(s) to connect to this backend. Likewise the user manual on the mythtv wiki is extraordinarily good on what you'll find box to box on the "General" portion of the frontend setup of each frontend machine, which frontend setup is accessible at all times when "mythfrontend" is run on the remote frontend machine.

---

### Post by fudnet on 2009-02-25
#-o

You are correct. If I actually do read the wiki thoroughly, I will learn how to do these things. I made the changes and now my frontend box works exactly as expected. Thank you so much for the help and patience with someone who just won't follow directions or read properly. :redface:

---

### Post by klc5555 on 2009-02-26
> **fudnet said:**
> #-o

You are correct. If I actually do read the wiki thoroughly, I will learn how to do these things. I made the changes and now my frontend box works exactly as expected. Thank you so much for the help and patience with someone who just won't follow directions or read properly. :redface:

Glad everything works! 

And besides, the first remote mythbox is always the hardest! :D

Cheers!

---

