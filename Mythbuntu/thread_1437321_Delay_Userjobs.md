---
title: "Delay Userjobs"
date: 2010-03-23
forum: Mythbuntu
---

### Post by zuixro on 2010-03-23
I have a userjob that edits the commercials out of recordings. It needs to run after the recording has been transcoded and commercial flagged, but because I have two backends it tries to edit out the commercials while it's transcoding and causes bad things to happen. If I could set it to defer "Commercial Removal" for an hour, that would do it. The only option like that is for transcoding, and is set to one day. 

I could add a one hour delay to the beginning of the script, but that would delay all of the jobs in the queue. 


Anybody have an ideas?

---

### Post by SiHa on 2010-03-24
I'm assuming that the Transcode, Mythcommflag and your user job are all called with the same parameter to define which file is to be worked on?

You could add a line at the beginning of the script which checks for the transcode or mythcommflag process running, for the same filename that has been passed to the user job, something like (assuming the filename is passed as the first parameter, $1:```
ps ax|grep -v grep|grep nuvexport mythcommflag|grep $1
```
If the above is true then either nuvexport or mythcommflag is running on your file, so your script could sleep 1 minute then check again.

Now, I'm no expert on 'ps ax'.(I generally use 'ps -A' so you don't get the full commandline that the script was called with), so you may get false hits, but it's what I'd try.

Edit: Sorry, maybe replace 'nuvexport' with 'mythtranscode'!

---

### Post by zuixro on 2010-03-24
That's what someone on IRC suggested. I'm gonna try that out a and see how it goes. I really wanted a way that wouldn't delay the whole queue though. I guess it would only really happen at the beginning of a big recording session. The script I'm using transcodes, but it doesn't use the right profile. I'll try what you suggested, thanks.

---

### Post by zuixro on 2010-03-24
Grr that's not gonna work. I have 3 different backends, so I'd have to check across all of them. Now I'm thinking I'll have the script pull the status page from the master backend, then I'll parse the xml file and see if there is a job running on the file. We'll see how that goes.

---

