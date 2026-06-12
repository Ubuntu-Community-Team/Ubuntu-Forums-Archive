---
title: "Mythbuntu 10.04 Live CD username/password"
date: 2010-05-06
forum: Mythbuntu
---

### Post by CaligulaSPQR on 2010-05-06
Was having headaches setting up an old Compaq Media Center Edition laptop as a PVR.  Decided to see if Mythbuntu supported my hardware by loading up the live CD.
 
Mythbuntu live loads fine, and I click on the frontend on the desktop.  It tells me I need a backend before it can run; ok, I load up the control panel and enable the database and then click on button to set up the myth tv backend.
 
It gives me some spiel about the user account needing to be part of the mythtv group, offers to add, I say yes, then it says it has to log out and back in to complete the process.  Alright-- I click yes, it takes me to the login screen (it had initially logged in automatically under the ubuntu user).
 
There is no mention of usernames/passwords so why am I presented with a login screen?  I try ubuntu/ubuntu    mythtv/mythtv   nothing, authentication failed every time.  I reboot a couple of times and see if there are other settings I'm missing.  I google for answers but don't find anything.  
 
Why wouldn't the ubuntu user be set up by default as part of the mythtv group if a lot of people want to try mythbuntu by testing it out with their hardware--and most like me if they are just testing out, wouldn't have a backend already set up.
 
I mean I'm kind of beside myself wondering why it's not easier.  Why make it so difficult?

---

### Post by tgm4883 on 2010-05-06
It's a live cd frontend. The backend is not meant to run from the live cd. You need to install this to a hard disk to get the backend to work.

---

