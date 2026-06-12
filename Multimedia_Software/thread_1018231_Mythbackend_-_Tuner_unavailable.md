---
title: "Mythbackend - Tuner unavailable"
date: 2008-12-21
forum: Multimedia Software
---

### Post by longhaired1 on 2008-12-21
Okay, I am almost set up and ready to go. Here is the problem.

Upon startup, mythbackend is running as user mythtv in the background. However running mythfrontend and checking status shows tuner unavailable. I can sudo killall mythbackend and then restart the backend (as regular user) and everything works fine. Needless to say this is a pain.

I've chown'd the video card to user mythtv with no luck. I've looked in the Ubuntu user manager and see root and my account as users , but no user mythtv in the user management system. When I go to add user mythtv I'm told that it is already an existing user (which it is but not showing up in the manager anywhere). I also grepped the group directory and it appears that mythtv is in the mythtv group.

No errors in the mythbackend log either. It just appears that the user mythtv is not able to start the tuner.

Any thoughts?

---

