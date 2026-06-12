---
title: "Xubuntu to Mythbuntu NEWBIE"
date: 2013-03-15
forum: Mythbuntu
---

### Post by rodneymckay7 on 2013-03-15
Hi everyone
I have installed The Mythbuntu Control Centre on Xubuntu

Does anyone know a Guide on what to do next ?

I just want to know how to start the front end - I must be blind or something but there should be more info on the mythbuntu website on what to do once you download the Control Center am I suppose to download anything else MythTV etc ??...
I am trying to get for a better understanding of the basics of moving between Mythbuntu and Xubuntu 12.04.

Or am I meant to just read the mythtv pages like [http://www.mythtv.org/wiki/Mythfrontend](http://www.mythtv.org/wiki/Mythfrontend)
Thanks for any comments.......

---

### Post by klc5555 on 2013-03-15
> **rodneymckay7 said:**
> Hi everyone
I have installed The Mythbuntu Control Centre on Xubuntu

Does anyone know a Guide on what to do next ?

I just want to know how to start the front end - I must be blind or something but there should be more info on the mythbuntu website on what to do once you download the Control Center am I suppose to download anything else MythTV etc ??...
I am trying to get for a better understanding of the basics of moving between Mythbuntu and Xubuntu 12.04.

Or am I meant to just read the mythtv pages like [http://www.mythtv.org/wiki/Mythfrontend](http://www.mythtv.org/wiki/Mythfrontend)
Thanks for any comments.......

It's not clear from your post --do you have a mythbackend already set up and configured (presumably on some other machine) that you intend to connect mythfrontend to? Mythfrontend is useless by itself and won't run without finding an already-configured backend somewhere. It's not a standalone.

Xubuntu with mythtv is the only way I still run mythtv on Ubuntu. But I rarely bother with the control center. If you need the full mythtv (because you do not already have a mythtbackend somewhere to connect mythfrontend to), you can install via synaptic or apt-get the "mythtv" metapackage, which will get the whole thing plus dependencies. Alternatively, you could start with the very minimum, which would be the packages mythtv-common, mythtv-backend, mythtv-frontend, and maybe mythtv-database (plus all the dependencies that get dragged along by the installer) You would then need to set up the backend, by any of the available methods, and when the backend is up and running, start mythfrontend. 

If, however, you really do only intend to run mythfrontend on your Xubuntu machine (because you already have a backend set up somewhere else to connect to) then you need to install only mythtv-common and mythtv-frontend. If the backend on the remote machine (more accurately its MySQL server) has been correctly configured to accept tcpip connections to the database from other machines, then you would start mythfrontend on you Xubuntu desktop (from the XFCE menu or from a terminal) and either fill out the popup form to point mythfrontend to where the backend is, or it may connect automatically if UPnP does its thing.

In any event, Mythtv is not very intuitive to set up. Particularly the first few (dozen) times. So since you've already found the wiki, it pays to dive headfirst into the installation manual at [http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index) Despite its numerous flaws, it's the only decent documentation that's out there.

---

### Post by rodneymckay7 on 2013-04-06
Thanks for your response
I have been slowly struggling to set up the MythTV.

---

