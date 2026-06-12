---
title: "Mythbuntu 9.04 - Mytharchive not working to create dvd iso"
date: 2009-05-22
forum: Mythbuntu
---

### Post by DominicF on 2009-05-22
Hi,

I recently done a fresh install on mythbuntu 9.04.  I'm trying to get mytharchive to create a dvd iso of a recording I made from livetv.

The problem I'm having is in specifying the temporary work directory in the setup menu.  After I specify a location and go through the process of creating the dvd iso image i.e. selecting the recording and proceeding to the logfile screen where I expect to see system information as Mytharchive begin the process but nothing happens here and system just sits there doing nothing.

After checking my mythfrontend log file I can see the Mytharchive has a problem to create the config and log files because it doesn't have write permission at that location.

I tried to create a temp location at different places like /usr/share/myth.... and /home/userme/temp  this doesn't work.
I tried chmod'ing the directories and chown'ing to mythtv user but still it didn't work.  I need some advise what to try next.

---

### Post by AlecJ on 2009-05-22
Nothing new, one solution is to delete .ICEauthority and add the delete line to the script as this thread shows
[http://ubuntuforums.org/showthread.php?p=6320530](http://ubuntuforums.org/showthread.php?p=6320530)

And for now it the best on offer,, anybody???

---

### Post by DominicF on 2009-05-24
okay, I fixed it.

I created a new directoy:

mkdir /home/<user>/temp

Changed permissions:
sudo chmod 775 temp

Changed owner and group to mythtv:
sudo chown mythtv:mythtv temp

That was it.

---

