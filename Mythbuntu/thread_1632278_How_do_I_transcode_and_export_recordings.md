---
title: "How do I transcode and export recordings?"
date: 2010-11-27
forum: Mythbuntu
---

### Post by itlarson on 2010-11-27
I am trying to transcode high-def programs to be played on a laptop, but can't figure out where to start.  In the program menu under "job options" there is a "begin transcoding" option, but this doesn't seem to do anything.  Is there a way to get this working?  And then, is there a way to export the program to a thumb drive?

---

### Post by winewood on 2010-11-27
You don't have to trancode anything to get it to work.
 
 
 
I simply use mythweb via http.  Put the IP of the mythbackend in a browser, or use the name "mythweb".  
 
Find the program under recorded programs and click on the green icon (watch).  The laptop will play the asx file using whatever is accociated.  If you have VLC, it will work and play.
 
If you wish to download it, under the green icon there is a white icon.   Click on it, and it will download the program in its entirety to a file on your target machine to a file labled with the program name.
 
The only downside, is there are commercials still present and they are at default size.

---

### Post by itlarson on 2010-11-27
Mythweb looks like it will work great for file transfer.  I have never really messed with it, and didn't realize it could do that.  I definitely need to transcode, though for file size.  Is there a way to get it working?

---

### Post by winewood on 2010-11-28
Altough I have not used transcoding...
 
I have seen options that will allow you to determine what size of files you can do.. ie. compression, and these transcodes can honor your commercial flags when they operate as well.   
 
I found this:
[http://ubuntuforums.org/showthread.php?t=346778](http://ubuntuforums.org/showthread.php?t=346778)
 
I would advise to read it all.  Once you read it, decide what direction/option you want.  This will allow you not to get overwelmed, and you can only do the steps you need.  There is a lot to consider when transcoding, especially on a low end processor, as it takes a lot of CPU time.  
 
cheers!

---

### Post by itlarson on 2010-11-28
That thread is awfully old-  is it really necessary to compile stuff to get this working?  The transcode options are built right into mythtv, isn't there just some setup thing I can do to get them working?  Besides, I know mythtv can transcode to make a DVD, and the lowest setting might be fine for what I want to do. I just don't want to burn it to a DVD.

---

### Post by laffinet on 2010-11-29
I transcode some of my recordings to mkv using the mythnuv2mkv script [here]("http://web.aanet.com.au/~auric/?q=node/6"). This can be set up as a user job which then appears under the "job options" context menu in myth.
Honours cut lists too.
A little bit of set up work to start with (not much really), but then it's as simple as selecting the job for a recording and away you go. Depending on the quality settings the reduction in size can be quite big.

---

