---
title: "Archiving series episodes"
date: 2015-02-21
forum: Mythbuntu
---

### Post by hollywoodpete on 2015-02-21
I have been using mythbuntu backend on a headless server with multiple different frontends but mostly Kodi. I am fairly happy with my setup but want to take one big step further to make the backend more functional. I would like to have my backend transcode the recorded episodes and store them in a Samba share file that I can access from my NAS. Oddly the default Samba workgroup was MSHome. Since I don't have any Window computers and have already been using workgroup as my workgroup I changed that in the default /etc/samba/smb.conf.  I created a folder 'recordings" and allowed access to the appropriate users. What would be the best way to have MythTV drop episodes into this file labeled "title SxxExx.mkv or .avi?

---

### Post by hollywoodpete on 2015-02-23
Well I didn't figure it out exactly like I wanted to but I made it functional with MythWeb. and Direct Download. I added some addons on the backend (noy 100% sure which ones) and then log into the server from a remote client using Myth Web. Mythweb>Recorded Programs>"show title I'm looking for">Direct Download and then it is downloaded into the download folder of the client as "show name".mpg SSxEE. Good enough for now

---

