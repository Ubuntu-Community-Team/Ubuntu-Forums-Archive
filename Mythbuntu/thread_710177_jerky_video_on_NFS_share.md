---
title: "jerky video on NFS share"
date: 2008-02-28
forum: Mythbuntu
---

### Post by jakev383 on 2008-02-28
I have a convoluted setup - my backend (with 1 PVR150 and 1 PVR500) is a P4 2.4G with 1G of RAM running MythDora.  My dedicated front end is a VIA 800Mhz with 512M of RAM running Mythbuntu (Feisty). I have the front end software installed on my desktop as well, which is a P4 2.4G 2G of RAM machine (Gutsy). The NFS share is a CentOS4 server with 750G of storage as NFS in a RAID5 array and 512M of RAM.
Everything USED to work great. My problem lies with ripped DVDs. They get ripped to the NFS share to be playable by the frontend (they're ripped on the desktop to the NFS share using the Optical Disk menu in Myth). I used to be able to play them just fine on the dedicated front end.  What is happening now is that when I watch shows, the video is 1.5 seconds behind the audio and jerky. I've tried various things including pausing, marking my position and exiting to return to the video, etc. The only thing that works is hitting the rewind button, which brings up the rewind window (doesn't actually rewind) and if I let it sit there for 2 seconds then hit play, it will jump back 12 seconds or so and the video will be fine afterwards. Sometimes it will happen again later in the show, and repeating the rewind trick once again solves the problem (although by leaving the rewind window up for 2 seconds causes the movie to actually jump back 10 minutes at this point).
I do not notice this on my desktop running the front end. My backend is headless so I can't really check there.
Now the NFS shares are exported on the Cent 4 machine like this:
```
/videos 192.168.76.0/255.255.255.0(rw)
```
And mounted on the dedicated front end like this:
```
192.168.76.1:/videos /media/videos              nfs     rw,rsize=8192,wsize=8192,timeo=14,intr  0 0
```
It USED to be mounted exactly like my desktop's is:
```
192.168.76.1:/videos    /media/videos   nfs     rw      0 0
```
But I changed it to try and stop the jerky video behavior.
Does any one have any ideas on what I could try to solve this? It's rather annoying to say the least. Next (this weekend) I'll try moving a couple movies to another NFS server I have and see if the problem is persistent.  
Thanks!

---

### Post by jakev383 on 2008-02-29
As an update -
I built a completely new test NFS server - Pentium 2.4G Celeron, 256M of RAM, and a 80G SATA drive running Debian 4. rsync'ed some movies over and redid the mount on the front end to to the new NFS server.
Same exact problem.
Needless to say I doubt it's my NFS server. Next I'll try putting a new drive in the frontend and installing using Gutsy.

---

### Post by badmedic on 2008-03-01
I had the same basic issue with my setup, though it uses an SMB share. 

I ended up adding some parameters to help mplayer cache better.

Under Video Settings > Player Settings, where it lists "mplayer" and some parameters, try adding the following two additional parameters:

-cache 8912 -cache-min 4

Hope it helps! :)

---

### Post by ian dobson on 2008-03-01
Hi,

I had the same sort of problems with ripped DVD's. I was using NFS but ended up going over to Samba/CIFS. Just going over to CIFS made a huge difference (almost no stuttering anymore).

After I added the line:-
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=8192 SO_SNDBUF=8192

to the smb.conf file all performance problems where solved.

Regards
Ian Dobson

---

### Post by jakev383 on 2008-03-01
> **badmedic said:**
> I had the same basic issue with my setup, though it uses an SMB share. 

I ended up adding some parameters to help mplayer cache better.

Under Video Settings > Player Settings, where it lists "mplayer" and some parameters, try adding the following two additional parameters:

-cache 8912 -cache-min 4

Hope it helps! :)


Thanks - tried that and it didn't help much.  I'll switch it over to CIFS when I get back this afternoon and see how it goes.

---

### Post by jakev383 on 2008-03-01
Tried under CIFS and it did the same thing. Even with the buffers in the samba file AND in the mplayer command. I played a video from a TV show I'd recorded (which I used the Archive to burn to a DVD, then pulled the files off the DVD and put them on the NFS - long process, but I give the show to my parents to have and I can still watch them that way), and the TV show I'd recorded played fine. Even some of the older movies I'd ripped from DVD (ones ripped a while ago) and they seemed to play okay. Maybe it's just the newer DVDs I've ripped that do that. Gives me an excuse to put a DVD player (or a DVD burner) in my backend I guess.
I have another set-top machine that I'll put the newer version of Ubuntu and Myth on and see if that works any better and let you know how it turns out.

---

### Post by ian dobson on 2008-03-02
Hi,

What's your network configuration like? I'm running 1Gb between frontend and backend through one Gbit switch. 

Any change that you're problem could be a network lagg problem? 
Could you try running network performance test. 

Regards
Ian Dobson

---

### Post by jakev383 on 2008-03-02
> **ian dobson said:**
> Hi,

What's your network configuration like? I'm running 1Gb between frontend and backend through one Gbit switch. 

Any change that you're problem could be a network lagg problem? 
Could you try running network performance test. 


I'm running a 100 Base network here. The NFS server is also my firewall/gateway. The frontend that is having the problems is on a 91' CAT 5e run from the switch.
Ping times from the backend to the NFS server are ~0.190ms.  
Using wget to grab a video from the web server running on the NFS shows average of 11.16M/s.  Not showing any packet loss, and since my wife and I are usually trying to watch the show when it gets jumpy there is no other network traffic to speak of.
Any other particular tests you would suggest running?
Thanks.

---

### Post by jakev383 on 2008-03-02
I install Mythbuntu on a MII-10000 board and do not notice the jerky video problem. Don't know if it's the newer packages/distro or the faster CPU. I'll try and put the newer version on the old frontend later in the week and see if the problem is still there.
Thanks for the suggestions everyone!

---

