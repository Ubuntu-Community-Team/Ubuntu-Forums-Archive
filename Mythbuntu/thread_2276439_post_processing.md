---
title: "post processing"
date: 2015-05-02
forum: Mythbuntu
---

### Post by kaudley on 2015-05-02
What are you all using for post processing scripts?

I'd like to shrink the recording keeping the hd quality - rename to something sane with episode and title names and then move to another folder for something like plex to recognize with commercials removed.

I'm recording OTA 1080i with and HD Homerun extend.  I'm fine to go to 720P but would like my file sizes to go from ~8GB to ~1GB

---

### Post by blm-ubunet on 2015-05-06
Broadcast HD material is already highly compressed.
Transcoding here is just a waste of time on a core2duo.
I remove commercials on "keepers" or make clips of things with TS file cutting script that uses MythTV cutlist editor etc.
Is as fast as file copy but must allow for A-V packet offset in file.

There's a script "mythlink" which makes a folder of symlinks to your actual recordings but with user configurable names.
You can de-reference copy the link & get a file with human readable name. This should be good with DLNA etc.

---

