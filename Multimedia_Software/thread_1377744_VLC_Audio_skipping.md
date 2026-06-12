---
title: "VLC Audio skipping"
date: 2010-01-10
forum: Multimedia Software
---

### Post by motonnerd on 2010-01-10
I've installed VLC on Windows, XUbuntu, Ubuntu, and Puppy Linux.  I don't remember any skipping problems with Windows or Puppy Linux, but VLC will skip and jump with the slightest provocation in Ubuntu, and in XUbuntu it did the same (XUbuntu was upgraded to 9.10, and I think the problem persisted, but I don't remember for sure.  (Current Ubuntu VLC was installed through the Ubuntu Software Center.

My system should be fast enough, it is certainly with everything else, and it did it with Windows.  So I today went into VLC's advanced settings and enabled realtime priority (previously I just tried to get it to raise it's priority in XUbuntu, which never seemed to do anything).  But after that, I got an idea and went in to increase the caching, from 300ms to 1000ms, which has mostly resolved the issue but it still skips noticeably every so often, I'll try to log the occasions it does here, if I can pin down what it is.

Summary: it skips on CD's and files, but not when streaming from the Internet.  Increasing the caching from 300ms to 1 sec seems to have helped.  The files are normal mp3's, mp4's, (of average bitrates) and occasionally .wav's at CD quality. Video seems to be the same.

Both examples are from non-Unix filesystems (NTFS for XUbuntu and FAT32 for Ubuntu), but as I wrote this I tested it by playing a file from my desktop, same thing.

Does anyone have any idea what is going on?

(PS played with the caching using and m4p file and couldn't get any significant difference between 600, 1000, 1500, and 2000ms of caching, further testing required)
Any help is appreciated!

---

