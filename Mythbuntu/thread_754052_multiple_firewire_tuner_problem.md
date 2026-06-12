---
title: "multiple firewire tuner problem"
date: 2008-04-13
forum: Mythbuntu
---

### Post by 4dognight on 2008-04-13
My setup consists of 3 myth srvers. I have all 3 running .21
These servers are setup as follows,

Backend - has 3 tuner cards (pvr350,pvr500,kworld115)
frontend (mythbuntu-hdtv) it is connected locally  to a HDSTB via firewire
frontend(mythtv-sdtv) it is connected locally to a HDSTB via firewire

The frontend(mythbuntu-hdtv) works fine from the point of seeing and using all the available inputs.

The other frontend(mythtv-sdtv) fails to run livetv. If you look at the accompanying logs, you will see that this frontend is trying to open tuner 11, which is the firewire tuner connected to the other frontend. The problem is, it is trying to connect to it as if it is local. Either it should be connecting to it remotely, or it is trying to connect to the wrong firewire tuner locally. I would guess i should connect to its local tuner, as all priorities are at zero.

here is the relevent contents of the capturecard table

mysql> select cardid,videodevice,hostname from capturecard;
+--------+------------------+-------------------+
| cardid | videodevice      | hostname          |
+--------+------------------+-------------------+
|      2 | /dev/video0      | Mythbuntu-backend | 
|      3 | /dev/video1      | Mythbuntu-backend | 
|      4 | /dev/video2      | Mythbuntu-backend | 
|      5 | 0                | Mythbuntu-backend | 
|      6 | /dev/video3      | Mythbuntu-backend | 
| [COLOR="red"]    11 | 001E46FFFE236CA1 | mythbuntu-hdtv    | 
|     10 | 001E5AFFFEAFD3C0 | mythtv-sdtv [/COLOR]      | 
+--------+------------------+-------------------+
7 rows in set (0.00 sec)


and here is the frontend logs from both frontends.

***** output from server mythtv-sdtv  
***** It is trying to open recorder 11 as localhost
*****  It is not on this host
*****  The recorder local to this host is recorder 10

2008-04-13 09:39:48.172 MythSocket(8443e48:22): attempting connect() to (192.168.2.6:6543)
2008-04-13 09:39:48.181 MythSocket(8443e48:22): state change Idle -> Connected
2008-04-13 09:39:48.181 write -> 22 21      MYTH_PROTO_VERSION 40
2008-04-13 09:39:48.183 read  <- 22 13      ACCEPT[]:[]40
2008-04-13 09:39:48.183 Using protocol version 40
2008-04-13 09:39:48.183 write -> 22 25      ANN Monitor mythtv-sdtv 0
2008-04-13 09:39:48.192 read  <- 22 2       OK
2008-04-13 09:39:48.192 MythSocket(8322650:20): attempting connect() to (192.168.2.6:6543)
2008-04-13 09:39:48.200 MythSocket(8322650:20): state change Idle -> Connected
2008-04-13 09:39:48.201 write -> 20 25      ANN Monitor mythtv-sdtv 1
2008-04-13 09:39:48.204 read  <- 20 2       OK
2008-04-13 09:39:48.205 MythSocket(8322650:20): UpRef: 1
2008-04-13 09:39:48.205 write -> 22 23      GET_FREE_RECORDER_COUNT
2008-04-13 09:39:48.213 MythSocket: readyread thread start
2008-04-13 09:39:48.714 read  <- 22 1       6
[COLOR="red"]2008-04-13 09:39:48.714 write -> 22 29      GET_NEXT_FREE_RECORDER[]:[]-1
2008-04-13 09:39:48.716 read  <- 22 25      11[]:[]127.0.0.1[]:[]6543[/COLOR]
2008-04-13 09:39:48.718 TV: Attempting to change from None to WatchingLiveTV
2008-04-13 09:39:48.719 MythSocket(836e340:28): new socket
2008-04-13 09:39:48.719 MythSocket(836e340:28): attempting connect() to (127.0.0.1:6543)

*** output fromserve mythbuntu-hdtv
**** It opens recorder 11 as local host
*** this worksbecause this recorder is on this host

2008-04-13 10:43:37.538 MythSocket(84237c0:23): state change Idle -> Connected
2008-04-13 10:43:37.538 write -> 23 28      ANN Monitor mythbuntu-hdtv 1
2008-04-13 10:43:37.538 read  <- 23 2       OK
2008-04-13 10:43:37.538 MythSocket(84237c0:23): UpRef: 1
2008-04-13 10:43:37.542 write -> 25 23      GET_FREE_RECORDER_COUNT
2008-04-13 10:43:37.542 read  <- 25 1       6
[COLOR="red"]2008-04-13 10:43:37.542 write -> 25 29      GET_NEXT_FREE_RECORDER[]:[]-1
2008-04-13 10:43:37.542 read  <- 25 25      11[]:[]127.0.0.1[]:[]6543[/COLOR]
2008-04-13 10:43:37.546 TV: Attempting to change from None to WatchingLiveTV
2008-04-13 10:43:37.546 MythSocket(8343c10:26): new socket
2008-04-13 10:43:37.546 MythSocket(8343c10:26): attempting connect() to (127.0.0.1:6543)
2008-04-13 10:43:37.546 MythSocket(8343c10:26): state change Idle -> Connected

---

### Post by volkswagner on 2008-04-13
Odd.  Does the firewire tuner list correctly in master backend, or mythweb (ie: correct hostname)?  May be database corruption, it is odd they are listed out of order.

Were these tuners ever swapped, may have retained id number???  Just guessing.

You have hinted at this and may help diagnose.  Create a recording group name and priority so the SD machine connects to another tuner first.

---

### Post by 4dognight on 2008-04-14
Ok, I went and removed both firewire tuners, and recreated them . I  have access to those now , but now just one of the pvr500 tuners is available. the other cant be used.! Something funky going on here. I suppose I could try removing them all, and try again. Maybe If I turn on full verbose while creating the tuners in the backend, might show some reason why?

---

### Post by newlinux on 2008-04-14
I  had similar problems back when I was first setting up everything, and I remember the only thing that worked everytime was deleting all tuners and recreating them again. At least it got the numbering right again too :) I never figured out why...

---

### Post by 4dognight on 2008-04-14
My guess is its a bug. 
Its probably in that GET_NEXT_FREE_RECORDER function. I had verbose on 'ALL'., but thats all it dumped out. IF I could turn on more debug for that function, we might figure out why its doing that.

---

### Post by majoridiot on 2008-04-14
> **4dognight said:**
> My setup consists of 3 myth srvers. I have all 3 running .21
These servers are setup as follows,

Backend - has 3 tuner cards (pvr350,pvr500,kworld115)
frontend (mythbuntu-hdtv) it is connected locally  to a HDSTB via firewire
frontend(mythtv-sdtv) it is connected locally to a HDSTB via firewire

The frontend(mythbuntu-hdtv) works fine from the point of seeing and using all the available inputs.

The other frontend(mythtv-sdtv) fails to run livetv. If you look at the accompanying logs, you will see that this frontend is trying to open tuner 11, which is the firewire tuner connected to the other frontend. The problem is, it is trying to connect to it as if it is local. Either it should be connecting to it remotely, or it is trying to connect to the wrong firewire tuner locally. I would guess i should connect to its local tuner, as all priorities are at zero.


the details are less than clear... 

are the backend, and both frontends running on the same machine?

---

### Post by 4dognight on 2008-04-14
the 2 frontends are actully secondary backends/frontends with just the firewire tuner configured on each.
The1 backend is configured also as a frontend with the other tuners, but is primarly just the backend.
The reason for having the frontends having the firewire tuner, is for PPV. As I still need the STB for that. As well, since Myth is not exactly stable at the moment, It is my fallback since the STB is connected to both the Myth box and the TV at the same time.

---

### Post by majoridiot on 2008-04-14
> **4dognight said:**
> the 2 frontends are actully secondary backends/frontends with just the firewire tuner configured on each.
The1 backend is configured also as a frontend with the other tuners, but is primarly just the backend.
The reason for having the frontends having the firewire tuner, is for PPV. As I still need the STB for that. As well, since Myth is not exactly stable at the moment, It is my fallback since the STB is connected to both the Myth box and the TV at the same time.

secondary backends... ok, that makes more sense.

are all three of your backends configuredin mythtv-setup with their actual ip addresses and not 127.0.0.1 or localhost or the hostname?

the same goes for the database location- do all three reflect the LAN address of the box were the database is located?

---

### Post by 4dognight on 2008-04-14
the localbackends were defined as 127.0.0.1 , the master backends were defined with the IP address of the master backend.

I fiddled with the tuners by deleting and re adding, in the backend config. I finally got them all to be available. So, while I got it working , it was more of a work around , rather than a fix.

I also dont think it was related to firewire, but rather a problem of some sorts with all the tuners being added.

---

### Post by newlinux on 2008-04-15
> **4dognight said:**
> the localbackends were defined as 127.0.0.1 , the master backends were defined with the IP address of the master backend.

I fiddled with the tuners by deleting and re adding, in the backend config. I finally got them all to be available. So, while I got it working , it was more of a work around , rather than a fix.

I also dont think it was related to firewire, but rather a problem of some sorts with all the tuners being added.

That really does sound like something that happened to me a while ago. Never figured it out, but its not like I add and delete tuners all the time anymore...

---

### Post by majoridiot on 2008-04-15
> **4dognight said:**
> the localbackends were defined as 127.0.0.1 , the master backends were defined with the IP address of the master backend.

I fiddled with the tuners by deleting and re adding, in the backend config. I finally got them all to be available. So, while I got it working , it was more of a work around , rather than a fix.

I also dont think it was related to firewire, but rather a problem of some sorts with all the tuners being added.

i agree that this was a config issue unrelated to firewire.  i think the problem would be solved by properly configuring
the backends, so that a work-around is not needed and unexpected problems won't surface in the future.

this is my recommendation for a proper configuration:

1. delete all tuners on all backends

2.  using MCC, make sure the "role" of the master backend is set as a master backend with frontend

3. run mythtv-setup on the master backend and enter 1. General.  enter the **actual** LAN ip of the master 
backend server in both the first field and the field for the master backend IP.

4. for **both** secondary backends:

using MCC, make sure the "role" of the each secondary backend is set as a secondary backend with frontend

run mythtv-setup and enter 1. General.  enter the **actual** LAN ip of the the **secondary** backend server 
in first field and the field and the IP of the **master** backend in the field for the master backend server.

5.  starting with the master backend, go back and set up your tuners in 3. capture cards and 4. video sources 
and 5. input connections.  then do the same for setting up your secondary backends with firewire tuners.

this way, each machine knows exactly what it is supposed to do, where it exists on the network and where
the to find the other machines.

---

### Post by 4dognight on 2008-04-15
That is pretty much what I did , except that I left the local address as 127.0.0.1 for the  secondary backend address.  I think the config suggests to leave it at 127.0.0.1. The master backend, I put the IP address in. I agree, its prob best to use actual address in this case. 

You should take your last  post and put it in  the documentation, for future reference by others.

Now, onto my next problem...

:)

---

