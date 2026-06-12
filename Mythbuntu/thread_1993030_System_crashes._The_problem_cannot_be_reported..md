---
title: "System crashes. The problem cannot be reported."
date: 2012-06-01
forum: Mythbuntu
---

### Post by elliott6 on 2012-06-01
Anybody have the following issue, or know of a possible solution?

I did a fresh install of Mythbuntu 12.04 with 0.25, "upgrading" my database following the wiki from 10.04 and 0.23-1.  On at least a daily, or every other day basis, I am getting an "Ubuntu 12.04 crashed.  Would you like to send an error report?" or at other times "The application MythTV Frontend has closed unexpectedly. Send error report to help fix this problem." On doing so, the following message appears - 

The problem cannot be reported:

You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

(when it's mythtv-transcode-utils it's these packages)
mythtv-transcode-utils, libmyth-0.25-0, libssl1.0.0, libxml2, mythtv-common

(when it's mythtv-frontend it's these packages)
mythtv-frontend, libmyth-0.25-0, libmyth-python, libssl1.0.0, libxml2, mythtv-common, openssl
(or these are the latest)
mythtv-frontend, libasound2, libgail-3-0, libgtk-3-0, libgtk-3-common, libmyth-0.25-0, libmyth-python, libssl1.0.0, libxml2, mythtv-common, openssl

When searching, it's recommended to update to fix, which is fine.  I perform the updates via update manager (also used apt-get update and upgrade via the command line), and all seems fine.  Until it happens again, which is the rub.  While I am okay that all is well after, this is a reoccurring annoyance I was hoping to stop once and for all (or at least less often).

Any thoughts?  Thanks!

Sean

---

