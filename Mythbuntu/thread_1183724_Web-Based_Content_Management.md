---
title: "Web-Based Content Management?"
date: 2009-06-10
forum: Mythbuntu
---

### Post by KevinFWB on 2009-06-10
I have a standalone Mythbuntu system hooked up in my living room with no keyboard or mouse hooked up to it, just the MCE remote.

I mapped a network drive to the Mythbuntu machine to transfer content, but I'm looking for an easy way to manage the content metadata.  Editing the data using the remote isn't entirely intuitive or practical.  

Has anybody created a web-based portal to edit the database information?  It wouldn't be entirely difficult for me to write this myself but there is no reason to duplicate work if this is already done.  I've played with MythWeb but it doesn't allow me to edit/delete any of the data.  It would be so much easier to just log into a web page and edit the info from another computer.

-Kevin

---

### Post by tgm4883 on 2009-06-10
Strange that mythweb wouldn't let you edit the metadata.  Are you talking about the metadata in mythvideos or the tv show metadata. 

AFAIK, there isn't any other interface to edit any of that. You could use phpmyadmin I guess.

---

### Post by KevinFWB on 2009-06-10
I'm mainly referring to the videos/music and not TV shows.  I set up a nearly identical setup for my brother-in-law and he's not technically inclined enough where phpMyAdmin would be a viable option.  

I'm working on creating a web-interface.  I just wanted to see if it's been done already.

---

### Post by crez79 on 2009-06-11
Music metadata comes from the tags of the files, so as long as the tags are correct, so should mythmusic. 

You can use mythweb to edit the metadata on the video files using http://<serverip>/mythweb/video and clicking on edit on the video you want to edit. It doesn't allow for the easy bulk editing of metadata, but it does allow for a relatively painless way to edit each individual video.

---

### Post by KevinFWB on 2009-06-11
Thanks - I finally got MythWeb to work. I had some path problems that was causing the problem.  

My last question: Is there a way to delete movies and/or music using a web interface?

---

