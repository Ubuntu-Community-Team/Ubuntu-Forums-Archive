---
title: "How to capture CNN.com videos?"
date: 2013-04-03
forum: Multimedia Software
---

### Post by Marcus Aurelius on 2013-04-03
I have download helper in Firefox browser.  It works fine for most things.  When I go to CNN to watch their videos, it shows the download file .flv with the proper name of the video, but the file size is 2 GB!  Obviously this is not correct for a short video.  
Is there anyone who has tried to capture a short video (any video) off CNN using Ubuntu and had success?  I've read tutorials where lots of software are thrown up as suggestions including download helper, but it doesn't seem to work properly. 
Any positive personal experiences?
Thanks

---

### Post by dabl on 2013-04-03
18 hours --- nothing.   :(     Here's my crude approach -- undoubtedly posting it will induce 27 more expert replies.

Find your browser cache directory. Typically they are in your home folder in a "hidden" directory, like ~/.mozilla/Cache or ~/.chromium/Cache.  You will know it because it is full of files that look like "f_00000e", if you've been playing videos.  At the directory prompt, and with nothing playing in your browser, issue "rm *" to delete everything in that folder.

Now, with your terminal still open on the cache directory, start your CNN video in your browser.  In the terminal, issue "ls -la" and note that there is a single file that looks like the ones you deleted.  Note the size of it.  Issue "ls -la" again, and again note the size of the file.  Wait 15 seconds, and issue "ls -la" again, and again note the size of the file.  Rinse and repeat.  At some point after not very long, you will notice that the file is no longer changing its size.  That's when you know the entire video has downloaded.  Now, cd to your home folder, and "cp /home/marcus/.mozilla/Cache/f_* ." to copy the entire video to your home folder where you can work on it.

If you haven't got it, install the libav-tools package.

To determine the encoding used to make the video, issue this command, substituting your captured file for "name":

```
avconv -i name
```

With that information, google will lead you to guidance on how to strip out the audio, if that's what you want, or how to convert it to .avi if you wish.

---

### Post by QIII on 2013-04-03
Closed for Staff review.

If this is in violation of EULAs, TOSs or copyright we do not support such discussions on the Forums.

Reopened after review.

---

### Post by Pinoy Tux on 2013-04-05
> **QIII said:**
> Reopened after review.

So how does this thread (or CNN videos for that matter) any different from the YouTube policy?  I mean even if they're different websites, the principle of prohibiting discussions on downloading copyrighted content is still the same, isn't it?

Just asking. :confused:

---

### Post by Elfy on 2013-04-05
> **Pinoy Tux said:**
> So how does this thread (or CNN videos for that matter) any different from the YouTube policy?  I mean even if they're different websites, the principle of prohibiting discussions on downloading copyrighted content is still the same, isn't it?

Just asking. :confused:

CNN ->  3. Copyright Ownership.
CNN.com contains copyrighted material, trademarks and other proprietary information, including, but not limited to, text, software, photos, video, graphics, music and sound, and the entire contents of CNN.com are copyrighted as a collective work under the United States copyright laws. CNN owns copyright in the selection, coordination, arrangement and enhancement of such content, as well as in the content original to it. You may not modify, publish, transmit, participate in the transfer or sale, create derivative works, or in any way exploit, any of the content, in whole or in part. **You may download copyrighted material for your personal use only. **Except as otherwise expressly permitted under copyright law, no copying, redistribution, retransmission, publication or commercial exploitation of downloaded material will be permitted without the express permission of CNN and the copyright owner. In the event of any permitted copying, redistribution or publication of copyrighted material, no changes in or deletion of author attribution, trademark legend or copyright notice shall be made. You acknowledge that you do not acquire any ownership rights by downloading copyrighted material. 

Youtube - > With the exception of Content submitted to the Service by you, all other Content on the Service is either owned by or licensed to YouTube, and is subject to copyright, trade mark rights, and other intellectual property rights of YouTube or YouTube's licensors. Any third party trade or service marks present on Content not uploaded or posted by you are trade or service marks of their respective owners. **Such Content may not be downloaded, copied, reproduced, distributed, transmitted, broadcast, displayed, sold, licensed, or otherwise exploited for any other purpose whatsoever without the prior written consent of YouTube or, where applicable, YouTube's licensors.** YouTube and its licensors reserve all rights not expressly granted in and to their Content. 

Anymore discussion of this should take place elsewhere - not in this thread. Thanks.

---

### Post by Pinoy Tux on 2013-04-05
> **Elfy said:**
> ...
Thanks for the clarification.  I was just surprised this one was re-opened when these kinds of threads are usually locked or removed.

Moving forward.

---

