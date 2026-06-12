---
title: "Podcasts download failure"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by TracyO on 2007-11-12
First off, I'm totally new to Ubuntu and Linux.  I'm trying to get my podcasts back, as I just made the switch, but they fail each time I try to download them.  I've heard that "writing permission" could be part of the issue, but I don't have any idea how to do that as of yet.   My default music folder is in the home folder, so ideally, they should be going there.

Any kind, knowledgeable souls willing to help?

Thanks in advance!
Tracy

---

### Post by avik on 2007-11-12
What do you mean "fail?"  Where are you downloading the podcasts from, and where are you downloading them to?  What are you using to download them?

---

### Post by TracyO on 2007-11-12
I download them using Rythmbox and the URL (from NPR).  It gets through the download, but at the end says "Failed."

---

### Post by ShogunMaster06 on 2007-11-12
I'm having the exact same problem.  It started with Miro Player all the sudden.  I thought it was a Miro issue so I installed gPodder and Banshee but they (along with Rhythmbox) will not download podcasts.  They all just say the podcast failed.  I'm not sure where to look for logs for these problems in order to determine what is happening.

I'm using Gutsy.

---

### Post by TracyO on 2007-11-12
For clarification purposes, I'm on Gusty as well.

---

### Post by paradoxni on 2007-11-20
im having podcast fail messages too, here is an example:

Ive added [http://www.stuff.tv/rss/podcast.xml](http://www.stuff.tv/rss/podcast.xml) to rythmbox and it seems to pull in the feeds ok, but when one episode reaches 100% it then says failed and will not play.

If however I goto my Home folder there is a Stuff.tv podcast folder with the MP4 podcast inside it, it will not play in Totem, giving a gstreamer error, but if i open the file with VLC player it plays the podcast fine. I do notice however that altthou its an mp4 audio file it seems to have a video track included with a few pictures in it, so I think perhaps the stream format is not readible by gstreamer/totem/rythmbox because of the included video stream.

I have added a BBC Radio 1 podcast ([http://downloads.bbc.co.uk/podcasts/radio1/moylesen/rss.xml](http://downloads.bbc.co.uk/podcasts/radio1/moylesen/rss.xml)) which only contains audio within an MP4 and it plays fine in Rythmbox.

---

### Post by TracyO on 2007-11-20
Thanks for the advice.  I tried it, but when I got to downloading VLC in the Synaptic Package Manager, it kept saying that the file or program was dependent on other files that were uninstallable, etc.  I'm realizing that there is something more to the problem because I can't download codecs either.  My system keeps cycling through things--completing them up to the point of working but starting over again and again.  If you have any ideas about this problem, I'd love to hear 'em!  

In any case, thanks for the help!  If I ever get this other thing fixed, that'll be a great program later on.
Tracy

---

### Post by tpmevec on 2007-11-26
You are missing the extra applications needed to run MP3 files.

1 - Launch Add/Remove...
2 - Change Show in the upper right corner to All available applications
3 - Look for Ubuntu restricted extras and check it
4 - Click Apply changes
5 - Re-launch your audio app and it should now download and play MP3 files.

Hope this helps. :)

---

### Post by TracyO on 2007-11-29
Thank you again!  The problem was solved just before you answered.  I was having difficulty downloading podcasts, but I was having trouble with codecs and packages, too.  This is what ended up fixing the problem:


But, go to System - Administration - Software Sources, and on the first
tab (Ubuntu Software), check off everything except the source code.

Then in the terminal do:

sudo apt-cache search ubuntu-restricted-extras

And you should get three packages like I did:

vadi@vadi-laptop:~$ sudo apt-cache search ubuntu-restricted-extras
[sudo] password for vadi:
kubuntu-restricted-extras - Commonly used restricted packages
ubuntu-restricted-extras - Commonly used restricted packages
xubuntu-restricted-extras - Commonly used restricted packages


If you do, try sudo apt-get install ubuntu-restricted-extras once again.

Thank you to all who helped!
Tracy

---

