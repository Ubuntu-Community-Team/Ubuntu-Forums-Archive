---
title: "Please help!!!"
date: 2009-05-06
forum: Mythbuntu
---

### Post by bgolpmp on 2009-05-06
Hello and thanks for reading. I am new to mythtv and am having some trouble. I have everything installed, and when I hit the watch tv button, the screen goes blank, and nothing else happrns. This is my log file.



2009-05-06 14:44:26.738 MainServer::HandleAnnounce Playback
2009-05-06 14:44:26.749 adding: andy-desktop as a client (events: 0)
2009-05-06 14:44:26.755 TVRec(1): Changing from None to WatchingLiveTV
2009-05-06 14:44:26.813 TVRec(1): HW Tuner: 1->1
2009-05-06 14:44:27.995 SG(LiveTV) Error: FindNextDirMostFree: '' does not exist!
2009-05-06 14:44:28.042 TFW, Error: Opening file '/1002_20090506144426.nuv'.
            eno: Permission denied (13)
2009-05-06 14:44:28.043 TVRec(1) Error: RingBuffer '/1002_20090506144426.nuv' not open...
2009-05-06 14:44:28.043 TVRec(1) Error: CreateLiveTVRingBuffer() failed
2009-05-06 14:44:28.044 TVRec(1) Error: Failed to create RingBuffer 2
2009-05-06 14:44:28.046 TVRec(1): Changing from WatchingLiveTV to None
2009-05-06 14:44:28.058 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

I searched and have found similar questions, but have trouble finding the answer, or more likely I don't understant it. I am not new to linux, I just don't know much, and am very excited to learn.
I am running a Hauppauge 500 card if that matters. 

Thanks for the help!!!!

Andy

---

### Post by nickrout on 2009-05-06
Firstly a subject line "please help" is useless. Everyone is posting here for help. Make the subject a short description of your problem.

Looks to me like you haven't told myth where to put its recordings OR mythbackend does not have rights to make a file there. In fact this line:

```
2009-05-06 14:44:28.042 TFW, Error: Opening file '/1002_20090506144426.nuv'. eno: Permission denied (13)
```

makes it look like you are trying to save recordings to the root directory of your hard drive.

---

### Post by bgolpmp on 2009-05-06
OK Thanks for the reply. When I go to mythbuntu setup and Storage Directories, I will put is a path for saving such as "andy/videos/" then say ok and exit out of there I get an error message telling me 
"Path live/ doesn't exist
Cannot create a file //.test - directory doesn't exist
Path /andy/videos/ doesn't exist
 
Do you want to fix the problems?
 
Yes please
No I know what I am doing"
 
I have no clue what do do here. I thy diffrent things, and I get the same result.
 
Thanks for the help

---

### Post by nickrout on 2009-05-06
> **bgolpmp said:**
> OK Thanks for the reply. When I go to mythbuntu setup and Storage Directories, I will put is a path for saving such as "andy/videos/" then say ok and exit out of there I get an error message telling me 
"Path live/ doesn't exist
Cannot create a file //.test - directory doesn't exist
Path /andy/videos/ doesn't exist
 
Do you want to fix the problems?
 
Yes please
No I know what I am doing"
 
I have no clue what do do here. I thy diffrent things, and I get the same result.
 
Thanks for the help

I don't think you will have a path /andy, you may have one /home/andy :)

Why you changed this from the mythbuntu default is a mystery to me :(

---

### Post by bgolpmp on 2009-05-06
Ok I tried that, and this is the new log file 


2009-05-06 16:26:22.706 MainServer::HandleAnnounce Playback
2009-05-06 16:26:22.709 adding: andy-desktop as a client (events: 0)
2009-05-06 16:26:22.711 TVRec(1): Changing from None to WatchingLiveTV
2009-05-06 16:26:22.717 TVRec(1): HW Tuner: 1->1
2009-05-06 16:26:23.835 TFW, Error: Opening file '/home/andy/Videos/1002_20090506162622.nuv'.
            eno: Permission denied (13)
2009-05-06 16:26:23.836 TVRec(1) Error: RingBuffer '/home/andy/Videos/1002_20090506162622.nuv' not open...
2009-05-06 16:26:23.837 TVRec(1) Error: CreateLiveTVRingBuffer() failed
2009-05-06 16:26:23.850 TVRec(1) Error: Failed to create RingBuffer 2
2009-05-06 16:26:23.854 TVRec(1): Changing from WatchingLiveTV to None
2009-05-06 16:26:23.857 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
What is the default directory, and would I be better of changing it to that?
1 more thing. When *try to delete one of the storage directories I get a / How do *I get rid of that??

Thanks for the help!!!

---

### Post by nickrout on 2009-05-06
the backend usually runs under the user mythtv. That user will not have permission to write to /home/andy/videos

Set the recording location to /var/lib/mythtv/recordings

---

### Post by tobiz on 2009-05-06
> **bgolpmp said:**
> Hello and thanks for reading. I am new to mythtv and am having some trouble. I have everything installed, and when I hit the watch tv button, the screen goes blank, and nothing else happrns. This is my log file.



2009-05-06 14:44:26.738 MainServer::HandleAnnounce Playback
2009-05-06 14:44:26.749 adding: andy-desktop as a client (events: 0)
2009-05-06 14:44:26.755 TVRec(1): Changing from None to WatchingLiveTV
2009-05-06 14:44:26.813 TVRec(1): HW Tuner: 1->1
2009-05-06 14:44:27.995 SG(LiveTV) Error: FindNextDirMostFree: '' does not exist!
2009-05-06 14:44:28.042 TFW, Error: Opening file '/1002_20090506144426.nuv'.
            eno: Permission denied (13)
2009-05-06 14:44:28.043 TVRec(1) Error: RingBuffer '/1002_20090506144426.nuv' not open...
2009-05-06 14:44:28.043 TVRec(1) Error: CreateLiveTVRingBuffer() failed
2009-05-06 14:44:28.044 TVRec(1) Error: Failed to create RingBuffer 2
2009-05-06 14:44:28.046 TVRec(1): Changing from WatchingLiveTV to None
2009-05-06 14:44:28.058 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

I searched and have found similar questions, but have trouble finding the answer, or more likely I don't understant it. I am not new to linux, I just don't know much, and am very excited to learn.
I am running a Hauppauge 500 card if that matters. 

Thanks for the help!!!!

Andy

If you're new to mythtv just take the defaults on install. Once you've got everthing working, and there's a lot to learn then try you own custom set up if you have to.

---

