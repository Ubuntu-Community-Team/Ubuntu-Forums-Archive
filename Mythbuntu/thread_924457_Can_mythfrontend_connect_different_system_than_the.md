---
title: "Can mythfrontend connect different system than the slave backend on same machine?"
date: 2008-09-19
forum: Mythbuntu
---

### Post by newlinux on 2008-09-19
Let me attempt to give the background.

I actually have two different myth systems running on the same network. Reason being I like my HD, and I have a machine in my garage that has a slow wireless connection to the rest of my network. So I have that machine as a combined frontend/backend in the garage so that I can watch HD programs without worrying about the network speed in addition to my distributed system on the rest of the network. One day I'll run cable into my garage, but there are a few complications and this is working fine for me now.

However, I would like to use one of my other machines (my primary user desktop) on the wired network to do job processing, so I have a secondary backend on the main network that connects to the garage system. 

But of course, on this system when I use mythfrontend, I want to be able to connect to the wired system so that the network speed for HD programs isn't a problem.

I think both the frontend and backend get their DB connection settings from the mysql.txt file, so I'm thinking this isn't possible. Anybody know a way around this?

If not, no biggie but would be nice for that occasional time I want to fire up mythfrontend while I'm using my primary desktop. I can always play the files over the network with mplayer, but it would be simpler to use mythfrontend.

---

### Post by volkswagner on 2008-09-19
I am still a little confused on your setup.

Is the garage pc a master backend/FE with its own database?
Do you have a second master backend elsewhere on the wired network?
The third pc in question is a wired desktop running what, a secondary backend to the garage?

So for instance you may need two separate instances of myth on the primary desktop.  You would need your current slave backend, plus add a frontend only to connect to the wired backend?

Do you currently use the desktop frontend to interface with the garage?  Can you get away with mythweb for these functions?

If you can't have two installs of myth, one slave and one frontend, perhaps a solution would be XBMC to connect to the wired system. 

[http://www.linux.com/feature/144530]("http://www.linux.com/feature/144530")

Much more work would be to have one master (combine your databases) and have the gagage store recordings locally.  Obviously a lot of work, for an existing setup.

You could also ssh -X to the wired master.  Oh it probably isn't running a frontend?

---

### Post by tgm4883 on 2008-09-19
You might be able to do this.  You need the frontend to be in UPNP mode though, which is what happens when it can't connect to the backend, the slave backend would get it's information from the mysql.txt file, but somehow you need to get mythfrontend into UPNP mode, not sure there is a command line flag for this.

---

### Post by anonymousdog on 2008-09-19
As long as the frontend on your primary desktop should only ever connect to the primary backend on your wired network, can't you just remove the symlink to /etc/mythtv/mysql.txt from your home directory, and create a ./mythtv/mysql.txt file in your home directory with the proper dbusername and password there.  Then (or maybe first) change the mythbackend hostname in mythfrontend setup.

---

### Post by newlinux on 2008-09-19
oddly, for now, it keeps connecting to the wired backend even though all mysql.txt files point to the other wireless backend, along with the slave backend on the same machine. So for now I don't have to do anything. Can't say I understand why... but I guess it doesn't want to give up its old settings yet? Where is it storing them? The logs indicate it is looking for the wired IP and in the setup information it still has the info for the wired IP and the wired DB password...

---

### Post by ian dobson on 2008-09-20
Hi,

Check the IP address set in the "MasterServerIP" in the settings table for allhosts.

The mysql.txt is just used to get a connection to the SQL server, the frontend then queries the SQL server for the IP address of the master backend.

Regards
Ian Dobson

---

### Post by newlinux on 2008-09-20
> **ian dobson said:**
> Hi,

Check the IP address set in the "MasterServerIP" in the settings table for allhosts.

The mysql.txt is just used to get a connection to the SQL server, the frontend then queries the SQL server for the IP address of the master backend.

Regards
Ian Dobson

I'm not sure I get what you are saying. I'm not sure how this helps, since I have two master backends (and thus two SQL servers), I would assume it would use mysql.txt to connect to one or the other, whereas I want the frontend to connect to a different master than the slave backend (with the frontend and slave backend being on the same machine).

---

### Post by ian dobson on 2008-09-20
Hi,

In a myth setup you usually only have 1 master backend and multiple slave backends. I don't think that a frontend can connect to multiple master backends.

All you can do when you want to switch between the backends is to edit the mysql.txt file to point to the required SQL server.

Sorry I misunderstood your first post.

Regards
Ian Dobson

---

### Post by newlinux on 2008-09-20
> **volkswagner said:**
> I am still a little confused on your setup.

Is the garage pc a master backend/FE with its own database?
Do you have a second master backend elsewhere on the wired network?
The third pc in question is a wired desktop running what, a secondary backend to the garage?

So for instance you may need two separate instances of myth on the primary desktop.  You would need your current slave backend, plus add a frontend only to connect to the wired backend?

Do you currently use the desktop frontend to interface with the garage?  Can you get away with mythweb for these functions?

If you can't have two installs of myth, one slave and one frontend, perhaps a solution would be XBMC to connect to the wired system. 

[http://www.linux.com/feature/144530]("http://www.linux.com/feature/144530")

Much more work would be to have one master (combine your databases) and have the gagage store recordings locally.  Obviously a lot of work, for an existing setup.

You could also ssh -X to the wired master.  Oh it probably isn't running a frontend?

Sorry somehow I missed this post and I clearly need to clarify.

Yes, the Garage PC is a frontend/master backend with it's on SQL server. I do have a second master on the wired network. and yes the third PC in question is on the wired network running a secondary backend to the wireless (garage) master backend. But I want the frontend on that machine to connect to the wired master. I don't want that frontend to interface with the garage - that's the problem.

Having the garage store the recordings for the entire system locally won't work because then none of the wired systems in the house would be able to view the HD recordings (they'd be viewing them over wireless G) - this is the whole reason I have a second master system in the garage - so I can watch HD on the wired system from any frontend in the house and HD on the wireless system in the garage.

I'll look into XBMC as the frontend on the machine in question - if it doesn't use mysql.txt that would be perfect. Forwarding X over ssh doesn't play videos very well for me.

Thanks for all the suggestions. This is just an overly complicated system because I want to have my cake and eat it too. It is all unecessary whenever I get a proper network connection to the garage.

---

### Post by volkswagner on 2008-09-21
> **newlinux said:**
> ................Having the garage store the recordings for the entire system locally won't work because then none of the wired systems in the house would be able to view the HD recordings (they'd be viewing them over wireless G) - this is the whole reason I have a second master system in the garage - so I can watch HD on the wired system from any frontend in the house and HD on the wireless system in the garage..............


I still have a little gray area here.  I am not 100% sure how you use the system.  I assumed you had, maybe just one tuner in the garage for certain content (live tv).  I figured you could just have the one turner record local while the master also recorded on its own local disk.

My setup I have a master/FE in the family room with several tuners and an SD display.  My bedroom PC (slave/FE) has a single tuner for HD, used mostly for live tv.  It has a separate line up so I don't usually schedule recordings here for hours when it would disturb sleep.  Each backend records to it's own local drive.

My setup has it's own issues.  For recording/watching content via a remote frontend located on the slave, it must be on or waken from the master.  My particular Dell MOBO has issues with WOL.

Perfection is a dynamic goal.

---

### Post by newlinux on 2008-09-21
Basically I want to be able to watch all recordings from the wired system or the wireless system. This requires me to duplicate all recordings on the wired and wireless systems (so nothing is watched over wireless). Thus i have two separate masters - the wired one has multiple slaves and tuners spread across different machines. The wireless has one master which has all the tuners (3) and recordings, and a slave on the wired network to do job processing. This way whenever I am using the wireless I am watching recordings locally (not over the network) and when I use the wired I am only watching recordings stored on a machine with a wired connection. Almost all my recordings are HD.

---

### Post by volkswagner on 2008-09-21
Hmm, that must be a long trench to dig out to the garage.   :lolflag:

I do understand your dilemma.

---

### Post by newlinux on 2008-09-21
> **volkswagner said:**
> Hmm, that must be a long trench to dig out to the garage.   :lolflag:

I do understand your dilemma.

I had a hard time explaining it :)

Yeah, I've been meaning to get around to running wire to the garage  for 2 years now, but this solution works for now. I think I may just hire someone to do it quickly.

---

