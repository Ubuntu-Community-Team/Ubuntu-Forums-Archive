---
title: "No response from Mythtv backend, Kodi pvr"
date: 2015-10-31
forum: Multimedia Software
---

### Post by 7.62Gaust on 2015-10-31
I'm not sure if this is the correct forum.  If it's not I apologize and please move to the correct one.

I can not get Kodi to connect to the Mythtv backend.  I had mythtv backend and Kodi 15.1 running perfectly on my system before I reinstalled Kodibuntu, updated to the latest stable build and updated Kodi to 15.2.  I ran the Mythtv backend setup, entered all my settings, including network address.  After setting up the Kodi PVR and enabling it I got the message  "Mythtv PVR client no response from Mythtv backend".  I ran the Mythtv backend setup to see if the backend is running and I'm asked if I want to shut down the backend before I make any changes.  I'm assuming the backend is running at that point?  When I exit the Mythtv setup it asks if I want to start the backend.  I tried changing the IP address in Kodi PVR settings to "localhost".  At that point I get TV channels listed but none of them work.   How do I troubleshoot the problem and get the backend connected?

---

### Post by 7.62Gaust on 2015-11-04
Does anyone have a suggestion?

---

### Post by TheFuzz4 on 2015-11-11
So I recently just took the plunge with my frontends and moving them over to Kodi.  My backend is separate of my frontends. However that being said:

What version of Myth are you currently running on?  I'm assuming that its .27? 

Your backend and Kodi are on the same box is that correct?  If so can you go to [http://localhost:6544](http://localhost:6544) and see if that displays anything.  That right there will tell you if your backend is running. 

You could also do a ps -ef | grep myth and look for the backend process.  If its not running a sudo service mythtv-backend start should start it right up.

Let me know if that helps ya out.  Sorry for the delayed response to you on this just saw your posts.

---

### Post by 7.62Gaust on 2015-11-21
Sorry for the delay.  Something I did got it working finally.  Thanks for the help.

---

### Post by Jake_Mulder on 2016-02-28
> **7.62Gaust said:**
> Sorry for the delay.  Something I did got it working finally.  Thanks for the help.

Do you know what you did? I am having the same issue.

Thanks

---

