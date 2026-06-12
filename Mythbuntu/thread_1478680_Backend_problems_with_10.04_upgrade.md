---
title: "Backend problems with 10.04 upgrade"
date: 2010-05-10
forum: Mythbuntu
---

### Post by JamesNorris on 2010-05-10
I am reposting this as I have realised that adding my problem to a thread with "solved" in the title is unlikely to get any assistence. 

Having upgraded to 10.04, I found my backend wasn't responding. It seems that the port number for the master backend had been changed to 6543, when I changed it back to the 3306 default, my frontend complained that

"Error: Mythtv is using all inputs, but there are no active recordings?" when I try to watch livetv. The backend has done a successful channel scan, but has not populated the listings and when I run mythfilldatabase I get 

```
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2010-05-09 18:35:54.120 MythContext: Connecting to backend server: 127.0.0.1:3306 (try 1 of 1)
2010-05-09 18:35:54.121 MythSocket(1dfe200:9): Protocol error: '>' is not a valid size prefix. 89 bytes pending.
2010-05-09 18:35:54.121 Protocol version check failure.
			The response to MYTH_PROTO_VERSION was empty.
			This happens when the backend is too busy to respond,
			or has deadlocked in due to bugs or hardware failure.
2010-05-09 18:35:54.121 Error rescheduling id -1 in ScheduledRecording::signalChange
2010-05-09 18:35:54.122 MythContext: Connecting to backend server: 127.0.0.1:3306 (try 1 of 1)
2010-05-09 18:35:54.122 MythSocket(1dfc5b0:9): Protocol error: '>' is not a valid size prefix. 58 bytes pending.
2010-05-09 18:35:54.122 Protocol version check failure.
			The response to MYTH_PROTO_VERSION was empty.
			This happens when the backend is too busy to respond,
			or has deadlocked in due to bugs or hardware failure.
2010-05-09 18:35:54.123 MythContext: Connecting to backend server: 127.0.0.1:3306 (try 1 of 1)
2010-05-09 18:35:54.123 MythSocket(1e01d70:9): Protocol error: '>' is not a valid size prefix. 58 bytes pending.
2010-05-09 18:35:54.123 Protocol version check failure.
			The response to MYTH_PROTO_VERSION was empty.
			This happens when the backend is too busy to respond,
			or has deadlocked in due to bugs or hardware failure.
```

I'm running the standard .23-fixes from the ubuntu repositories (although I have avenard's repos enabled, I'm pretty sure there's no .23 in there for lucid yet) 

Any help will be gratefully accepted.

---

### Post by db260179 on 2010-05-10
> **JamesNorris said:**
> I am reposting this as I have realised that adding my problem to a thread with "solved" in the title is unlikely to get any assistence. 

Having upgraded to 10.04, I found my backend wasn't responding. It seems that the port number for the master backend had been changed to 6543, when I changed it back to the 3306 default, my frontend complained that

"Error: Mythtv is using all inputs, but there are no active recordings?" when I try to watch livetv. The backend has done a successful channel scan, but has not populated the listings and when I run mythfilldatabase I get 

```
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2010-05-09 18:35:54.120 MythContext: Connecting to backend server: 127.0.0.1:3306 (try 1 of 1)
2010-05-09 18:35:54.121 MythSocket(1dfe200:9): Protocol error: '>' is not a valid size prefix. 89 bytes pending.
2010-05-09 18:35:54.121 Protocol version check failure.
			The response to MYTH_PROTO_VERSION was empty.
			This happens when the backend is too busy to respond,
			or has deadlocked in due to bugs or hardware failure.
2010-05-09 18:35:54.121 Error rescheduling id -1 in ScheduledRecording::signalChange
2010-05-09 18:35:54.122 MythContext: Connecting to backend server: 127.0.0.1:3306 (try 1 of 1)
2010-05-09 18:35:54.122 MythSocket(1dfc5b0:9): Protocol error: '>' is not a valid size prefix. 58 bytes pending.
2010-05-09 18:35:54.122 Protocol version check failure.
			The response to MYTH_PROTO_VERSION was empty.
			This happens when the backend is too busy to respond,
			or has deadlocked in due to bugs or hardware failure.
2010-05-09 18:35:54.123 MythContext: Connecting to backend server: 127.0.0.1:3306 (try 1 of 1)
2010-05-09 18:35:54.123 MythSocket(1e01d70:9): Protocol error: '>' is not a valid size prefix. 58 bytes pending.
2010-05-09 18:35:54.123 Protocol version check failure.
			The response to MYTH_PROTO_VERSION was empty.
			This happens when the backend is too busy to respond,
			or has deadlocked in due to bugs or hardware failure.
```

I'm running the standard .23-fixes from the ubuntu repositories (although I have avenard's repos enabled, I'm pretty sure there's no .23 in there for lucid yet) 

Any help will be gratefully accepted.


You need to change the settings in mythfrontend to the same port number of the backend.

There is no reason to change the port numbers from the default?

---

### Post by JamesNorris on 2010-05-10
> **db260179 said:**
> You need to change the settings in mythfrontend to the same port number of the backend.

There is no reason to change the port numbers from the default?

No, you misunderstand... something changed them during the upgrade process... I think. I changed them back to what they used to be as the frontend initially complained about not being able to connect to the backend at all. Now it connects, but gives the errors above. 

My frontend says 3306, my backend says local backend 6543 and 6544 and 3306 for the master backend.

Have I missed something?

---

