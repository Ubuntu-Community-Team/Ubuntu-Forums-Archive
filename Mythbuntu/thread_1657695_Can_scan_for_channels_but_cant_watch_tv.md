---
title: "Can scan for channels but cant watch tv"
date: 2011-01-01
forum: Mythbuntu
---

### Post by thusgaard on 2011-01-01
Hi 

I just installed MythBuntu 10.10 on a HP DC7600, with 4GB RAM, 80 GB disk and a Happauge 150 card. 

I can scan ok, but when I want to watch TV it writes "Please..." on the screen, and after a short while it returns to the menu. 

I know that the setup is a little old fashioned and analog, but it was for free. Now I just would love to have it working. 

Please ask for any info and I'll try to provide it. 

J;-)

---

### Post by LowSky on 2011-01-01
go to Utilities/Setup > Setup > TV Settings > Playback > Playback Profiles (page 3/8) > change the Current Video Playback profile to a different option, note you can only use VDPAU if you have a Nvidia graphics card 84xx or better. I would try **Normal** first

---

### Post by newlinux on 2011-01-01
Can you make recordings, or just not playback anything? The answer to that will help us know more if it is a frontend or backend configuration problem. It would be good to see your front and backend logs from when you try to watch livetv, or play back a recording if you can make them.

---

### Post by thusgaard on 2011-01-02
> **LowSky said:**
> go to Utilities/Setup > Setup > TV Settings > Playback > Playback Profiles (page 3/8) > change the Current Video Playback profile to a different option, note you can only use VDPAU if you have a Nvidia graphics card 84xx or better. I would try **Normal** first

I've just tried Normal, Slim, high quality and CPU--. It was set for CPU+. Still not working.

J;-)

---

### Post by thusgaard on 2011-01-02
> **newlinux said:**
> Can you make recordings, or just not playback anything? The answer to that will help us know more if it is a frontend or backend configuration problem. It would be good to see your front and backend logs from when you try to watch livetv, or play back a recording if you can make them.

Are these logs any good?
[http://mythbuntu.pastebin.com/iVHEwHNn](http://mythbuntu.pastebin.com/iVHEwHNn)

from line 2613:
#
2011-01-02 06:25:26.268 TV: Attempting to change from None to WatchingLiveTV
#
2011-01-02 06:25:26.271 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
#
2011-01-02 06:25:26.272 Using protocol version 23056
#
2011-01-02 06:25:26.369 Spawning LiveTV Recorder -- begin
#
2011-01-02 06:25:27.126 Spawning LiveTV Recorder -- end
#
2011-01-02 06:25:27.130 ProgramInfo(): Updated pathname '':'' -> '1046_20110102062526.nuv'
#
2011-01-02 06:25:27.135 We have a playbackURL(/var/lib/mythtv/livetv/1046_20110102062526.nuv) & cardtype(V4L)
#
2011-01-02 06:25:27.339 We have a RingBuffer
#
2011-01-02 06:26:07.396 TV Error: StartRecorder() -- timed out waiting for recorder to start
#
2011-01-02 06:26:07.396 TV Error: LiveTV not successfully started
#
2011-01-02 06:26:13.454 Deleting UPnP client...
#
Error in my_thread_global_end(): 1 threads didn't exit
#
Starting mythfrontend.real..


J;-)

---

### Post by thusgaard on 2011-01-08
In a week I have come no closer to a solution. 
I havn't tried anything, but I have googled a lot to see if I could find any hit to what is wrong. 

The closest I get is that my signal is poor, but it looks fine on my TV!

Regards J;-)

---

### Post by Senkoboy on 2011-01-08
> 2011-01-02 06:25:27.135 We have a playbackURL(/var/lib/mythtv/livetv/1046_20110102062526.nuv) & cardtype(V4L)

What are your settings on the backend with the Happauge 150 card?   A PVR 150 card should be set up under MPEG-2  

Try changing the V4L option to MPEG-2

[http://wiki.linuxmce.org/index.php/Hauppauge_WinTV-PVR-150_MCE]("http://wiki.linuxmce.org/index.php/Hauppauge_WinTV-PVR-150_MCE")

---

### Post by newlinux on 2011-01-08
> **thusgaard said:**
> In a week I have come no closer to a solution. 
I havn't tried anything, but I have googled a lot to see if I could find any hit to what is wrong. 

The closest I get is that my signal is poor, but it looks fine on my TV!

Regards J;-)

Somehow I completely missed your reply. Looks like a  backend configuration problem from your logs (I second the suggestion above) so it will probably be helpful to see your backend logs too.

Also double check your permissions on your recording directory. the mythtv user has to be able to read and write to that directory.

---

### Post by thatguruguy on 2011-01-08
Have you tried running a program called "tvtime"? It's available in synaptic.

It's fairly fault-tolerant, and can sometimes grab analog signals that mythtv has trouble with.  If tvtime doesn't work, try running it from a terminal and post any errors it generates here.

---

