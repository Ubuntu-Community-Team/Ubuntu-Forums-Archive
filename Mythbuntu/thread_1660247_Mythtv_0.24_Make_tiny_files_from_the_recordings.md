---
title: "Mythtv 0.24 Make tiny files from the recordings?"
date: 2011-01-05
forum: Mythbuntu
---

### Post by Archmage on 2011-01-05
I did managed to install MythTV 0.24 from the Mythbuntu-PPA-repos on my Ubuntu 10.04 machines and it seems to work flawless (beside the beta MythNetvision – but I guess that it seemed to be expected)

But now I’m wondering if there is an easy way after a recording had been finished to make a very small copy (keep the original file) and move this copy to a different folder?

I guess that it should work with the additional jobs that can be performed after one recording, but I’m clueless what I can insert there. I even don’t know what convert I have installed.

I’m hoping that someone can tell me what magic formula I must type in there to get files that will make files with round about 150 MB for 1 hour. I don’t care if it will take a whole day to convert it, I don’t care about what codec I’m using, I just hope that someone can help me to get the best quality with this extreme small filesizes.

---

### Post by ian dobson on 2011-01-05
Hi,

By "make tiny files", you mean transcoding. Mythtv can transcode a recording through a job. Your goal of about 150mb per hour is not much. The only thing I can think of is if you can transcode the video to a format thats compatible with a portable device (Nintendo DS,Portable phone etc). That'll produce 320x200 pixel 
x264 files.

My assistant has just told me that he's transcoded a normal DVB-T film for a Nintendo (For his children) and got about 150Mb per Hour. He thinks he used handbrake to transcode.

Regards
Ian Dobson

---

### Post by bcg30506 on 2011-01-06
Archmage, I'm more interested in the process you did to get 0.24 running on a 10.04 mythbuntu box.  I've been pondering this for quite some time.  I currently have a running mythbuntu 10.04 combination backend/frontend running 0.23.1-fixes and thought to get to 0.24 of mythtv I'd have to upgrade the OS to 10.10.

---

### Post by thatguruguy on 2011-01-06
> **bcg30506 said:**
> Archmage, I'm more interested in the process you did to get 0.24 running on a 10.04 mythbuntu box.  I've been pondering this for quite some time.  I currently have a running mythbuntu 10.04 combination backend/frontend running 0.23.1-fixes and thought to get to 0.24 of mythtv I'd have to upgrade the OS to 10.10.

I'm running a backend/frontend combo on a mythbuntu 10.10 box with myth .24, and running the myth .24 frontend on two remote computers, both of which are running ubuntu 10.04.  You add the .24 packages to 10.04 the same way you do in 10.10; simply enable the correct repository and upgrade your packages.

---

### Post by tgm4883 on 2011-01-06
> **thatguruguy said:**
> I'm running a backend/frontend combo on a mythbuntu 10.10 box with myth .24, and running the myth .24 frontend on two remote computers, both of which are running ubuntu 10.04.  You add the .24 packages to 10.04 the same way you do in 10.10; simply enable the correct repository and upgrade your packages.

[http://mythbuntu.org/repos](http://mythbuntu.org/repos)

---

