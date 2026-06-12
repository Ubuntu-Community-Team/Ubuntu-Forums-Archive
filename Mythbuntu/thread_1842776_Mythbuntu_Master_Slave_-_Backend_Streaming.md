---
title: "Mythbuntu Master Slave - Backend Streaming"
date: 2011-09-12
forum: Mythbuntu
---

### Post by sanctusmob on 2011-09-12
Hello everyone ...

I want to implement on a live stream where there is a master server that will stream to the slave server and the client will be connected to the slave server and play the stream. After a quick search on the internet came to MythTV, namely the distribution of mythbuntu.

I set up the master forntend (master server), I set up The secondary backend. From the client when connected to a master server I see the normal stream. But when I connect the slave does not even get the list of channels ... In the slave normally see list of channels and is normally communicate with the master.

Master server is a pc with tvtuner up and mythbuntu 10.04.
Slave server is a virtual machine and mythbuntu 10.04.
Client is a windows pc and play the stream using MythTV Player.

Does anyone have a look and help me;
Is the secondary backend can not stream to other client?
I am open to other proposals for operating the system

Sorry for my bad english.

---

### Post by nickrout on 2011-09-13
I think you are confused.

mythtv is essentially two programs. The backend records TV, presents the electronic programme guide, schedules recordings etc. The frontend presents the user interface, and allows you to watch recorded programmes, setup recordings, delete programmes you no longer want etc. You can think of the backend as the "server" and the frontend as the "client". There is also a mysql database server involved, which is usually on the master backend machine, but doesn't have to be.

You can have any number of backends and any number of frontends on a network. If you have more than one backend, then one is a master backend and the others are slave backends.

The frontends connect to backends to get database information and stream files. Some people run a very simple system with the backend and frontend on the same machine, but essentially this is still the same system.

I am not sure why you want to use three computers for what is essentially streaming from a "server" to a "client". But anyway mythtv is for the main part a PVR or personal video recorder. If you don't want to record TV then you could look at XBMC, which works well over a network.

If you can explain your usage scenario better (and the reason for the third computer) then you may get more explicit help.

---

### Post by sanctusmob on 2011-09-13
From company headquarters to branches and by streaming them to end customers. I'm talking about chain internet cafe.

---

### Post by nickrout on 2011-09-13
I don't think mythtv is what you want. For one thing the recorded files use too much bandwidth to be of much use over the internet, unless you have a very very fat pipe.

For another thing copyright would prevent this sort of thing. The developers are very big on NOT breaking copyright laws or terms of use of web sites.

---

### Post by sanctusmob on 2011-09-13
ok thanks. You can close topic.

---

### Post by tgm4883 on 2011-09-14
> **sanctusmob said:**
> ok thanks. You can close topic.

Actually, you can mark it as solved. Nobody else can

---

