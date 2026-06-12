---
title: "Cannot Transfer Whole Directories in gFTP"
date: 2012-07-07
forum: Networking &amp; Wireless
---

### Post by SillySod on 2012-07-07
I'm having trouble trying to transfer whole directories using gFTP.  If I select several items, which are all directories, from the "local" window then press the transfer button, I get the following error message:

"Cannot create a file when that file already exists"

The file it refers to is the directory itself, which of course already exists on the remote site because I am uploading updated files into it!

Is there a way round this?  Otherwise I have to go into each directory on the local and remote windows, select all the files in the directory on the local window then press transfer, and repeat this for as many directories as I need to update (sometimes 50 or more!!)

---

### Post by Paddy Landau on 2012-07-08
I don't know gFTP, but I know that [FileZilla]("apt:filezilla") works perfectly for this.

---

### Post by SillySod on 2012-07-08
Brilliant, I am converted to Filezilla!

I just selected the whole of my website from the local copy and dropped it into the remote window and chose "Overwrite newer or size different" and it updated everything (over 20,000 files to work through) in about 10 mins!

I can do this every time I write an update now, instead of having to trawl through all my local directories and upload them one-by-one.  No more risk of forgetting to upload something!

---

### Post by Paddy Landau on 2012-07-09
Yes, I love FileZilla. I've been using it for years. It's also cross-platform, which is good for some people.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

