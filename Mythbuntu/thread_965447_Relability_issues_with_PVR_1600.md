---
title: "Relability issues with PVR 1600"
date: 2008-10-31
forum: Mythbuntu
---

### Post by fishfreek on 2008-10-31
I have had the PVR 1600 working for a few months now but with some recent kernel updates its operation has become very unstable.  The issue I am seeing is that I can get the system to see the card in both analog and digital capture.  If I capture an analog signal the first signal has dropped frames.  I know this is an issue with the beta driver.  The second capture looks fine except as of late the capture ends up failing and the backend service ends up crashing.  If I restart the backend process I have to capture a junk show to deal with the dropped frames problem and again the backend ends up crashing upon the next capture.  The capture can go for a few minutes or almost the entire duration of a 30 min show before the backend crashes.

I just tried upgrading to 8.10 but that didnt help either.  I ran a test recording last night and the backend crashed on that recording after a fresh install of 8.10.  Again this was not an upgrade but a fresh install of 8.10.

I have now found out my graphics card, a geforce 4 mx 440 does not work with ubuntu 8.10's x serv so I have to down grade to 8.04LTS tonight with a fresh install.

Has anyone seen this issue with the backend crashing on capture and what has been the fix?

---

